---
title: "Issue with mdadm (removed and faulty removed)"
date: 2011-03-15
forum: Server Platforms
---

### Post by jcs2011 on 2011-03-15
Hi,
 
Since today, i have important issue with my mdadm raid5. I'm not an expert about that but now, i'm confused about my raid status and what I can do or not.
 
Now, i'm trying to figure what is the exact meaning of the State "removed" and "faulty removed".
 
My current and only target is to copy data somewhere else if it's still possible to read it again.
 
Here the commands I ran to get the raid informations:
 
------------------------------------------------------------
sudo mdadm --examine /dev/sd[b,c,d,e]
mdadm: No md superblock detected on /dev/sdb.
mdadm: No md superblock detected on /dev/sdc.
mdadm: No md superblock detected on /dev/sdd.
mdadm: No md superblock detected on /dev/sde.
 
------------------------------------------------------------
sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : af885ff7:76583e6a:e368bf24:bd0fce41
  Creation Time : Wed Jun 30 10:11:27 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Update Time : Tue Mar 15 00:04:10 2011
          State : clean
Active Devices : 2
Working Devices : 2
Failed Devices : 1
  Spare Devices : 0
       Checksum : 7d9fefa6 - correct
         Events : 442
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1
   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       17        3      active sync   /dev/sdb1

---

### Post by rubylaser on 2011-03-15
First of all what happened, to get you to this point?  And, have you done anything (I'm assuming so, because you have a drive that's showing as removed rather than faulty).  If you want to examine your drives for superblocks, you have to specify the partitions like this...
```
sudo mdadm --examine /dev/sd[b,c,d,e]1
```

Have you ran SMART test on all of these drives? And can you paste the results of the SMART tests in here, so we can look at them?

Can you paste in the results of the above command, and this too..
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by jcs2011 on 2011-03-15
Thanks for reply. I'm not really sure what happend but I think it's related to electric problem with one connector contact. The problem occur when i'm was away... the only thing i made is to fix the connector and reboot the server.
 
Hope command results above can guide you
 
> **rubylaser said:**
> First of all what happened, to get you to this point? And, have you done anything (I'm assuming so, because you have a drive that's showing as removed rather than faulty). If you want to examine your drives for superblocks, you have to specify the partitions like this...
```
sudo mdadm --examine /dev/sd[b,c,d,e]1
```

[INDENT]sudo mdadm --examine /dev/sd[b,c,d,e]1
/dev/sdb1:
Magic : a92b4efc
Version : 00.90.00
UUID : af885ff7:76583e6a:e368bf24:bd0fce41
Creation Time : Wed Jun 30 10:11:27 2010
Raid Level : raid5
Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
Raid Devices : 4
Total Devices : 4
Preferred Minor : 0
Update Time : Tue Mar 15 00:04:10 2011
State : clean
Active Devices : 2
Working Devices : 2
Failed Devices : 1
Spare Devices : 0
Checksum : 7d9fef98 - correct
Events : 442
Layout : left-symmetric
Chunk Size : 64K
Number Major Minor RaidDevice State
this 3 8 17 3 active sync /dev/sdb1
0 0 0 0 0 removed
1 1 0 0 1 faulty removed
2 2 8 33 2 active sync /dev/sdc1
3 3 8 17 3 active sync /dev/sdb1
 
 
/dev/sdc1:
Magic : a92b4efc
Version : 00.90.00
UUID : af885ff7:76583e6a:e368bf24:bd0fce41
Creation Time : Wed Jun 30 10:11:27 2010
Raid Level : raid5
Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
Raid Devices : 4
Total Devices : 4
Preferred Minor : 0
Update Time : Tue Mar 15 00:04:10 2011
State : clean
Active Devices : 2
Working Devices : 2
Failed Devices : 1
Spare Devices : 0
Checksum : 7d9fefa6 - correct
Events : 442
Layout : left-symmetric
Chunk Size : 64K
Number Major Minor RaidDevice State
this 2 8 33 2 active sync /dev/sdc1
0 0 0 0 0 removed
1 1 0 0 1 faulty removed
2 2 8 33 2 active sync /dev/sdc1
3 3 8 17 3 active sync /dev/sdb1
 
 
/dev/sdd1:
Magic : a92b4efc
Version : 00.90.00
UUID : af885ff7:76583e6a:e368bf24:bd0fce41
Creation Time : Wed Jun 30 10:11:27 2010
Raid Level : raid5
Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
Raid Devices : 4
Total Devices : 4
Preferred Minor : 0
Update Time : Mon Mar 14 19:16:33 2011
State : active
Active Devices : 4
Working Devices : 4
Failed Devices : 0
Spare Devices : 0
Checksum : 7d9faa75 - correct
Events : 437
Layout : left-symmetric
Chunk Size : 64K
Number Major Minor RaidDevice State
this 1 8 49 1 active sync /dev/sdd1
0 0 8 65 0 active sync /dev/sde1
1 1 8 49 1 active sync /dev/sdd1
2 2 8 33 2 active sync /dev/sdc1
3 3 8 17 3 active sync /dev/sdb1
 
 
/dev/sde1:
Magic : a92b4efc
Version : 00.90.00
UUID : af885ff7:76583e6a:e368bf24:bd0fce41
Creation Time : Wed Jun 30 10:11:27 2010
Raid Level : raid5
Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
Raid Devices : 4
Total Devices : 4
Preferred Minor : 0
Update Time : Mon Mar 14 19:16:33 2011
State : active
Active Devices : 4
Working Devices : 4
Failed Devices : 0
Spare Devices : 0
Checksum : 7d9faa83 - correct
Events : 437
Layout : left-symmetric
Chunk Size : 64K
Number Major Minor RaidDevice State
this 0 8 65 0 active sync /dev/sde1
0 0 8 65 0 active sync /dev/sde1
1 1 8 49 1 active sync /dev/sdd1
2 2 8 33 2 active sync /dev/sdc1
3 3 8 17 3 active sync /dev/sdb1
 
[/INDENT]> **rubylaser said:**
> Have you ran SMART test on all of these drives? And can you paste the results of the SMART tests in here, so we can look at them?
[INDENT]sudo smartctl -Hc /dev/sdb1
SMART overall-health self-assessment test result: PASSED
 
sudo smartctl -Hc /dev/sdc1
SMART overall-health self-assessment test result: PASSED
 
sudo smartctl -Hc /dev/sdd1
SMART overall-health self-assessment test result: PASSED
 
sudo smartctl -Hc /dev/sde1
SMART overall-health self-assessment test result: PASSED
[/INDENT]> **rubylaser said:**
> Can you paste in the results of the above command, and this too..
```
cat /etc/mdadm/mdadm.conf
```
[INDENT]cat /etc/mdadm/mdadm.conf
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
MAILADDR root
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=af885ff7:76583e6a:e368bf24:bd0fce41
# This file was auto-generated on Tue, 06 Jul 2010 16:52:05 -0400
# by mkconf $Id$
 
[/INDENT]

---

### Post by rubylaser on 2011-03-15
Since all your disks seem to be in good shape, have you tried to stop the array, and then assemble from the device partitions?  Also, what is the output of
```
cat /proc/mdstat
```
I'd like to see this before you do the next steps :)

If all your disks are in good shape, and you haven't done anything on the array, you should be able to put it back together like this.
```
mdadm --stop /dev/md0
```
```
mdadm --assemble --force /dev/md0 /dev/sd[b,c,d,e]1
```

---

### Post by jcs2011 on 2011-03-15
I didn't really try any changes or stop on the array because 2 drives look critic.
 
> **rubylaser said:**
> Since all your disks seem to be in good shape, have you tried to stop the array, and then assemble from the device partitions? Also, what is the output of
```
cat /proc/mdstat
```
I'd like to see this before you do the next steps :)
 
[INDENT]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdc1[2](S) sdb1[3](S) sdd1[1](S) sde1[0](S)
      7814047744 blocks
unused devices: <none>
[/INDENT] 
That was my result.
 
I'm pretty nervous to try anything before having external opinion. You help is really appreciated.

---

### Post by rubylaser on 2011-03-15
This is showing that it believes all of your devices are spares.
```
md0 : inactive sdc1[2](S) sdb1[3](S) sdd1[1](S) sde1[0](S)
```

At this point, you should try to stop /dev/md0 and try to force assemble it as I showed in the previous post.  Please let me know what output it gives you.  Two of your drives are stale meaning that their Events don't match the other two.  But, you should be able to assemble them without a problem.

---

### Post by disabledaccount on 2011-03-15
I wonder what informations are in kernel log from that time...

---

### Post by jcs2011 on 2011-03-15
sudo cat /proc/mdstat
[INDENT]
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[0] sdb1[3] sdc1[2] sdd1[1]
      5860535808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  0.1% (2144256/1953511936) finish=825.0min speed=39420K/sec
unused devices: <none>

[/INDENT]I made what you suggest and now it's resyncing.
 
I made a fast verification and it look like all data is there... 
 
Big thanks for your support rubylaser!

---

### Post by rubylaser on 2011-03-15
No problem, happy to help :) And very glad it's working for you.  Potentially losing data can leave an awful feeling in the pit of your stomach.  Can you please click on thread tools and mark the thread as SOLVED?

---

### Post by theRemix on 2013-02-05
I'm having a similar problem to yours, except stopping the md device then force assembling did not work for me

```
#mdadm stop /dev/md1
```

```
# mdadm --assemble --verbose /dev/md1 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot 3.
mdadm: added /dev/sdb1 to /dev/md1 as 1
mdadm: added /dev/sdc1 to /dev/md1 as 2
mdadm: added /dev/sdd1 to /dev/md1 as 3
mdadm: added /dev/sda1 to /dev/md1 as 0
mdadm: /dev/md1 assembled from 2 drives - not enough to start the array.
```

```
#mdadm --assemble --verbose --force /dev/md1 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

mdadm: looking for devices for /dev/md1
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has no superblock - assembly aborted
```

```
# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md1 : inactive sda1[0](S) sdd1[3](S) sdc1[2](S) sdb1[1](S)
      136744704 blocks
       
unused devices: <none>
```

any help would be greatly appreciated!

---

