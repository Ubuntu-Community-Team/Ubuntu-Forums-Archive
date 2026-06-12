---
title: "Ubuntu Minimal Size Discrepancy"
date: 2020-12-17
forum: Virtualisation
---

### Post by mstarks01 on 2020-12-17
[This]("https://ubuntu.com/blog/minimal-ubuntu-released") blog post states that the base Docker image is 29MB. It also links to the releases page where it can be downloaded. However, if I look at the Ubuntu 18.04 minimal page [here]("https://cloud-images.ubuntu.com/minimal/releases/bionic/release/"), the smallest compressed image is [COLOR=#000000]83M. Installed in an LXC container, it comes in at 425MB. Does anyone know where I can get the ~29MB version so that I can build my own container with the smallest base size possible?[/COLOR]

---

### Post by deadflowr on 2020-12-17
Docker images are expected to be pulled from docker's image repository hub.
See: [https://hub.docker.com/_/ubuntu?tab=tags&page=1&ordering=last_updated]("https://hub.docker.com/_/ubuntu?tab=tags&page=1&ordering=last_updated")
For a list of available images.
follow the command
```
docker pull ubuntu
```
add the :XXXX version to whichever version you want to install.
(as shown in the listing per release image.)

---

