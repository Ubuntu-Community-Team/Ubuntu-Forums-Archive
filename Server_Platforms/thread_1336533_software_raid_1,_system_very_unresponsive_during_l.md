---
title: "software raid 1, system very unresponsive during large writes."
date: 2009-11-24
forum: Server Platforms
---

### Post by captaintrav on 2009-11-24
I rebuilt my 8.04 file server from scratch to try out mdraid.  Two 500 disks in raid 1.  The first 4gb of each disk is partitioned as swap, the second partition takes up the remainder of the drive.
Write performance is good:

```
dd if=/dev/zero of=test.img count=300 bs=10M
300+0 records in
300+0 records out
3145728000 bytes (3.1 GB) copied, 70.2997 s, 44.7 MB/s

dd if=test.img of=/dev/null bs=10M
300+0 records in
300+0 records out
3145728000 bytes (3.1 GB) copied, 58.6145 s, 53.7 MB/s


```

Nothing interesting here either:

```
travis@tbird:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda2[0] sdb2[1]
      484375744 blocks [2/2] [UU]
      
unused devices: <none>
travis@tbird:~$ 
```

and

```

travis@tbird:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Nov 22 18:27:31 2009
     Raid Level : raid1
     Array Size : 484375744 (461.94 GiB 496.00 GB)
  Used Dev Size : 484375744 (461.94 GiB 496.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Nov 24 15:28:05 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 8d4ced2f:e8711eef:e368bf24:bd0fce41
         Events : 0.21

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2

```

Problem is, if I am writing a large amount of data to the raid, the system more or less becomes unresponsive - try to launch an application that usually takes 2 seconds may take 15 minutes.  Also weirdly enough, the system tends to "hitch" becoming unresonsive for a second or two at a time at random intervals during which there is intense disk thrashing.  This wasn't seen prior to going software raid 1.  System was running hardy before the rebuild as well with no issue.  So the issue here isn't really performance, but issues with i/o contention?  CPU usage is not an issue during large writes either.  Any suggestions?

---

### Post by grenoml on 2009-11-24
I have dozens of systems on mdraid and whenever this unresponsive symptom happens it has always been a bad hard drive that was causing the problem.  It sounds like one of your drives may be going but not yet dead.  I would certainly try to make a backup asap.  Then boot a drive tools disk and perform a sector analysis and see if you have any bad sectors showing up.  The other possibility is loose cabling.

-Gerry

---

### Post by captaintrav on 2009-11-24
> **grenoml said:**
> I have dozens of systems on mdraid and whenever this unresponsive symptom happens it has always been a bad hard drive that was causing the problem.  It sounds like one of your drives may be going but not yet dead.  I would certainly try to make a backup asap.  Then boot a drive tools disk and perform a sector analysis and see if you have any bad sectors showing up.  The other possibility is loose cabling.

-Gerry

I'm running smartd with daily self-tests, but I have had my share of issues with sata cables, i'll check that.  Most of the time I've seen issues in /var/log/messages when things were going wonky with sata devices though.

---

### Post by aprigiosimoes on 2009-11-25
try
#echo 50000 > /proc/sys/dev/raid/speed_limit_min

---

### Post by grenoml on 2009-11-25
> **captaintrav said:**
> I'm running smartd with daily self-tests, but I have had my share of issues with sata cables, i'll check that.  Most of the time I've seen issues in /var/log/messages when things were going wonky with sata devices though.

Half of the time I never saw anything in /var/log/messages from smartd when the drive went bad.  The only way I found the problem was when I ran the drive tools tests and saw a lot of bad sectors and replacing the drive always fixed the problem.

-Gerry

---

### Post by captaintrav on 2009-11-25
> **aprigiosimoes said:**
> try
#echo 50000 > /proc/sys/dev/raid/speed_limit_min

This seems to have helped a fair bit.. Anyone care to explain why?

I will keep an eye out for drive failing though, if I move some stuff around I could try removing one drive and adding another.

---

