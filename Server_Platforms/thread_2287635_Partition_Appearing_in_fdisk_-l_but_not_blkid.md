---
title: "Partition Appearing in fdisk -l but not blkid"
date: 2015-07-21
forum: Server Platforms
---

### Post by Alexander_Rey on 2015-07-21
Hi,

I'm trying to track down the UUIDs of my disk partitions; however, the partitions aren't showing up when I use the blkid command. I recently formatted the disk in Windows, and when I run fdisk -l I get the following output (sdb is what I'm having issues with- specially partitions 3 and 4):

```

alexander@Server:/media$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004f5a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308457471   154227712   83  Linux
/dev/sda2       308459518   312580095     2060289    5  Extended
/dev/sda5       308459520   312580095     2060288   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f03ce06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39a9762a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      409639      204819+  ee  GPT
/dev/sdb2          411648   727044095   363316224    7  HPFS/NTFS/exFAT
/dev/sdb3       727044096  1034244095   153600000    7  HPFS/NTFS/exFAT
/dev/sdb4      1034244096  1953521663   459638784    f  W95 Ext'd (LBA)
/dev/sdb5      1034246144  1953521663   459637760    7  HPFS/NTFS/exFAT



```

blkid returns the following: 

```
/dev/sda1: UUID="a6090337-2597-485e-acb0-d6a8a30f70f9" TYPE="ext4"
/dev/sda5: UUID="b2ebbce8-90df-4a8b-aec2-19bac0e0164d" TYPE="swap"
/dev/sdc1: LABEL="EFI" UUID="67E3-17ED" TYPE="vfat"
/dev/sdc2: LABEL="MediaNTFS" UUID="9A6C7D846C7D5C47" TYPE="ntfs"
/dev/sdb1: LABEL="EFI" UUID="67E3-17ED" TYPE="vfat"
/dev/sdb2: LABEL="PICTURES" UUID="EAFA83E9FA83AFFD" TYPE="ntfs"


```

As far as I know, dev/sdb3 and dev/sdb4 should be formatted as NTFS the same as sdb2 (which I've already successfully mounted). I've looked around online for a solution, but I can't seem to find anything. 
[https://askubuntu.com/questions/179938/ntfs-drive-show-in-fdisk-l-not-when-i-run-blkid-unable-to-mount-drive](https://askubuntu.com/questions/179938/ntfs-drive-show-in-fdisk-l-not-when-i-run-blkid-unable-to-mount-drive) is close, but I get a "not found" error when I try to mount the partition using the mount command, even with the correct /dev/sdb3 

Any help would be appreciated!

---

### Post by oldfred on 2015-07-21
Fdisk does not support gpt partitioned drives. There is a brand new fdisk that does, but most will not have it.
You need to use parted or gdisk.
       sudo parted /dev/sdc unit s print

 sudo gdisk -l /dev/sdc
If you do not have gdisk
sudo apt-get install gdisk

Drives partitioned with gpt have a protective MBR. It normally just has one gpt entry, so older partition tools do see the drive is partitioned and you do not attempt to repartition with wrong tools.

      
 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.
Ubuntu will boot from gpt with either BIOS or UEFI if correct supporting partitions are on drive. 
You need an efi partition at beginning of drive for UEFI boot or a unformatted 1MB bios_grub partition for BIOS/CSM/Legacy boot.

---

### Post by Alexander_Rey on 2015-07-21
Hi,

Thank you for the reply- it send me in the right direction to figure this one out. In case anyone else has this problem in the future, here's what worked. 

Apparently formatting the disk in windows created a GPT with a hybrid MBR and logical partitions, aka. a bit of a mess all around. Blkid only recognized the GPT, which (if I understand it correctly) had a protective partition setup to cover the entire disk. So it showed the name for the second partition, but the size of the rest of the disk. 

In any case, to fix it I ran gdisk -> repair (r) -> Load MBR and build fresh GPT from it (f). I had all the data backed up, so I just ran with it, and it worked!  The disk no longer has a hybrid MBR, and is just three partitions with a GPT.

Moral of the story, don't format disks in windows with several partitions and NTFS formatting and then use them in Linux... seems obvious now.

---

### Post by oldfred on 2015-07-21
Glad you got it resolved.

If just a data drive, you can have MBR(msdos) or gpt(GUID) partitioning. It sounds like you just used gdisk to clean up and convert to gpt. You may have been able to convert to MBR also. 

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

