---
title: "Unable to Rebuild Raid 1"
date: 2012-06-26
forum: Server Platforms
---

### Post by nclucid on 2012-06-26
Hello,

I am running Ubuntu Server 12.04. I installed with a software raid1 array. To test the array I pulled one of the drives and made sure it would boot. I then tried the same with the other drive. Both booted as expected.

When I try to rebuild the array I am running into issues. Some background info:

```

~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb3[1]
      479008632 blocks super 1.2 [2/1] [_U]

md1 : active raid1 sdb1[1]
      975860 blocks super 1.2 [2/1] [_U]

unused devices: <none>

``````

~# mdadm --query --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu May 24 11:46:44 2012
     Raid Level : raid1
     Array Size : 479008632 (456.82 GiB 490.50 GB)
  Used Dev Size : 479008632 (456.82 GiB 490.50 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Tue Jun 26 15:52:31 2012
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : DunnAppraisals:0
           UUID : d154ced9:cd0fcc08:0f4f2986:cae8dc98
         Events : 14729

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       19        1      active sync   /dev/sdb3

``````

~# mdadm --query --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Thu May 24 11:49:04 2012
     Raid Level : raid1
     Array Size : 975860 (953.15 MiB 999.28 MB)
  Used Dev Size : 975860 (953.15 MiB 999.28 MB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Tue Jun 26 15:51:38 2012
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : DunnAppraisals:1
           UUID : 741ee215:7c42dd3a:f7ec0cff:5a5b9ae9
         Events : 117

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1

```To me this looks like md0 is missing sda3 and md1 is missing sda1, so I tried to add them:

```

~# mdadm --manage /dev/md0 --add /dev/sda3
mdadm: /dev/sda3 reports being an active member for /dev/md0, but a --re-add fails.
mdadm: not performing --add as that would convert /dev/sda3 in to a spare.
mdadm: To make this a spare, use "mdadm --zero-superblock /dev/sda3" first.

```I get the same result when trying to add sda1 to md1. I also tried --force. How is sda3 an active member of md0? Nowhere in /proc/mdstat or the mdadm query does it hint that. Thinking I am crazy or am getting something backwards, I tried to add sdb3 to md0:

```

~# mdadm --manage /dev/md0 --add /dev/sdb3
mdadm: Cannot open /dev/sdb3: Device or resource busy

```Again I get the same result when adding sdb1 to md1. Last thing that I tried was to add nodmraid to /etc/default/grub ("GRUB_CMDLINE_LINUX_DEFAULT="nodmraid quiet splash"), update-grub, reboot and try everything again. Nada. (As a side note, I tried entering nodmraid straight into the grub command line and it said it wasn't a valid command)

Thanks in advance for reading this and taking the time to respond. This is my first time managing a raid in linux, be gentle.

---

### Post by darkod on 2012-06-26
If I am not mistaken when reinserting the same disk it's better to use the --re-add command. So try something like:
mdadm --manage /dev/md0 --re-add /dev/sda3

---

### Post by nclucid on 2012-06-26
Thanks for the reply darkod. No luck though...
```

~# mdadm --manage /dev/md0 --re-add /dev/sda3
mdadm: --re-add for /dev/sda3 to /dev/md0 is not possible

```

---

### Post by rubylaser on 2012-06-26
> **darkod said:**
> If I am not mistaken when reinserting the same disk it's better to use the --re-add command. So try something like:
mdadm --manage /dev/md0 --re-add /dev/sda3

This only works it there is an intent bitmap, and cat /proc/mdstat doesn't reflect one, so I'm sure one doesn't exist.  What's the state of the superblock on each disk?

```
mdadm -E /dev/sd[ab]1
mdadm -E /dev/sd[ab]3
```

If the event counters are similar, it's probably easiest to boot from the LiveCD, install mdadm, and then reassemble each array.  Once they are in sync, you can reboot, and all should be well.

---

### Post by nclucid on 2012-06-27
State of all superblocks is clean. Events:

sda1 - 77
sdb1 - 127
sda3 - 177
sdb3 - 22011

Based on that, should I install mdadm from the LiveCD? Seems like sdb3 is a little out of whack...

Both disks are identical at this point (for all practical purposes). Would another option be to wipe the disk, re-partition and then build the raid? How could I do this safely?

---

### Post by darkod on 2012-06-27
> **nclucid said:**
> State of all superblocks is clean. Events:

sda1 - 77
sdb1 - 127
sda3 - 177
sdb3 - 22011

Based on that, should I install mdadm from the LiveCD? Seems like sdb3 is a little out of whack...

Both disks are identical at this point (for all practical purposes). Would another option be to wipe the disk, re-partition and then build the raid? How could I do this safely?

rubylaser mentioned that option if the counters are similar. They look very different especially for md0.

Since this is only raid1, assuming the sdb disk has the full data, you could zero the superblock of sda1 and sda3 for example and try to add the disk as if it was new.

But lets wait what rubylaser says, he's the expert for raid.

---

### Post by rubylaser on 2012-06-27
> **darkod said:**
> rubylaser mentioned that option if the counters are similar. They look very different especially for md0.

Since this is only raid1, assuming the sdb disk has the full data, you could zero the superblock of sda1 and sda3 for example and try to add the disk as if it was new.

But lets wait what rubylaser says, he's the expert for raid.

+1. I would zero the superblock on both of those sda partitions (sda1 and sda3), and then add them back to their appropriate arrays just as darkod has said.  Being slightly different on the counters isn't typically a being deal for putting an array back together, but being off by over 20,000 is :)

---

### Post by nclucid on 2012-06-27
> **darkod said:**
> 
Since this is only raid1, assuming the sdb disk has the full data, you could zero the superblock of sda1 and sda3 for example and try to add the disk as if it was new.


Worked like a charm!

```

~# mdadm --zero-superblock /dev/sda1
~# mdadm --zero-superblock /dev/sda3
~# mdadm --manage /dev/md0 --add /dev/sda3
mdadm: added /dev/sda3
~# mdadm --manage /dev/md1 --add /dev/sda1
mdadm: added /dev/sda1

``````

~# watch -n1 cat /proc/mdstat
Every 1.0s: cat /proc/mdstat                                                                                                                                                   Wed Jun 27 08:56:12 2012

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda3[2] sdb3[1]
      479008632 blocks super 1.2 [2/1] [_U]
      [=>...................]  recovery =  7.8% (37384832/479008632) finish=61.8min speed=119022K/sec

md1 : active raid1 sda1[2] sdb1[1]
      975860 blocks super 1.2 [2/1] [_U]
        resync=DELAYED

unused devices: <none>

```Looks like it's rebuilding as expected. Thank you Darko and rubylaser for the quick and extremely helpful responses :smile:

---

### Post by rubylaser on 2012-06-27
Glad you got it working :)

---

### Post by steeldriver on 2012-06-27
pmji but would one of you good folks be able to give a short explanation of what the RAID event counters are counting? how do they relate (if at all) to the various SMART disk counters? tia

---

### Post by rubylaser on 2012-06-27
> **steeldriver said:**
> pmji but would one of you good folks be able to give a short explanation of what the RAID event counters are counting? how do they relate (if at all) to the various SMART disk counters? tia

The result of monitoring the arrays can lead to the generation of events.  These are the types of events.

> The different events are:

**DeviceDisappeared**
An md array which previously was configured appears to no longer be configured. (syslog priority: Critical)
If mdadm was told to monitor an array which is RAID0 or Linear, then it will report DeviceDisappeared with the extra information Wrong-Level. This is because RAID0 and Linear do not support the device-failed, hot-spare and resync operations which are monitored.

**RebuildStarted**
An md array started reconstruction. (syslog priority: Warning)
**RebuildNN**
Where NN is a two-digit number (ie. 05, 48 ). This indicates that rebuild has passed that many percent of the total. The events are generated with fixed increment since 0. Increment size may be specified with a commandline option (default is 20). (syslog priority: Warning)
**RebuildFinished**
An md array that was rebuilding, isn't any more, either because it finished normally or was aborted. (syslog priority: Warning)
**Fail**
An active component device of an array has been marked as faulty. (syslog priority: Critical)

**FailSpare**
A spare component device which was being rebuilt to replace a faulty device has failed. (syslog priority: Critical)
**SpareActive**
A spare component device which was being rebuilt to replace a faulty device has been successfully rebuilt and has been made active. (syslog priority: Info)
**NewArray**
A new md array has been detected in the /proc/mdstat file. (syslog priority: Info)
**DegradedArray**
A newly noticed array appears to be degraded. This message is not generated when mdadm notices a drive failure which causes degradation, but only when mdadm notices that an array is degraded when it first sees the array. (syslog priority: Critical)
**MoveSpare**
A spare drive has been moved from one array in a spare-group or domain to another to allow a failed drive to be replaced. (syslog priority: Info)
**SparesMissing**
If mdadm has been told, via the config file, that an array should have a certain number of spare devices, and mdadm detects that it has fewer than this number when it first sees the array, it will report a SparesMissing message. (syslog priority: Warning)
**TestMessage**
An array was found at startup, and the --test flag was given. (syslog priority: Info)
Only Fail, FailSpare, DegradedArray, SparesMissing and TestMessage cause Email to be sent. All events cause the program to be run. The program is run with two or three arguments: the event name, the array device and possibly a second device.

They do not relate to the SMART counters.  But, a SMART event or a failed disk could certainly increase the mdadm event counter.  Hope that helps.

---

### Post by steeldriver on 2012-06-27
Thanks muchly yes that's very helpful :-)

---

### Post by pban02 on 2012-11-18
Tried this and it didn't work. Whenever I add the new disk partition to the raid array, it is showing up as a spare, rather becoming a mirror. I have removed the disk from the raid, zeroed the super block and added it back, but it is always showing up as a spare and not resyncing with the existing disk.

Any tips on how to force this?

> **rubylaser said:**
> +1. I would zero the superblock on both of those sda partitions (sda1 and sda3), and then add them back to their appropriate arrays just as darkod has said.  Being slightly different on the counters isn't typically a being deal for putting an array back together, but being off by over 20,000 is :)

---

### Post by rubylaser on 2012-11-18
It's hard to provide directions without knowing what you've done, or we mdadm is at.  These [directions]("http://www.howtoforge.com/software-raid1-grub-boot-debian-etch") are pretty good to get a RAID1 set up with mdadm on a running system.

---

