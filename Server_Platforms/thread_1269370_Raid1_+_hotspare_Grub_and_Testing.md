---
title: "Raid1 + hotspare: Grub and Testing"
date: 2009-09-18
forum: Server Platforms
---

### Post by sisyphus1978 on 2009-09-18
Please bear with me. I am by no means a linux expert. I have set up a raid system with a hotspare (using ubuntu server). I am using the system as a clonezilla PXE backup server. It consists of 3 120gb hdd (none of them are new) and they have been partitioned into 3: 15gb OS, 5gb swap and 100GB home. 
This is the output from cat /proc/mdstat:
 > Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[2](S) sdc2[1]
      4883648 blocks [2/2] [UU]
  md2 : active raid1 sda3[0] sdb3[2](S) sdc3[1]
       97659008 blocks [2/2] [UU]
  md0 : acivve raid1 sda1[0] db11[2]() ssdc1[1]
      14651136 blocks [2/2] [UU]
  unused devices: <none>                      sudo mdadm --query --detail /dev/md0
 > Version : 00.90
  Creation Time : Wed Sep 16 10:24:54 2009
     Raid Level : raid1
     Array Size : 14651136 (13.97 GiB 15.00 GB)
  Used Dev Size : 14651136 (13.97 GiB 15.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent
      Update Time : Thu Sep 17 15:11:56 2009
          State : active
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
UUID : 7885268e:c206d4c0:45790112:3fb57865
         Events : 0.127
      Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
         2       8       17        -      spare   /dev/sdb1                      sudo mdadm --query --detail /dev/md1
 > Version : 00.90
  Creation Time : Wed Sep 16 10:25:16 2009
     Raid Level : raid1
     Array Size : 4883648 (4.66 GiB 5.00 GB)
  Used Dev Size : 4883648 (4.66 GiB 5.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent
      Update Time : Thu Sep 17 15:07:20 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
UUID : 4f6e9a41:0196bdb3:0e215fd1:a734c833
         Events : 0.18
      Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       34        1      active sync   /dev/sdc2
         2       8       18        -      spare   /dev/sdb2                      sudo mdadm --query --detail /dev/md2
> /dev/md2:
              Version : 00.90
  Creation Time : Wed Sep 16 10:25:40 2009
     Raid Level : raid1
     Array Size : 97659008 (93.13 GiB 100.00 GB)
  Used Dev Size : 97659008 (93.13 GiB 100.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 2
    Persistence : Superblock is persistent
      Update Time : Thu Sep 17 15:08:17 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
             UUID : 28de3a8b:42202b7b:9f3e4ea9:32618cf8
         Events : 0.64
      Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       35        1      active sync   /dev/sdc3
         2       8       19        -      spare   /dev/sdb3                      
My questions
 
1) If I pull out sda (to simulate a fail) I presume it will start to use the hotspare. Once I put back sda, how do I return to the original state (ie sdb as the hotspare)?
 
2) find /boot/grub/stage1 returns:

> (hd0,0)
 (hd1,0)
 (hd2,0)                      Does this mean that all the disks will boot regardless of which fails?
 
Here's hoping someone can explain a bit. Thanks.

---

### Post by maxim_86ualb2 on 2009-10-14
1. You would have to re-add the sdc to all of your arrays. And then remove sdb and add it again as a spare.

2. I am not expert myself, but Ubuntu had an issue with grub and raid (I am not sure if it is fixed). Where grub is not installed on all the drives. Here is a fix for it:

[https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles#Boot](https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles#Boot) Loader

---

### Post by epsolon77 on 2009-10-14
> **sisyphus1978 said:**
> 
1) If I pull out sda (to simulate a fail) I presume it will start to use the hotspare. Once I put back sda, how do I return to the original state (ie sdb as the hotspare)?


This may be a stupid question, so please forgive me and understand that I am not an expert either, just a jack of all trades, and master of none.

Why does it matter which drive is the hot spare?  If you have 3 identical drives sda, sdb, and sdc, and you remove sda and the raid rebuilds on sdb and sdc, then you replace sda and it becomes your hot spare, the only issue is that the hot spare is a different name.  Functionally it should be exactly the same.

---

### Post by sisyphus1978 on 2009-10-14
One of the drives was given to me. I don't know its' history. Hence use it as a hotspare in a raid1 (for emergencies only). 

As it happens, I ditched the hotspare (it was for learning about raid anyway) and went back to a standard raid1.

---

