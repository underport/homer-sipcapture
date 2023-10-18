<img src="https://user-images.githubusercontent.com/1423657/55069501-8348c400-5084-11e9-9931-fefe0f9874a7.png" width=150/>

# HOMER + Grafana + Prometheus + Loki

<img src="https://i.imgur.com/Atdig3X.gif" width=500>

--------

## Setup

```bash
docker-compose up -d
```

to bring up:  

* [Homer]        localhost:9080 (admin/sipcapture)
* [Grafana]      localhost:3000 (admin/admin)
* [Prometheus]   localhost:9090 (admin/admin)
* [Loki]         localhost:3100 (admin/admin)
* [Alertmanager] localhost:9093 (admin/admin)

When the Grafana dashboard autoprovisioning does not work for you make sure you have no old grafana volumes.

## Configuration

When you change some files inside the Prometheus or Alertmanager folder you can reload them without interruption.

#### Prometheus
```bash
curl -s -XPOST localhost:9090/-/reload -u admin:admin
```

#### Alertmanager
```bash
curl -s -XPOST localhost:9093/-/reload -u admin:admin
```

#### Service
When you need to change the docker-compose file i.e to setup smtp for Grafana:
```bash
docker-compose up -d
```
Docker will only restart the service you changed inside the docker-compose file. 

#### Reinstall, Reset
To reset and cause db provisioning, simply empty out the `bootstrap` file
```
echo "" > ./bootstrap
```


SOURCE: [GITHUB SIPCAPTURE](https://github.com/sipcapture)