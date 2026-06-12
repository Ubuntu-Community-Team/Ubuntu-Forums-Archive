---
title: "New Install, Old Hardware RAID5"
date: 2009-02-01
forum: Server Platforms
---

### Post by scambro on 2009-02-01
Hi all,

I'm actually using the desktop version, but I'm guessing this is more of a server type issue, so thought I may find greater assistance here.  I just installed 8.10 with a Promise SuperTrak EX8350.  I built one new RAID5 (4 x 1.5 TB  GPT), and now I'm trying to mount my previously existing RAID5 (4 x 500 GB NTFS), which has existing data that needs to be preserved.

When I do fdisk -l, for the RAID that I'm missing I see: 
```
Disk /dev/sdb: 1499.9 GB, 1499999895552 bytes
255 heads, 63 sectors/track, 182364 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf538398a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182364  1464838798+  42  SFS
```

When I try to mount the drive, I get this:
```
/# mount -t ntfs /dev/sdb1 /home/raid
Failed to read last sector (2929677596): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

I read quite a bit about mdadm, but I don't believe that's what I want because this is a HW RAID, not Software based.  I tried mdadm anyway, but didn't see anything:
```
/# mdadm --assemble --scan
mdadm: No arrays found in config file or automatically

```

At this point, I'm a bit perplexed because if I toss in the WinXP boot drive, I can see the missing RAID and it's data without a problem.  Any help is greatly appreciated!  Thanks!

EDIT:  Here's what I get with testdisk /list.  SDA is the new one, SDB the other RAID, SDC is the Ubuntu system drive, and SDD is the old XP one, which I can mount and read without issue.

```
Disk /dev/sda - 4500 GB / 4191 GiB - CHS 547179 255 63, sector size=512
Disk /dev/sdb - 1499 GB / 1396 GiB - CHS 182364 255 63, sector size=512
Disk /dev/sdc - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512
Disk /dev/sdd - 80 GB / 74 GiB - CHS 9726 255 63, sector size=512

Disk /dev/sda - 4500 GB / 4191 GiB - CHS 547179 255 63
     Partition			Start        End    Size in sectors
 1 P MS Data                       34  200503518  200503485 [primary]
Disk /dev/sdb - 1499 GB / 1396 GiB - CHS 182364 255 63
     Partition			Start        End    Size in sectors
 1 P W2K Dynamic/SFS          0   1  1 182363 254 63 2929677597
```

---

### Post by scambro on 2009-02-03
Any ideas what I could try to look into?  Thanks!

---

