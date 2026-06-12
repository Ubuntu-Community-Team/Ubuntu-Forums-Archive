---
title: "New RAID 5 array won't auto start or mount."
date: 2008-10-19
forum: Server Platforms
---

### Post by xyvian on 2008-10-19
I have recently set up a raid 5 array using mdadm, i have it set up to what I assume is a correct setup (followed the instructions here [http://www.mythtv.org/wiki/index.php/RAID](http://www.mythtv.org/wiki/index.php/RAID)) but whenever I reboot the system, /dev/md0 disappears.

Upon reboot my fdisk -l looks as following:
```
root@NAS:/home/nas# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60614   486881923+  83  Linux
/dev/sda2           60615       60801     1502077+   5  Extended
/dev/sda5           60615       60801     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b401f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003a9e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   fd  Linux raid autodetect

```

It SHOULD also show /dev/md0. If i were to try to go ahead and mount md0 I would get an error as follows:
```
root@NAS:/home/nas# mount /dev/md0 /mnt/raid
mount: /dev/md0 is not a valid block device
```

Quirky. I did some googling and found that if I used the command modprobe md, then this issue would go away. I type in the command, and once again try to mount, I will get the following error:
```
root@NAS:/home/nas# modprobe md
root@NAS:/home/nas# mount /dev/md0 /mnt/raid -t xfs
mount: /dev/md0: can't read superblock
```

So once again I did some more googling and found a very nifty command that will get me up and running again. mdadm --assemble --scan –v

```
root@NAS:/home/nas# mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdd is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sdc is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sdb is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sda5 is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sda2 is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sda1 is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sda is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives.

```

After doing this I can now mount the raid device with no problem.

Now I know that this is a lot to look over for me but I'm at my wit's end here. It's been bugging me that I can't seem to fix this bug. I really don't want to have to put in three commands every time I restart the system. I'm not sure what additional information you will want but I'll go ahead and post my mdadm.conf since that may be relevant. 

```
DEVICE partitions
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=4e25facb:fc7a98aa:598dff76:ba33d639 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1 auto=yes
```

I do have a filesystem on the raid (xfs) and I have tested if it will retain data. It seems fine once I get it up and running it's just a matter of punching in a few commands to get it there.

I am running Ubuntu server 7.10 headless. If you need any more information please let me know.

Thank you for any help,
Brian

---

### Post by xyvian on 2008-10-20
After some thought I feel like I should add a little more information. the following is my --detail:
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Oct 18 21:13:51 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Oct 20 00:17:34 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 32K

           UUID : 4e25facb:fc7a98aa:598dff76:ba33d639
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1

```
Thought I would put down my output for cat /proc/mdstat:
```
 cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      1465143808 blocks level 5, 32k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

```

I believe I have now covered all my bases. I look forward to your input,
Brian

---

### Post by xyvian on 2008-10-20
bump :guitar:

---

### Post by fjgaude on 2008-10-20
I don't know anything about xfs filesystems... such can handle drive arrays of three 750GB?

Shouldn't the mount command go like this:

```
sudo mount -t xfs /dev/md0 /mountpoint
```

The array should mount.

Let us know how you are doing.

---

### Post by ilrudie on 2008-10-20
Doesn't mdadm use mapper?  Is md0 available under /dev/mapper/md0?

---

### Post by xyvian on 2008-10-20
@jfgaude The XFS filesystem is not the issue i have. This was found on wikipedia [http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

> Specifications
Capacity
XFS is a 64-bit file system. It supports a maximum file system size of 8 exbibytes minus one byte, though this is subject to block limits imposed by the host operating system. On 32-bit Linux systems, this limits the file and file system sizes to 16 terabytes.

Plus I have been able to mount the drive with the array formatted in XFS, add data to it, etc. On reboot (after reinitializing md and reassembling the array and mounting it) I can still get to said data. My mount command seems to work fine so long as I have used the previous 2 commands. My issue I believe is that the md module is not being loaded when the kernel is, and being such it does not mount the array. In fact it doesn't seem to load md at all.

If i try to mount the array without initializing md and reassembling my array I get an error saying

```
mount: /dev/md0 is not a valid block device
```

@ilrudie I'm not sure if it uses mapper however I would have to assume not seeing as md0 does not appear in /dev/mapper/md0 nor does /dev/mapper exist on my system. If it does indeed require mapper could this be yet another problem I have run into?

---

### Post by xyvian on 2008-10-21
I've done some more intense googling and I may have some information that somebody may be able to make some sense of. I ran **dmesg | more** and searched through it for anything relevant to my hard drives and/or RAID array:
```
[   17.830000] raid5: automatically using best checksumming function: pIII_sse
[   17.880000]    pIII_sse  :  7032.000 MB/sec
[   17.880000] raid5: using function: pIII_sse (7032.000 MB/sec)
[   18.050000] raid6: int32x1    982 MB/s
[   18.220000] raid6: int32x2   1003 MB/s
[   18.390000] raid6: int32x4    847 MB/s
[   18.560000] raid6: int32x8    603 MB/s
[   18.730000] raid6: mmxx1     1851 MB/s
[   18.900000] raid6: mmxx2     3369 MB/s
[   19.070000] raid6: sse1x1    1858 MB/s
[   19.240000] raid6: sse1x2    3108 MB/s
[   19.410000] raid6: sse2x1    3105 MB/s
[   19.580000] raid6: sse2x2    4273 MB/s
[   19.580000] raid6: using algorithm sse2x2 (4273 MB/s)
[   19.580000] md: raid6 personality registered for level 6
[   19.580000] md: raid5 personality registered for level 5
[   19.580000] md: raid4 personality registered for level 4
[   19.840000] EXT3 FS on sda1, internal journal
[   20.090000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   20.090000] SGI XFS Quota Management subsystem
[   20.100000] XFS: SB read failed

.
.
.

[   98.860000] md: md0 stopped.
[  100.600000] md: bind<sdc1>
[  100.600000] md: bind<sdd1>
[  100.600000] md: bind<sdb1>
[  100.660000] raid5: device sdb1 operational as raid disk 0
[  100.660000] raid5: device sdd1 operational as raid disk 2
[  100.660000] raid5: device sdc1 operational as raid disk 1
[  100.660000] raid5: allocated 3163kB for md0
[  100.660000] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[  100.660000] RAID5 conf printout:
[  100.660000]  --- rd:3 wd:3
[  100.660000]  disk 0, o:1, dev:sdb1
[  100.660000]  disk 1, o:1, dev:sdc1
[  100.660000]  disk 2, o:1, dev:sdd1
[  128.430000] Filesystem "md0": Disabling barriers, not supported by the underlying device
[  128.430000] XFS mounting filesystem md0
[  129.250000] Ending clean XFS mount for filesystem: md0

```

I also took a look at my syslog in /var/log/syslog for anything relevant. It looked almost the same with a little different information here and there:
```
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.030000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.030000]  sda: sda1 sda2 < sda5 >
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.060000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.060000]  sdb: sdb1
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 1:0:0:0: [sdb] Attached SCSI disk
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.080000] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.080000]  sdc: sdc1
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 2:0:0:0: [sdc] Attached SCSI disk
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] 1465149168 512-byte hardware sectors (750156 MB)
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] 1465149168 512-byte hardware sectors (750156 MB)
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] Write Protect is off
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Oct 20 21:30:26 NAS kernel: [    8.100000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 21:30:26 NAS kernel: [    8.100000]  sdd: sdd1
Oct 20 21:30:26 NAS kernel: [    8.110000] sd 3:0:0:0: [sdd] Attached SCSI disk
Oct 20 21:30:26 NAS kernel: [    8.110000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 20 21:30:26 NAS kernel: [    8.110000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Oct 20 21:30:26 NAS kernel: [    8.110000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Oct 20 21:30:26 NAS kernel: [    8.110000] sd 3:0:0:0: Attached scsi generic sg3 type 0
Oct 20 21:30:26 NAS kernel: [    8.130000] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
Oct 20 21:30:26 NAS kernel: [    8.130000] ehci_hcd 0000:00:13.2: EHCI Host Controller
Oct 20 21:30:26 NAS kernel: [    8.130000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
Oct 20 21:30:26 NAS kernel: [    8.130000] ehci_hcd 0000:00:13.2: debug port 1
Oct 20 21:30:26 NAS kernel: [    8.130000] ehci_hcd 0000:00:13.2: irq 20, io mem 0xfe029000
Oct 20 21:30:26 NAS kernel: [    8.130000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

.
.
.

Oct 20 21:30:26 NAS kernel: [   16.250000] EXT3 FS on sda1, internal journal
Oct 20 21:30:26 NAS kernel: [   16.590000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Oct 20 21:30:26 NAS kernel: [   16.590000] SGI XFS Quota Management subsystem
Oct 20 21:30:26 NAS kernel: [   16.600000] XFS: SB read failed

.
.
.

Oct 20 21:31:18 NAS kernel: [   70.280000] XFS: SB read failed
Oct 20 21:31:31 NAS kernel: [   83.580000] XFS: SB read failed
Oct 20 21:32:30 NAS kernel: [  141.990000] md: md0 stopped.
Oct 20 21:32:31 NAS kernel: [  143.740000] md: bind<sdc1>
Oct 20 21:32:31 NAS kernel: [  143.740000] md: bind<sdd1>
Oct 20 21:32:31 NAS kernel: [  143.740000] md: bind<sdb1>
Oct 20 21:32:32 NAS kernel: [  143.820000] raid5: automatically using best checksumming function: pIII_sse
Oct 20 21:32:32 NAS kernel: [  143.870000]    pIII_sse  :  3062.800 MB/sec
Oct 20 21:32:32 NAS kernel: [  143.870000] raid5: using function: pIII_sse (3062.800 MB/sec)
Oct 20 21:32:32 NAS kernel: [  144.050000] raid6: int32x1    427 MB/s
Oct 20 21:32:32 NAS kernel: [  144.220000] raid6: int32x2    435 MB/s
Oct 20 21:32:32 NAS kernel: [  144.390000] raid6: int32x4    368 MB/s
Oct 20 21:32:32 NAS kernel: [  144.560000] raid6: int32x8    262 MB/s
Oct 20 21:32:32 NAS kernel: [  144.730000] raid6: mmxx1      813 MB/s
Oct 20 21:32:33 NAS kernel: [  144.900000] raid6: mmxx2     1473 MB/s
Oct 20 21:32:33 NAS kernel: [  145.070000] raid6: sse1x1    1497 MB/s
Oct 20 21:32:33 NAS kernel: [  145.240000] raid6: sse1x2    3075 MB/s
Oct 20 21:32:33 NAS kernel: [  145.410000] raid6: sse2x1    3103 MB/s
Oct 20 21:32:33 NAS kernel: [  145.580000] raid6: sse2x2    4257 MB/s
Oct 20 21:32:33 NAS kernel: [  145.580000] raid6: using algorithm sse2x2 (4257 MB/s)
Oct 20 21:32:33 NAS kernel: [  145.580000] md: raid6 personality registered for level 6
Oct 20 21:32:33 NAS kernel: [  145.580000] md: raid5 personality registered for level 5
Oct 20 21:32:33 NAS kernel: [  145.580000] md: raid4 personality registered for level 4
Oct 20 21:32:33 NAS kernel: [  145.580000] raid5: device sdb1 operational as raid disk 0
Oct 20 21:32:33 NAS kernel: [  145.580000] raid5: device sdd1 operational as raid disk 2
Oct 20 21:32:33 NAS kernel: [  145.580000] raid5: device sdc1 operational as raid disk 1
Oct 20 21:32:33 NAS kernel: [  145.580000] raid5: allocated 3163kB for md0
Oct 20 21:32:33 NAS kernel: [  145.580000] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
Oct 20 21:32:33 NAS kernel: [  145.580000] RAID5 conf printout:
Oct 20 21:32:33 NAS kernel: [  145.580000]  --- rd:3 wd:3
Oct 20 21:32:33 NAS kernel: [  145.580000]  disk 0, o:1, dev:sdb1
Oct 20 21:32:33 NAS kernel: [  145.580000]  disk 1, o:1, dev:sdc1
Oct 20 21:32:33 NAS kernel: [  145.580000]  disk 2, o:1, dev:sdd1
Oct 20 21:32:36 NAS kernel: [  148.760000] Filesystem "md0": Disabling barriers, not supported by the underlying device
Oct 20 21:32:37 NAS kernel: [  148.780000] XFS mounting filesystem md0
Oct 20 21:32:37 NAS kernel: [  149.090000] Ending clean XFS mount for filesystem: md0

```

I hope this helps at all :???: Ugh this is really getting on my nerves. It makes sense that if a raid array is created that it would continue to work after a system reboot. 

Thinking that the module was not starting automatically with the kernel I added it to my /etc/modules as well as a raid5 entry, so now it looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
md
raid5

```

It didn't change anything. I'm really taking stabs in the dark here :lolflag:

I spoke to a friend today and he recommend I attempt to us "mkinitramfs" which is part of the "initramfs-tools" package. I've never heard of it until he brought it up and I would like some input on it.

I actually found something amusing and it MAY by my issue but I'm not sure how I would go about fixing it. After I have my array working and mounted (that is after modprobe md, mdadm --assemble --scan, and mount) I did an fdisk -l and got the following:

```
nas@NAS:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60614   486881923+  83  Linux
/dev/sda2           60615       60801     1502077+   5  Extended
/dev/sda5           60615       60801     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b401f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003a9e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/md0: 1500.3 GB, 1500307259392 bytes
2 heads, 4 sectors/track, 366285952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

I could swear it's formatted in XFS ](*,) The whole reason I chose XFS was for Online Resizing. Is this my culprit somehow?

PS. sorry for my exuberantly long posts :)

---

### Post by fjgaude on 2008-10-21
For one thing fdisk doesn't understand raid arrays...

I believe I understand your situation, but I'm not that up on things like **initramfs** but is likely a trick to get md to load if we knew all the code to put into the script.

What kernel are you running?

---

### Post by xyvian on 2008-10-21
I am currently running kernel version 2.6.22-15-server

---

### Post by fjgaude on 2008-10-21
Don't remember if I had any troubles with kernels autoloading arrays that far back. I'm using 2.6.24-21 now, testing 2.6.27, and that really looks good, what with 2.6.7 of mdadm. The 2.6.24 kernel comes with 2.6.3.

Can't say if any of this makes any difference. 2.6.7 is more robust at handling errors than 2.6.3, lots of other small changes.

---

### Post by xyvian on 2008-10-22
I've been thinking about upgrading to Hardy soon anyways so I guess I am going to nuke and pave. Start fresh and hope everything works out alright. I'll get back when I am through. Thanks for your help so far :)

---

### Post by xyvian on 2008-10-24
Alright so funny thing just happened. I wanted to back up all of my data from my current OS drive to an external drive before I reinstalled. So I attempted to boot into an Ubuntu live CD (since my server suddenly stopped booting). During the boot process I was getting a lot of IO errors and problems reading from sectors on the hard disk. 

Naturally I suspected my disk was failing and popped in my Hiren's Boot CD to run a HDD Regenerator. (I wanted it booted long enough to retrieve my data). My system took a good 10 minutes to detect all hard drives in my system and found all but the disk I wanted.

So now the hard drive is no longer recognized in any computer I put it in and makes the boot process take forever. I have to assume the reason why I was having so many issues with this raid array was because mdadm must have been installed on a portion of the disk with the bad sectors. when trying to read those sectors on boot-up it would give up and continue the boot process (I hope. Really don't want this problem when I get my "new" refurbished RMA drive from Western Digital). 

Anyways I did put all of my data on the RAID array before any of this happened just as curiosity to see if it would retain all of my data through the --assemble --scan process. I have since then booted into a live CD and found all my data to still be there (whew). 

I would like to thank everyone for their help so far and I will keep you up to date as to whether the "new" drive will fix my problem.

On a side note ---- I would suggest never using a Dell Optiplex (the really really small ones with absolutely no air flow) as an interim file server. I did until I could afford more drives, mobo, cpu, case, and psu and where did it get me? It killed my 500GB drive. It really perturbed me that it was always running at 65*C (yes that's about 150 Degrees F!) but I was helpless to do anything about it. I was constantly checking my SMART status, as I would suggest all of you doing, but sadly it never picked anything up. I was just lucky enough to have backed up all of my data before hand (even if it is on a RAID array I don't quite trust yet).

Anyways have a great day everybody and thanks,
Brian

---

### Post by fjgaude on 2008-10-24
Okay, it's good to see you have a clear head... I can't comment on any of the hardware issues but I can urge all to have backups of any data that is valuable. I have three backups, one on-line, one near-line, and one off-line, that how important my data is to me. <smile>

By all means keep us informed as to how you are doing.

---

### Post by xyvian on 2008-11-07
Ok I've gotten my new hard disk! Yay! Tired of running ubuntu off the live CD. After running a badblocks on it I've installed Ubuntu Server 8.04.1, and I've gotten my raid array working just as I want it to working flawlessly. Installed mdadm, built the array, mounted it. Edited my fstab and it will mount automatically on reboot. All of my problems I would have to say were caused by a bad hard drive.

I would like to thank you for your help, fjgaude. *bows*

---

### Post by fjgaude on 2008-11-07
Peace, brother, chin up all is well, one way or the other. <smile>

---

