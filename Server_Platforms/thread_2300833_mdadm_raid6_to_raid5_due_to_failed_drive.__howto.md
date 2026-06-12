---
title: "mdadm raid6 to raid5 due to failed drive.  howto?"
date: 2015-10-28
forum: Server Platforms
---

### Post by bnut2 on 2015-10-28
This is my current array:
```
[/etc/mdadm]cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdc1[0] sdf1[8] sde1[5] sdh1[3] sdg1[2] sdb1[6]
      9669893120 blocks super 1.2 level 6, 512k chunk, algorithm 2 [7/6] [UUUU_UU]

unused devices: <none>
```


sde1 is the failed drive.

I'd like to reduce this to a raid5 so I can use /dev/sde for something else (another raid, actually).

What's the best way to change this to a raid5 without the sde so that md0 is not degraded?

Cheers,

---

### Post by darkod on 2015-10-28
md0 looks already degraded, it says one member missing from a total of 7. How many members do you have in this raid6?

Also, sde1 is shown as present, so it can not be the missing member.

Post the output of:
```
sudo mdadm --detail /dev/md0
```

That should show more details.

Otherwise note that reshaping raid6 to raid5 like you intend to do is quite dangerous from the point of view that disk(s) can fail during the high load of the reshaping... Make a very good backup first before starting.

---

### Post by bnut2 on 2015-10-28
I guess you're right.  it doesn't appear to be the sde...

```
]mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Jul  1 08:23:27 2012
     Raid Level : raid6
     Array Size : 9669893120 (9221.93 GiB 9901.97 GB)
  Used Dev Size : 1933978624 (1844.39 GiB 1980.39 GB)
   Raid Devices : 7
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Wed Oct 28 13:11:47 2015
          State : clean, degraded
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : server:0  (local to host server)
           UUID : c64d8bc1:fe26faa5:c9f6538f:8cb82480
         Events : 42332

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       6       8       17        1      active sync   /dev/sdb1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       0        0        4      removed
       5       8       65        5      active sync   /dev/sde1
       8       8       81        6      active sync   /dev/sdf1
```


Ultimately, I'm going to tear down this array (built with 2TB drives) and replace is with a larger array (built with 4TB drives).

So let's ask this question differently, then.  I'd like to release the removed drive so that I can replace it with a drive to use in the new array.  Any suggestion on what my next step should be?



Also, what does this show?
```
]mdadm --examine /dev/sdd1 /dev/sdf1 | grep "Role\|Array\ UUID\|dev\/"
/dev/sdd1:
     Array UUID : c64d8bc1:fe26faa5:c9f6538f:8cb82480
   Device Role : Active device 6
/dev/sdf1:
     Array UUID : c64d8bc1:fe26faa5:c9f6538f:8cb82480
   Device Role : Active device 6


```

---

### Post by darkod on 2015-10-28
From this output it's difficult to see the failed disk. I don't see /dev/sda (which could be the OS disk, not part of the array). Also /dev/sdd is missing so that could be your failed disk.

But if you plan to use it in another array, the question is why it failed. Because the disk is damaged/dead, or it simply dropped from the array. You wouldn't install a damaged disk in a new array right?

If you plan to upgrade the whole array with 4TB disks you also have the option to replace one disk at a time. At the end you will end up with 7x4TB array. Do you still want to have 7 disks?

---

### Post by bnut2 on 2015-10-28
/dev/sda is the OS and not part of the array.

I'm not planning on re-using the failed drive.

I am hoping NOT to replace one disk at a time.  I'd rather build a new md1 array using the 4TB drives and retire the drives from md0 (after I transfer the data from md0 to md1).



This array originally had a hot spare.  I had a drive failure and it automatically rebuilt.  I believe that was /dev/sdd

---

### Post by darkod on 2015-10-28
Well, the mdadm --detail shows current array members. If you check all your disks that could point you towards the answer which is the missing disk. You can easily see disks and partitions with:
```
cat /proc/partitions
```

Or other tools like parted, fdisk, etc...

---

