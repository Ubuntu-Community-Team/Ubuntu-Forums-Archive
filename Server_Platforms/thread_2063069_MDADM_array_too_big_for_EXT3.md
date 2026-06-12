---
title: "MDADM array too big for EXT3"
date: 2012-09-26
forum: Server Platforms
---

### Post by JoyMonkey on 2012-09-26
I have an odd problem.

I have an MDADM RAID-5 array with 9 2TB devices. The MD device is formatted ext3. I have 16TB of usable space and 2TB of parity.

I decided to add a 10th 2TB device to increase space. So I added one to the array. As usual, it showed as a Spare and then I grew the MD device with...
```
mdadm --grow /dev/md1 --raid-devices=10
```
I unmounted the MD device and ran e2fsck, which came up clean. Then I went to resize2fs to expand the filesystem from 16TB to 18TB. Then I realized something awful...
```
resize2fs: New size too large to be expressed in 32 bits
```
EXT3 filesystems can not go over 16TB. #-o

I panicked and removed the 10th device from the array, thinking I could easily switch it to a Spare somehow. But it's still set at 10 devices, so is showing as degraded.
Here is the current status...
```
user@xubu:~$ sudo mdadm --detail /dev/md2
/dev/md2:
        Version : 0.90
  Creation Time : Wed Apr 14 18:18:00 2010
     Raid Level : raid5
     Array Size : 17581607424 (16767.13 GiB 18003.57 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 10
  Total Devices : 9
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Wed Sep 26 08:02:58 2012
          State : clean, degraded 
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : cc0ab622:558008a7:2e29483d:f114274d (local to host storage)
         Events : 0.605489

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8      113        1      active sync   /dev/sdh1
       2       8       81        2      active sync   /dev/sdf1
       3       8       65        3      active sync   /dev/sde1
       4       8      161        4      active sync   /dev/sdk1
       5       8       49        5      active sync   /dev/sdd1
       6       8      145        6      active sync   /dev/sdj1
       7       8       17        7      active sync   /dev/sdb1
       8       8        1        8      active sync   /dev/sda1
       9       0        0        9      removed
```

**I need to get it back to 9 devices and use this 10th drive as a Spare. Is it possible to un-grow my array without damaging data?**

---

### Post by JoyMonkey on 2012-09-26
I think I found my answer in this very useful blog post...
[http://www.starcoder.com/wordpress/2011/08/shrinking-a-linux-software-raid-volume/](http://www.starcoder.com/wordpress/2011/08/shrinking-a-linux-software-raid-volume/)

If I'm reading that correctly I should be able to resize the array to use 9 devices by first getting the expected array-size for 9 devices by doing...
```
mdadm --grow -n9 /dev/md2
```
then setting the array to that size...
```
mdadm --grow /dev/md2 --array-size 15628095488
```
and then doing a reshape with...
```
mdadm --grow -n9 /dev/md2 --backup-file /tmp/mdadm.backup
```

---

