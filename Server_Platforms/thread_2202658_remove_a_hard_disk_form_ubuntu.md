---
title: "remove a hard disk form ubuntu??"
date: 2014-01-30
forum: Server Platforms
---

### Post by mohammad alsharqi on 2014-01-30
hello
i'd like to remove a hard disk from my ubuntu server 

this is my fdisk -l
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes78 heads, 63 sectors/track, 397542 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e825583


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953525167   976761560   8e  Linux LVM


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000554ef


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773167   488385560   8e  Linux LVM


Disk /dev/mapper/ALSHARQI-root: 3496.2 GB, 3496191459328 bytes
255 heads, 63 sectors/track, 425054 cylinders, total 6828498944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ALSHARQI-root doesn't contain a valid partition table


Disk /dev/mapper/ALSHARQI-swap_1: 4253 MB, 4253024256 bytes
255 heads, 63 sectors/track, 517 cylinders, total 8306688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ALSHARQI-swap_1 doesn't contain a valid partition table



```

i'd like to remove /dev/sdb one

---

### Post by AmbiguousOutlier on 2014-01-30
I assume Ubuntu is installed on sda?

Edit your /etc/fstab to stop it from mounting, put # in front of the line, in case you decide you want to put it back. Then you can physically take the drive out. Have you shared the drive? You may want to comment out the respective lines in those configs.

---

### Post by oldfred on 2014-01-30
I do not know LVM, but they say if any drive fails you lose all data. So if breaking an LVM be sure to backup all data first.

       Advantages/Disadvantages LVM Post #9 notice disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by mohammad alsharqi on 2014-01-31
> **RhysGM said:**
> I assume Ubuntu is installed on sda?

Edit your /etc/fstab to stop it from mounting, put # in front of the line, in case you decide you want to put it back. Then you can physically take the drive out. Have you shared the drive? You may want to comment out the respective lines in those configs.

this is my /etc/fstab

```
# /etc/fstab: static file system information.#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ALSHARQI-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=73893e8f-9e93-44db-8731-4a6e2e865e8f /boot           ext2    defaults     $
/dev/mapper/ALSHARQI-swap_1 none            swap    sw              0       0



```

---

### Post by mohammad alsharqi on 2014-01-31
> **oldfred said:**
> I do not know LVM, but they say if any drive fails you lose all data. So if breaking an LVM be sure to backup all data first.

       Advantages/Disadvantages LVM Post #9 notice disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

thanks for replay 
i hope it does not

---

### Post by AmbiguousOutlier on 2014-02-01
I'm still learning about LVM, but the first thing I'd look at is pvdisplay and lvdisplay to understand how the LVM has been built.

---

### Post by mohammad alsharqi on 2014-02-01
ok .... 
i'd like to remove physical volume {pvremove -ff /dev/sdb1}
but the i got this problem
  Can't open /dev/sdb1 exclusively - not removing. Mounted filesystem?

---

### Post by prasys on 2014-02-09
Well it seems that your /dev/mapper/ALSHARQI-root is spanned across 3 Hard Disks , that is your sda,sdb,sdc 

First you need to resize your root partition , to do that use resize2fs 

```
 resize2fs /dev/mapper/blah 180G 
```
Replace 180GB with the size you want and it must be 90% of the size you want final volume to be i.e 200GB 

Then you gotta resize the volume with 
```
lvreduce -L 200G /dev/mapper/blah 
```

These are your steps/guidelines

---

