---
title: "Ubuntu softraid - read hdd in other computer"
date: 2009-09-17
forum: Server Platforms
---

### Post by nemopeti on 2009-09-17
Hello!

I'm new in Ubuntu Server platform, and I have two SoftRaid releated question.

I installed a 9.04 x64 version of ubuntu with the following hdd options (in the server there are 2x500 HDD):

2 GB partition to swap with RAID0
10 GB partition to system with RAID1, EXT3
~488 GB partition to data with RAID1, EXT3

It works fine, even if I disconnect one of the hdd's.

BUT, what if disaster happens:
- how can I read the content one of the hdd's in a nother (linux  or windows) PC?
- if one of the hdd's dead, and I replace it to a new one, what happend with the syncronisation? (auto/manual, how, where)

Than's for your help, and sorry for my english.

---

### Post by Bachstelze on 2009-09-17
> **nemopeti said:**
> 
- how can I read the content one of the hdd's in a nother (linux  or windows) PC?

Just mount the partitioons like you would do with a normal (non-RAID) drive.

> **nemopeti said:**
> - if one of the hdd's dead, and I replace it to a new one, what happend with the syncronisation? (auto/manual, how, where)

It will be done automatically when you power on your computer after replacing the drive.

---

### Post by nemopeti on 2009-09-17
> **Bachstelze said:**
> Just mount the partitioons like you would do with a normal (non-RAID) drive.


I connect it to a nother ubuntu desktop pc with usb, and it's not recognise it. Also tryout with windows pc and ext2 ifs, I see the partitions but not the data.


> **Bachstelze said:**
> 
It will be done automatically when you power on your computer after replacing the drive.

I try it out, and nothing happend, I disconnect one of the hdd's, and connect a new empty one to it's cable. System starts normal, I wait some time, then shutdown the system, and try to read some data to the newly connected drive, but it has no partition at all.

---

### Post by fjgaude on 2009-09-17
Auto re-sync with raid0 and 1? How about raid5?

---

### Post by nemopeti on 2009-09-17
I don't use raid 5

I use 2 physical disc, with 3 softraid "partition"

the 2 GBswap partition uses RAID 0 because it's quick
the system and data partitions 10 GB + 488 Gb uses RAID 1 because it's secure

RAID 5 need minimum 3 physical disc as I know.

---

### Post by fjgaude on 2009-09-17
I was hoping that Bachstelze would answer yes or no... I know what your situation is. Sorry about the confusion caused.

---

