# docker-newman

This image runs newman 3.3.0 on node 4.6.2 on Alpine 3.4.

This image does not have an entrypoint so it is usable in GitLab CI.

## Build image

Build the image by running:

```terminal
docker build -t rovecom/newman .
```

## Pull image

You can get it from [docker hub](https://registry.hub.docker.com/u/rovecom/newman)

```terminal
docker pull rovecom/newman:3.3.0
```

## Run the image

For newman to be able to use collections and environment files saved on the host machine, and to save reports generated by newman, a directory containing the collection and environment files needs to be mounted on to the docker instance at `/work`, which is the default working directory.

```terminal
docker run -v ./collections:/work rovecom/newman newman run mycollection.json --reporters cli,html --reporter-html-export newman-report.html
```

In case you don't need to save newmans report to the host, and your collection is available online and it does not require any environment, then you can directly pass the collection url to newman.

```terminal
docker run -t rovecom/newman newman run https://www.getpostman.com/collections/df0a40ef41d570c48154
```
