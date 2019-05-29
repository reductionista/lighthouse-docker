# Lighthouse Testing Environment

A `docker-compose` environment providing a network of beacon node/validator
clients monitored by a Prometheus/Grafana setup.

## Usage

### Requirements

- `docker`
- `docker-compose`

E.g., on Arch: `$ pacman -S docker docker-compose`

### Bringing the Environment Up

```
$ docker-compose up
```

### Interfaces

- View and manage dashboards at [localhost:3000](http://localhost:3000).
- Inspect Prometheus at [localhost:9090](http://localhost:9090).


## Notes

### Volumes

Both Promethus and Grafana persist their data using docker volumes. `$
docker-compose stop` (or `ctrl+c` on a foreground process) will _not_ delete
volumes, whilst `$ docker-compose down` will remove containers and volumes.

### Persisting Dashboards

The [`grafana/built-in-dashboards`](grafana/built-in-dashboards) directory may
contain dashboard JSON files (as exported from the UI) that will be provisioned
to all new installations. Otherwise, dashboards are stored in your local
volumes, won't be available to others and will be deleted when local docker
volumes are removed.