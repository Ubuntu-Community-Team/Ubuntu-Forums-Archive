---
title: "Failed to mount"
date: 2013-12-23
forum: Ubuntu Studio
---

### Post by Henry04 on 2013-12-23
Fresh install of Ubuntu Studio 13.10... mounted on a 2 TB external usb 3.0 drive, I also have a 3 TB usb 3.0 attached to my HP Pavillion 500-046, AMD64, that I do dual boot with Windows 8.1, with UEFI "bios," & hard drives use GPT formatting (hope I said that correctly). 

The *first external drive* is ext4 & linux-swap partitioned (which has my Ubuntu Studio OS in it), the *second external hd is partitioned into two:* one 1 TB, & the other is 2 TB (approx). When I added the second external hd, I originally had the first partition (1 TB) formated to NTFS, & the second (2 TB) to ext4, thinking that would be space for my linux OS... couldn't mount it, so I tried NTFS, & voila, it mounted, & was read/writable. 

NOW just the first aforementioned (1 TB) NTFS, will not mount... I get the following error message:


**"Failed to mount "canissound".**

Error mounting system-managed device /dev/sdc1: Commandline 'mount "/media/cannissound" exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 3).

Failed to mount 'dev/sdc1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/Fake hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/Fake then first activate it and mount a different device under the /dev/mapper/ directory. (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for details."

& this is my output of /etc/fstab:

"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdd6 :
UUID=ab0552f2-9065-40a5-bb4d-7c18137ef4f5       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sdc1 :
UUID=01CEFDE61ECB2BE0   /media/canissound       ntfs-3g defaults,locale=en_US.UTF-8     0       0
#Entry for /dev/sda4 :
UUID=A472BE6C72BE433A   /media/henry/Windows    ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8        0       0
#Entry for /dev/sdb1 :
UUID=534472A67410316A   /media/henry/littledog  ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8        0       0
#Entry for /dev/sdc5 :
UUID=123E17EB37BC763D   /media/henry/woof       ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8        0       0
#Entry for /dev/sdd5 :
UUID=255f33ac-b7d4-4ca9-85c5-1532265d8758       none    swap    sw      0       0 "

This is definitely NOT a Raid setup... & though I have not done the prescribed 'chkdsk /f' i'm suspecting a /etc/fstab error... I have discovered the Disk program that can change ones /etc/fstab settings... so I guess I'm wondering if any person out there in virtual Ubuntu land might have some suggestions to try, in these regards.

Thanks much,
Henry04

P.s., *I sure would like to also know what I can do (in these same regards) to get the** second partition formatted into ext4**, & mounted with read/write privileges! *

One other question, is, whom can I contact in Ubuntu/Linux to complain about the difficulty of mounting Linux formatted disks, versus NTFS (from Linux)? When I first started Linux, some years ago (it was on Ubuntu Heron when it first came out), I thought connecting with Windows was the difficult task. I do not think quite this way now... This is a real time waster as far as I'm concerned (assuming it is avoidable).

---

### Post by Henry04 on 2013-12-23
SOLVED.

That was easy... (in the end)... there was a problem with the disk partition... still would like to know (better) about getting Linux formatted disks (external to the OS disk) to be more compatible with Linux... Oh well, that's another topic I will try to pursue. (apologies if I wasted anyone's time reading the above).

Henry04

---

