---
title: "Need help recovering RAID 5 array"
date: 2007-05-20
forum: Server Platforms
---

### Post by Luft on 2007-05-20
I have three 120 GB dirves in a software RAID 5 configuration.  It looks like I have a hardware failure on one of my drives.  I was backing up all of the data because I was going to rebuild the server using three 500 GB drives and I guess the data transfer was too much for it.

Anyway I tried using mdadm to try to rebuild the array but even after rebuilding it the failed drive can't be used so I figure it's probably hardware.  

My questions are: If I can't find another 120 GB drive can I use a larger one and simply partition it so it has a 120 GB partition?  Or do I even need to partition it?

How do I identify the physical drive that has failed so that I can replace the correct one?

Any step by step instructions would really be appreciated.

Thanks!

---

### Post by mbradlcu on 2007-05-22
here's my notes (stolen from here [http://home.gagme.com/greg/linux/raid-lvm.php](http://home.gagme.com/greg/linux/raid-lvm.php)),, and yes you can use a larger drive:

Handling a Drive Failure
As everything eventually does break (some sooner than others) a drive in the array will fail. It is a very good idea to run smartd on all drives in your array (and probably ALL drives period) to be notified of a failure or a pending failure as soon as possible. You can also manually fail a partition, meaning to take it out of the RAID array, with the following command:

# mdadm /dev/md0 -f /dev/hdb1
mdadm: set /dev/hdb1 faulty in /dev/md0

Once the system has determined a drive has failed or is otherwise missing (you can shut down and pull out a drive and reboot to similate a drive failure or use the command to manually fail a drive above it will show something like this in mdadm:

# mdadm --detail /dev/md0
Update Time : Wed Jun 15 11:30:59 2005
State : clean, degraded
Active Devices : 2
Working Devices : 2
Failed Devices : 1
Spare Devices : 0
.
.
Number Major Minor RaidDevice State
0 3 1 0 active sync /dev/hda1
1 0 0 - removed
2 33 65 2 active sync /dev/hdf1

You'll notice in this case I had /dev/hdb fail. I replaced it with a new drive with the same capacity and was able to add it back to the array. The first step is to partition the new drive just like when first creating the array. Then you can simply add the partition back to the array and watch the status as the data is rebuilt onto the newly replace drive.

# mdadm /dev/md0 -a /dev/hdb1
# mdadm --detail /dev/md0
Update Time : Wed Jun 15 12:11:23 2005
State : clean, degraded, recovering
Active Devices : 2
Working Devices : 3
Failed Devices : 0
Spare Devices : 1

---

