---
title: "Server 18.04.2 can't use my RAID-card"
date: 2019-03-15
forum: Server Platforms
---

### Post by mattiash on 2019-03-15
I am running kernel v5.0.2 and Ubuntu Server 18.04.2, on a Asus B450 mobo and an Ryzen 3 processor.
I got an Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller and the newly installed system can't seem to use it.
The disk connected to it doesn't appear.
It say that the kernel driver ache is in use for it.

What can I do?

Oh yeah I had to fiddle a lot inside bios to get the system to boot, I might have turned off something crucial... I got an IMMOU error, so that is turned off, secure boot is turned off.

---

### Post by SeijiSensei on 2019-03-15
So when IMMOU was enabled, you got an error?  Sounds like this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1810239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1810239)

---

### Post by mattiash on 2019-03-17
So yesterday I finally got the system to boot Ubuntu Server. The short version is that I updated the kernel and the AMD drivers, turned off a few things in the BIOS, that made it happen.
I will write a blog post about explaining in much more detail what I did.

---

