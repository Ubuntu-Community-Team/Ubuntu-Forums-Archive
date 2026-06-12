---
title: "&quot;The backup GPT table is corrupt, but the primary appears OK, so that will be used.&quot;"
date: 2017-05-15
forum: Server Platforms
---

### Post by gian on 2017-05-15
Hello All,

I am building a new server for storage.

Some say it is better to keep the system partition out of RAID, so I installed Ubuntu Server 16.04 LTS on one 250GB disk, planning to manually dd the disk on a second one.
The storage is delivered with 2x 4TB non-bootable disks in RAID1.

The setup is almost finished, and the array is currently syncing.
However, if I do "fdisk -l" I get a warning message:


Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000cf850

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048  48828415  48826368 23.3G 83 Linux
/dev/sda2       48828416  60547071  11718656  5.6G 82 Linux swap / Solaris
/dev/sda3       60547072 488396799 427849728  204G 83 Linux


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00067a33

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sdb1           2048  48828415  48826368 23.3G 83 Linux
/dev/sdb2       48828416  60547071  11718656  5.6G 83 Linux
/dev/sdb3       60547072 488396799 427849728  204G 83 Linux


[COLOR="#FF0000"]The primary GPT table is corrupt, but the backup appears OK, so that will be used.[/COLOR]
Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4569A918-8C49-4687-A5B7-60D7F4CD0660

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux RAID


[COLOR="#FF0000"]The primary GPT table is corrupt, but the backup appears OK, so that will be used.[/COLOR]
Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 11D415C1-A848-4621-B5D3-1F22DBC1BD55

Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 7814035455 7814033408  3.7T Linux RAID


Disk /dev/md0: 3.7 TiB, 4000652787712 bytes, 7813774976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Should I worry?
At the moment I have no data on the server, so I am in time to make necessary corrections.

Thanks for your time and advice,

-Gian

---

### Post by TheFu on 2017-05-15
I would recreate the partition table. If that doesn't fix it, then there's an issue with the disk and more detailed analysis would be warranted.  I wouldn't bring a new disk into use with this issue.  It won't get better and can get worse.

---

### Post by gian on 2017-05-15
this would imply deleting the array, or just formatting md0?

---

### Post by TheFu on 2017-05-15
The array has nothing to do with the issue. Create a new GPT partition table. That happens **before** partitioning and before creating an array.

---

### Post by gian on 2017-05-15
sorry, I wasn't able to express myself clearly... that's what I wanted to say... if I should go backwards, deleting the array first, and deleting the partition before I create the new GPT table.

---

### Post by darkod on 2017-05-15
You won't be able to modify partitions correctly while they are part of an array. First stop the array:
```
sudo umount /dev/md0
sudo mdadm --stop /dev/md0
```

After that delete the partition tables and create new gpt tables, preferably using parted. I don't know if fdisk supports gpt correctly these days, earlier it wasn't. Use which ever tool you prefer, just make sure you have created the partitions correctly and there are no errors reported.

Only after that create new array and adjust mdadm.conf if needed.

---

### Post by gian on 2017-05-16
ok, thanks Darkod,

all clear, mark as solved...

---

### Post by gian on 2017-05-16
sorry, I was too fast.. as soon as I recreate the array, the error comes back.

This is what I did...

sudo umount /dev/md0
sudo mdadm --stop /dev/md0
parted /dev/sdc
    (parted) mklabel gpt
    (parted) unit TB
    (parted) mkpart primary 0.00TB 4.00TB
    (parted) quit 
parted /dev/sdd
    (parted) mklabel gpt
    (parted) unit TB
    (parted) mkpart primary 0.00TB 4.00TB
    (parted) quit 

At this point fdisk -l shows no errors:

gian@scala-17:~$ sudo fdisk -l                              
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000cf850

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048  48828415  48826368 23.3G 83 Linux
/dev/sda2       48828416  60547071  11718656  5.6G 82 Linux swap / Solaris
/dev/sda3       60547072 488396799 427849728  204G 83 Linux


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00067a33

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sdb1           2048  48828415  48826368 23.3G 83 Linux
/dev/sdb2       48828416  60547071  11718656  5.6G 83 Linux
/dev/sdb3       60547072 488396799 427849728  204G 83 Linux


Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0668928C-F92E-4444-83CC-A4A356DCBA86

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux filesystem


Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0D770C12-36AB-4670-BA08-EB2BF4558675




sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdc /dev/sdd
sudo mkfs.ext4 -F /dev/md0

Now, the error is back:

gian@scala-17:~$ sudo fdisk -l
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000cf850

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048  48828415  48826368 23.3G 83 Linux
/dev/sda2       48828416  60547071  11718656  5.6G 82 Linux swap / Solaris
/dev/sda3       60547072 488396799 427849728  204G 83 Linux


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00067a33

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sdb1           2048  48828415  48826368 23.3G 83 Linux
/dev/sdb2       48828416  60547071  11718656  5.6G 83 Linux
/dev/sdb3       60547072 488396799 427849728  204G 83 Linux


[COLOR="#FF0000"]The primary GPT table is corrupt, but the backup appears OK, so that will be used.[/COLOR]
Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0668928C-F92E-4444-83CC-A4A356DCBA86

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux filesystem


[COLOR="#FF0000"]The primary GPT table is corrupt, but the backup appears OK, so that will be used.[/COLOR]
Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0D770C12-36AB-4670-BA08-EB2BF4558675

Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 7814035455 7814033

---

### Post by TheFu on 2017-05-16
Please use **code tags** so things line up. Hard to read.

/dev/sdc /dev/sdd in the mdadm create is wrong! You need to use the partitions, not the whole disk.

---

### Post by darkod on 2017-05-16
Correct, like TheFu says, after you create the partitions the array members are the partitions, not the whole disks. So you need to use sdc1 and sdd1. I think using the whole disks is messing up things...

---

### Post by gian on 2017-05-16
that's it! thanks.

sorry about the code tags, I wasn't aware.

---

