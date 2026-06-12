---
title: "Windows cant see Ubuntu HDD"
date: 2014-02-21
forum: Windows
---

### Post by andrew80 on 2014-02-21
Guys,

One of my old laptops has an old version of Ubuntu on it and I want to put windows XP on it so I can install a car program I need called VCDS.

When I put the windows XP disc in it wont recognise the HDD.

I have tried numerous things like deleting the partitions, Using FDISK and DBAN to reformat but it still wont recognise them when I put the disc in? Any ideas?

---

### Post by buzzingrobot on 2014-02-21
Have you tried using fdisk to initialize the drive as an msdos drive?  And, set it as a boot drive?

---

### Post by mips on 2014-02-21
Open Gparted, from the menu go Device, Create Partition Table, create a new partition and format it NTFS.

If this does not work then you have a problem with your install media.

---

### Post by fdrake on 2014-02-21
+1 mips:
either format the hdd to ntffs/fa32 or delete all the partitions making unlocated space

---

### Post by andrew80 on 2014-02-22
DBan'd it to FAT32 and still nothing

---

### Post by fdrake on 2014-02-22
using the live cd open the terminal and type
```
sudo fdisk -l (it's a lower-case  L)
```
post here the output please

---

### Post by Don_Stahl on 2014-02-22
All good suggestions. 

A utility for checking and repairing problem drives: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I used the Linux version to repair a balky Passport USB external HDD.

---

### Post by andrew80 on 2014-03-05
Il try these tomorrow thanks

---

