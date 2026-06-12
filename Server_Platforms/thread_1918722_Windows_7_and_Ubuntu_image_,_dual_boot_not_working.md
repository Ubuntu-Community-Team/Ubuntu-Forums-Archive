---
title: "Windows 7 and Ubuntu image , dual boot not working"
date: 2012-02-01
forum: Server Platforms
---

### Post by deepakdeshp on 2012-02-01
I use clonezilla to restore images.I had a Mint12  and Ubuntu server  10.04 set up as a multiboot on  single disk using grub2. I restored  WIndows 7 image on the first partition , then Grub did not recognize  Linux partitions, 
I restored 10.04. server on the disk booted from it and did  #update-grub. It recognized all partitions and I could boot all distros.  But  now Windows will not boot.

*The error is:status 0xc000000e boot selection failed because a required device is inaccessible.*

---

### Post by deepakdeshp on 2012-02-14
I used Windows 7 recovery cd, made it usb bootable with universal usb  installer . I booted from this usb and recovered the Windows system and  now all the distros are bootable.

---

