---
title: "mdadm degraded but doesn't use spare"
date: 2021-11-26
forum: Server Platforms
---

### Post by clarknova on 2021-11-26
Ubuntu 20.04.3

I created a RAID device thus:
```
mdadm --create --verbose /dev/md1 --level=10 --layout=n2 --raid-devices=20 /dev/mapper/...
mdadm --add-spare /dev/md1 /dev/dm-3 /dev/dm-20
```

This worked as expected and /dev/md1 began the resync process. At some point I had to reboot the host, and after rebooting I found that /dev/md1 was degraded and missing a device. I didn't copy the output of 'mdadm -D' at the time, but I recall it showed 1 device as "removed" and 2 spares. 

After determining that /dev/dm-15 was available to the host but missing from the array, I added it back thus:
```
mdadm /dev/md1 -a /dev/dm-15
```

But the array continues to show as degraded, now with three spares:
```
# mdadm -D /dev/md1
/dev/md1:
           Version : 1.2
     Creation Time : Wed Nov 24 14:45:07 2021
        Raid Level : raid10
        Array Size : 117187532800 (111758.74 GiB 120000.03 GB)
     Used Dev Size : 11718753280 (11175.87 GiB 12000.00 GB)
      Raid Devices : 20
     Total Devices : 22
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Fri Nov 26 10:00:28 2021
             State : clean, degraded, resyncing 
    Active Devices : 19
   Working Devices : 22
    Failed Devices : 0
     Spare Devices : 3

            Layout : near=2
        Chunk Size : 512K

Consistency Policy : bitmap

     Resync Status : 25% complete

              Name : vs-02:1  (local to host vs-02)
              UUID : 42b2d522:9a51d908:99970c48:c0e7b3f4
            Events : 38440

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1     253       21        1      active sync set-B   /dev/dm-21
       2     253        4        2      active sync set-A   /dev/dm-4
       3     253        5        3      active sync set-B   /dev/dm-5
       4     253        9        4      active sync set-A   /dev/dm-9
       5     253        1        5      active sync set-B   /dev/dm-1
       6     253       12        6      active sync set-A   /dev/dm-12
       7     253       16        7      active sync set-B   /dev/dm-16
       8     253       11        8      active sync set-A   /dev/dm-11
       9     253        2        9      active sync set-B   /dev/dm-2
      10     253        8       10      active sync set-A   /dev/dm-8
      11     253        7       11      active sync set-B   /dev/dm-7
      12     253       17       12      active sync set-A   /dev/dm-17
      13     253       13       13      active sync set-B   /dev/dm-13
      14     253        6       14      active sync set-A   /dev/dm-6
      15     253        0       15      active sync set-B   /dev/dm-0
      16     253       10       16      active sync set-A   /dev/dm-10
      17     253       19       17      active sync set-B   /dev/dm-19
      18     253       18       18      active sync set-A   /dev/dm-18
      19     253       14       19      active sync set-B   /dev/dm-14

      20     253        3        -      spare   /dev/dm-3
      21     253       20        -      spare   /dev/dm-20
      22     253       15        -      spare   /dev/dm-15
```

What did I do wrong and how do I get mdadm to make one of the three spares active? How do I know that if another active device fails, a spare will automatically replace it?

---

### Post by darkod on 2021-11-26
I can't be 100% sure yet, but I think you are seeing this because it is still doing the initial array sync/create. Note how the status says 'clean, degraded, resyncing'. It's a very large array of 120TB and it looks like you rebooted it before the initial sync completed.

Since it says it is in resync, wait, and only if it doesn't show correctly after the resync completes, start looking into it.

---

### Post by clarknova on 2021-11-26
That makes sense. I'll post an update next week after the resync has completed. Thanks.

---

