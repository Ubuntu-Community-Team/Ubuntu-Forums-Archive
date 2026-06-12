---
title: "How do you remove a GPT disk label/partition?"
date: 2012-05-04
forum: Server Platforms
---

### Post by MakOwner on 2012-05-04
No matter what I do, I can't get rid of this error message that everything except parted displays when dealing with this disk:

```

# sfdisk -l /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


```

I have even tried dd if=/dev/zero of=/dev/sdb bs=1 and letting it write 50 MB of data.  I tried bs=4096 and it wrote GB's of data.

I have tried doing this and rebooting in between, and I still see this (error?) message.

---

### Post by darkod on 2012-05-04
That is actually not an error message, just a warning that those tools don't work with gpt disks (or don't work correctly which is worse).

If you want to create msdos table, simply do:
sudo parted /dev/sdX
mklabel msdos
quit

That's it.

If you want to keep using it as gpt, start investigating gpt partitioning tools, like gdisk, cgdisk, etc.

---

### Post by CharlesA on 2012-05-04
> **darkod said:**
> That is actually not an error message, just a warning that those tools don't work with gpt disks (or don't work correctly which is worse).

This. Depending on the size of the disk, you might have to stick with gpt because msdos partition tables do not support disks larger than 2TB.

---

### Post by MakOwner on 2012-05-04
> **CharlesA said:**
> This. Depending on the size of the disk, you might have to stick with gpt because msdos partition tables do not support disks larger than 2TB.

This disk is only 750GB 512b sector, so fdisk/sfdisk should work fine with it.

I had been putzing about with parted/sfdisk/fdisk to see which was friendliest at the command line.  parted apparently leaves things on the disk like this.

---

### Post by CharlesA on 2012-05-04
> **MakOwner said:**
> This disk is only 750GB 512b sector, so fdisk/sfdisk should work fine with it.

I had been putzing about with parted/sfdisk/fdisk to see which was friendliest at the command line.  parted apparently leaves things on the disk like this.
Just set the partition table to msdos using gparted or parted, or just leave it as is.

Note: Changing the partition table type will wipe the anything that is on the drive.

---

### Post by oldfred on 2012-05-04
One of the advantages of gpt is that it keeps a backup partition table. Windows ignores the backup and some try to just overwrite the primary expecting it to work. But most Linux tools see the backup partition table and still think it is gpt or recognize there is an inconsistency.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by MakOwner on 2012-05-04
> **oldfred said:**
> One of the advantages of gpt is that it keeps a backup partition table. Windows ignores the backup and some try to just overwrite the primary expecting it to work. But most Linux tools see the backup partition table and still think it is gpt or recognize there is an inconsistency.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

I don't really care if I use GPT on these disks are not, but not being able to completely clear this disk after touching it with parted with standard/shipped tools ... just doesn't sit right.

Anyway, the reason I have GPT on the disk is that I was trying to speed up what I'm doing 

```

# parted -s -- /dev/sdb mklabel gpt
# parted -s -- /dev/sdb mkpart primary 2048s -0
# parted -s -- /dev/sdb set 1 raid on

(parted) print                                                            
Model: ATA ST3750641NS (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  750GB  750GB               primary  raid



# fdisk  -l /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1465149167   732574583+  ee  GPT

```

While parted reports the partition is raid, I'm looking for the partition to be fd, Linux auto raid.  Shouldn't it be when using it with mdadm?

Probably still work, just wasn't what I expected.

---

### Post by oldfred on 2012-05-04
gpt creates a protective MBR. That is so tools like fdisk see the protective MBR and report the entire drive (or first partition if you will) is gpt. The real partition table is the gpt table. Do not use fdisk with gpt.

You can download gdisk which is the fdisk for gpt drives.

---

