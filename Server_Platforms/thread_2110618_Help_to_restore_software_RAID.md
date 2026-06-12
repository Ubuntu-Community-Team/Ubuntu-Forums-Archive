---
title: "Help to restore software RAID"
date: 2013-01-30
forum: Server Platforms
---

### Post by selvinkuik on 2013-01-30
Hey guys


A drive on my server recently failed and had to be replaced. I now have 2 drives in my RAID - my old drive as sda and my new, blank drive as sdb.

```
The /proc/mdstat file currently contains the following:

Personalities : [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md125 : active (auto-read-only) raid1 sdb1[1]
      4194240 blocks [2/1] [_U]

md126 : active (auto-read-only) raid1 sdb2[1]
      524224 blocks [2/1] [_U]

md127 : active (auto-read-only) raid1 sdb3[1]
      151569024 blocks [2/1] [_U]

md2 : active raid1 sda3[0]
      153668544 blocks [2/1] [U_]

md1 : active raid1 sda2[0]
      524224 blocks [2/1] [U_]

md0 : active raid1 sda1[0]
      2096064 blocks [2/1] [U_]
```

I'm familiar, but not proficient, with removing and integrating using the mdadm command. And this setup is confusing me more as I only had md0, md1 and md2 before.

Not sure if this is enough information to get help - but how can I get my RAID back up and running?

---

### Post by darkod on 2013-01-30
Can you post also the output of:
```
sudo parted -l
```

What did you do exactly? You simply disconnected the old disk and connected a blank new one?

Did you first do the --fail and --remove before disconnecting the old disk?

---

### Post by selvinkuik on 2013-01-31
Below is the output of parted -l

```
Model: ATA SAMSUNG HD160JJ (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  2147MB  2146MB  primary  linux-swap(v1)  raid
 2      2147MB  2684MB  537MB   primary  ext3            raid
 3      2684MB  160GB   157GB   primary  ext4            raid


Model: ATA SAMSUNG HD160JJ (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  4296MB  4295MB  primary  linux-swap(v1)
 2      4297MB  4834MB  537MB   primary  ext3            raid
 3      4835MB  160GB   155GB   primary  ext4            raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 2146MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  2146MB  2146MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 537MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  537MB  537MB  ext3


Model: Linux Software RAID Array (md)
Disk /dev/md2: 157GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  157GB  157GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md127: 155GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  155GB  155GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md126: 537MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  537MB  537MB  ext3


Model: Linux Software RAID Array (md)
Disk /dev/md125: 4295MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4295MB  4295MB  linux-swap(v1)
```

It's actually a server in a data centre - so I'm not exactly sure what the technicians did there. But I'm pretty sure it it's safe to presume they would have used --fail and --remove.

---

### Post by darkod on 2013-01-31
Well, first as you can see the partitioning on sdb is not exactly the same. Close, but not the same.

Also, if sdb was earlier used in SW raid and still has superblock information, I'm not sure if this could affect the "creation" of these new md devices.

In your place, I would check mdadm.conf for ARRAY definitions, and if there are these new arrays in there, comment them out by adding # in front.

After that stop the arrays with:
sudo mdadm --stop mdXXX

Just in case, update the initramfs:
sudo update-initramfs -u

Open parted and write a new msdos table for sdb, then make new partitions comparing the values to sda. For example you can work with unit MiB. First print a list of sda and write it down (if it stays on screen you don't need to do this):
sudo parted /dev/sda unit MiB print

After that open sdb with parted, make new table, and create the three partitions with exact start and end MiB values as for sda:
sudo parted /dev/sdb
unit MiB
mklabel msdos
mkpart primary <start> <end> #(repeat this for all three partitions)
set 1 raid on #(repeat this for partitions 2 and 3 also)
quit

After that you should have identical partitions. Add the sdb1, sdb2 and sdb3 to the correct md devices with:
sudo mdadm --manage /dev/mdX --add /dev/sdbX

Wait for the arrays to resync, and that should be it. I'm not sure if you need to update the initramfs again.

---

