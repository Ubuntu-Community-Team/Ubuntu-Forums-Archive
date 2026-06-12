---
title: "Mdadm Reshape stall. What to do?"
date: 2012-04-16
forum: Server Platforms
---

### Post by mcordell on 2012-04-16
Hi guys,

So I was trying to reshape my raid-5 to raid6.
The array was orginally 4x2TB raid-5.
I added another drive and set it to reshape to raid-6. Everything was going fine, if not a bit slow during the reshape. Over the last hr, it appears to have completely stopped.


Here's the best I can do diagnostically:

```

sudo mdadm -D /dev/md0

```

gives:

```

/dev/md0:
        Version : 1.2
  Creation Time : Mon Jan  9 13:41:49 2012
     Raid Level : raid6
     Array Size : 5860536960 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953512320 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Mon Apr 16 16:02:43 2012
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 128K

 Reshape Status : 18% complete
     New Layout : left-symmetric

           Name : GlaDoS:0  (local to host GlaDoS)
           UUID : d7b5c7fc:144c0df7:09692912:dc1973a0
         Events : 330014

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       4       8       65        3      active sync   /dev/sde1
       5       8       81        4      spare rebuilding   /dev/sdf1

```


```

cat /proc/mdstat

```

gives:

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdf1[5] sdb1[0] sdc1[1] sdd1[2] sde1[4]
      5860536960 blocks super 1.2 level 6, 128k chunk, algorithm 18 [5/4] [UUUU_]
      [===>.................]  reshape = 18.6% (364929024/1953512320) finish=1430090.5min speed=18K/sec
      
unused devices: <none>

```


Where it has stayed on 364929024 and the speed just keeps going down, and the finish just keeps going up :mad:

dmesg output:
```

[179609.583336] mdadm: sending ioctl 1261 to a partition!
[179609.583342] mdadm: sending ioctl 1261 to a partition!
[179713.489070] mdadm: sending ioctl 1261 to a partition!
[179713.489076] mdadm: sending ioctl 1261 to a partition!
[181132.439933] mdadm: sending ioctl 1261 to a partition!
[181132.439939] mdadm: sending ioctl 1261 to a partition!
[181132.843719] mdadm: sending ioctl 1261 to a partition!
[181132.843724] mdadm: sending ioctl 1261 to a partition!
[181132.844974] mdadm: sending ioctl 1261 to a partition!
[181132.844978] mdadm: sending ioctl 1261 to a partition!
[181132.888338] mdadm: sending ioctl 1261 to a partition!
[181132.888343] mdadm: sending ioctl 1261 to a partition!
[181132.888529] mdadm: sending ioctl 1261 to a partition!
[181132.888530] mdadm: sending ioctl 1261 to a partition!
[181177.816665] scsi_verify_blk_ioctl: 14 callbacks suppressed
[181177.816670] mdadm: sending ioctl 1261 to a partition!
[181177.816675] mdadm: sending ioctl 1261 to a partition!
[181178.250449] mdadm: sending ioctl 1261 to a partition!
[181178.250454] mdadm: sending ioctl 1261 to a partition!
[181178.251750] mdadm: sending ioctl 1261 to a partition!
[181178.251755] mdadm: sending ioctl 1261 to a partition!
[181178.286923] mdadm: sending ioctl 1261 to a partition!
[181178.286928] mdadm: sending ioctl 1261 to a partition!
[181178.287380] mdadm: sending ioctl 1261 to a partition!
[181178.287384] mdadm: sending ioctl 1261 to a partition!
[181624.481216] md: md0 still in use.
[181624.485800] scsi_verify_blk_ioctl: 110 callbacks suppressed
[181624.485804] mdadm: sending ioctl 1261 to a partition!
[181624.485809] mdadm: sending ioctl 1261 to a partition!
[181873.550277] mdadm: sending ioctl 1261 to a partition!
[181873.550283] mdadm: sending ioctl 1261 to a partition!
[181881.664073] mdadm: sending ioctl 1261 to a partition!
[181881.664079] mdadm: sending ioctl 1261 to a partition!
[182324.231769] mdadm: sending ioctl 1261 to a partition!
[182324.231775] mdadm: sending ioctl 1261 to a partition!

```

```

iostat -cdmx 60 2

```

shows 0's for all of the array disks across the board, which really proves that nothing is happening with them





Other thoughts:
I had the backupfile on a usb disk that apparently got unplugged while I was moving furniture near the server, could this be the problem?

The array is mounted and I can read and write fine as far as I can tell.




Should I reboot? 
Should I kill and restart the reshape somehow (if so, how?) ?
Am I in danger here with data loss? 


Any help would be much appreciated


Thanks,
Mike

---

### Post by mcordell on 2012-04-16
Solved my own problem I think:

Took the array down by unmounting and then

```

sudo mdadm -S /dev/md0

```

Then I tried assembling

 ```

sudo mdadm -assemble 

```

```

mdadm --assemble /dev/md0 /dev/sd[bcdef]1 --backup-file=/media/external/md0backup

```

This failed and I got the Failed to restore critical section for reshape, sorry.
And then I started sweating.... 

So after turning on verbose mode I get:

```

mdadm: too-old timestamp on backup-metadata on /media/external/md0backup
mdadm: Failed to find backup of critical section
mdadm: Failed to restore critical section for reshape, sorry.

```

After some googling: the solution was to log on as root (su).
And the following:
```

export MDADM_GROW_ALLOW_OLD=1

```

And then re-ran with the force flag
```

mdadm --assemble /dev/md0 /dev/sd[bcdef]1 -vv -f --backup-file=/media/external/md0backup

```

Much success:
```

dadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm:/dev/md0 has an active reshape - checking if critical section needs to be restored
mdadm: accepting backup with timestamp 1334611281 for array with timestamp 1334620289
mdadm: restoring critical section
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 4 drives (out of 5) and 1 rebuilding.

```

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdb1[0] sdf1[5] sde1[4] sdd1[2] sdc1[1]
      5860536960 blocks super 1.2 level 6, 128k chunk, algorithm 18 [5/4] [UUUU_]
      [===>.................]  reshape = 18.6% (365002752/1953512320) finish=8481.4min speed=3120K/sec

```


Whew

---

