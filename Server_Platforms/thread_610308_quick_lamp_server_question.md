---
title: "quick lamp server question"
date: 2007-11-11
forum: Server Platforms
---

### Post by mrblue182 on 2007-11-11
I want to install a lamp server, then put drupal on top of it, just so I can experiment with it. I'm new to developing on the internet, so would installing lamp make my computer accessible via ip address. I don't want my server put on the internet, just something i can screw around with.

---

### Post by scxtt on 2007-11-11
if you install openssh-server you can connect to the server from an ssh client, and if you don't forward port 22 from your router to the LAMP server's IP - the rest of the internet can't touch it ... LAMP doesn't really have anything to do w/ the accessibility ...

L=linux
A=apache
M=mysql
P=php

---

### Post by maxbear on 2007-11-12
You can have a look of this guide, teach you how to setup lamp server, setup a gui for server edition and also how to install webmin.

[http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html](http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html)

---

