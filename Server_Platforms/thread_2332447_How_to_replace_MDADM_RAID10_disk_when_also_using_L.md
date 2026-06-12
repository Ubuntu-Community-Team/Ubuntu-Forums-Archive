---
title: "How to replace MDADM RAID10 disk when also using LVM?"
date: 2016-07-31
forum: Server Platforms
---

### Post by volkswagner on 2016-07-31
I can't seem to find a comprehensive guide to replacing MDADM disk, when also using LVM.

I have Ubuntu Server 14.04 with (4) disks in RAID10. When I originally built the server I used
different size hard drives, with the intent to replace with all same size. I want to replace two larger drives so all (4) will be 250gig.

/boot is on RAID10 /dev/md0, while /dev/md1 holds LVM VG1

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid10 sdb1[1] sda1[0] sdc1[2] sdd1[3]
      779264 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
md1 : active raid10 sdb2[1] sda2[0] sdc2[2] sdd2[3]
      487234560 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>

```

```
lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg1/rootfs
  LV Name                rootfs
  VG Name                vg1
  LV UUID                kCUQwe-UsNR-C0Bg-OQGN-Fzjl-ZNp9-91jNeT
  LV Write Access        read/write
  LV Creation host, time kvmhost, 2015-11-01 14:49:33 -0500
  LV Status              available
  # open                 1
  LV Size                11.18 GiB
  Current LE             2861
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     4096
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/vg1/home
  LV Name                home
  VG Name                vg1
  LV UUID                tTsVZo-1puG-Zt57-V6WX-Iejq-P3C0-HTl2w0
  LV Write Access        read/write
  LV Creation host, time kvmhost, 2015-11-01 14:50:01 -0500
  LV Status              available
  # open                 1
  LV Size                11.18 GiB
  Current LE             2861
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     4096
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/vg1/usr
  LV Name                usr
  VG Name                vg1
  LV UUID                dreNXM-bKqO-DoOH-sgwS-7sVn-GRJK-ykcF42
  LV Write Access        read/write
  LV Creation host, time kvmhost, 2015-11-01 14:50:26 -0500
  LV Status              available
  # open                 1
  LV Size                6.52 GiB
  Current LE             1668
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     4096
  Block device           252:2
   
  --- Logical volume ---
  LV Path                /dev/vg1/var
  LV Name                var
  VG Name                vg1
  LV UUID                MPYFdJ-S3l3-Qaus-H0Pi-yRid-kdf3-UW7VNu
  LV Write Access        read/write
  LV Creation host, time kvmhost, 2015-11-01 14:50:49 -0500
  LV Status              available
  # open                 1
  LV Size                13.04 GiB
  Current LE             3337
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     4096
  Block device           252:3
   
  --- Logical volume ---
  LV Path                /dev/vg1/varlibvirt
  LV Name                varlibvirt
  VG Name                vg1
  LV UUID                ZQGJHr-KaxR-SeXr-AP0A-77k4-8oWY-XPjZa1
  LV Write Access        read/write
  LV Creation host, time kvmhost, 2015-11-01 14:51:15 -0500
  LV Status              available
  # open                 1
  LV Size                204.89 GiB
  Current LE             52452
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     4096
  Block device           252:4
   
  --- Logical volume ---
  LV Path                /dev/vg1/swap
  LV Name                swap
  VG Name                vg1
  LV UUID                7AhI1w-zKF9-yn5X-OmFK-S0jm-3Udo-AHgMMz
  LV Write Access        read/write
  LV Creation host, time kvmhost, 2015-11-01 14:51:54 -0500
  LV Status              available
  # open                 2
  LV Size                11.18 GiB
  Current LE             2861
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     4096
  Block device           252:5

```

```
cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg1-rootfs /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=753695bc-a0da-41fc-bbd6-e2e382a33ae6 /boot           ext4    defaults        0       2
/dev/mapper/vg1-home /home           ext4    defaults        0       2
/dev/mapper/vg1-usr /usr            ext4    defaults        0       2
/dev/mapper/vg1-var /var            ext4    defaults        0       2
/dev/mapper/vg1-varlibvirt /var/lib/libvirt ext4    defaults        0       2
/dev/mapper/vg1-swap none            swap    sw              0       0
```

```
root@kvmhost:/home/eric# /sbin/mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Nov  1 14:38:48 2015
     Raid Level : raid10
     Array Size : 779264 (761.13 MiB 797.97 MB)
  Used Dev Size : 389632 (380.56 MiB 398.98 MB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Jul  3 00:57:07 2016
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 512K

           Name : kvmhost:0  (local to host kvmhost)
           UUID : a734f91a:d8296946:97cfe43c:72b06115
         Events : 43

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
root@kvmhost:/home/eric# /sbin/mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sun Nov  1 14:39:14 2015
     Raid Level : raid10
     Array Size : 487234560 (464.66 GiB 498.93 GB)
  Used Dev Size : 243617280 (232.33 GiB 249.46 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Jul 31 17:01:30 2016
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 512K

           Name : kvmhost:1  (local to host kvmhost)
           UUID : bc8a712a:22d2ee2f:230eb104:03d4da3e
         Events : 202

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2
```

```
root@kvmhost:/home/eric# fdisk -l

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c3f46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      782335      390144   fd  Linux raid autodetect
/dev/sdb2          782336   488280063   243748864   fd  Linux raid autodetect

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d40cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      782335      390144   fd  Linux raid autodetect
/dev/sdc2          782336   488282111   243749888   fd  Linux raid autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048      782335      390144   fd  Linux raid autodetect
/dev/sdd2          782336   488282111   243749888   fd  Linux raid autodetect

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af63d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      782335      390144   fd  Linux raid autodetect
/dev/sda2          782336   488280063   243748864   fd  Linux raid autodetect

Disk /dev/md1: 498.9 GB, 498928189440 bytes
2 heads, 4 sectors/track, 121808640 cylinders, total 974469120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 797 MB, 797966336 bytes
2 heads, 4 sectors/track, 194816 cylinders, total 1558528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/mapper/vg1-rootfs: 12.0 GB, 11999903744 bytes
255 heads, 63 sectors/track, 1458 cylinders, total 23437312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg1-rootfs doesn't contain a valid partition table

Disk /dev/mapper/vg1-home: 12.0 GB, 11999903744 bytes
255 heads, 63 sectors/track, 1458 cylinders, total 23437312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg1-home doesn't contain a valid partition table

Disk /dev/mapper/vg1-usr: 6996 MB, 6996099072 bytes
255 heads, 63 sectors/track, 850 cylinders, total 13664256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg1-usr doesn't contain a valid partition table

Disk /dev/mapper/vg1-var: 14.0 GB, 13996392448 bytes
255 heads, 63 sectors/track, 1701 cylinders, total 27336704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg1-var doesn't contain a valid partition table

Disk /dev/mapper/vg1-varlibvirt: 220.0 GB, 219999633408 bytes
255 heads, 63 sectors/track, 26746 cylinders, total 429686784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg1-varlibvirt doesn't contain a valid partition table

Disk /dev/mapper/vg1-swap: 12.0 GB, 11999903744 bytes
255 heads, 63 sectors/track, 1458 cylinders, total 23437312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg1-swap doesn't contain a valid partition table

```

I found [this how to]("https://wiki.archlinux.org/index.php/Software_RAID_and_LVM"), which include a command to copy partition scheme:
```
sgdisk --backup=table /dev/sda
$ sgdisk --load-backup=table /dev/sdb
```
Then randomize UUIDs with following:
```
 sgdisk -G /dev/<newDrive>
```

I assume I can use the remove and replace commands in [this tutorial]("http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/") for the MDADM, but
I'm unaware what I need to do with the LVM structure.

I do believe there are enough SATA ports to have all six drives (four current to two replacements) installed at the same time. I think
this can help reduce the rebuild time/disk load on syncing?

Any pointers are greatly appreciated.

---

### Post by darkod on 2016-07-31
Yes, you can use something like sfdisk or sgdisk to copy the partition table from one to another disk but I always prefer creating the partitions manually using parted on the new disk. It's not complicated and you are one of the "older" members on this forum so I'm sure you know how to do it... :)

As for replacing the disks... If you are really paranoid and can afford the server downtime you can power off and work from live cd.

But in theory, you can do it all while the server is happily running. The /dev/md1 device is the PV for the LVM, right? While replacing disk by disk you never actually stop the md device, so the LVM on top of it should be running just fine all that time... Simply remove one partition (disk) from md1 and then add the new partition (disk). Let it rebuild... Do it for the other disk too...

That should be it. Same like when not using LVM, it doesn't matter...

Of course, it's always best to have a full backup before starting these operations, if possible.

PS. Forgot to mention, but I'm sure you know that part too. After extending the array you will need to check if the new size is seen by the VG right away (not sure 100% on that), and then you will have that space available to extend your LVs when necessary. And after extending a LV you need to extend the FS too...

---

### Post by volkswagner on 2016-08-02
@darkod, thanks for the reply.

I "thought" my skills were good enough to manually create the partitions, but after looking at my previous creations... I have doubt.
If you notice my two larger disks are the same but not the same as the two smaller disks' partition scheme.

I'm not sure I'll be extending the array. My plan is to simply replace physical disks, with the same geometry. So this is why I'm confused about the LVM
component. How does LVM "know" to "remove and reattach" the physical volume when replacing a disk?

---

### Post by darkod on 2016-08-02
But why "remove and reattach"?

You will be replacing one disk at a time, right? Raid10 supports staying online during single disk replacement/failure. So all your /dev/mdX devices will stay online, regardless if on top of them you are using LVM or not. The LVM will not even notice it...

Or is there something in the setup I'm not understanding???

---

### Post by volkswagner on 2016-08-02
There is nothing else. 
Yes, I shouldn't have to "attach/reattach" because the LVM is on top of MDADM. Great!

So do you agree when replacing disk with same partition scheme, I shouldn't have to grow/modify file system nor LVM?

---

### Post by darkod on 2016-08-03
Yes, I agree that when replacing with identical disks you don't need to resize any FS or the LVM. At first I thought you are upgrading to bigger disks.

The only thing that can present a problem, and that you are probably aware of, is that after replacing a disk in a raid and during the rebuild process, the rest of the disks have higher load. If one of them fails, you can be left with one disk half-rebuilt and one failed, in other words two missing members. Now, raid10 in most cases can keep on working with two members missing, but not if they form the raid1 array (as part of the raid10).

That's why I said if possible, better to have a full backup before performing this and any other similar operation... However the probability of another disk failing during the rebuild, and that it is the one disk out of three that you can't afford to lose, is very slim...

---

### Post by volkswagner on 2016-08-20
Thanks again @darkod.

I was able to swap out two disks (one at a time). I did run into an issue, which I'd like to document here.
The problem was unique to installing used disks which were part of a software RAID prior.

When I tried to format the replacement disk, I kept getting device busy. I couldn't find anywhere it was mounted, 
but mdstat showed a new array. mdadm was recognizing the disks prior life in an array.
I had to stop the device and remove the raid.

```
mdadm --stop /dev/md127
mdadm --remove /dev/md127
```

I could then use fdisk to partition the drive, but I was forced to reboot for the 
repartition to work. Simply running:
```
partprobe /dev/sdc
```
would not work. Running partprobe would cause the system to recognize the old raid again, so I had
to run fdisk again and reboot.

Again I'm sure things would have been much smoother if I was using new disks.

---

