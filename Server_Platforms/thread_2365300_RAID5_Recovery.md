---
title: "RAID5 Recovery"
date: 2017-07-05
forum: Server Platforms
---

### Post by kevmev122 on 2017-07-05
Hi guys,

I have a home server that failed about 3-4 years ago; but due to personal circumstances and the fact that I had most things backed up already, I didn't bother trying to fix it. Now I'm in a position to try to fix it, but I've forgotten most of the basic Linux knowledge I acquired while I was building this server. So I'm hoping for a little help.

I built the server with Ubuntu Server 10.04.4; I had 4 x 1TB drives in a RAID5 configuration, and an 80GB disk presumably for the Ubuntu Server OS. When the server failed, I found that one of the 1TB drives had a SMART failure, and two other drives had bad sectors but are still usable. Skip ahead to now, and I've removed the failed drive and replaced with a tested and confirmed to be working 1TB drive - I didn't replace the 2 drives with bad sectors. Now when I turn on the server, this is what I see:
```
fsck from util-linux-ng 2.17.2
/dev/sda2: clean, 570369/4644864 files, 2029691/18561024 blocks
The disk drive for /home is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
```

I figure this means the RAID array has not mounted, so I press M and type in fdisk -l to see what's going on - this is the output:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads. 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0161

    Device Boot    Start    End    Blocks        ID    System
/dev/sda1        1    487    3905536        82    Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2    *        487    9730    74244096    83    Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads. 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b4cd

    Device Boot    Start    End    Blocks        ID    System
/dev/sdb1        1    121602    976760832    fd    Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads. 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads. 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ecd2

    Device Boot    Start    End    Blocks        ID    System
/dev/sde1        1    121602    976760832    fd    Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads. 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f766

    Device Boot    Start    End    Blocks        ID    System
/dev/sdd1        1    121602    976760832    fd    Linux raid autodetect
```

And this is the output when I type in cat /proc/mdstat:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[2](S) sdb1[0](S) sde1[3](S)
      2930282304 blocks

unused devices: <none>
```

So I believe the raid is inactive, and I need to partition the new disk and then rebuild the raid - is this correct? How do I partition the new disk to be part of the raid array? I read that I need to use mdadm --manage to add the disk to the array - is this correct? Are the data on the raid still retrievable?

Thank you in advance for any help you can provide. This is not urgent as I've already got whatever I had in there backed-up; it's more for me to learn how to recover from a raid failure.

---

### Post by darkod on 2017-07-05
First I would check the existing information on the existing partitions that were part of the raid. Partitioning and adding the new disk is the least of your problems.

Post the output of:
```
sudo mdadm --examine /dev/sd[bde]1
```

That will show you info from the mdadm superblock on the three partitions. We can use that to estimate if you can re-assemble the array.

---

### Post by kevmev122 on 2017-07-05
Thank you for the prompt reply. Here is the output of mdadm --examine as requested:
```
/dev/sdb1:    
    Magic : a92b4efc
    Version : 00.90.00
    UUID : 80f3ad7e:fb0d4b56:6dd8f1b6:439d720d
    Creation Time : Fri Jun 25 00:10:07 2010
    Raid Level : raid5
    Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
    Array Size : 2930282304 (2794.54 GiB 3000.61 GB)
    Raid Devices : 4
    Total Devices : 4
    Preferred Minor : 0

    Update Time : Sun Jun 9 12:15:53 2013
    State : clean
    Active Devices : 2
    Working Devices : 2
    Failed Devices : 2
    Spare Devices : 0
    Checksum : aeb33b8b - correct
    Events : 2310

    Layout : left-symmetric
    Chunk Size : 64K

    Number    Major    Minor    RaidDevice    State
this    0    8    17    0        active sync /dev/sdb1

0    0    8    17    0        active sync /dev/sdb1
1    1    0    0    1        faulty removed
2    2    0    0    2        faulty removed
3    3    8    65    3        active sync /dev/sde1


/dev/sdd1:
    Magic : a92b4efc
    Version : 00.90.00
    UUID : 80f3ad7e:fb0d4b56:6dd8f1b6:439d720d
    Creation Time : Fri Jun 25 00:10:07 2010
    Raid Level : raid5
    Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
    Array Size : 2930282304 (2794.54 GiB 3000.61 GB)
    Raid Devices : 4
    Total Devices : 4
    Preferred Minor : 0

    Update Time : Sun Jun 9 11:56:14 2013
    State : clean
    Active Devices : 4
    Working Devices : 4
    Failed Devices : 0
    Spare Devices : 0
    Checksum : aeb336f0 - correct
    Events : 2304

    Layout : left-symmetric
    Chunk Size : 64K

    Number    Major    Minor    RaidDevice    State
this    2    8    49    2        active sync /dev/sdd1

0    0    8    17    0        active sync /dev/sdb1
1    1    8    33    1        active sync
2    2    8    49    2        active sync /dev/sdd1
3    3    8    65    3        active sync /dev/sde1


/dev/sde1:
    Magic : a92b4efc
    Version : 00.90.00
    UUID : 80f3ad7e:fb0d4b56:6dd8f1b6:439d720d
    Creation Time : Fri Jun 25 00:10:07 2010
    Raid Level : raid5
    Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
    Array Size : 2930282304 (2794.54 GiB 3000.61 GB)
    Raid Devices : 4
    Total Devices : 4
    Preferred Minor : 0

    Update Time : Sun Jun 9 12:15:53 2013
    State : clean
    Active Devices : 2
    Working Devices : 2
    Failed Devices : 2
    Spare Devices : 0
    Checksum : aeb33bc1 - correct
    Events : 2310

    Layout : left-symmetric
    Chunk Size : 64K

    Number    Major    Minor    RaidDevice    State
this    3    8    65    3        active sync /dev/sde1

0    0    8    17    0        active sync /dev/sdb1
1    1    0    0    1        faulty removed
2    2    0    0    2        faulty removed
3    3    8    65    3        active sync /dev/sde1
```

It's interesting that /sdd1 is reporting 4 active and working devices while /sdb1 and /sde1 are both reporting 2 working and 2 failed devices. Why is it doing that?

Thanks again for the help.

---

### Post by darkod on 2017-07-05
The Events are little different but close enough to be able to assemble. But if two disks have bad sectors not sure how long it will work before failing again and there is big possibility of data to be corrupted.

If you want to, you can try assembling it with:
```
sudo mdadm --stop /dev/md0
sudo mdadm --verbose --assemble /dev/md0 /dev/sdb1 /dev/sdd1 /dev/sde1
```

If that doesn't work, try forcing it by adding --force:
```
sudo mdadm --stop /dev/md0
sudo mdadm --verbose --assemble --force /dev/md0 /dev/sdb1 /dev/sdd1 /dev/sde1
```

---

### Post by kevmev122 on 2017-07-05
I stopped /dev/md0 and tried the first command to assemble and it gave me this output:
```

mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: Cannot open /dev/sdb1: Device or resource busy
```

Then I tried stopping /dev/md0 and forcing it to assemble and it gave me this output:
```

mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: forcing event count in /dev/sdd1(2) from 2304 upto 2310
mdadm: Couldn't open /dev/sdd1 for write - not updating
mdadm: Cannot open /dev/sdb1: Device or resource busy
```

The error sounds like a permissions thing even though I'm doing all this as root; don't seem to be a bad sector-related error.

---

### Post by darkod on 2017-07-05
Hmmm, device busy is usually if it is mounted... Can you confirm it is not mounted?

```
df -h
```

Right now i don't know how to check if anything else is using it.

And that couldn't open message might be connected to the health of the disk. It says it can't open it for write which is little worrying too.

---

### Post by kevmev122 on 2017-07-05
After running df -h I get this output:
```

Filesystem     Size     Used     Avail     Use%     Mounted on
/dev/sda2       70G     6.7G       60G      11%     /
none           950M     516K      949M       1%     /dev
none           955M        0      955M       0%     /dev/shm
none           955M      16K      955M       1%     /var/run
none           955M        0      955M       0%     /var/lock
none           955M        0      955M       0%     /lib/init/rw
```
This looks like the 80GB drive that the Ubuntu Server OS on it. Doesn't appear to be any of the 1TB drives at all.

---

