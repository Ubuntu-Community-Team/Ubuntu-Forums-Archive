---
title: "fix the mbr without FIXMBR?"
date: 2006-12-03
forum: Windows
---

### Post by an.echte.trilingue on 2006-12-03
Does anybody know how to restore a windows MBR without using the recovery console on the windows CD?

Namely, I am getting tired of the dual boot thing, and I want to take GNU/Linux off of one of my boxen in favor of XP only.  Normally I would simply put the recovery CD in and use the FIXMBR command.  However, the manufacturer of this particular machine (asus), in what appears to be an attempt to combat "piracy", has replaced the standard windows setup with their own application that pretty much copies a pre-made disk image to the hard drive and lacks all the windows recovery utilities.  As a Linux guy, I didn't bother keeping any of the other windows disks I have received over the years cause I didn't think I would ever use them...  And I should have made a backup of my MBR...  And I don't want to re-install from scratch, either...

Thanks,
-mat

---

### Post by lucia_engel on 2006-12-03
Had that problem once. I did a search and came across Test Disk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I was in Windows when I did this. It worked for me but I forgot the exact steps.

I think the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") also has quite a few MBR tools you can try (including TestDisk).

---

### Post by scc4fun on 2006-12-08
[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by r76 on 2006-12-15
I used the following page, and the MbrFix.exe technique:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Very fast and straightforward.  I was using an Acer Travelmate 372Tmi which uses a recovery disk like you describe.  The method above was painless and leaves the partitions, which you can sort out afterwards (I find [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD easiest) - I just left them because one day I will get this thing working with Ubuntu... :twisted:

---

