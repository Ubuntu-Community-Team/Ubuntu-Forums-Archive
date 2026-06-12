---
title: "NTFS harddrive mounting issue"
date: 2016-11-05
forum: Server Platforms
---

### Post by DarkAz on 2016-11-05
Greetings everyone.

I'm in the process of (trying) to make a home server with Ubuntu Server 16.04.1. Installed fine, setup fine, mounted 3 out of 4 HDD's fine. The 4th one however is giving me a headache.

It's a 3TB hdd with a single partition (full size) with NTFS file size. Since the hdd has about 2TB of content I was looking for a way to fix whatever is the issue without having to format it. The drive itself works fine in Windows, as in it's detected in its full size with all content. Chkdsk has been run, and no errors were found.

Fast forward to Ubuntu and we get these results:

dmesg
```
[    2.688804] sd 3:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.73 TiB)
[    2.688805] sd 3:0:0:0: [sdd] 4096-byte physical blocks
[    2.688832] sd 3:0:0:0: [sdd] Write Protect is off
[    2.688833] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.688845] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.733788]  sdd: sdd1
[    2.733897] sd 3:0:0:0: [sdd] Attached SCSI disk
[ 6148.133683]  sdd: sdd1
```

fdisk -l (note the detected partition size at 350GB, as mentioned it's the full 3TB)
```
Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00028375

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdd1  *      256 732558335 732558080 349.3G  7 HPFS/NTFS/exFAT
```

mapping attempt with sudo mount /dev/sdd1 /location
```
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

mapping attempt with -t ntfs or ntfs-3g
```
NTFS signature is missing.
Failed to mount '/dev/sdd1': Invalid argument
The device '/dev/sdd1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

ntfsfix
```
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
```

Also tried TestDisk, but no luck. I'm at me wit's end, before I go for the tactical format strike does anyone have any tips or magical solutions?

---

### Post by darkod on 2016-11-05
1. Before we get into more details. Why would you keep ntfs drives for a linux server? Do you still need to move them between linux and windows? If not, move the data somewhere temporarily and format the disk with linux filesystem, the way it's supposed to be. Not to mention that ubuntu will be able to better control and use permissions on linux filesystem, not ntfs.

2. For 3TB disk to have one single partition, it needs to have gpt table, not msdos. fdisk seems to show dos table but fdisk is no good for gpt disks. Try what parted says about the disk:
```
sudo parted /dev/sdd print
```

In any case, windows is known to work in its own way sometimes, so maybe the disk did not get formatted correctly under windows. Yes I know, you say windows can read it, but that doesn't mean other tools will be able to read it correctly.

To summarize, if you plan to use this disk only on linux from now on, I would really try to find a way to temporarily move the data and format it with ext4 or similar. That goes for all disks, not just that one.

PS. And don't keep trying ntfs fixing tools in linux, they are not native to linux and I wouldn't trust them a lot. You can mess up your data potentially. Stick to ntfs fixing on windows OS only.

---

### Post by oldfred on 2016-11-05
Some vendors use proprietary drivers to allow a MBR(msdos) partitioned drive to work on a drive over 2TiB which is the limit with MBR.
You really should have gpt.There are tools to convert, but if a proprietary format they may not work, so you need to backup anyway.

       MBR details including 2TiB limit and GPT link
[URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record
[/URL]
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 

[URL="http://en.wikipedia.org/wiki/Extended_boot_record"]http://en.wikipedia.org/wiki/Extended_boot_record

      [/URL]
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
    [URL="http://en.wikipedia.org/wiki/Extended_boot_record"]
[/URL]

---

### Post by DarkAz on 2016-11-05
Apologies on the late reply, and thank you for the answers oldfred and darkod. The output for parted is as follows:
```
Model: ATA WDC WD30EZRX-00S (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start  End    Size   Type     File system  Flags
 1      131kB  375GB  375GB  primary               boot
```

For now I've mostly surrendered to the fact that I will be formatting the drive, so I'll start copying things around. If in the meantime I find anything else to try cool, if not I'll go ahead and format once completed.

---

