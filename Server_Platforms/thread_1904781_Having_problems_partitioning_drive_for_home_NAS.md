---
title: "Having problems partitioning drive for home NAS"
date: 2012-01-05
forum: Server Platforms
---

### Post by WhatTheHell? on 2012-01-05
I am trying to make a home NAS.

I've installed ubuntu server and have ssh'd into it.

The server has 2 HDs each 2tb in size.  I want to share them with SAMBA as JBOD.

OS version - Linux 2.6.32-34-server #77-Ubuntu SMP x86_64 GNU/Linux
Command line only, there is no gui.
Other Hardware - Irrelevant 


_My problem:_
I am simply trying to partition or mount a partition on one of the disks.  (I'm not really sure which because I'm semi-noob.)
The second drive, sdb is formatted, mounted and working fine.  It is the  first drive that is the problem.  The first drive (which has the OS),  seems to have 1.8TB missing or unallocated or unformatted, mounted,  whatever, I don't know.  I can't figure out how mount or format the unused space so it can be mounted and shared.



A "lshw -c disk" gives the following:

[COLOR=Navy]$ sudo lshw -c disk
  *-disk:0                
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 51.0
       serial: WD-WMAZA1210747
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=1bd8394a-be0a-429b-812d-b20b15b46b4a
  *-disk:1
       description: ATA Disk
       product: WDC WD20EARS-00M
       vendor: Western Digital
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 51.0
       serial: WD-WMAZA0721933
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5[/COLOR]



"df -h"  gives the following:

[COLOR=Navy]razux@Alpha:/etc/samba$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   2.1G     16G   12% /
none                    431M  200K  431M   1% /dev
none                    436M        0  436M   0% /dev/shm
none                    436M  324K  436M   1% /var/run
none                    436M        0  436M   0% /var/lock
none                    436M        0  436M   0% /lib/init/rw
none                       19G   2.1G     16G  12% /var/lib/ureadahead/debugfs
/dev/sdb1             1.8T  196M    1.8T   1% /media/Alpha_Primary_002[/COLOR]



"fdisk -l"  gives the following:

[COLOR=Navy]$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux
[/COLOR]


So then I try parted and list the current partitions:

[COLOR=Navy]$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  20.0GB  20.0GB  ext4                  boot
 2      20.0GB  22.0GB  2000MB  linux-swap(v1)[/COLOR]



See, only 22 GB seems to be formatted.

Any help?

---

### Post by 2F4U on 2012-01-05
You have to create a filesystem on the unallocated space before you can mount it.

---

### Post by WhatTheHell? on 2012-01-05
Followup.  Success.

Ok.  This is what I attempted to do.  I listed the partitions using print, in parted.  

[COLOR=Navy](parted) print
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system           Name  Flags
 1      1049kB  20.0GB    20.0GB  ext4                               boot
 2       20.0GB  22.0GB  2000MB  linux-swap(v1)[/COLOR]


Then I listed partitions using command line.

[COLOR=Navy]$ cat /proc/partitions
major minor  #blocks  name

   8        0  1953514584 sda
   8        1      19530752 sda1
   8        2        1952768 sda2
   8       16 1953514584 sdb
   8       17 1953512001 sdb1[/COLOR]

Then I attempted to make a partition using that information and parted.

[COLOR=Navy](parted) mkpart logical 21483520 1953514584
Error: The location 1953514584 is outside of the device /dev/sda.     [/COLOR]

I tried a whole bunch of stuff thinking I was supposed to use blocks or bytes or something and kept getting errors till I finally figured out I could just put "22GB 2000GB" in there.


[COLOR=Navy](parted) mkpart logical 22GB 2000GB
(parted) print                                                            
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  20.0GB  20.0GB  ext4                     boot
 2      20.0GB  22.0GB  2000MB  linux-swap(v1)
 3      22.0GB  2000GB  1978GB                  logical[/COLOR]




Victory!  Much thanks.

---

