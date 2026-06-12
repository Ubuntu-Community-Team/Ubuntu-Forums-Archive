---
title: "hard drive error"
date: 2014-01-13
forum: Ubuntu Studio
---

### Post by anilkumar212005 on 2014-01-13
i had boot problem used boot-repair software to repair grub and boot problems unfortunately something went wrong and i am not able to read one partition of my external hard disk.

the file system of this partion was exfat and now gparted shows 


gparted:

filesystem: ntfs
size: 931.32gb

path:/dev/sdc2
status: not mounted

first sector: 1953905625
last sector: 3907024064
total sectors: 1953118440

warning:
ntfs_mst_post_read_fixup_warn: magic: 0x616e3e13  size: 1024   usa_ofs: 54791  usa_count: 65073: Invalid argument
Record 0 has no FILE magic (0x616e3e13)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdc2': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.

can anybody help me get through this, please.

---

### Post by tfrue on 2014-01-13
Would you try boot-repair again, but instead of doing the recommended fix create a boot-info and paste the url here.

Thanks!
Chris

---

### Post by anilkumar212005 on 2014-01-13
thank for your reply chris, i do not have problem booting now, the operating system is installed in internal hard drive, i did boot-repair using live pendrive to repair boot forgot to remove external harddrive while carrying this task, the problem is one partition of my external harddisk is missing it looks like it is formatted to ntfs. do you still recommend me to perform boot-repair.

---

### Post by jejeman on 2014-01-14
No, leave boot repair alone.

If the partition is NTFS use windows to fix it, as gparted recommended.
Do you have any important data on it?

---

### Post by tfrue on 2014-01-14
Don't forget to mark this thread as solved!

Have a great day!

Chris

---

### Post by anilkumar212005 on 2014-01-14
yes that is exactly why i am worried of, i had all my important documents in it and suddenly i see the exfat partition is turned to ntfs and i donot see any of my documents, any help to recover all of them is greatly appreciated

---

### Post by jejeman on 2014-01-14
Moderators should move this thread to more appropriate place for hard drive problems / data recovery.

---

