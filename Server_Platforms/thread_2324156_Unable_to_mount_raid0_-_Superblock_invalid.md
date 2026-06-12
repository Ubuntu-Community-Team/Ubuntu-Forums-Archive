---
title: "Unable to mount raid0 - Superblock invalid"
date: 2016-05-11
forum: Server Platforms
---

### Post by kestutiz on 2016-05-11
Hi, 
I had restored soft raid1 (md2) on same disks partitions, but not this raid0 (md3). I can assemble it, but cannot mount. below logs. Ubuntu server 14.04.3
Any ideas how to assemble and mount to able to read it?

Some history, it was created few years ago with ubuntu 8.04 and probably formatted with ext2. I did disk's tests by manufacturer tools. I can access it physically.
I spend a lot of time trying to boot ubuntu on raid disks, but there was a lot of problems. Finally decided to add third disk for system and voila! Like freenas is

```
sudo mount /dev/md3 /media/share -t ext2
mount: wrong fs type, bad option, bad superblock on /dev/md3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail
[  648.386496] md: bind<sdc4>
[  648.390141] md/raid0:md3: md_size is 539269632 sectors.
[  648.390149] md: RAID0 configuration for md3 - 1 zone
[  648.390153] md: zone0=[sdb4/sdc4]
[  648.390162]       zone-offset=         0KB, device-offset=         0KB, size= 269634816KB
[  648.390164]
[  648.390202] md3: detected capacity change from 0 to 276106051584
[  648.399923]  md3: unknown partition table
[  902.960830] EXT4-fs (md3): VFS: Can't find ext4 filesystem
[  962.575092] EXT4-fs (md3): VFS: Can't find ext4 filesystem
```

assembled like:
```
sudo mdadm --assemble --metadata=0.90 /dev/md3  /dev/sdb4 /dev/sdc4
# or like
sudo mdadm --create --assume-clean --metadata=0.90 --chunk=64 /dev/md3 --level=0 --raid-disks=2 /dev/sdb4 /dev/sdc4

```
some useful info:
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md3 : active raid0 sdc4[1] sdb4[0]
      269634816 blocks 64k chunks

md1 : active raid1 sdb2[0] sdc2[1]
      9759232 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb3[0] sdc3[1]
      97659008 blocks [2/2] [UU]

md0 : active raid0 sdb1[1] sdc1[0]
      3903488 blocks 64k chunks

unused devices: <none>

```
```
sudo fdisk -l

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c3a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3903794     1951866   fd  Linux raid autodetect
/dev/sdb2         3903795    23438834     9767520   fd  Linux raid autodetect
/dev/sdb3        23438835   218757104    97659135   fd  Linux raid autodetect
/dev/sdb4       218757105   488392064   134817480   fd  Linux raid autodetect

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00085391

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     3903794     1951866   fd  Linux raid autodetect
/dev/sdc2         3903795    23438834     9767520   fd  Linux raid autodetect
/dev/sdc3        23438835   218757104    97659135   fd  Linux raid autodetect
/dev/sdc4       218757105   488392064   134817480   fd  Linux raid autodetect

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e113e11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      514143    30716279    15101068+   7  HPFS/NTFS/exFAT
/dev/sda2        30716341   312576704   140930182    f  W95 Ext'd (LBA)
/dev/sda5        30716343    92148839    30716248+   7  HPFS/NTFS/exFAT
/dev/sda6        92148903   153581399    30716248+  83  Linux
/dev/sda7       153581463   312576704    79497621    7  HPFS/NTFS/exFAT

Disk /dev/md0: 3997 MB, 3997171712 bytes
2 heads, 4 sectors/track, 975872 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 100.0 GB, 100002824192 bytes
2 heads, 4 sectors/track, 24414752 cylinders, total 195318016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 9993 MB, 9993453568 bytes
2 heads, 4 sectors/track, 2439808 cylinders, total 19518464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md3: 276.1 GB, 276106051584 bytes
2 heads, 4 sectors/track, 67408704 cylinders, total 539269632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table
```

```
sudo blkid

/dev/sdb1: UUID="56e4c31e-37af-8c96-0883-b10d409e1e0a" TYPE="linux_raid_member"
/dev/sdb2: UUID="db436aeb-43c9-9f9a-82ea-64e94faaa192" UUID_SUB="d5e1e4c6-997f-2b2d-3120-f09802edb4ee" LABEL="ubuntu:128" TYPE="linux_raid_member"
/dev/sdb3: UUID="b4b25b5c-f2e1-c236-e368-bf24bd0fce41" TYPE="linux_raid_member"
/dev/sdb4: UUID="34b1c998-afc8-a376-e368-bf24bd0fce41" TYPE="linux_raid_member"
/dev/sdc1: UUID="56e4c31e-37af-8c96-0883-b10d409e1e0a" TYPE="linux_raid_member"
/dev/sdc2: UUID="db436aeb-43c9-9f9a-82ea-64e94faaa192" UUID_SUB="5b7104c0-344a-b694-c0b8-ce34b76c69db" LABEL="ubuntu:128" TYPE="linux_raid_member"
/dev/sdc3: UUID="b4b25b5c-f2e1-c236-e368-bf24bd0fce41" TYPE="linux_raid_member"
/dev/sdc4: UUID="34b1c998-afc8-a376-e368-bf24bd0fce41" TYPE="linux_raid_member"
/dev/sda1: UUID="5074AA4674AA2F22" TYPE="ntfs"
/dev/sda5: UUID="50EED880EED86030" TYPE="ntfs"
/dev/sda6: UUID="a21c57ec-5a4c-4b9b-b640-25d0bd9bf10b" TYPE="ext4"
/dev/sda7: UUID="04E42E6DE42E6162" TYPE="ntfs"
/dev/md0: UUID="251b2eb6-25d6-4b35-8d4d-e3b96b8222c1" TYPE="swap"
/dev/md2: UUID="bc7ffa9a-77a2-48d2-8441-50c85ec13318" TYPE="ext3"
/dev/md1: UUID="e4929a4b-7b0e-4448-be52-ac0118bd8f83" TYPE="ext4"

```
```
sudo mdadm --misc --detail /dev/md3
/dev/md3:
        Version : 0.90
  Creation Time : Wed May 11 11:14:29 2016
     Raid Level : raid0
     Array Size : 269634816 (257.14 GiB 276.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Wed May 11 11:14:29 2016
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 34b1c998:afc8a376:e368bf24:bd0fce41 (local to host ubuntu)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       20        0      active sync   /dev/sdb4
       1       8       36        1      active sync   /dev/sdc4

```
```
sudo fsck.ext4 -v /dev/md3
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/md3

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```
and no success when change blocks sudo e2fsck -b block_number /dev/md3

EDIT: I tried restore superblock, no success:
 ```
sudo resize2fs /dev/md3
resize2fs 1.42.9 (4-Feb-2014)
resize2fs: Bad magic number in super-block while trying to open /dev/md3
Couldn't find valid filesystem superblock.

```

---

### Post by kestutiz on 2016-05-16
Any suggestions?
I has restored raid1 on same set of hdd another partitions, but unable to mount raid0, always have superblock issues. 

Is possible to restore superblock? or mount without superblock? Any tools or manuals how to restore raid0?

some more info:
```
 sudo parted -l
Model: ATA SAMSUNG HD160JJ (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      263MB   15.7GB  15.5GB  primary   ntfs         boot
 2      15.7GB  160GB   144GB   extended               lba
 5      15.7GB  47.2GB  31.5GB  logical   ntfs
 6      47.2GB  78.6GB  31.5GB  logical   ext4
 7      78.6GB  160GB   81.4GB  logical   ntfs


Model: ATA SAMSUNG HD250HJ (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1999MB  1999MB  primary               boot, raid
 2      1999MB  12.0GB  10.0GB  primary  ext4         raid
 3      12.0GB  112GB   100GB   primary  ext3         raid
 4      112GB   250GB   138GB   primary               raid


Model: ATA SAMSUNG HD250HJ (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  1999MB  1999MB  primary  linux-swap(v1)  boot, raid
 2      1999MB  12.0GB  10.0GB  primary                  raid
 3      12.0GB  112GB   100GB   primary  ext3            raid
 4      112GB   250GB   138GB   primary                  raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 3997MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  3997MB  3997MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 9993MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  9993MB  9993MB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md2: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  100GB  100GB  ext3


Error: /dev/md3: unrecognised disk label


```

---

### Post by darkod on 2016-05-16
Unfortunately I have no suggestions too. The difference between raid1 and raid0 is that if one member fails, raid1 is easily recoverable (assuming the other member doesn't fail too), while with raid0 you lose all the data. It looks like that is what happened to you. The filesystem is not good any more.

When you use raid0 you accept losing the data if a member fails. Only if you are very very lucky you might be able to save something I guess...

---

### Post by kestutiz on 2016-05-16
Darko, thank You for kindle message :) 
I'm ready to do format drive, but... Maybe I'm waist my and others time, sorry for that. I learned a lot about linux and ubuntu in this process. Lucky? Is not enough, but need too!

Repeat my questions, Is possible to restore superblock? or mount raid0 without superblock?
I has tried assemble command --build without superblock, but cannot mount, same error as before
```
sudo mdadm --build /dev/md3 --level=raid0 --raid-devices=2  /dev/sdb4 /dev/sdc4
```
and one more check:
```
sudo mkfs -c /dev/md3
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=16 blocks, Stripe width=32 blocks
16859136 inodes, 67408704 blocks
3370435 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
2058 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872

Checking for bad blocks (read-only test): done                                  
Allocating group tables: done
Writing inode tables: done
Writing superblocks and filesystem accounting information: done
```

---

### Post by darkod on 2016-05-16
What does that 'mkfs -c' command do? I haven't used it before. Wouldn't that format the partition /dev/md3?

---

### Post by kestutiz on 2016-05-16
no, -c mean read-only check. Normally use to format

---

### Post by darkod on 2016-05-16
Assuming you have not formatted md3 again, did you try all the superblock backups listed in post #4? Apart from that, I don't know what else to try either. You seem to have tried the standard options, and there isn't much else to do if the filesystem is not recognized. Sorry I can't help more.

PS. You probably already know this, but there is some info here too: [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

### Post by kestutiz on 2016-05-18
Darko, thanks for link, I did once or twice again. I don't know if there is step forward, anyway still can't mount, but mgs are different. After reboot I have drive renamed to md127:
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[0] sdc2[1]
      9759232 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb3[0] sdc3[1]
      97659008 blocks [2/2] [UU]

md0 : active raid0 sdb1[1] sdc1[0]
      3903488 blocks 64k chunks

md127 : active raid0 sdb4[0] sdc4[1]
      269634816 blocks 64k chunks

unused devices: <none>


```
```
sudo resize2fs /dev/md127
resize2fs 1.42.9 (4-Feb-2014)
The filesystem is already 67408704 blocks long.  Nothing to do!


```
```
 sudo e2fsck /dev/md127
e2fsck 1.42.9 (4-Feb-2014)
/dev/md127: clean, 11/16859136 files, 1073193/67408704 blocks
```
there are no more errors, but same issue with superblock when i try to mount:
```
sudo mount /dev/md127 /media/share -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
dmesg | tail
[  796.692996] EXT4-fs (md127): couldn't mount as ext3 due to feature incompatibilities
[38858.691209] EXT4-fs (md127): couldn't mount as ext3 due to feature incompatibilities

```

Wow!!! is mounted as ext2 :)
```
sudo mount /dev/md127 /media/share -t ext2
```
I'm trying to do disk test now...

---

### Post by darkod on 2016-05-18
Are you sure the filesystem is ext3? Try to check with:
```
sudo file -sL /dev/md127
or
sudo fsck -N /dev/md127
```

That should help you identify the filesystem. After that you can try mounting it correctly.

---

### Post by kestutiz on 2016-05-19
No, it's actually ext2, but I had mounted as as ext3, as I remember.
```
sudo file -sL /dev/md127
/dev/md127: Linux rev 1.0 ext2 filesystem data (mounted or unclean), UUID=93d65594-546f-433e-b1f4-66cd57c5668a (large files)

~$ sudo fsck -N /dev/md127
fsck from util-linux 2.20.1
[/sbin/fsck.ext2 (1) -- /dev/md127] fsck.ext2 /dev/md127
```

Darko, thank You for your valuable input. I value Your support :smile:
Problem generally solved, I has mounted my old partition, but there are no files on it.
Next I'll resize and format to swap and only 1 partition as ext4 and will make raid1 array. 

I has read somewhere that raid10 on 2 drives is also good choice, safe and fast. It is?

I use it as development and test home server (apache, php etc) and as file server (samba).

> **kestutiz said:**
> 
I has read somewhere that raid10 on 2 drives is also good choice, safe and fast. It is?



let's make life simple do not complicate more as it is ;)

Here is explanation and links about raid10 on 2 drives, [I]writes need to go to both disks, and involve significant head movement:
[/I][http://serverfault.com/questions/733811/linux-raid10-on-2-disks](http://serverfault.com/questions/733811/linux-raid10-on-2-disks) even here [https://blog.a2o.si/2014/09/07/linux-software-raid-why-you-should-always-use-raid-10-instead-of-raid-1/](https://blog.a2o.si/2014/09/07/linux-software-raid-why-you-should-always-use-raid-10-instead-of-raid-1/) > do not create 2 partitions on each drive, just create RAID 10 instead of  RAID 1, with only 2 devices. Instant single-threaded performance boost,  and do not worry about device order ever again:)

I'll stay with raid1

---

