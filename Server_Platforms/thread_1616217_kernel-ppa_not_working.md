---
title: "kernel-ppa not working"
date: 2010-11-07
forum: Server Platforms
---

### Post by bitmonkey on 2010-11-07
Trying to update 10.04 to the latest natty kernel in the kernel-ppa (2.6.36 if I recall correctly) in order to unbreak iotop I did:

sudo apt-add-repository ppa:kernel-ppa/ppa
sudo apt-get update

then apt-get install linux-image-server-lts-backport-natty linux-headers-server-lts-backport-natty

About a couple of weeks ago this worked on 3 of my boxes, all running 10.04, now I've gone to do the fourth and it doesn't work any more - the package is not being seen. I've also tried linux-lts-backport-natty and it doesn't see that, even though that now shows up on the kernel-ppa page. 

What's up with it?

thanks

---

