---
title: "defragment Ubuntu"
date: 2012-01-30
forum: Server Platforms
---

### Post by cccc on 2012-01-30
hi

I'm doing backups using Acronis 2012 Home, but on one machine it won't compress.
Data size = image size.   
Is it any way to defragment Ubuntu 10.04 EXT4 machine, before creating a backup image?
I've tried shutdown -F -r now, but it doesn't help.

---

### Post by shumifan50 on 2012-01-30
Have a look at PING to back up entire disks. It copies only in use areas and compresses the backup. It runs off CD using an embedded Linux so all system files can also be backed up. It also backs up to a local disk or over the network and speeds are quite acceptable, depending on CPU speed and device speeds. You cold also just boot the embedded Linux and use tar/gzip to backup specific directories.
It is no good for backing up 24/7 servers as the machine has to be booted off the CD.

Good news is that it is totally free and works for Linux and Windows.
See here:

ping.windowsdream.com/

---

### Post by arrrghhh on 2012-01-30
> **cccc said:**
> hi

I'm doing backups using Acronis 2012 Home, but on one machine it won't compress.
Data size = image size.   
Is it any way to defragment Ubuntu 10.04 EXT4 machine, before creating a backup image?
I've tried shutdown -F -r now, but it doesn't help.

I don't think there's any defragment tools for EXT, as that file system doesn't really fragment...  It's fairly good at cleaning up after itself.

None of your other (Linux) machines exhibit this problem?  I will admit, I'm not much of a backup guru.

---

### Post by cccc on 2012-01-30
> **arrrghhh said:**
> I don't think there's any defragment tools for EXT, as that file system doesn't really fragment...  It's fairly good at cleaning up after itself.

None of your other (Linux) machines exhibit this problem?  I will admit, I'm not much of a backup guru.

Yep, just one machine has this problem.

---

### Post by arrrghhh on 2012-01-30
> **cccc said:**
> Yep, just one machine has this problem.

I also assume the disk isn't completely full?

How do you know this isn't an issue with Arconis?

---

### Post by mcarrara on 2012-01-31
Depending on the type of file the amount of compression will vary.  Already compressed files will not change much in size.  My back ups of mixed data sees about 30% compression.  This may sound trite, but did you check that compression is turned on for that one client?

As to defraging, Linux does not need to be defragmented, I doubt there is a tool available.  I was told once many years ago that when you copy a file in Linux it is defraged during the copy.  I don't know if that was true then or if it is true now, but I do know in 8 years of running Linux I have never defraged a computer.

---

### Post by shumifan50 on 2012-01-31
>  was told once many years ago that when you copy a file in Linux it is defraged during the copy.

All file systems, that allocate fles automatically, will fragment over time. Linux reduces fragmentation to some extent by allocating the closest next free block when it is required. However, if you have a file that extends over a longer period, like a log file, many blocks can be inserted in between, causing fragmentation. This improves from ext2 to ext3 to ext4, but can never be eliminated.
Defrag tools exist fro ext2 but not for ext3 or ext4 (that are safe).

All non-mainframe OS suffer from not having file allocation utilities allowing pre-allocation of files and so full control over disk organisation. On mainframes a lot of time is spent to put related files in specific relationships to each other, at specific disk addresses, to improve performance. Because of pre-allocation of the in-use as well as future extents, mainframe file systems do not fragment.


A simple way to do a defrag (but time consuming) would be to tar all the files to a different disk, then delete all the files and untar back to the disk, as this will create each file contiguous.

---

### Post by cccc on 2012-03-04
First, THX a lot for all answers.
Perhaps, this problem occurs after migrating (converting) Ext3 to Ext4.

[http://www.debian-administration.org/articles/643](http://www.debian-administration.org/articles/643)

I've done a fresh Ubuntu installation with Ext4 and now it works well.

---

### Post by suppo84 on 2012-10-29
There is also defrag tool for ubuntu 12.04 and newer: [https://apps.ubuntu.com/cat/applications/hdd-ranger/](https://apps.ubuntu.com/cat/applications/hdd-ranger/)

Sorry for bad english.

---

### Post by cccc on 2012-10-29
> **suppo84 said:**
> There is also defrag tool for ubuntu 12.04 and newer: [https://apps.ubuntu.com/cat/applications/hdd-ranger/](https://apps.ubuntu.com/cat/applications/hdd-ranger/)

Sorry for bad english.

Quite interesting..
Has anyone already tried this [defrag tool]("https://apps.ubuntu.com/cat/applications/hdd-ranger")?

---

### Post by thnewguy on 2012-10-29
This is a bit roundabout, but when I wanted to have a defragged copy of my data, I would copy all the files on my drive to another partition. This really only works if you have a spare disk/partition or if you have enough free space on your disk for a file that can hold all your data. The copy (cp) command will defrag data as it copies so long as the destination does not have any existing files on it.

---

### Post by ian dobson on 2012-10-29
Hi,

I've used e4defrag on several of my systems. It's included in the e2fsutils package in 11.10 und 12.04

Regards
Ian Dobson

---

