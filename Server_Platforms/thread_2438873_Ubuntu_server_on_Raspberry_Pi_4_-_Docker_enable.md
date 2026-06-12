---
title: "Ubuntu server on Raspberry Pi 4 - Docker enable"
date: 2020-03-19
forum: Server Platforms
---

### Post by vawaver on 2020-03-19
Good evening,
I'm trying to run a Home Assistant docker on Ubuntu server 18.04.4 that I have installed on Raspberry Pi 4. I used Berryboot + server image from here [https://berryboot.alexgoldcheidt.com/search-downloads/?dl_cat=0&dl_search=LTS](https://berryboot.alexgoldcheidt.com/search-downloads/?dl_cat=0&dl_search=LTS)
After that I installed Docker via Snap and then docker.io

Problem is that I cannot enable docker.

```
root@ubuntu:/home/tony# docker version
Client:
 Version:           19.03.6
 API version:       1.40
 Go version:        go1.12.17
 Git commit:        369ce74a3c
 Built:             Fri Feb 28 23:48:23 2020
 OS/Arch:           linux/arm
 Experimental:      false
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```

```
root@ubuntu:/home/tony# docker stats
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```

Can you please help me how to solve it?
Thank you.

---

