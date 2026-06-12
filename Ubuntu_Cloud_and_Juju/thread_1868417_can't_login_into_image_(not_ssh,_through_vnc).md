---
title: "can't login into image (not ssh, through vnc)"
date: 2011-10-24
forum: Ubuntu Cloud and Juju
---

### Post by MCVIC on 2011-10-24
Hello to everybody !

I'm setting up UEC on ubuntu 11.04

and have a problem :

I'm not able to ssh to running instance because of "permission denied (public key)" error,so I connect to instance through vnc to fix this issue, but I can't login with username: ubuntu password: ubuntu ..(password incorrect) Could anybody help ?

I tried two images from 
[http://uec-images.ubuntu.com/releases/karmic/beta/ubuntu-uec-karmic-amd64.img.gz](http://uec-images.ubuntu.com/releases/karmic/beta/ubuntu-uec-karmic-amd64.img.gz)
and
[http://uec-images.ubuntu.com/releases/karmic/beta/ubuntu-uec-karmic-i386.img.gz](http://uec-images.ubuntu.com/releases/karmic/beta/ubuntu-uec-karmic-i386.img.gz)

PS

instances are up and running I can ping them .


Thanks

---

### Post by nosmadar on 2011-11-15
Regarding the public key error.  Try logging into the server with the same user and then try the ssh connection. If ssh works now, then see if the .ssh directory is in /home/<user> when perhaps it should be in root ("/").  At least that was the problem I had with this symptom.

---

