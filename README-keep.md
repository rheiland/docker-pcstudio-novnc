# PhysiCell Studio noVNC Container
This image is used to display the PhysiCell Studio (a PyQt5/X11 GUI) from other containers in a browser. 

## Usage
First, build the two required images, e.g.:
```
docker build -t pcstudio-novnc .  # in its own repo
```

and
```
docker build -t theasp/novnc .    # using the Dockerfile in this repo
```
then run:
```
docker compose up    # -d
```
* See `docker-compose.yml` for details.

### Variables

You can specify the following variables:
* `DISPLAY_WIDTH=<width>` (1024)
* `DISPLAY_HEIGHT=<height>` (768)
* `RUN_XTERM={yes|no}` (yes)
* `RUN_FLUXBOX={yes|no}` (yes)

Open a browser and see the demo at `http://<server>:8080/vnc.html`

Some notable features:
* An `x11` network is defined to link the IDE and novnc containers
* The IDE `DISPLAY` environment variable is set using the novnc container name
* The screen size is adjustable to suit your preferences via environment variables
* The only exposed port is for HTTP browser connections

**If the Studio fails to start, try `docker compose restart <container-name>`.**

___

# Thanks

* DockerHub [theasp/novnc](https://hub.docker.com/r/theasp/novnc/)
* GitHub [theasp/docker-novnc](https://github.com/theasp/docker-novnc)
___
This is based on the alpine container by @psharkey: https://github.com/psharkey/docker/tree/master/novnc
Based on [wine-x11-novnc-docker](https://github.com/solarkennedy/wine-x11-novnc-docker) and [octave-x11-novnc-docker](https://hub.docker.com/r/epflsti/octave-x11-novnc-docker/).
