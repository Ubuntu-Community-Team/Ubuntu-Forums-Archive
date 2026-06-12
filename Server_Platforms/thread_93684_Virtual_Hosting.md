---
title: "Virtual Hosting?"
date: 2005-11-22
forum: Server Platforms
---

### Post by darkfro on 2005-11-22
I think this is a virtual hosting problem. I have Apache 2.x running on my Ubuntu 5.10 machine. What i'm trying to do is have a way for users to ftp to my box and have thier own storage space on the apache server. I want to be able to allocate only a certain amount of space to each person. Ex:

darkfro@ubuntubox: ftp 192.168.2.1
darkfro@ubuntubox: user: Darkfro
darkfro@ubuntubox: pass: *****
darkfro@ubuntubox: ls
darkfro@ubuntubox: index.html
                            welcome.gif
                            etc
                            cgibin

darkfro@ubuntubox: ftp 192.168.2.1
darkfro@ubuntubox: user: Mike
darkfro@ubuntubox: pass: ********
darkfro@ubuntubox: ls
darkfro@ubuntubox: Mikeindex.html
                            oldindex.html
                            video.avi
                            etc
                            cgibin 

Do you get the picture. I only want them to have a certain amount of space. And they can't exceed it.

---

### Post by casper_2095 on 2005-11-23
[http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html)

---

### Post by casper_2095 on 2005-11-23
[http://souptonuts.sourceforge.net/quota_tutorial.html](http://souptonuts.sourceforge.net/quota_tutorial.html)

---

