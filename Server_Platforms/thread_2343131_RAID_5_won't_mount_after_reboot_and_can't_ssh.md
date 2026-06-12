---
title: "RAID 5 won't mount after reboot and can't ssh"
date: 2016-11-13
forum: Server Platforms
---

### Post by jfs9112 on 2016-11-13
Hello,

I can now ssh so I'm editing the post. Initially this issue started as my server not being able to boot up due to my raid volume not being able to mount. It is not the boot drive, just a separate data drive. Mount is complaining that it can't find and ext4 fs. I have since edited my fstab to not auto mount this and I'm able to ssh now and better troubleshoot.

When I try to manually mount:
```
sudo mount /dev/md0 /media/md0mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

dmesg | tail shows me this:

```


[ 3397.784804] RAID conf printout:
[ 3397.784808]  --- level:5 rd:4 wd:4
[ 3397.784814]  disk 0, o:1, dev:sda
[ 3397.784818]  disk 1, o:1, dev:sdb
[ 3397.784823]  disk 2, o:1, dev:sdd
[ 3397.784827]  disk 3, o:1, dev:sde
[ 3397.785105] created bitmap (15 pages) for device md0
[ 3397.793117] md0: bitmap initialized from disk: read 1 pages, set 29807 of 29807 bits
[ 3397.818371] md0: detected capacity change from 0 to 6000793878528
[ 3508.877821] EXT4-fs (md0): VFS: Can't find ext4 filesystem



```

```
cat /proc/mdstatPersonalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid5 sde[3] sdd[2] sdb[1] sda[0]
      5860150272 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk



```

```
sudo mdadm --detail /dev/md0/
dev/md0:
        Version : 1.2
  Creation Time : Sun Nov 13 11:24:03 2016
     Raid Level : raid5
     Array Size : 5860150272 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 1953383424 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sun Nov 13 11:24:03 2016
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : sv:0  (local to host sv)
           UUID : 6c7a5d72:8418a122:cff47284:45a8d066
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde
```

To me the raid looks fine, and this was working fine until reboot. I probably rebooted to apply latest kernel changes so maybe that is related but I'm a novice so not sure where to go from here. Appreciate any help provided.

---

### Post by johnb410312 on 2017-01-25
Did you get your RAID up and running?  I'm having the same issue.  Kernel change fried the FS, I'm thinking.

---

### Post by hydn79 on 2017-01-28
Try this: [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

