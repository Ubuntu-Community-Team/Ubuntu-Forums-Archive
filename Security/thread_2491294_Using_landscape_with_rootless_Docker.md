---
title: "Using landscape with rootless Docker"
date: 2023-10-03
forum: Security
---

### Post by jimclark2 on 2023-10-03
[COLOR=#333333][FONT=&amp]I'd like to use Landscape to be able to graph web site activity from my rootless Docker containers. The following is the Bash script set up in Landscape and the error that is being generated. 

Even though the DOCKER_HOST and DBUS_SESSION_BUS_ADDRESS variables are set to the rootless Docker address and the script is being run under the user account that rootless Docker was installed under, Landscape seems to be trying to access Docker as if it were a normal rooted installation. Any ideas on how to get this to work correctly under Landscape?

Landscape script:
"
[/FONT][/COLOR]#!/bin/bash

DOCKER_HOST=unix:///run/user/1000/docker.sock
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus

cd /mydockerdir
docker compose logs --since 5m myapp | grep -a -i 'Completed 200 OK' | wc -l
"
[COLOR=#333333][FONT=&amp]
Landscape error:
InvalidFormatError: Failed to convert to number: 'Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running? 0 '

Thanks in advance for any and all help!

[/FONT][/COLOR]

---

