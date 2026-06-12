---
title: "correct fstab for dual-boot with Windows 10 Pro 64"
date: 2015-09-14
forum: Windows
---

### Post by cigtoxdoc on 2015-09-14
Ubuntu OS is 15.10 beta.

Ubuntu stopped loading claiming problems mounting Windows drives (from journalctl -xb listing).  My fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda9 :
UUID=902272c0-5d86-4ed6-9d21-b2696a6e8df7	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=2e1281c7-3575-4729-9216-c859d8f29015	/media/MyChemistry	ext4	defaults	0	2
#Entry for /dev/sda6 :
UUID=d6a56646-c65c-4377-95e9-37931444a550	/media/MyDocuments	ext4	defaults	0	2
#Entry for /dev/sda2 :
UUID=1E980FF3980FC7EB	/media/OS	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=32b7ffe2-622f-4a86-a9d8-d64555f9529b	/media/Spare	ext4	defaults	0	2
#Entry for /dev/sda1 :
UUID=BE460C7C460C3823	/media/System_Reserved	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda3 :
UUID=4406F41006F40528	/media/sda3	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda8 :
UUID=01c96bca-7ede-44ca-84dc-5a41608c140f	none	swap	sw	0	0

Ubuntu is on /dev/sda9.  Windows "C:" is on /dev/sda2.

Where have I gone wrong?

Thank you,

John

---

### Post by yancek on 2015-09-14
What message and which partition in particular does it refer to?  Which version of windows are you using?  If it is 8.0 or newer, you need to shutdown and not do the default hibernate from windows.

---

### Post by cigtoxdoc on 2015-09-15
Thank you for your reply.  I have tried starting Ubuntu from a cold boot (i.e. PC is off) and same thing happens.  Only way to get Ubuntu to load is to use the following fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda9 :
UUID=902272c0-5d86-4ed6-9d21-b2696a6e8df7	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=2e1281c7-3575-4729-9216-c859d8f29015	/media/MyChemistry	ext4	defaults	0	2
#Entry for /dev/sda6 :
UUID=d6a56646-c65c-4377-95e9-37931444a550	/media/MyDocuments	ext4	defaults	0	3
#Entry for /dev/sda2 :
UUID=1E980FF3980FC7EB	/media/OS	ntfs-3g	ro,locale=en_US.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=32b7ffe2-622f-4a86-a9d8-d64555f9529b	/media/Spare	ext4	defaults	0	4
#Entry for /dev/sda1 :
UUID=BE460C7C460C3823	/media/System_Reserved	ntfs-3g	noauto,locale=en_US.UTF-8	0	0
#Entry for /dev/sda3 :
UUID=4406F41006F40528	/media/sda3	ntfs-3g	noauto,locale=en_US.UTF-8	0	0
#Entry for /dev/sda8 :
UUID=01c96bca-7ede-44ca-84dc-5a41608c140f	none	swap	sw	0	0

#Output of blkid
#/dev/sda1: LABEL="System Reserved" UUID="BE460C7C460C3823" TYPE="ntfs" PARTUUID="355ada93-01"
#/dev/sda2: LABEL="OS" UUID="1E980FF3980FC7EB" TYPE="ntfs" PARTUUID="355ada93-02"
#/dev/sda3: UUID="4406F41006F40528" TYPE="ntfs" PARTUUID="355ada93-03"
#/dev/sda5: LABEL="Spare" UUID="32b7ffe2-622f-4a86-a9d8-d64555f9529b" TYPE="ext4" PARTUUID="355ada93-05"
#/dev/sda6: LABEL="MyDocuments" UUID="d6a56646-c65c-4377-95e9-37931444a550" TYPE="ext4" PARTUUID="355ada93-06"
#/dev/sda7: LABEL="MyChemistry" UUID="2e1281c7-3575-4729-9216-c859d8f29015" TYPE="ext4" PARTUUID="355ada93-07"
#/dev/sda8: UUID="01c96bca-7ede-44ca-84dc-5a41608c140f" TYPE="swap" PARTUUID="355ada93-08"
#/dev/sda9: UUID="902272c0-5d86-4ed6-9d21-b2696a6e8df7" TYPE="ext4" PARTUUID="355ada93-09"

journalctl -xb keeps saying windows partitions are not clean.  Windows 10 says its disk partitions are clean.

If I knew how to get journalctl -xb to write to something I could access I would post the offending lines on this forum.

John

---

### Post by cigtoxdoc on 2015-09-15
The ntfs configuration tool gives the following error for /media/OS

Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by cigtoxdoc on 2015-09-15
The ntfs configuration tool gives the following error for /media/OS

Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by cigtoxdoc on 2015-09-15
More information:  Windows 10 (apparently like Win 8) has a Fast Start option.  This apparently is what is causing Ubuntu to see "unclean" partitions.  Getting rid of the the Fast Start option solved the problem and allowed /media/OS to mount with defaults instead of ro option.

So for dual-boot Ubuntu 15.10 and Windows 10, make sure you remove the Windows 10 Fast Start option.

John

---

### Post by physicist1616 on 2016-09-06
The thread title with the [SOLVED] tag is misleading because he was asking the wrong question, yet it still makes it to the top of my search results looking for ideal fstab options for Windows partitions.

I propose a mod or OP change the thread title to something more accurate to both the problem and solution, like "Issues mounting Windows partition."

The specific solution to that problem is to disable hibernation in Windows.  One way to do this is in an Administrator command prompt:
```
powercfg /h off
```

---

### Post by QIII on 2016-09-06
Rest in peace, thread.

---

