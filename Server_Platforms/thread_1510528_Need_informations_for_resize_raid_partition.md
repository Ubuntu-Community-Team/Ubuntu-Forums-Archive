---
title: "Need informations for resize raid partition"
date: 2010-06-15
forum: Server Platforms
---

### Post by ouafnico on 2010-06-15
Hi all,

I've got 2 hard disk drives of 250GB, with this partitions :

sda1 : 15Gb
sda2: 2Gb
sda3 : 218Gb
sdb1 : 15Gb
sdb2 : 2Gb
sdb3 : 218Gb

All partitions are with format "linux raid software". I made 3 raid1 with them like that :

md0 : 15Gb (/)
md1 : 2Gb (swap)
md2 : 218Gb (/home)

I want to clone them to news hdd of 500Gb, to have this partitions :

md0 : 15Gb (/)
md1 : 2Gb (swap)
md2 : all rest of disk (/home)

My problem, how can I resize partitions, before resize the array md2 with the command **mdadm --grow /dev/md1 --size=max** ?

After, how can I rebuild /dev/md2 without lost any datas ?

I'm using ubuntu-server 10.04 64bits.

Thanks for your help

---

### Post by ouafnico on 2010-06-18
no one ?

---

### Post by Bachstelze on 2010-06-18
It will work for / and swap but not for /home. All partitions in the same RAID array must be the same size. If some are larger, the extra space will just not be used.

Also, RAID-1 basically just duplicates data, so you will not have any more storage space available, just added redundancy.

---

### Post by benderisgreat on 2010-06-18
Don't try to resize the raid arrays. No reason to. Just make new bigger raid arrays on the new drives and copy the data (with rsync or something).
Also why would you create three seperate raid-1 arrays when you could just easily create partitions or logical volumes on one raid array?

---

