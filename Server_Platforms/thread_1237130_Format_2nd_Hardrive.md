---
title: "Format 2nd Hardrive"
date: 2009-08-11
forum: Server Platforms
---

### Post by Loan_Refi on 2009-08-11
Hi, I need help formating my 2nd hard drive.

I'm in the process of setting up a server and I don't understand fdisk to format my 2nd hardrive

I have Ubuntu Server 8.04 with 2 hard drives, this is the results of sudo fdisk -l
administrator@L1:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120373   966896091   83  Linux
/dev/sda2          120374      121601     9863910    5  Extended
/dev/sda5          120374      121601     9863878+  82  Linux swap / Solaris

Disk /dev/sdb (Sun disk label): 255 heads, 63 sectors, 56065 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
/dev/sdb1             0     56065 450342112+  83  Linux native

Disk /dev/sdb1 (Sun disk label): 255 heads, 63 sectors, 56065 cylinders
Units = cylinders of 16065 * 512 bytes

    Device Flag    Start       End    Blocks   Id  System
/dev/sdb1p1             0     56065 450342112+  83  Linux native


Both hardrives are same size 1000GB
I tried to start over to format and use entire hard drive but I don't get the prompts I think I'm suppose to get using; sudo fdisk /dev/sdb

I type "n" and get;
Partition number (1-8):
I type "1" and says Partition 1 is already defined.  Delete it before re-adding it. So I delete it and start with "n" 
Partition number (1-8): 1
First cylinder (0-56065): at this point I can only hit enter and I get
Last cylinder or +size or +sizeM or +sizeK (0-56065, default 56065):
I hit enter again and back to 
Command (m for help):
so I write table to disk and exit.

Can someone help me format this disk to use it entirely as a 2nd hard drive?

I started following this guide at: 
[http://bloggajim.com/blog1.php/2009/03/11/linux-second-hard-drive](http://bloggajim.com/blog1.php/2009/03/11/linux-second-hard-drive)
but I messed something up and don't know how to start over.

---

### Post by Loan_Refi on 2009-08-11
Okay I just remember to try; 
sudo cfdisk /dev/sdb and crated the partition using the entire hard drive.

What is the proper way to set up (format) the 2nd hard drive?

---

### Post by Loan_Refi on 2009-08-11
Okay, I used cfdisk than came back to fdisk and followed the instructions to start over and this is how my 2nd hard drive looks like;

~$df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             915G  2.2G  867G   1% /
varrun                4.0G  220K  4.0G   1% /var/run
varlock               4.0G     0  4.0G   0% /var/lock
udev                  4.0G   52K  4.0G   1% /dev
devshm                4.0G     0  4.0G   0% /dev/shm
/dev/sdb1             925G  200M  915G   1% /hdb

~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120373   966896091   83  Linux
/dev/sda2          120374      121601     9863910    5  Extended
/dev/sda5          120374      121601     9863878+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      12160

I think I set things up right?

---

