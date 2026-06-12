---
title: "Storage On ubuntu dedicated server 18:04"
date: 2019-01-17
forum: Server Platforms
---

### Post by darkzea123 on 2019-01-17
Hi people 

My dedicated server Spec's

[CENTER][COLOR=#727272][FONT=&quot]
[LIST]
[*]Unmetered Bandwidth | Gigabit Conn.
[*]Any Linux/Windows* OS available!
[*]Intel Core i7-2600 - Quad Core (8t)
[*]16GB RAM | 2x 3TB HDD Space
[*]Located in Europe & USA!
[*]Custom ISO through IPMI request!
[/LIST]
[/FONT][/COLOR][/CENTER]















What i have done installed GUI on the server when i use vnc to see the desktop the storage available is 1tb but when i go to storage in settings it shows the 2x 3tbh hdd my question is how do i access them?

Thank you

---

### Post by TheFu on 2019-01-17
How to you want them setup?

RAID1, RAID5, no RAID?
Do you want to use LVM2 or not?
Which file systems do you want?
Where will the backups go?  What about disaster recovery?

Storage design is very important for DR and backup planning.

These answers will determine "how do I access them" ... right now, they are completely empty. You'd need to partition them, add a file system, then mount at least 1. This is the minimal required.

---

### Post by darkzea123 on 2019-01-17
Thanks for your reply 

Atm there already setup as RAID it says on disk management, i am not experienced with the different file systems i would like full access to the 6tb total for media storage. 
if you can tell the best way to do this i would appreciate any help

---

### Post by TheFu on 2019-01-17
Like I said, I'd > partition them, add a file system, then mount at least 1. This is the minimal required. 
There are guides for doing each of those steps all over the internet.  If you are really new, expect to be tripped up by things that more experienced people learned in their Admin 101 classes.  You'll probably want at least 3 partitions on 1 disk (swap, /, and data) and 1 partition on each of the other disks. This assumes you don't use LVM and have a good backup/replication plan already. If you use LVM, there are many other choices.  I would use LVM, but if you aren't a Unix admin, then that is probably to complex.

You'll need tools like fdisk, mkfs, and mount at the minimum.  If the disks are already configured for RAID, you'll need to remove all RAID bits from the disk. This can be trivial or it may require a special tool. That just depends on which of the 3 types of RAID the vendor uses.  I use a type of RAID that avoids those issues, at least I think it does.  Haven't setup a RAID system in a very long time, to I have a few RAID1 storage arrays here.

All this work should happen from live boot system where all three disks aren't being used.

Sorry that I'm not any more help and cannot tell you 3 commands to type to make everything just work.  Just ballpark, I'd guess about 5 specific commands for each partition involved and editing of the fstab.

I cannot say what the best answer is for your needs.
LPI has free Linux Admin training stuff.  All of it should work for 18.04 Server except the network stuff.  I cannot help at all with that, sorry.

---

### Post by Tadaen_Sylvermane on 2019-01-17
For media storage you would be hard pressed to beat Snapraid + MergerFS. Built in bit rot protection, good for files that never change. Easy to manage. Not locked in to a hardware raid. Acts as a backup as well although technically not an offsite one. They are dead simple to use, lay on top of normal filesystems instead of being their own special thing. And worst case if you lose more disks than you have parity for, you only lose those disks. Not the whole array. Been using that combination myself for awhile and it hasn't let me down yet.

For data that is constantly changing ZFS would be the better choice.

Regardless of if you choose ZFS, Raid{5|6}, or Snapraid you will not get your full 6tb of space without adding one more drive. You need at least a single drive dedicated to parity, and that drive cannot be used for normal storage.

---

