---
title: "Loading Debian in Virtualbox from image"
date: 2008-11-28
forum: Virtualisation
---

### Post by lsutiger on 2008-11-28
I am trying to load debian from a cd image and having problems after the scan for hardware. After the scan, it looks at the CD for the installation files. Is there a trick to making it look at the image?

---

### Post by bodhi.zazen on 2008-11-28
Typically you point the "CDROM" to the Debian.iso and boot.

If it does not boot it may not have all the drivers. What image are you using ?

---

### Post by lsutiger on 2008-11-29
It is booting from the image. I do have the image set as the boot device. After the boot starts, it goes through a few questions then scans the hardware. After that, it reports that the installation files can not be found on the CD-ROM.

One of the image files I am using is debian-40r4a-i386-CD-1.iso.

---

### Post by bodhi.zazen on 2008-11-29
Is that a live CD ?

If not, try the live CD instead.

---

### Post by Pom2122 on 2008-11-30
Is it expecting the next cd (ie: debian-40r4a-i386-CD-2.iso)? I usually use the netinst or business card iso's. :)

---

### Post by lsutiger on 2008-12-01
HOLY CRAP! I found my problem. I just had the first cd. Even if you d/l the DVD image, it takes 4 DVDs!!

Thanx for the input and sorry for my bonehead mistake!

---

