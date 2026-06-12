---
title: "Added disk to raid5 array, but having issues expanding the partition."
date: 2016-12-19
forum: Server Platforms
---

### Post by David_Moore on 2016-12-19
I've added the disk and rebuilt the raid array, but I'm having issues resizing the partition to utilize the new drive size.

/dev/sdb1 is my raid array and currently showing 11TB

Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-34-generic x86_64)

david@FREYJA:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   14M  1.6G   1% /run
/dev/sda1        95G  9.9G   80G  12% /
tmpfs           7.9G  4.0K  7.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sdb1        11T  9.7T  1.2T  90% /Storage
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G     0  1.6G   0% /run/user/1000

As you can see below, sdb is showing a max size of 13.7TB after I've added the drive.

david@FREYJA:~$ sudo fdisk -l
Disk /dev/sdb: 13.7 TiB, 15002522091520 bytes, 29301800960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 871A2F45-5673-41DB-82B2-B890EF1DA82F

Device     Start         End     Sectors  Size Type
/dev/sdb1   2048 23441438719 23441436672 10.9T Linux filesystem

I've attempted to use resize2fs to expand the partition, but I'm getting the following error.
david@FREYJA:~$ sudo resize2fs -f /dev/sdb1
[sudo] password for david:
resize2fs 1.42.13 (17-May-2015)
The filesystem is already 2930179584 (4k) blocks long.  Nothing to do!

Has anyone ran into this issue?

---

### Post by darkod on 2016-12-19
The partition sdb1 still takes only 11TB from the 13TB. That is why resize2fs has no possibility to extend the filesystem. You first need to extend the partition sdb1 to take all of sdb, and then extend the filesystem.

Situation like this is why it is recommended to use LVM especially if you estimate that you will need storage expansion on the server in the future. It makes extending LVs very easy and trouble free.

PS. Since your root is not on sdb1 you might be able to temporarily unmount sdb1 (you might need to stop some services if they are using it), extend it using parted or similar...

---

### Post by David_Moore on 2016-12-20
> **darkod said:**
> The partition sdb1 still takes only 11TB from the 13TB. That is why resize2fs has no possibility to extend the filesystem. You first need to extend the partition sdb1 to take all of sdb, and then extend the filesystem.

Situation like this is why it is recommended to use LVM especially if you estimate that you will need storage expansion on the server in the future. It makes extending LVs very easy and trouble free.

PS. Since your root is not on sdb1 you might be able to temporarily unmount sdb1 (you might need to stop some services if they are using it), extend it using parted or similar...

Darko,

Thanks for your response. I was able to successfully resize my partition!

First I determined which services were using the mount by issuing the "lsof +f-- /Storage" command.

Next, I stopped the services then unmounted the drive.

david@FREYJA:~$ sudo service plexmediaserver stop
[sudo] password for david:
david@FREYJA:~$ sudo service smbd stop
david@FREYJA:~$ sudo umount /Storage

Ran parted and set the new size to 15TB

david@FREYJA:~$ sudo parted
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  103GB  103GB   primary   ext4            boot
 2      103GB   120GB  17.1GB  extended
 5      103GB   120GB  17.1GB  logical   linux-swap(v1)

(parted) select /dev/sdb
Using /dev/sdb
(parted) print
Model: HPT DISK_6_0 (scsi)
Disk /dev/sdb: 15.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  12.0TB  12.0TB  ext4

(parted) resizepart 1
End?  [12.0TB]? 15TB
(parted) print
Model: HPT DISK_6_0 (scsi)
Disk /dev/sdb: 15.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  15.0TB  15.0TB  ext4

(parted) quit
Information: You may need to update /etc/fstab.

The first time I ran resize2fs on the partition it asked me to run "sudo e2fsck -f /dev/sdb1", so I did that first and fixed everything it found. Then I reran resize2fs. At some point the drive remounted, I'm unsure when, but the online resizing worked fine as you can see my information still exists on the partition.

david@FREYJA:~$ sudo resize2fs /dev/sdb1
resize2fs 1.42.13 (17-May-2015)
Filesystem at /dev/sdb1 is mounted on /Storage; on-line resizing required
old_desc_blocks = 699, new_desc_blocks = 874

The filesystem on /dev/sdb1 is now 3662109119 (4k) blocks long.

david@FREYJA:~$
david@FREYJA:~$ cd /Storage/
david@FREYJA:/Storage$ ls
Anime  Anime Movies  Brandy  Configurations  David  Documentaries  Educational TV  Kid Shows  Kid Stuff  lost+found  Manga  Movies  Music  Pictures  Plex  Plex Media Server  PlexPy  Racing  RIP  TV Shows  Uploads

I then restarted the processes that I previously had to stop.

david@FREYJA:/Storage$ sudo service plexmediaserver start
david@FREYJA:/Storage$ sudo service smbd start

---

