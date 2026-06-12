---
title: "Raid 1 question"
date: 2009-10-19
forum: Server Platforms
---

### Post by Ubunt2u on 2009-10-19
i setup a couple of servers using raid 1 but failed to raid the swap partions on each of the drives.  is it possible to go back & raid them without starting over completely and/or destroying data on the main raid drives?
Thanks in advance

---

### Post by windependence on 2009-10-19
Your partitioning should be done AFTER you set up your RAID array. Set up your array as one logical volume and then partition the volume or better yet use LVM for more flexibility. You don't want to set up a swap as a RAID array. I'm not even sure you could do it, but I wouldn't want to anyway.

-Tim

---

### Post by R.Bucky on 2009-10-19
Um yeah. I am the guy who was not thinking about it and RAID'd his swap. Here goes:
```
mdadm --detail /dev/md4
/dev/md4:
        Version : 00.90.03
  Creation Time : Fri Aug 28 19:44:19 2009
     Raid Level : raid1
     Array Size : 1951808 (1906.38 MiB 1998.65 MB)
  Used Dev Size : 1951808 (1906.38 MiB 1998.65 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 4
    Persistence : Superblock is persistent

    Update Time : Sun Oct 18 00:10:07 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : secret UUID :-)
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       34        1      active sync   /dev/sdc2

```
Confirmed. It works and has been for many months now without issue. Granted, I will do it the CORRECT way next time. :-)

---

### Post by Ubunt2u on 2009-10-20
Thanks for the replies.  I'll leave it alone.

---

