---
title: "RAID 5 - Failed"
date: 2010-08-20
forum: Server Platforms
---

### Post by chj-se on 2010-08-20
I have just come home from vacation, my server storage raid (mdraid) is offline. I have run smart test on the 3 drives, and one of the drives are broken. But I am unable to get the raid started.

**Raid Drives**
/dev/sdb1
/dev/sdc1 (Smart error on this one and assume it is broken)
/dev/sdd1

These drives have been setup as a RAID 5. This is just data drives, no OS drive. I am running Ubuntu 10.04 Server.

```

root@atom:/# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdc1[1](S) sdd1[2](S) sdb1[0](S)
      4395407808 blocks

unused devices: <none>

```

```
root@atom:/# mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

```

```

root@atom:/# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR atom@xxx

# definitions of existing MD arrays

# This file was auto-generated on Tue, 05 Jan 2010 22:58:10 +0100
# by mkconf $Id$
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 level=raid5 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1
```

How can I get the RAID working again? Any tips on what to test? Shouldn't I be able to run with one drive offline?

---

### Post by ratcheer on 2010-08-20
I have never used RAID on such small systems, but when I worked with large UNIX systems I seem to recall that you were supposed to replace the failed drive, then rebuild the RAID array. I was not a system administrator, so I am not intimately familiar with all the exact steps.

We always used RAID 1+0 so we could continue operating 24x7 with a failed drive. If one drive failed, its mirror was always able to support the array until the failed drive could be replaced and the mirror reestablished.

IMHO, 3 drives is not enough for a decent RAID-5 array. But, as a database administrator in a critical systems shop, I kept my systems away from RAID-5.

Tim

---

### Post by Confucius! on 2010-08-20
I ran into something like this not to long ago. I am using mdadm for raid though. What i would suggest you do is to turn your computer off and disconnect the drive you think it bad or having issue. Then see if the array comes back online. If the array does not come back up try the process again a different disk. Once you find the disk that is having issue. I would repartition the disk and run HD tests to make sure the drive is not dead. If you find out that the disk is ok. Try adding it back to the array.

---

### Post by Slonda828 on 2010-08-20
I'm not saying that this will work on all RAIDs, but a RAID 5 is distributed parity. This means that you should be able to shut down your server, remove the bad drive, replace it with a new one, drink water, and drive on. When the RAID controller (HW or SW) boots, it will utilize the distributed parity stored in the other drives and your RAID will function again. By design, most RAID 5s without a hot spare that I have seen work this way. If I am incorrect, as I use only a certain type of RAID here at work, then by all means correct me.

---

### Post by wirelessmonkey on 2010-08-20
```
 
mdadm --assemble /dev/md0

```

...should at least provide failure data, if the array won't reassemble.

---

### Post by psusi on 2010-08-20
> **ratcheer said:**
> I have never used RAID on such small systems, but when I worked with large UNIX systems I seem to recall that you were supposed to replace the failed drive, then rebuild the RAID array. I was not a system administrator, so I am not intimately familiar with all the exact steps.

We always used RAID 1+0 so we could continue operating 24x7 with a failed drive. If one drive failed, its mirror was always able to support the array until the failed drive could be replaced and the mirror reestablished.

IMHO, 3 drives is not enough for a decent RAID-5 array. But, as a database administrator in a critical systems shop, I kept my systems away from RAID-5.

Tim

3 drives is exactly the number for a raid-5 array.  It is the minimum number requires, and also the most safe since each additional drive increases the probability of a double failure.  Given 4 drives, raid 1+0 provides only slightly better fault tolerance than raid-5 since it can handle 2 drives failing, but only if they are the right combination.  It also wastes more space and gives worse throughput than raid-5.

For the OP: the array is not automatically activated since it would have to become degraded and operate without fault tolerance.  You either need to replace the failed drive with a good one, or manually start it.  mdadm --run /dev/md0 should do the trick.

---

