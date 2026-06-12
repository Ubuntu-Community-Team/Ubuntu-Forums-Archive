---
title: "Rootles podman and serial devices"
date: 2024-04-10
forum: Ubuntu Development Version
---

### Post by NachoMas on 2024-04-10
Hi all,
I'm trying to run a podman container in a dedicated rootless account and the container needs access to a serial port (/dev/ttyACM0) but I am unable to make it work. I've been surfing all around trying to find an answer but so far I cannot find how to enable the rootless container to access the port. 

I am starting the container like this:

podman run --name=zwavejs --group-add keep-groups --userns=keep-id --replace  -it -p 192.168.1.2:8091:8091 -p 192.168.1.2:3000:3000 --device=/dev/ttyACM0:/dev/zwave -e TZ="Europe/Stockholm" -v /etc/timezone:/etc/timezone:ro -v /etc/zwavejs:/usr/src/app/store --label io.containers.autoupdate=registry docker.io/zwavejs/zwave-js-ui:latest

wich works as root but not as the dedicated podman user. The dedicated podman user (id=podman) is a member of the dialout group and the permissions of /dev/ttyACM0 are as follows:

podman@calixto:~$ ls -la /dev/ttyACM0 
crw-rw---- 1 root dialout 166, 0 Apr 10 14:05 /dev/ttyACM0

I assume I must have some problem with AppArmor and the only thing I find online is how to fix SELinux, which I do not have in my server.

Anyone with some hints on how to make it work?

Thanks!

---

