# fluentd-shipper
ship logs to fluentd instances running on hosts `fluentd[1-4]`, failed logs stored in `/var/log/fluent/forward/failed`

[![Docker Hub](https://img.shields.io/badge/docker-ready-blue.svg)](https://registry.hub.docker.com/u/waleedsamy/fluentd-shipper/)

#### run
```bash
  # run shipper in your machine first
  docker run \
    -d -p 24224:24224 \
    --add-host fluentd1:172.18.34.140 \
    --add-host fluentd2:172.18.34.141 \
    --add-host fluentd3:172.18.34.142 \
    --add-host fluentd4:172.18.34.251 \
    -e FLUENTD_OUT_PORT=24224 \
    --name fluentd \
    waleedsamy/fluentd-shipper

 # run your containers with fluentd log driver
 docker run --log-driver=fluentd -d -e NODE_ENV=tschuss -P waleedsamy/hello-world-expressjs-docker
```
