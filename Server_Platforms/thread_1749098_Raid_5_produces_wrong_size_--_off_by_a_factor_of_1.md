---
title: "Raid 5 produces wrong size -- off by a factor of 1000"
date: 2011-05-04
forum: Server Platforms
---

### Post by TaleSlinger on 2011-05-04
I bought an Acer H340 and 4-2 TB Drives, and I'm trying to set up a Raid 5.
- I installed Ubuntu server 10.10 on a USB, and I'm sshing in.
- I used parted to partition each drive as ext2 - I created the raid with:
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
I get mdadm: size set to 1951680K
I expected about a 6 TB (Terra-Bytes) raid, I got a 5 GB (NOT TB -- its GB)
(from watch cat /proc/mdstat ):
5855040 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
The space is usable, but obviously not what I'm looking for.

Any idea what I'm doing wrong, or where I should look to find the answer?

Below are the mdadm detail results, the list of partitions from parted and mdadm.conf

    /dev/md0:
            Version : 00.90
      Creation Time : Tue May  3 20:51:31 2011
         Raid Level : raid5
         Array Size : 5855040 (5.58 GiB 6.00 GB)
      Used Dev Size : 1951680 (1906.26 MiB 1998.52 MB)
       Raid Devices : 4
      Total Devices : 4
    Preferred Minor : 0
        Persistence : Superblock is persistent
    
        Update Time : Tue May  3 21:48:06 2011
              State : clean
     Active Devices : 4
    Working Devices : 4
     Failed Devices : 0
      Spare Devices : 0
    
             Layout : left-symmetric
         Chunk Size : 64K
    
               UUID : 10679595:f26c982c:1f8d381f:de335696
             Events : 0.19
    
        Number   Major   Minor   RaidDevice State
           0       8        1        0      active sync   /dev/sda1
           1       8       17        1      active sync   /dev/sdb1
           2       8       33        2      active sync   /dev/sdc1
           3       8       49        3      active sync   /dev/sdd1
    
-----------------------------------
    Here's the parted output: 
    
    GNU Parted 2.3
    Using /dev/sda
    Welcome to GNU Parted! Type 'help' to view a list of commands.
    (parted) print list
    Model: ATA ST32000542AS (scsi)
    Disk /dev/sda: 2000GB
    Sector size (logical/physical): 512B/512B
    Partition Table: gpt
    
    Number  Start   End     Size    File system  Name     Flags
     1      1049kB  2000MB  1999MB  ext2         primary
    
    
    Model: ATA ST2000DL003-9VT1 (scsi)
    Disk /dev/sdb: 2000GB
    Sector size (logical/physical): 512B/512B
    Partition Table: gpt
    
    Number  Start   End     Size    File system  Name     Flags
     1      1049kB  2000MB  1999MB  ext2         primary
    
    
    Model: ATA ST2000DL003-9VT1 (scsi)
    Disk /dev/sdc: 2000GB
    Sector size (logical/physical): 512B/512B
    Partition Table: gpt
    
    Number  Start   End     Size    File system  Name     Flags
     1      1049kB  2000MB  1999MB  ext2         primary
    
    
    Model: ATA WDC WD20EADS-00R (scsi)
    Disk /dev/sdd: 2000GB
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    
    Number  Start   End     Size    Type     File system  Flags
     1      1049kB  2000MB  1999MB  primary  ext2
    
    
    Model:   (scsi)
    Disk /dev/sde: 4052MB
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    
    Number  Start   End     Size    Type      File system     Flags
     1      1049kB  3815MB  3814MB  primary   ext4            boot
     2      3816MB  4051MB  235MB   extended
     5      3816MB  4051MB  235MB   logical   linux-swap(v1)
    
    
    Model: SMI USB DISK (scsi)
    Disk /dev/sdf: 257MB
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    
    Number  Start   End    Size   Type     File system  Flags
     1      32.3kB  247MB  247MB  primary  ntfs         boot
    
    
    Model: Linux Software RAID Array (md)
    Disk /dev/md0: 5996MB
    Sector size (logical/physical): 512B/512B
    Partition Table: loop
    
    Number  Start  End     Size    File system  Flags
     1      0.00B  5996MB  5996MB  ext2
    
----------------------
    
    mdadm.conf:
    
    DEVICE partitions
    #changed the 00.90 to 0.90 below
    ARRAY /dev/md0 level=raid5 num-devices=4 metadata=0.90 UUID=10679595:f26c982c:1f

---

### Post by apeganz on 2011-05-04
Your partition sizes are off by said factor. mdadm worked correctly, something went wrong when the partitions were created.

Best regards,
Alex

---

