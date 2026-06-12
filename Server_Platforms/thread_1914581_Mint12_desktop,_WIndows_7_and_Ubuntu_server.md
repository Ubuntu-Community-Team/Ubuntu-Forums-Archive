---
title: "Mint12 desktop, WIndows 7 and Ubuntu server"
date: 2012-01-24
forum: Server Platforms
---

### Post by deepakdeshp on 2012-01-24
I was trying to install Ubuntu 10.04 server on WIndows 7 box.

I had clonezilla images for server Mint12. I created partitions on WIndows 7 box, restored Mint12 and later the server. Both Linux distros are working fine but WIndows 7, which was working earlier, doesnt work

*The error is:status 0xc000000e boot selection failed because a required device is inaccessible.* 

But when I mount the Windows partitions, all the data in them is intact.

How do I recover windows?

---

### Post by Jive Turkey on 2012-01-24
did you delete the mounted volume registry keys before cloning the windows partition?

These guys seem to have it figured out:
[http://sourceforge.net/projects/clonezilla/forums/forum/394751/topic/3523829](http://sourceforge.net/projects/clonezilla/forums/forum/394751/topic/3523829)

---

### Post by deepakdeshp on 2012-01-25
> **Jive Turkey said:**
> did you delete the mounted volume registry keys before cloning the windows partition?

[]("http://sourceforge.net/projects/clonezilla/forums/forum/394751/topic/3523829")

I did not clone the Windows partition.I made a partition on a WIndows 7  desktop and restored a clone of Ubuntu on this partition. The MBR was overwritten by GRUB , I get the option to boot Windows but when I choose it, the above error occurs. Let me try out the solution.

---

### Post by deepakdeshp on 2012-01-31
I use clonezilla to restore images.I had a Mint12  and Ubuntu server 10.04 set up as a multiboot on  single disk using grub2. I restored WIndows 7 image on the first partition , then Grub did not recognize Linux partitions, 
I restored 10.04. server on the disk booted from it and did #update-grub. It recognized all partitions and I could boot all distros. But  now Windows will not boot.

*The error is:status 0xc000000e boot selection failed because a required device is inaccessible.*

---

### Post by deepakdeshp on 2012-02-15
I used Windows 7 recovery cd, made it usb bootable with universal usb installer . I booted from this usb and recovered the Windows system and now all the distros are bootable.

---

