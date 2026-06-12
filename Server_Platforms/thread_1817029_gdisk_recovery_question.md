---
title: "gdisk recovery question"
date: 2011-08-02
forum: Server Platforms
---

### Post by kelargo on 2011-08-02
I have a hard drive with a corrupted partition table.

The drive is 2 TB. I *thought* I only had one partition in it.
I dont remember. In any event, there was a power interruption and the drive's partition table became corrupt.  

I'm trying to recover the table. appreciate any help / guidance .. 
not sure how to specify the correct boundaries..


Initially showed these four problems:

```

Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 3907027055 sectors, needs to be 3907029167 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: partition 3 is too big for the disk.

Caution: Partition 2 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Identified 4 problems!

```


```
Expert command (? for help): p
Disk /dev/sde: 3907027055 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): D1D89D5B-DDAD-4586-A799-52E7C4DD78D4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907027021
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            4096      3884769279   1.8 TiB     0700  
   2              34            4095   2.0 MiB     0700  
   3      3884769280      3907028991   10.6 GiB    8200  


```

```
Expert command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: partition 3 is too big for the disk.

Warning! Secondary partition table overlaps the last partition by
1970 blocks!
You will need to delete this partition or resize it in another utility.

Caution: Partition 2 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Identified 3 problems!


```

---

### Post by kelargo on 2011-08-02
This is a stand alone disk.. not part of a RAID array.. and I think I had ext4 on it.

---

