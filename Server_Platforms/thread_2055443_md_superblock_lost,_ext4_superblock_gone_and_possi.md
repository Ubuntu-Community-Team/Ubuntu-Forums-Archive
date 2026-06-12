---
title: "md superblock lost, ext4 superblock gone and possibly some moved partitions"
date: 2012-09-09
forum: Server Platforms
---

### Post by hinnerkh on 2012-09-09
Hello,

my server, running Ubuntu 12.04, has two hard drives and a total of seven md raid devices each a mirror on both drives. Last friday it lost a hard disk (/dev/sda) due to faulty hardware. After replacing it, the system came up successfully from the second drive (/dev/sdb). I partitioned it using sgdisk:

```
$ sgdisk -G -R=/dev/sda /dev/sdb
```

After that the system did not boot. The only way to start it was using a rescue system which the hoster provides: Debian GNU/Linux 6.0.2 (squeeze), Linux rescue 2.6.39.2 #1 SMP Mon Jul 25 18:36:18 CEST 2011 x86_64 GNU/Linux and mdadm v3.1.4 31st August 2010.

Problem is, of the seven raid devices only /dev/md0 came up automatically, which isn't very helpful as that's the swap device. :(

Building the other devices manually like this didn't give any errors, but mounting the device failed with mount: wrong fs type, bad option, bad superblock on /dev/md1

```
$ mdadm -B --verbose -n 2 -l mirror --assume-clean /dev/md1 missing /dev/sdb2
```

Manually assembling the devices didn't work at all:

```
$ mdadm --assemble --run /dev/md1 /dev/sdb2
mdadm: no recogniseable superblock on /dev/sdb2
mdadm: /dev/sdb2 has no superblock - assembly aborted

```

Mounting the file systems directly did work for one device, /dev/sdb3, the others said:

```
$ mount -t ext4 -o ro,noload /dev/sdb6 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I've included the data from parted -l, mdadm -Evvvvs, mdadm.conf and sgdisk below, hopefully anyone sees something I've missed or has any ideas?

Additionally it seems to me that the partitions are slightly off (or that mdadm doesn't include metadata in its reports?). If the partitions changed, it might explain why most superblocks could not be found:

```
/dev/sdb:
sgdisk:  Disk /dev/sdb: 5860533168 sectors, 2.7 TiB, Logical sector size: 512 bytes
DMESG:sd 1:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
All entries from mdadm: 5860515630, difference is 17538

/dev/sdb1:
mdadm: Array Size : 67106672 (32.00 GiB 34.36 GB)
sgdisk size:        67182591, difference: 75919

/dev/sdb2:
mdadm: Array Size : 20969328 (10.00 GiB 10.74 GB)
sgdisk size:        20899839, difference: 69489

/dev/sdb3:
mdadm: Array Size : 419428208 (200.00 GiB 214.75 GB)
sgdisk size:        419725311, difference: 297103

/dev/sdb4
mdadm: Array Size : 419428208 (200.00 GiB 214.75 GB)
sgdisk size:        419921919, difference: 493711

/dev/sdb5
mdadm: Array Size : 2795501296 (1333.00 GiB 1431.30 GB)
sgdisk size:        2794921983, difference: 579313

/dev/sdb6
mdadm: Array Size : 2138081918 (1019.52 GiB 1094.70 GB)
sgdisk size:        2137876479, difference: 205439

/dev/sdb7
mdadm: Not part of any array
sgdisk: 2048            4095   1024.0 KiB  EF02

```

Output of parted -l before the replacement of /dev/sda

```
$ sudo parted -l
Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 7      1049kB  2097kB  1049kB                     bios_grub
 1      2097kB  34.4GB  34.4GB                     raid
 2      34.4GB  45.1GB  10.7GB                     raid
 3      45.1GB  260GB   215GB                      raid
 4      260GB   475GB   215GB                      raid
 5      475GB   1906GB  1431GB                     raid
 6      1906GB  3001GB  1095GB                     raid


Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 7      1049kB  2097kB  1049kB                     bios_grub
 1      2097kB  34.4GB  34.4GB                     raid
 2      34.4GB  45.1GB  10.7GB                     raid
 3      45.1GB  260GB   215GB                      raid
 4      260GB   475GB   215GB                      raid
 5      475GB   1906GB  1431GB                     raid
 6      1906GB  3001GB  1095GB                     raid


Model: Linux Software RAID Array (md)
Disk /dev/md1: 10.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  10.7GB  10.7GB  ext3


Model: Linux Software RAID Array (md)
Disk /dev/md3: 215GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  215GB  215GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md5: 1095GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1095GB  1095GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md0: 34.4GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  34.4GB  34.4GB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md4: 1431GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1431GB  1431GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md2: 215GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  215GB  215GB  ext4

```

Output of mdadm -Evvvvs before replacing the disk

```
$ sudo mdadm -Evvvvs
[sudo] password for hinnerk: 
mdadm: No md superblock detected on /dev/md/2.
mdadm: No md superblock detected on /dev/md/4.
mdadm: No md superblock detected on /dev/md/0.
mdadm: No md superblock detected on /dev/md/5.
mdadm: No md superblock detected on /dev/md/3.
mdadm: No md superblock detected on /dev/md/1.
mdadm: No md superblock detected on /dev/sdb7.
/dev/sdb6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 85ae5862:6e0470db:35da6510:083e55da
           Name : rescue:5
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2138082191 (1019.52 GiB 1094.70 GB)
     Array Size : 2138081918 (1019.52 GiB 1094.70 GB)
  Used Dev Size : 2138081918 (1019.52 GiB 1094.70 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 10edcb91:9686cb45:4843b750:4d50b89d

    Update Time : Fri Sep  7 12:26:12 2012
       Checksum : cea03421 - correct
         Events : 25


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
/dev/sdb5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ecb053e6:4d637746:151d02a3:6a414cf8
           Name : rescue:4
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2795501568 (1333.00 GiB 1431.30 GB)
     Array Size : 2795501296 (1333.00 GiB 1431.30 GB)
  Used Dev Size : 2795501296 (1333.00 GiB 1431.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9ee535fa:878a880b:52dfee50:b6bf0b81

    Update Time : Fri Sep  7 12:26:27 2012
       Checksum : cd46bc8e - correct
         Events : 25


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
/dev/sdb4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f2bfa4fc:886e6ce1:9c60b807:b903a7ab
           Name : rescue:3
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 419428352 (200.00 GiB 214.75 GB)
     Array Size : 419428208 (200.00 GiB 214.75 GB)
  Used Dev Size : 419428208 (200.00 GiB 214.75 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1cb1a45f:38b6d6a9:366112c0:dc60a2f5

    Update Time : Fri Sep  7 12:26:27 2012
       Checksum : 61d4f75e - correct
         Events : 25


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3fe84ba0:18265e97:84964398:774b023b
           Name : rescue:2
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 419428352 (200.00 GiB 214.75 GB)
     Array Size : 419428208 (200.00 GiB 214.75 GB)
  Used Dev Size : 419428208 (200.00 GiB 214.75 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0597cef5:ab3ac1cf:813dfa18:c5783fde

    Update Time : Fri Sep  7 12:26:26 2012
       Checksum : d7edb373 - correct
         Events : 29


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c5325591:6a0eed7a:7bfd49ea:d06bb77a
           Name : rescue:1
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 20969472 (10.00 GiB 10.74 GB)
     Array Size : 20969328 (10.00 GiB 10.74 GB)
  Used Dev Size : 20969328 (10.00 GiB 10.74 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : df19c892:fff351bd:6450ba27:b287a9f1

    Update Time : Fri Sep  7 06:26:40 2012
       Checksum : ba757743 - correct
         Events : 25


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d400275b:276d2798:a0e908b2:7deb36c3
           Name : rescue:0
  Creation Time : Wed Jun  6 15:37:24 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 67106816 (32.00 GiB 34.36 GB)
     Array Size : 67106672 (32.00 GiB 34.36 GB)
  Used Dev Size : 67106672 (32.00 GiB 34.36 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1548ecc3:5d872e0b:54f064eb:68fa6608

    Update Time : Wed Sep  5 02:03:19 2012
       Checksum : fa60361 - correct
         Events : 25


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sda7.
/dev/sda6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 85ae5862:6e0470db:35da6510:083e55da
           Name : rescue:5
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2138082191 (1019.52 GiB 1094.70 GB)
     Array Size : 2138081918 (1019.52 GiB 1094.70 GB)
  Used Dev Size : 2138081918 (1019.52 GiB 1094.70 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 49889f6a:3cc3bd55:98a2f8ef:1f9f6a4d

    Update Time : Fri Sep  7 12:26:12 2012
       Checksum : 659ba22 - correct
         Events : 25


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sda5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ecb053e6:4d637746:151d02a3:6a414cf8
           Name : rescue:4
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2795501568 (1333.00 GiB 1431.30 GB)
     Array Size : 2795501296 (1333.00 GiB 1431.30 GB)
  Used Dev Size : 2795501296 (1333.00 GiB 1431.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 26ba8652:1539677f:93444d85:7a08ac9f

    Update Time : Fri Sep  7 12:26:27 2012
       Checksum : ec74f1f9 - correct
         Events : 26


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sda4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f2bfa4fc:886e6ce1:9c60b807:b903a7ab
           Name : rescue:3
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 419428352 (200.00 GiB 214.75 GB)
     Array Size : 419428208 (200.00 GiB 214.75 GB)
  Used Dev Size : 419428208 (200.00 GiB 214.75 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a95db231:f143d3ae:90ee5a7e:ea227583

    Update Time : Fri Sep  7 12:26:27 2012
       Checksum : 84fa810a - correct
         Events : 25


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3fe84ba0:18265e97:84964398:774b023b
           Name : rescue:2
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 419428352 (200.00 GiB 214.75 GB)
     Array Size : 419428208 (200.00 GiB 214.75 GB)
  Used Dev Size : 419428208 (200.00 GiB 214.75 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2e44e91b:9f070e66:3896f6fb:edf14fe4

    Update Time : Fri Sep  7 12:26:26 2012
       Checksum : 7d61ff6e - correct
         Events : 29


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c5325591:6a0eed7a:7bfd49ea:d06bb77a
           Name : rescue:1
  Creation Time : Wed Jun  6 15:37:25 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 20969472 (10.00 GiB 10.74 GB)
     Array Size : 20969328 (10.00 GiB 10.74 GB)
  Used Dev Size : 20969328 (10.00 GiB 10.74 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 03cdb81c:a8326065:d7071af5:d00fc877

    Update Time : Fri Sep  7 06:26:40 2012
       Checksum : 3ff2a8a0 - correct
         Events : 25


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d400275b:276d2798:a0e908b2:7deb36c3
           Name : rescue:0
  Creation Time : Wed Jun  6 15:37:24 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 67106816 (32.00 GiB 34.36 GB)
     Array Size : 67106672 (32.00 GiB 34.36 GB)
  Used Dev Size : 67106672 (32.00 GiB 34.36 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b50e9e4b:45dd8e56:9eac5d2d:439b633e

    Update Time : Wed Sep  5 02:03:19 2012
       Checksum : 5aad7d0c - correct
         Events : 25


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

```


Content of /etc/mdadm/mdadm.conf before replacement

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=d400275b:276d2798:a0e908b2:7deb36c3 name=rescue:0
ARRAY /dev/md/1 metadata=1.2 UUID=c5325591:6a0eed7a:7bfd49ea:d06bb77a name=rescue:1
ARRAY /dev/md/2 metadata=1.2 UUID=3fe84ba0:18265e97:84964398:774b023b name=rescue:2
ARRAY /dev/md/3 metadata=1.2 UUID=f2bfa4fc:886e6ce1:9c60b807:b903a7ab name=rescue:3
ARRAY /dev/md/4 metadata=1.2 UUID=ecb053e6:4d637746:151d02a3:6a414cf8 name=rescue:4
ARRAY /dev/md/5 metadata=1.2 UUID=85ae5862:6e0470db:35da6510:083e55da name=rescue:5

```

Output of parted -l after replacing the disk and partitioning the new disk

```
root@rescue ~ # parted -l /dev/sda
Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 7      1049kB  2097kB  1049kB                     bios_grub
 1      2097kB  34.4GB  34.4GB                     raid
 2      34.4GB  45.1GB  10.7GB                     raid
 3      45.1GB  260GB   215GB                      raid
 4      260GB   475GB   215GB                      raid
 5      475GB   1906GB  1431GB                     raid
 6      1906GB  3001GB  1095GB                     raid


Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 7      1049kB  2097kB  1049kB                     bios_grub
 1      2097kB  34.4GB  34.4GB                     raid
 2      34.4GB  45.1GB  10.7GB                     raid
 3      45.1GB  260GB   215GB   ext4               raid
 4      260GB   475GB   215GB                      raid
 5      475GB   1906GB  1431GB                     raid
 6      1906GB  3001GB  1095GB                     raid
 
```


Output of sgdisk -l /dev/sdb after replacement


```
# sgdisk -p /dev/sdb
Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6C614A1C-565F-4AAE-83E0-7C8BB30E8814
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            4096        67186687   32.0 GiB    FD00  
   2        67186688        88086527   10.0 GiB    FD00  
   3        88086528       507811839   200.1 GiB   FD00  
   4       507811840       927733759   200.2 GiB   FD00  
   5       927733760      3722655743   1.3 TiB     FD00  
   6      3722655744      5860532223   1019.4 GiB  FD00  
   7            2048            4095   1024.0 KiB  EF02
```

---

