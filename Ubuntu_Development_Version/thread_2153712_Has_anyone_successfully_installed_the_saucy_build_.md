---
title: "Has anyone successfully installed the saucy build of Ubuntu touch?"
date: 2013-06-12
forum: Ubuntu Development Version
---

### Post by z3nhakr on 2013-06-12
I have successfully installed raring on my nexus 10 by flashing the zips with TWRP recovery. When try the same thing with saucy it does not boot but instead reboots immediately after displaying the Google boot logo. I was able to boot one of the first saucy builds by install it with the device specific files from raring but the WiFi and sound didn't work. On the recent builds this method leaves me with a blank screen. How can I get saucy running?

---

### Post by grahammechanical on 2013-06-12
Ubuntu touch Saucy ISO images are found here

[http://iso.qa.ubuntu.com/qatracker/milestones/270/builds](http://iso.qa.ubuntu.com/qatracker/milestones/270/builds)

You know more about the practical things of installing Ubuntu touch than I do. I have never tried it. So, this is the best that I can give you.

Regards

EDIT: found this. It is good news.

[https://lists.launchpad.net/ubuntu-phone/msg02176.html](https://lists.launchpad.net/ubuntu-phone/msg02176.html)

---

### Post by oldos2er on 2013-06-12
Moved to Ubuntu +1

---

### Post by z3nhakr on 2013-06-13
UPDATE:

The developers preview has now been moved to saucy. I'm gonna try the device specific file from the preview and the the image from the non preview and see if i can get it working as a daily driver. will post back after i try it.

BTW checkout this good news:
[https://plus.google.com/u/0/102351181217041965310/posts/MepsJtV7xNy](https://plus.google.com/u/0/102351181217041965310/posts/MepsJtV7xNy)

And the XDA thread following ubuntu touch:
[http://forum.xda-developers.com/showthread.php?t=2078727&highlight=ubuntu+touch+saucy&page=85](http://forum.xda-developers.com/showthread.php?t=2078727&highlight=ubuntu+touch+saucy&page=85)

---

### Post by z3nhakr on 2013-06-13
UPDATE: good news! [Saucy]("http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/") has the containers flipped so instead of ubuntu being a chroot in android, android is now in an lxc container in ubuntu. Acording to [this]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-June/037242.html") it works on Maguro and Mako but doesn't work on Grouper and Manta is not tested...I tested it and it doesn't work on manta yet.

---

