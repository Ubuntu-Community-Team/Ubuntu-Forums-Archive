---
title: "Recreate an old RAID-1"
date: 2007-11-14
forum: Server Platforms
---

### Post by Patrick80 on 2007-11-14
Hello,

I'm not sure, that this is the right forum for my problem. Maybe you know a better place to ask. You are welcome to move this post into a better forum.

Okay, I have (a big) Problem. I have a harddisk from an RAID-1 (mirror). There are 3 Partitions on it. I need the data on the HD, but i have no idea how to get the data.

The layout of the old disk is (nothing unusual):
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   fd  Linux raid autodetect
/dev/sda2            6080        6201      979965   82  Linux swap / Solaris
/dev/sda3            6202       60801   438574500   fd  Linux raid autodetect

I don't have the second HD, but this shouldn't be a problem.

Any idea is welcome :-)

Bye,
 Patrick

---

### Post by crouton on 2007-11-14
A degraded RAID1 is still usable.  Fire up the system and copy the files off.  If you no longer have the system, the system refuses to boot from the degraded RAID1, the RAID card is bad, etc you have a different problem.

---

### Post by Patrick80 on 2007-11-14
Hello :-),

thanks for the answer :), but i don't have the old OS, I only have this harddisk, but there is no OS on it :-(

Bye,
 Patrick

---

### Post by Patrick80 on 2007-11-14
if anyone have the same problem maybe this will help you:

recreation of an untouched ex-raid-1 partition is simple:
mdadm --assemble /dev/md5 /dev/sda1

maybe you need to set the uuid:
mdadm --assemble --uuid ea3b1c3e:26608223:cfed343b:691746d /dev/md5 /dev/sda1

you can get it from an old config file or with:
mdadm --examine /dev/sda1

if you have a corrupted superblock you can try to clean it um and create a new array:
mdadm --zero-superblock /dev/sda1
mdadm --create /dev/md4 --verbose --level=1 --raid-devices=2 /dev/sda1 missing

it works also with raid-5 :-)

so, now have fun again with your linux raid :-)

---

### Post by crouton on 2007-11-14
That sounds like a software RAID within Linux rather than a hardware RAID... but congrats on getting it working. :)

---

