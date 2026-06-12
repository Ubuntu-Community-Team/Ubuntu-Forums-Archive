---
title: "Partititioning windows and ubuntu"
date: 2009-04-03
forum: Virtualisation
---

### Post by ubantuwannabe on 2009-04-03
with reference to [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Pictured above is a more common scenario—a Ubuntu partition, a Windows partition, and a FAT32 partition in the middle to share data between the two operating systems.

Am I right to say any data written to that partition can be viewed by either os

I have a nc 4400 laptop specifications are as follow

60G Harddisk
3 RAM

usually on windows platform I partition the hard disk into c:\ and d:\ so that any reinstall of windows xp will not affect any data file

so if I want to do the following

for windows xp
c:\
d:\

different partitions for windowx sp, is this necessary?

or is the d:\ supposed to be in the shared partition?

the swap partitioned should be 3G since 3G RAM

If shared data can be shared the two OS, that would be good.

So is it possible to partition the disk according to the diagram refered?

I actually wanted to switch to ubuntu completely, but there's some software that can only run on windows os, that's why I'm thinking of a dual boot system with vmware.

[http://imrannazar.com/Running-a-Windows-Partition-in-VMware](http://imrannazar.com/Running-a-Windows-Partition-in-VMware)

the laptop is brand new so would not require any backups.

thanks a lot

---

### Post by InspiredIndividual on 2009-04-03
It's not clear what diagram you're referring to, as there are multiple diagrams in the psychocats tutorial. I'll try to interpret your wished as good as possible, please correct me if I'm misunderstanding something.

First, you will need a NTFS partition for the Windows XP data. I suppose this is C:\ in your situation. 

Second, it's most convenient to store all other data on a 'shared' partition that can be accessed by both Windows XP and Ubuntu. You could use a FAT32 partition for this, or an ext3 partition. This last option is the favorite choice of the Psychocats author, using FS-Drive to allow Windows to read and write to ext3 partitions. See Psychocats article for the reasoning. I think this would correspond to D:\ .

If you decide to go with a FAT32 partition for shared data, it's useful to create a separate /home partition for Ubuntu. If you decide to use an ext3 partition for the shared data, this becomes the /home partition.

Third, you'll need a partition for Ubuntu's system files. This ext3 partition has / as its mount point.

Fourth, you could use a swap partition. However, you may well have enough RAM to be perfectly fine without one. With a total hard disk space of 60 GB, you might need the space. Anyway, in case you do decide to employ a swap partition, you certainly won't need 3 GB. According to the guide on Partitioning Basics on this forum, the rule of thumb is the following: 
RAM < 1 GB , then swap size = 2xRAM
RAM > 1 GB , then swap size = 2 GB
Note that this 2 GB recommendation is 'conservative', and some claim a swap > 1GB is excessive.
( Brief partitioning introduction: 
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) )

To sum things up: Psychocats mentions multiple partitioning schemes, and there are multiple diagrams in the article you referred to. It's certainly possible to use one of the diagrammed partitioning schemes. You'll probably want to choose between "FAT32 for shared data + extra ext3 /home in Ubuntu" and "ext3 for shared data using FS-Drive to read/write to ext3 within Windows". When deciding how big you want the separate partitions to be, you certainly won't need 3GB swap. I hope this helps, please mention it if anything is still unclear.

---

### Post by ubantuwannabe on 2009-04-04
thanks for the clear and thorough explanation.

I think I would go for third last diagram, which is the last diagram for dual boot.

Also just need to confirm Linux can't read NTFS, right?

thanks

---

### Post by bodhi.zazen on 2009-04-05
> **ubantuwannabe said:**
> thanks for the clear and thorough explanation.

I think I would go for third last diagram, which is the last diagram for dual boot.

Also just need to confirm Linux can't read NTFS, right?

thanks

Linux can both read and write to a NTFS partition.

---

