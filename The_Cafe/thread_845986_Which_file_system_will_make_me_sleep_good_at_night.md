---
title: "Which file system will make me sleep good at night ?"
date: 2008-07-01
forum: The Cafe
---

### Post by conphara on 2008-07-01
Which file system should I use on a backup disk in the same desktop PC as Ubuntu Hardy related to file/disk corruption, security/hacking, encryption and so on. The disk is a SATA, 160 GB, APM enabled.

Hint: The files that are gonne be stored on it is mostly large files (> 100 MB) combined with about 100+ personal documents. 

Ext2, Ext3, ReiserFS, Fat ?

---

### Post by LookTJ on 2008-07-01
EXT2 or EXT3.

didn't ReiserFS go out of development?

Fat holds files(file size) =< 4GB

EDIT: Also, read this though it might be old. [http://www.valhenson.org/review/choosing.pdf](http://www.valhenson.org/review/choosing.pdf)

---

### Post by Trail on 2008-07-01
I myself prefer XFS. You might like it.

It is supposed to be very performant for large files, and makes recovery of deleted files very difficult (if that's what you have in mind by security).

Also it is supposed to guarantee non-file corruption, but I hear this requires some hardware support as well, so in desktop systems it might not apply. Never had a crash so I don't know :P


I do not like ext2/3 that much, mostly because of the preallocation system it uses. By default it reserves 5% of the disk for the root user; which I find kinda unneeded for my use on /, and totally annoying for my large backup disks (5% of 1TB is a lot). You can set this to 0, of course, with tune2fs, but somehow ext2/3 still uses a bit of the disk for no apparent reason (maybe too many inodes or whatever).

I don't have too strong opinions on which filesystem to use, but I usually pick XFS as I said for non-root.

---

### Post by Vishal Agarwal on 2008-07-01
Although EXT2 or EXT3 will be better,But also you can consider the FAT32 system. It supports more then 4 GB partitions. Fat32 can be recognized by Windows also as well as UBUNTU. 

Vishal Agarwal

---

### Post by LookTJ on 2008-07-01
If you get power outages where you live, I wouldn't recommend XFS as for the fact that it gets corrupted after power loss.

---

### Post by mcduck on 2008-07-01
If the disk is in the same machine you shouldn't worry too much about the file system used,a s it's almost worthless as a backup anyway..

Just a small PSU failure, for example, and you loose both the originals _and_ the backup.

If your data is any value to you, get some external (or remvable) drive and use that for your backups. And when not actually doing a backup store the drive somewhere safe, definitely not connected to the computer.

---

### Post by klange on 2008-07-01
> **Taylor said:**
> didn't ReiserFS go out of development?
No, but you won't be able to sleep at night using it when you know the original developer is a murderer.
@OP: Wonderful way of phrasing that, there would have been no other way the previous statement would have fit well if you hadn't put it that way.

I use EXT3, but I've never bothered trying anything else (except FAT and NTFS back in the days, but they suck either way)

---

### Post by Solicitous on 2008-07-01
I've always thought that no matter how good a file system is, it's still no match for a faulty hdd.
Personally with the price of HDDs being so cheap I'd be thinking of buying a second 160gb hdd and mirror the two, that way if the data is **that important** and one hdd fails, you can replace the drive, rebuilt the array and not lose any data.
File system wise I've always used EXT3 and never gone wrong.

---

### Post by tigrezno on 2008-07-01
> **WindowsSucks said:**
> No, but you won't be able to sleep at night using it when you know the original developer is a murderer.

hehehe that's the reason why i'll be using it forever :)
i like murderer's filesystems!

---

### Post by x1a4 on 2008-07-01
Hi,

If you're dual booting with win you might want to use ext2 as it can be recognized by win using the [fs-driver]("http://www.fs-driver.org/").  Otherwise ext3.

[color=crimson]**Happy Canada Day!**[/color]

---

### Post by g2g591 on 2008-07-01
x1a4 actually ext3 can be mounted by that fs-driver too, just mounted as ext2 is all. Also , if you set data=journal using tune2fs, it improves performance, and lets e2fsck recover lost data much more easily if you have a power outage (for more ext3 performance hints, see [this post]("http://forums.gentoo.org/viewtopic-t-305871.html") ,yes its on Gentoo's forums, yes they work FINE for Ubuntu as well)

---

