---
title: "EasyBCD 1.7 Released"
date: 2007-09-06
forum: The Cafe
---

### Post by Computer Guru on 2007-09-06
EasyBCD 1.7 has just been released with a bunch of new features for Linux fans.

* EasyBCD can search your drive for Linux and boot it; you don't need GRUB installed on your bootsector to make it work!
* Install and manage GRUB from within Windows with EasyBCD's NeoGrub - rewritten from scratch (special thanks to the Grub4Dos project)
* Support for multiple separate bootloaders of the same type.

There are [a bunch more features]("http://neosmart.net/blog/2007/easybcd-17-released-up-for-download/") and [an entire changelog]("http://neosmart.net/dl.php?id=1")

[Download]("neosmart.net/dl.php?id=1") (858 KB)

---

### Post by forrestcupp on 2007-09-06
Just curious about something.  What would be the purpose or benefit of having multiple boot loaders?  It seems like it's just one more hoop to jump through before getting where you want to go.

This project does sound interesting, though.

---

### Post by original_jamingrit on 2007-09-06
> **forrestcupp said:**
> Just curious about something.  What would be the purpose or benefit of having multiple boot loaders?  It seems like it's just one more hoop to jump through before getting where you want to go.

This project does sound interesting, though.

Might be a good way to organize several Linux partitions.  If you had partitions A, B, and C, each with their own OS, each one may have a couple of extra things to choose at boot time.  SO you'd have a menu to choose A, B, and C, and then choose one of the kernels or memtest to boot with per partition.

Although, I am happy with my GRUB as it is now.

---

### Post by @trophy on 2007-09-06
> **original_jamingrit said:**
> Might be a good way to organize several Linux partitions.  If you had partitions A, B, and C, each with their own OS, each one may have a couple of extra things to choose at boot time.  SO you'd have a menu to choose A, B, and C, and then choose one of the kernels or memtest to boot with per partition.

Although, I am happy with my GRUB as it is now.


I think the purpose of it is to have your linux partition (possibly on an external hard drive) boot if you want it to without messing with Windows at all.  Kind of like a liveCD, but with read/write access.

---

### Post by Quillz on 2007-09-06
> **forrestcupp said:**
> Just curious about something.  What would be the purpose or benefit of having multiple boot loaders?  It seems like it's just one more hoop to jump through before getting where you want to go.

This project does sound interesting, though.
It's useful because Vista works differently with GRUB, and the difficulties people had with it was the reason for EasyBCD's popularity in the first place. Now with 1.7, you don't even need to have EasyBCD set up the GRUB boot loader for you, it just finds and boots Linux. This means Linux could be on an entirely different hard drive, completely untouched by Windows, and still work.

---

### Post by Computer Guru on 2007-09-07
Thanks Quillz, that's an excellent explanation :)

It'll also let ou use multiple bootloaders in sync, such as having different OSes associated with GRUB, Lilo, Darwin, NTLDR, etc; all of them accessible from one place.

---

### Post by ssican on 2007-09-07
EasyBCD Frequently Asked Questions [http://neosmart.net/wiki/display/EBCD/FAQ](http://neosmart.net/wiki/display/EBCD/FAQ)

The "Configure Boot" SCREEN  [http://neosmart.net/wiki/display/EBCD/Configuring+the+Bootloader](http://neosmart.net/wiki/display/EBCD/Configuring+the+Bootloader)

---

### Post by gusanto on 2008-01-04
I dual boots Windows Vista and Ubuntu and use EasyBCD for the bootloader succesfully.  
1. How can I change the time out, it's 30 second now, toooo long.
2. How to rename "NeoSmart Linux" into a new name.

Thanks.

---

### Post by Computer Guru on 2008-01-07
1) EasyBCD in the "Change Settings" section
2) EasyBCD in the "Change Settings" section

:)

Cheeers.

---

