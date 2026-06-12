---
title: "Please help - Ubuntu RAID with mdadm"
date: 2013-03-24
forum: Server Platforms
---

### Post by S2267 on 2013-03-24
Hello everybody,

I am experiencing a strange behavior with software RAID5 in Ubuntu 12.10.

I created a RAID5 device with 3 x 2TB disks (capacity 4 TB + spare).
I added a forth 2TB drive, same model and used   mdadm --add to add it to the existing RAID5.

Now, it I execute a mdadm --detail on the md drive I get:

-----------------------------------------------------------------------
/dev/md0:
        Version : 1.2
  Creation Time : Fri Mar 15 20:52:54 2013
     Raid Level : raid5
**     Array Size : 5860141056 (5588.67 GiB 6000.78 GB)**
  Used Dev Size : 1953380352 (1862.89 GiB 2000.26 GB)
**   Raid Devices : 4**
**  Total Devices : 4**
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sun Mar 24 10:24:56 2013
          State : active 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : Hulk:0  (local to host Hulk)
           UUID : 4db896f2:38b1dfc5:3552ef0c:92418427
         Events : 125988


    Number   Major   Minor   RaidDevice State
       0       8       97        0      active sync   /dev/sdg1
       1       8      113        1      active sync   /dev/sdh1
       3       8      145        2      active sync   /dev/sdj1
       4       8      129        3      active sync   /dev/sdi1
-----------------------------------------------------------------------


It seems like all four drive are correctly seen by the system.
But I believe I should see a total capacity (Array Size) of 8 TB (with Used Dev Size of 2TB) right?

The RAID is mounted under /var?raid and df show a total capacity of 4TB (as it was before I added the 4th drive).

Any idea?


Whan I do a

mdadm --grow /dev/md0 --raid-devices=4
it says

mdadm: /dev/md0: no change requested


I tried to google for smilar problem, but couldn't find any solution.

I hope somebody could head me to a solution.
 
Thank you.
Stefano

---

### Post by darkod on 2013-03-24
I think the array size is correct at 6TB since it doesn't count the parity disk in raid5 (the fourth disk). The Used Dev size looks correct at 2TB since I think that shows the parity capacity.

As for what df shows (4TB) you probably only need to extend the filesystem. Unmount /dev/md0 and try something like:
```
sudo resize2fs /dev/md0
```

That should extend it to the max size.

---

### Post by S2267 on 2013-03-24
Darko, a huge

**[SIZE=7]THANK YOU!!![/SIZE]**

I thought mdadm took also care of expanding the md partition.
I was lost for a few hours before posting my message and you solved my problem in 20 minutes.
Amazing. Thanks a lot again.
Stefano

---

