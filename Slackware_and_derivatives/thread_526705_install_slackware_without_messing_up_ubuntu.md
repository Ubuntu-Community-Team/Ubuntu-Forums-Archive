---
title: "install slackware without messing up ubuntu"
date: 2007-08-15
forum: Slackware and derivatives
---

### Post by ry4n on 2007-08-15
I have a problem I have nothing in hd1 and have my main system in hd2 when i install slackware12 the lilo boot loader deletes grub so i can't use ubuntu? It just says error, what do i do?:confused:

---

### Post by Bachstelze on 2007-08-16
> **ry4n said:**
> I have a problem I have nothing in hd1 and have my main system in hd2 when i install slackware12 the lilo boot loader deletes grub so i can't use ubuntu? It just says error, what do i do?:confused:

If you don't have a separate /boot partition, you'll have to install LILO in the boot sector of your Slack partition instead of the MBR. If you prefer GRUB, you can also not install LILO at all and install GRUB afterwards, it's in Slack's /extra packages, or you can use your Ubuntu Live CD.

---

### Post by ry4n on 2007-08-19
I will have to try this, thank you for the help.

---

### Post by ry4n on 2007-09-01
i did try this and it still did not work so i am not sure what i am doing wrong I tried to install LILO in the first hard drive but nothing.... I don't know?

---

### Post by Bachstelze on 2007-09-02
I think your best option is not to install LILO at all, and install GRUB after the installation is complete. I don't remember if Slack's installation lets you install LILO on the boot sector of a partition instead of on the MBR. And LILO is kind of archaic, anyway...

---

### Post by ry4n on 2007-09-02
thank you for replying back:

um... if i don't install LILO would grub still be there and if not what would i do then?

---

### Post by Bachstelze on 2007-09-02
GRUB ill still be there if you don't overwrite it, and if it's not, just reinstall it using your Ubuntu Live CD.

By the way, is your Slack root partition a primary or a logical one ?

---

### Post by ry4n on 2007-09-03
this is really embarrassing but i don't really know the difference (i'm sorry) i'm such a n00b

---

### Post by Bachstelze on 2007-09-03
No problem, boot your Ubuntu Live CD, paste the output of

```
sudo fdisk -l
```

and tell me which partition you installed slack on.

---

### Post by ry4n on 2007-09-05
I thank you for helping me so much, but i decided to just install debian on the other hard-drive, and it works great. So i guess it was not meant to ever have slack on it lol. 

sorry for wasting your time ( really do feel bad)

---

### Post by kellemes on 2007-09-29
For those finding this thread and wondering how to do this..
[http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader")

This method works great.

---

