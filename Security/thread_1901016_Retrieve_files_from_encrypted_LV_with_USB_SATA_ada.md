---
title: "Retrieve files from encrypted LV with USB SATA adapter"
date: 2011-12-27
forum: Security
---

### Post by jaguare22 on 2011-12-27
Hello,

I have connected my old laptop drive and done a lot of searching for a means to mount and access LVM partition to access my encrypted files.  Here is what I have tried...

Last night I had the volume mounted and based on the readme tried clicking Access-Your-Private-Data.desktop.  Researched error and tried making that file exe and giving all users permissions.  No error but still no access.  After clicking, a blank file window comes up then closes.  Tried ecryptfs-mount-private... as instructed in readme.  Can't recall error and today I can't even mount the drive.  When I try to mount through the ubuntu disk utility or access through dolphin I get - 

Unable to mount - Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/mapper/G50-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Also tried dmesg | tail for help understanding what happens right after I connect adapter/drive -

dmesg | tail
[15068.095539] sd 4:0:0:0: [sdc] Write Protect is off
[15068.095552] sd 4:0:0:0: [sdc] Mode Sense: 00 38 00 00
[15068.095561] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[15068.097868] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[15068.474422]  sdc: sdc1 sdc2 < sdc5 >
[15068.477516] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[15068.477524] sd 4:0:0:0: [sdc] Attached SCSI disk
[15068.928402] EXT2-fs (sdc1): warning: mounting unchecked fs, running e2fsck is recommended
[15921.592740] EXT4-fs (dm-2): unable to read superblock
[16017.132118] EXT4-fs (dm-2): unable to read superblock


Also tried - 

sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        7296    58353665    5  Extended
/dev/sda5              32        7296    58353664   8e  Linux LVM

Disk /dev/dm-0: 57.3 GB, 57264832512 bytes
255 heads, 63 sectors/track, 6962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2487 MB, 2487222272 bytes
255 heads, 63 sectors/track, 302 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table
sysuser@HPDV:~/Private$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sysuser@HPDV:~/Private$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        7296    58353665    5  Extended
/dev/sda5              32        7296    58353664   8e  Linux LVM

Disk /dev/dm-0: 57.3 GB, 57264832512 bytes
255 heads, 63 sectors/track, 6962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2487 MB, 2487222272 bytes
255 heads, 63 sectors/track, 302 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000400b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              32       19458   156039169    5  Extended
/dev/sdb5              32       19458   156039168   8e  Linux LVM

Disk /dev/dm-2: 153.5 GB, 153490554880 bytes
255 heads, 63 sectors/track, 18660 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 6291 MB, 6291456000 bytes
255 heads, 63 sectors/track, 764 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table




I have the passphrase, just can't get setup to use it.

Thanks in advance...

---

