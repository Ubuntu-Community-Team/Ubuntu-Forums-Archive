---
title: "RAID5 &quot;grow&quot; is taking a long time to reshape"
date: 2008-07-18
forum: Server Platforms
---

### Post by samosamo on 2008-07-18
>  sudo cat /proc/mdstat 
[sudo] password for sean: 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[2] sde1[1] sdd1[0]
      732571904 blocks super 0.91 level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      [>....................]  reshape =  3.7% (27140224/732571904) finish=7978.9min speed=1472K/sec
      
unused devices: <none>

I started a RAID5 using 2 disks, then added a 3rd.  Is this really gonna take 5 days to complete??  There isn't any strain on the CPU or RAM, so it must be a hard drive bottleneck.  Anyone have any ideas?  Its a P4 box with an Intel ICH8 SATA controller.

---

