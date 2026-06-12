---
title: "Sound Driver mistakenly uninstalled"
date: 2011-01-14
forum: Ubuntu Studio
---

### Post by maddy_rox on 2011-01-14
Sorry if i'm posting in a wrong thread.. I'm completely new to this community and Ubuntu.

I had this trouble of both my headset and laptop in built speaker producing sound even though my headset is plugged in.

In solving that , i tried many things mentioned in the forum but couldn't resolve

I run this script alsa_setup_15.sh and it uninstalled my alsa driver...

now my sound preference doesn't show anything and there is no sound driver now to play the sound..

Pls help me out. If possible in an explanatory way as i'm yet to get used to all tech things in ubuntu

---

### Post by maddy_rox on 2011-01-14
[http://www.alsa-project.org/db/?f=17fec3e1ed45c94c3b7dc3e146c0ddf55ceeaa82](http://www.alsa-project.org/db/?f=17fec3e1ed45c94c3b7dc3e146c0ddf55ceeaa82)


This is the information i got...

---

### Post by maddy_rox on 2011-01-14
bounce

---

### Post by Pablo_F on 2011-01-14
Hi, 

Reinstall ubuntu from scratch. Then post the alsa-info script again and we will try to help you. Your system is completely broken at this point and it is very difficult to help you through forum posts.

Cheers! Pablo

---

### Post by maddy_rox on 2011-01-15
I fear to reinstall ubuntu as i've installed as a partition in C: drive along with windows 7 and all my datas are again in the same drive.

[http://www.alsa-project.org/db/?f=92df26f9368aa4021ab780b5a92de71574e0132a](http://www.alsa-project.org/db/?f=92df26f9368aa4021ab780b5a92de71574e0132a)

This is the new file i got after updating alsa.

---

### Post by Pablo_F on 2011-01-16
Hi, 

You don't have the drivers. Solving this is not as easy as installing one package. You could check this guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Nevertheless, a clean install won't hurt. In Windows, Drive C: refers to a partition, not to a physical unit. Take a look at the terminal output of:

sudo fdisk -l

In Linux, a hard disk is /dev/sdx. Probably /dev/sda. Partitions are /dev/sda1, /dev/sda2, etc.

Cheers, Pablo

---

