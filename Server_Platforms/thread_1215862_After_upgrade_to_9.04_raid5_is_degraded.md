---
title: "After upgrade to 9.04 raid5 is degraded"
date: 2009-07-17
forum: Server Platforms
---

### Post by RocKKer on 2009-07-17
I upgraded from 8.10 to 9.04 last night.
Now a drive in my R5 array is removed and the array is degraded (this is a 4 disk R5 array):

```
root@media:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Mar  3 18:59:55 2009
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 17 13:12:05 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 0749982d:e5e17146:462a36bb:f8f383a4 (local to host media)
         Events : 0.25068

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```

I really don't know if it was degraded/removed before the upgrade or not.

After the reboot I had to assemble and scan to bring the degraded array up:

```
mdadm -A -s
```

I then tried to remove the offending disk then add it back in, but the remove failed:

```
mdadm /dev/md0 -r /dev/sda1

mdadm: hot remove failed for /dev/sda1: No such device or address
```


mdstat info:
```
root@media:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sde1[3] sdd1[2]
      2930279808 blocks level 5, 128k chunk, algorithm 2 [4/3] [_UUU]
      
md_d0 : inactive sda1[0](S)
      976759936 blocks
       
unused devices: <none>
```


Unsure how to proceed to fix this?



EDIT (7/17/09 - 18:53)

Seems I had two problems - in ubunto 9.04, they moved where mdadm.conf lives, used to be in /etc/mdadm.conf, now it's in /etc/mdadm/mdadm.conf

easy way to fix for me (with only one raid array is):

```
cat /etc/mdadm.conf > /etc/mdadm/mdadm.conf
```

then reboot, array starts up auto now. 


Then I had to:
```
mdadm --manage /dev/md0 --add /dev/sda1
```

Which re-added my drive back into the array and my array is syncing now. :D


Pure RAID Sweetness!!

---

### Post by fjgaude on 2009-07-19
Wonderful the way we learn something new whenever we run into a situation... praise life!

---

