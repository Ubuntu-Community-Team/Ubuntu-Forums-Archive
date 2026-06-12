---
title: "Boot From CD in BIOS not working* Ubuntu to Win 7"
date: 2015-01-08
forum: Windows
---

### Post by dustin-sullivanj on 2015-01-08
Okay guys and gals I need some assistance.
I have ubuntu 14.04 installed by itself on my laptop, Acer Aspire V model Z5WV2. I need to get Ubuntu off and windows installed so i can have a duel boot. I know i need to install windows first then ubuntu. the problem im having is install windows. For whatever reason Im unable to boot windows from CD. In the BIOS there is no option to install from CD. The CD is bootable, it has been used to install windows on multiple systems but for whatever reason I cannot get it CD boot options in the BIOS. 

Please Help!

---

### Post by Frogs Hair on 2015-01-08
Hello and Welcome 

How was Ubuntu installed ? I was thinking a bootable usb might work if the the bios supports that option and if your of  copy genuine Windows can be legally installed on multiple machine.

---

### Post by dustin-sullivanj on 2015-01-08
Ubuntu was installed over windows. Meaning I deleted windows after installing ubuntu. The windows version I have can be installed on multiple machines. I'm going to try the bootable USB tomorrow when I get a chance. Thank you.

---

### Post by coffeecat on 2015-01-09
> **dustin-sullivanj said:**
> In the BIOS there is no option to install from CD.

There won't be. What you need to look for is the boot order and put the optical drive before the hard drive. If you do that and put a bootable CD/DVD in the optical drive, the BIOS will boot from that rather than the hard drive. If you put a non-bootable disc in - say a data CD or DVD - the BIOS will check it, ignore it when it finds it is not bootable, and then continue onto the hard drive. The BIOS merely chooses each drive in the order you specify looking for a bootable medium. 

This article takes you through the basics:

[http://www.howtogeek.com/129815/beginner-geek-how-to-change-the-boot-order-in-your-computers-bios/](http://www.howtogeek.com/129815/beginner-geek-how-to-change-the-boot-order-in-your-computers-bios/)

---

### Post by mips on 2015-01-11
You don't have to install windows first. 

Backup your mbr using dd.
Resize your existing partitions.
Install windows in the free space.
Restore the mbr using dd from your livecd.
Reboot & update grub.

On you bios splash screen you should have an option to select a boot device via one of the F keys. What hardware do yo have.

---

