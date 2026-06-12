---
title: "Software RAID5 -- Kernel [attempt to access beyond end of device]"
date: 2010-10-14
forum: Server Platforms
---

### Post by ChrisAIX on 2010-10-14
Hello, 

seems I've got a little trouble (or not?)

What is the meaning of the following? Am I really in trouble ?

**I'm a bit nervous because of the KERNEL Meassage**

[LIST]
[*]Board : Intel_DH55HC
[*]4 Samsung HDDs
[/LIST] 

**/var/log/syslog**

```

Oct 14 09:56:42 nas kernel: [ 4401.411349] attempt to access beyond end of device
Oct 14 09:56:42 nas kernel: [ 4401.411361] md0: rw=1, want=4611686018508871960, limit=8784539136
Oct 14 09:56:42 nas kernel: [ 4401.411368] Buffer I/O error on device md0, logical block 576460752313608994
Oct 14 09:56:42 nas kernel: [ 4401.411477] lost page write due to I/O error on md0
Oct 14 09:56:43 nas kernel: [ 4402.450546] JBD: Detected IO errors while flushing file data on md0

```

The are some additional entries within the syslog short before:
```
Oct 14 08:43:17 nas kernel: [    6.669626] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 14 08:43:17 nas kernel: [    6.675493] md: bind<sdc2>
Oct 14 08:43:17 nas kernel: [    6.677401] md/raid:md0: device sdc2 operational as raid disk 1
Oct 14 08:43:17 nas kernel: [    6.677403] md/raid:md0: device sdd2 operational as raid disk 2
Oct 14 08:43:17 nas kernel: [    6.677405] md/raid:md0: device sdb2 operational as raid disk 0
Oct 14 08:43:17 nas kernel: [    6.677406] md/raid:md0: device sde2 operational as raid disk 3
Oct 14 08:43:17 nas kernel: [    6.677758] md/raid:md0: allocated 4282kB
Oct 14 08:43:17 nas kernel: [    6.677781] md/raid:md0: raid level 5 active with 4 out of 4 devices, algorithm 2
Oct 14 08:43:17 nas kernel: [    6.677783] RAID conf printout:
Oct 14 08:43:17 nas kernel: [    6.677784]  --- level:5 rd:4 wd:4
Oct 14 08:43:17 nas kernel: [    6.677786]  disk 0, o:1, dev:sdb2
Oct 14 08:43:17 nas kernel: [    6.677787]  disk 1, o:1, dev:sdc2
Oct 14 08:43:17 nas kernel: [    6.677788]  disk 2, o:1, dev:sdd2
Oct 14 08:43:17 nas kernel: [    6.677789]  disk 3, o:1, dev:sde2
Oct 14 08:43:17 nas kernel: [    6.677809] md0: detected capacity change from 0 to 4497684037632
Oct 14 08:43:17 nas kernel: [    6.678608]  md0: unknown partition table
Oct 14 08:43:17 nas kernel: [    6.786691] EXT3-fs (sda5): using internal journal
Oct 14 08:43:17 nas kernel: [    6.908869] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    6.909172] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    6.909315] EXT3-fs (sdb1): using internal journal
Oct 14 08:43:17 nas kernel: [    6.909322] EXT3-fs (sdb1): mounted filesystem with ordered data mode
Oct 14 08:43:17 nas kernel: [    6.929244] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    6.929430] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    6.929567] EXT3-fs (sdc1): using internal journal
Oct 14 08:43:17 nas kernel: [    6.929574] EXT3-fs (sdc1): mounted filesystem with ordered data mode
Oct 14 08:43:17 nas kernel: [    6.976447] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    6.976691] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    6.976837] EXT3-fs (sdd1): using internal journal
Oct 14 08:43:17 nas kernel: [    6.976844] EXT3-fs (sdd1): mounted filesystem with ordered data mode
Oct 14 08:43:17 nas kernel: [    7.017368] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    7.017600] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    7.017783] EXT3-fs (sde1): using internal journal
Oct 14 08:43:17 nas kernel: [    7.017790] EXT3-fs (sde1): mounted filesystem with ordered data mode
Oct 14 08:43:17 nas kernel: [    7.312618] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    7.322581] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    7.334608] EXT3-fs (sda1): using internal journal
Oct 14 08:43:17 nas kernel: [    7.334619] EXT3-fs (sda1): mounted filesystem with ordered data mode
Oct 14 08:43:17 nas kernel: [    7.691942] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    7.692212] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    7.699118] EXT3-fs (md0): using internal journal
Oct 14 08:43:17 nas kernel: [    7.699127] EXT3-fs (md0): mounted filesystem with ordered data mode
Oct 14 08:43:17 nas kernel: [    7.763934] EXT3-fs: barriers not enabled
Oct 14 08:43:17 nas kernel: [    7.784600] kjournald starting.  Commit interval 5 seconds
Oct 14 08:43:17 nas kernel: [    7.785351] EXT3-fs (sda7): using internal journal
Oct 14 08:43:17 nas kernel: [    7.785357] EXT3-fs (sda7): mounted filesystem with ordered data mode


```

Raid Info:

```
root@nas:~# mdadm --detail  /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Sep 12 16:35:38 2010
     Raid Level : raid5
     Array Size : 4392269568 (4188.79 GiB 4497.68 GB)
  Used Dev Size : 1464089856 (1396.26 GiB 1499.23 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct 14 12:08:11 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : a36f5ca6:ccdddda9:766716cf:05dd1868 (local to host nas)
         Events : 0.156

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       34        1      active sync   /dev/sdc2
       2       8       50        2      active sync   /dev/sdd2
       3       8       66        3      active sync   /dev/sde2


```

Is there anyone who can help?

Thanks in advance

Chris

---

