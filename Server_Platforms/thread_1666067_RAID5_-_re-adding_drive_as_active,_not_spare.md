---
title: "RAID5 - re-adding drive as active, not spare"
date: 2011-01-13
forum: Server Platforms
---

### Post by habrys on 2011-01-13
I have a little nice Ubuntu server with 6x 1TB drives assebmbled into a RAID5 array. Recently SATA cable of one of the drives failed. So I ordered a new cable and ran the server in degraded mode for a few days. Like this:
```
/dev/md0:
        Version : 00.90
  Creation Time : Sat Sep 19 10:39:11 2009
     Raid Level : raid5
     Array Size : 4883812480 (4657.57 GiB 5001.02 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jan 13 12:02:04 2011
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 8c78154a:440b8913:01f9e43d:ac30fbff (local to host server)
         Events : 0.2058164

    Number   Major   Minor   RaidDevice State
       0       8       48        0      active sync   /dev/sdd
       1       8       32        1      active sync   /dev/sdc
       2       8       16        2      active sync   /dev/sdb
       3       8       80        3      active sync   /dev/sdf
       4       8       96        4      active sync   /dev/sdg
       5       0        0        5      removed

```

Finally the new cable arrived and I tried to add the 6th drive to the array again. In the meantime I rearranged all the SATA cables inside the server, so order of drives (sdb, sdc and so on) was different, than before. For better airflow. After adding the 6th drive it shows up as spare (not active), and on the 6th, instead of 5th position. And starts rebuilding.
```
habrys@server:~/bin$ sudo mdadm --add /dev/md0 /dev/sde
mdadm: re-added /dev/sde
habrys@server:~/bin$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Sep 19 10:39:11 2009
     Raid Level : raid5
     Array Size : 4883812480 (4657.57 GiB 5001.02 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jan 13 12:18:30 2011
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 8c78154a:440b8913:01f9e43d:ac30fbff (local to host server)
         Events : 0.2058236

    Number   Major   Minor   RaidDevice State
       0       8       48        0      active sync   /dev/sdd
       1       8       32        1      active sync   /dev/sdc
       2       8       16        2      active sync   /dev/sdb
       3       8       80        3      active sync   /dev/sdf
       4       8       96        4      active sync   /dev/sdg
       6       8       64        5      spare rebuilding   /dev/sde

```

I'd like the 6th drive to be active, not spare, like before. Should I just wait for rebuild to be finished (it can easily take over 1 day)? Or should I add it somehow differently to be active immediately?

I'm not sure, but I think as I simulated failures unplugging one of the disk, after plugging it in again, the "failed" drive was active again and rebuilding was started as well of course. But it was 2 years ago, so...

The array works just fine for now - I can access files, etc. But I suspect, that in this state if another cable or drive fails, it won't survive anymore. Even after rebuilding is finished, but the 6th drive stays is still marked as "spare". Right?

---

### Post by rubylaser on 2011-01-13
The output of
```
watch cat /proc/mdstat
```
will show you that it's already adding the spare back to the array.  Meaning that the spare will become active once it has synced.  Because the hard drive has been out of the array, it needs to resync.  It just takes a long time to resync a multi terabyte array.  Based on what speed mdadm is showing you for the rebuild process, you can make it go faster you can turn on the bitmap option.

```
mdadm --grow --bitmap=internal /dev/md0
```

Once array rebuild or fully synced, disable bitmaps:
```
mdadm --grow --bitmap=none /dev/md0
```

Also, you can adjust the min/max sync speed options...
```
echo 200000 > /sys/block/md0/md/sync_speed_max 
echo 50000 > /sys/block/md0/md/sync_speed_min
```

It's already rebuilding properly, so you could just let it finish, and it will be added back to the array properly.

---

### Post by habrys on 2011-01-13
> **rubylaser said:**
> It's already rebuilding properly, so you could just let it finish, and it will be added back to the array properly.

That's true. Rebuilding is finished and all 6 devices are active now. Even numbered as before - from 0 to 5, not from 1 to 6. I like this Linux software raid more and more :)

Thanks for explanations, rubylaser.

---

### Post by rubylaser on 2011-01-13
I'm glad that helped, and mdadm is awesome.  I've been running it for years and it's worked great.

---

### Post by rubylaser on 2011-01-13
I'm glad that helped, and mdadm is awesome.  I've been running it for years and it's worked great.

---

