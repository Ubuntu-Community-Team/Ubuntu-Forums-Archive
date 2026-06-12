---
title: "Error mounting spare harddrive"
date: 2020-05-04
forum: Ubuntu/Debian BASED
---

### Post by revrobcox on 2020-05-04
I installed elementary OS 5 (ubuntu based) and accidentally did something to my storage HDD. Now it won't mount. 
error msg is: error mounting device /dev/sdc1 @ media/robjudy/ storage: mount(2) system call failed: structure needs cleaning.

The 'storage' drive is EXT4 (2TB) but with a tiny DOS section at one end. (not sure how that happened)
I have some important data on the drive, and would appreciate help accessing it please??

Here is what I assume you would need first???

Output of "sudo parted -l"
```
[sudo] password for robjudy:     
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32        boot
 2      539MB   500GB  500GB  extended
 5      539MB   500GB  500GB  logical   ext4




Model: ATA WDC WD20EFRX-68E (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4




Model: ATA SanDisk SDSSDA24 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  525MB  524MB  primary  ntfs         boot
 2      525MB   240GB  239GB  primary  ntfs
 3      240GB   240GB  492MB  primary  ntfs         diag
```

Output of "cat /etc/fstab"
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc5 during installation
UUID=35016ec8-7f57-4a00-8255-21012a7a989e /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
```

---

### Post by howefield on 2020-05-04
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by deadflowr on 2020-05-04
sdc1 is listed as the ntfs boot partition not ext4.
the ext4 partition is shown as sdb1.
based on the parted output.

---

