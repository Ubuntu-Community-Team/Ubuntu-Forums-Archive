---
title: "CMAN - GFS related problems"
date: 2007-01-25
forum: Server Platforms
---

### Post by trandism on 2007-01-25
I'm trying to setup GFS2 in edgy eft with kernel 2.6.17-10-server 

i did an apt-get install of gfs-tools, cman, redhat-cluster-suite etc. etc., prepared a cluster.conf following various howtos on the internet.

Problem is when i try to /etc/init.d/cman start

It says that module dlm_device is not found.. 

I have understood that the cman package's gonna change in feisty and it won't need dlm_device anymore, correct me on that if i say BS..

Anyways, i'll be grateful if someone can offer a work-around on this

Alternatively it'll be great if anyone can provide some pointers (links) to documentation regarding GFS or any other clustering storage solution that will work under ubuntu

I'm coming from a 3-day googling session trying to find a storage clustering solution  to set up here and i'm kinda overwhelmed up to now

Thanks in advance

Nikos Sarakenidis
Athens, Greece

---

