---
title: "thinking of getting a darter... how easy is it to install XP and dual-boot?"
date: 2007-12-10
forum: System76 Support
---

### Post by alwiap on 2007-12-10
Hi,

I'm considering buying a Darter Ultra (I need a SMALL laptop), but I have to use XP occasionally for music software (Sibelius 5).  

How easy is it to install XP after I get the laptop?  I mean, can I just put the XP disk in, partition the disks in setup like usual, and be fine?  I've heard that XP doesn't play nice with Ubuntu already installed, so would I have to clear the HD, install XP in a partition (I'm getting 160 GB HD regardless, so I would partition about 15-20 to XP), and then reinstall Ubuntu on the remaining 140 like a normal dual-boot AFTER XP?  Or is there a workaround/is it necessary? How would that affect the system76 drivers etc.?

Cheers

---

### Post by thomasaaron on 2007-12-10
If you want to dual boot, you will need to actually re-install Ubuntu.
To do this you would just install windows on however much of the HD you choose and then re-install Ubuntu on the remainder.

Your other option would be to virtualize XP using vmware. Then you would not have to re-install Ubuntu at all.

---

### Post by rockin_goliath on 2007-12-10
If you have not even gotten the laptop yet, then there is no data or special setups that you have to worry about loosing, so I would just install XP on its own (modest) partition before I do anything else with the laptop; Don't waste your time trying to resize the Ubuntu partition, installing XP, and then restoring GRUB, it will take about the same amount of time anyway.

When setting up the partition table in the XP installation, create a partition that does not fill the entire disk and leave the remaining space unallocated. When you go to install Ubuntu again, choose the option "Use largest continuous free space," and the installer will do all the GRUB dirty work for you automatically.

---

### Post by palintheus on 2007-12-10
The darter also needs special drivers for XP due to the SATA drive and since the installer will only accept drivers from a floppy you may have to modify the install iso.

---

### Post by tedrampart on 2007-12-13
this might help with the process of installing XP:
[http://forums.hexus.net/operating-systems-applications/20748-windows-xp-installing-sata-_without_-floppy-disk.html](http://forums.hexus.net/operating-systems-applications/20748-windows-xp-installing-sata-_without_-floppy-disk.html)

or maybe this:
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

ones a manual way of doing it, the other is a program that will help with it.  sadly the program is for winblow$

---

### Post by rcsarver on 2008-01-03
alwiap,

i have done exactly what you are talking about for the same reasons- to use sibelius. rockin-goliath is right, it is much easier to install windows first, then ubuntu. the ubuntu installer configures grub so you don't have to worry about it.

also, i think wine is getting close to working completely with Sibelius 4. i haven't tried it yet but it has recieved platinum status in the application database. soon we may not need xp at all.

---

