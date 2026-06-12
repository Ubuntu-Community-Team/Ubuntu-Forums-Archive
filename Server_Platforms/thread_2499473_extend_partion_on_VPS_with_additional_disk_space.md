---
title: "extend partion on VPS with additional disk space"
date: 2024-07-29
forum: Server Platforms
---

### Post by lister171254 on 2024-07-29
I'm no sysadmin and would appreciate help with the following.

I'm using a VPS and have recently added additional disk space.

Initially the partitions were as follows
```
umber  Start   End     Size    Type      File system     Flags
 1      1049kB  60.0GB  60.0GB  primary   ext4            boot
 5      60.0GB  70.0GB  9999MB  logical   linux-swap(v1)
 6      70.0GB  859GB   789GB   logical   ext4
```

This now looks like this
```
Disk /dev/sda: 1.56 TiB, 1717986918400 bytes, 3355443200 sectors
Disk model: QEMU HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0ae7b40d

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048  117186559  117184512  55.9G 83 Linux
/dev/sda2       117188606 1677719551 1560530946 744.1G  5 Extended
/dev/sda5       117188608  136718335   19529728   9.3G 82 Linux swap / Solaris
/dev/sda6       136720384 1677719551 1540999168 734.8G 83 Linux
```

I'm not sure why the additional space ended up on /dev/sda2 and not after /dev/sda6

My question is how I can use the additional space using the command line (no GUI)

---

### Post by TheFu on 2024-07-29
> **lister171254 said:**
> 
```
Disklabel type: dos
Disk identifier: 0x0ae7b40d

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048  117186559  117184512  55.9G 83 Linux
/dev/sda2       117188606 1677719551 1560530946 744.1G  5 Extended
/dev/sda5       117188608  136718335   19529728   9.3G 82 Linux swap / Solaris
/dev/sda6       136720384 1677719551 1540999168 734.8G 83 Linux
```

I'm not sure why the additional space ended up on /dev/sda2 and not after /dev/sda6

My question is how I can use the additional space using the command line (no GUI)

You have an MBR partition table.  That method allows only 4 primary partitions. It has been around since 1980.  "Extended Partition", which there can only be 1, is a type of primary partition created to hold "Logical Partitions" - and only logical partitions.  There can be 100+ logical partitions, but they must fit completely inside the 1, single, Extended partition.
All primary partitions are numbered 1-4.  Logical partitions start with number 5 and increase.  The numbers are chosen purely by the order that partitions are created, not their locations on "disk".  So it is possible for the end of the disk to have a partition sda22, if all prior logical partitions 5-21 have been created. Of course, you can delete partitions, leaving those numbers gone and out of order on disk too.

Do you want to hear the part that sucks?  You cannot change the extended partition while there are any logical partitions inside it.
Those are the rules. So, you'll need to backup sda5 and sda6, delete both of those, resize sda2, then recreate sda5 and sda6 again, in the sizes you want.  If that seems like a long way to go, it is.  The fun of MBR partition tables.  You can read more about them on wikipedia.  [https://en.wikipedia.org/wiki/DOS_partition_table#Disk_partitioning](https://en.wikipedia.org/wiki/DOS_partition_table#Disk_partitioning)

I'm not exactly certain when, but a replacement standard partition table showed up for use in Linux sometime in the 2005-2010 timeframe.  The GUID Partition Table, aka GPT.  This method of partitioning doesn't have the 4 primary partition table limitation. It allows 128 partitions on a disk, so there isn't any need for "Extended partitions" or "Logical Partitions" either.  Additionally, while MBR had 2 copies of the partition table for safety/redundancy, both copies were at the beginning of the disk, side by side and prone to having both lost if the 2 disk blocks were failing or corrupted.  With GPT, there are 2 copies - 1 at the beginning of the disk and the other at the opposite end. This physical separation greatly increases safety, since data blocks on a storage device near each other are more likely to have the same issue, than data blocks on opposite sides of the disk will.  All new partition tools were created to handle GPT and eventually, even fdisk was updated to support it (though that took about 5 yrs too long).  Tools like parted, gparted, fdisk, gdisk are all capable of doing GPT partitioning.
Read more about GPT [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

In theory, there is a method to convert from MBR to GPT.  I've never accomplished that with an installed OS.  I've never tried. Seems like there would be some important boot changes that would need to be addressed by the tools.  It would make sense to test it using purely data disks, since those only have a few, simple, dependencies, like how they are mounted using the /etc/fstab.

For many people, the easiest answer would be to backup your data and settings, then do a fresh install of the OS into the storage at your VPS, then restore the data and settings from those backups after the OS is installed, using the new space.  While you are at it, you might want to ensure that GPT is used, not MBR during the installation. You didn't say which OS was being installed.  At some point, MBR wasn't the default, so it is likely you have an older OS installed and probably need to use a newer OS anyway to keep support.  For about 10 yrs, MBR was the default in Ubuntu Server installs.  I remember crying with joy when the Canonical installer finally, years later than it should have taken, used GPT by default.  Prior to that, I was manually setting up the partitions BEFORE doing an install by booting from the installation ISO, then stopping the install, switching to a different tty, installing ssh, and pulling a manually created, custom, partitioning and disk layout script over, then running that to setup the storage how I wanted it.  It looks much like this: [Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144) though I don't dual boot and we all have different preferences for partitioning, logical volumes and file systems.

For example, I'd never have swap larger than 4.1GB.  Anything more is usually a waste, but there are exceptions, of course.  For a server, I strive to only need less than 500MB of swap, since RAM is cheap and easily resized for virtual machines to meet the workload requirements.  Due to the way the Linux kernel is setup, some performance enhancements only get turned on if there is "some" swap, so that's my goal on servers. Have a minimal amount of swap that is never actually used.  On a desktop, swap is there so users can "feel" the system getting slower as RAM is exhausted.  This is a hint to close huge programs so the OS doesn't crash.  Swap is like morphine.  You want the minimal amount to do the job, but not more and if you add too much, your system can die.  Ok ... perhaps too much swap isn't going to kill the system, but it certainly is a waste.  OSes that have to manage huge amounts of swap aren't managing processes as efficiently.

---

### Post by currentshaft on 2024-07-29
> **lister171254 said:**
> I'm no sysadmin and would appreciate help with the following.

I'm using a VPS and have recently added additional disk space.

Initially the partitions were as follows
```
umber  Start   End     Size    Type      File system     Flags
 1      1049kB  60.0GB  60.0GB  primary   ext4            boot
 5      60.0GB  70.0GB  9999MB  logical   linux-swap(v1)
 6      70.0GB  859GB   789GB   logical   ext4
```

This now looks like this
```
Disk /dev/sda: 1.56 TiB, 1717986918400 bytes, 3355443200 sectors
Disk model: QEMU HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0ae7b40d

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048  117186559  117184512  55.9G 83 Linux
/dev/sda2       117188606 1677719551 1560530946 744.1G  5 Extended
/dev/sda5       117188608  136718335   19529728   9.3G 82 Linux swap / Solaris
/dev/sda6       136720384 1677719551 1540999168 734.8G 83 Linux
```

I'm not sure why the additional space ended up on /dev/sda2 and not after /dev/sda6

My question is how I can use the additional space using the command line (no GUI)

Isn't it obvious?

sudo mount /dev/sda2 /mnt

---

### Post by TheFu on 2024-07-29
> **currentshaft said:**
> Isn't it obvious?

sudo mount /dev/sda2 /mnt

What!?   extended partitions don't have any file system.  Trying to mount a non-existent file system won't work.

---

### Post by lister171254 on 2024-07-29
Thanks for the quick and comprehensive reply.

I'll probably pay for an additional VPS and configure the new (Ubuntu) OS the way it should be and then move the various components (i.e. mail server, apache, etc) to the new VPS.
Thanks

---

### Post by TheFu on 2024-07-29
That's what I'd do, if it were on a VPS.   The time to transfer things over shouldn't be more than 1 hr and most of the VPS I rent cost pennies per hour to run.  Just don't forget to wipe the original system AND storage when you are done (and validate the new system works as desired) so they don't keep charging for storage.

Oh, and please use the "Thread Tools" button near the top to mark this thread as SOLVED to help others find it and so people wanting to help don't bother reading the entire thread to discover it is already handled.

---

### Post by currentshaft on 2024-07-30
> **TheFu said:**
> What!?   extended partitions don't have any file system.  Trying to mount a non-existent file system won't work.

I know. You run "mkfs.ext4" or whatever on it first.

---

