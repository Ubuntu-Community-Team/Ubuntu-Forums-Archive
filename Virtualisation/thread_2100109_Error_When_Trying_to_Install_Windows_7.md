---
title: "Error When Trying to Install Windows 7"
date: 2012-12-31
forum: Virtualisation
---

### Post by chome4 on 2012-12-31
Running Ubuntu 12.04 in KDE mode successfully on a Compaq Presario CQ58 laptop.

Installed Virtualbox but when trying to install Windows 7, I get a 'Windows failed to start' message. Picture attached showing full message.

The hard disk was completely wiped, leaving nothing but one partition. Ubuntu didn't have any objections to using the entire hard disk.

I got the same message before I installed Ubuntu. I tried to do a fresh install of Windows 7 in preparation for a dual-boot situation with Ubuntu. This worked before I decided to obliterate all partitions.

In the world of Windows, do you need to have some sort of extra partition?

---

### Post by JiuJitsu500 on 2013-01-01
Try this mess:

Wipe the Virtual HDD.

Put the HDD as the FIRST boot device
Disable Floppy, and move CD to second boot device

Then, when you boot, it acts like a BIOS would and chooses the HDD, can't see anything there, then moves to the CD... which install WIndows. Then when Windows reboots during install like it always does, it goes to the HDD like it should, then borrows the CD for the rest of it like it should.

Looks like you might have backward that part, or something else stupid happened you couldn't control. Either way, try this and give it another whirl :D

---

### Post by chome4 on 2013-01-01
There's no option for wiping the virtual HDD. I recreated the virtual machine from scratch but left out the creation of the HDD. Made the changes to the boot sequence but got the same message.

---

