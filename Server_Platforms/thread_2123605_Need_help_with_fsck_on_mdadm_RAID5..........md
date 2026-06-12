---
title: "Need help with fsck on mdadm RAID5........."
date: 2013-03-08
forum: Server Platforms
---

### Post by hogfan on 2013-03-08
Ok, long story short.  I had a single drive fail in my RAID5 array.  I have already completed the process of removing the failed drive from the array, replacing it it with a new drive, and the array successfully rebuilt over night.    Now I am wanting to run a fsck on /dev/md0 just as a precaution.  However, I keep getting device or resource busy when trying to unmount:

/dev/md0
/mnt/raid

I was able to successfully unmount the samba share I had at /export/media-raid.

After unmounting the Samba share,  I went ahead and stop the smbd service.  

What am I missing?  Why can't I umount the raid md0 device or /mnt/raid?  I have done this once before after a power outage but didn't document it at the time. I need to ensure everything is unmounted so I can run fsck on the /dev/md0 I believe.

My RAID 5 array contains 4 x 2TB drives and looks like this:

sudo mdadm cat /proc/mdstat

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[1] sdd1[2] sde1[3] sdb1[0]
      5860540224 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
```

sudo mdadm --detail /dev/md0
```
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Thu Mar  1 21:56:54 2012
     Raid Level : raid5
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Fri Mar  8 11:09:19 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 64K


           UUID : 2068b124:43ab2872:50b15dd6:9583be21
         Events : 0.6543


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
```


Any help is appreciated.  I just want to run a filesystem check to make sure all is good after replacing the failed drive. Thanks in advance.

-hogfan

---

### Post by Cheesemill on 2013-03-08
Try doing...
```
lsof | grep /mnt/raid
```
To see if any processes have open files on the array.

Also can you tell us what output you are getting when trying to unmount.

---

### Post by hogfan on 2013-03-09
Ok, I ran that command and it returned nothing, so there did not appear to be any processes using the device.  I reboot the box and unmount everything again, and this time I worked.  When I ran fsck I didn't get any messages about it still be mounted and it immediately came back clean, so I think I'm good to go.  Something must have had a lock on the device.  If this was a windows box I would have rebooted it immediately, but rebooting is my last resort on linux because it shouldn't normally be necessary. Thanks.

-hogfan

---

