---
title: "Issue with gdm on Ultra60"
date: 2007-11-22
forum: Sun Sparc Users
---

### Post by roadruner on 2007-11-22
Hi experts,

I'm using an Ultra60 with Elite3D video card.

I've installed ubuntu 7.04 alternate. 
I've copied afb.ucode from a Solaris9 to /usr/lib

But after a reboot, I have to run the command :
```
sudo afbinit /dev/fb0 /usr/lib/afb.ucode
```
to have the graphic UI

What file I have to modify to not to have to run this command after each reboot ?

Regards.

---

### Post by jcastill on 2007-11-22
you have to add it to a rc.d file and make it load on rc2 before gdm.

---

