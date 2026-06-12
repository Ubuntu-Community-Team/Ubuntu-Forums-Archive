---
title: "Trying to repair Win 10 boot error, getting boot-repair issues"
date: 2019-07-01
forum: Windows
---

### Post by ambograeme3257 on 2019-07-01
Hi, Although pretty new to ubuntu, I have used it in the past to recover a broken Win 10 PC.
I'm having trouble again and have spent most of the day trying different things without success.

I have got to the point of trying boot-repair but it doesn't give me the option of "recommended repair", instead I only get "create bootinfo summary"

This is the result, which it asked me to write down and post for help, which is why I am here.

[http://paste.ubuntu.com/p/ybZDyTS2b2/](http://paste.ubuntu.com/p/ybZDyTS2b2/)

What other info is needed for someone to help me with my problem? When I try to boot all I get is the message "operating system not found", which I'm assuming is due to an mbr problem?

---

### Post by oldfred on 2019-07-01
Moved to Windows sub-forum since Windows issue.

You show no drive?'
Does UEFI/BIOS show drive? In list of hardware not boot menu. 
If not, then no operating system will show it.

Also Windows 8 or 10 defaults to fast start up which sets hibernation flag. Then NTFS partitions are not normally seen as they are hibernated, but drive still should show.

---

### Post by ambograeme3257 on 2019-07-01
"you show no drive" - is that what it says in the report which I linked to?
Do I need to mount the drive in ubuntu live for it to show?

---

### Post by yancek on 2019-07-01
> Do I need to mount the drive in ubuntu live for it to show? 		

You need to access the BIOS setup on the computer immediately on boot to see ifyour hard drive is recognized there.  If it is not then it is probably dead.  The boot repair software should try to mount the various partitions.  ntfs partitions left hibernated will not be mounted, did you leave windows hibernated when you ran boot repair.  That is the default.

---

### Post by ambograeme3257 on 2019-07-01
If I go into BIOS I get the following under the "main" tab - 

BIOS version
ME Version
Machine Name
Serial Number
UUID

System memory 8192MB
Hard Disk Drive 1000GB

System Date
System Time

---

### Post by ambograeme3257 on 2019-07-01
I have now tried - 

sudo fdisk -l

The result - 

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1905045504 bytes, 3720792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.8 GiB, 4051697664 bytes, 7913472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *       56 7913471 7913416  3.8G  b W95 FAT32


ubuntu@ubuntu:~$

---

### Post by oldfred on 2019-07-01
Hard Disk Drive 1000GB
Looks like UEFI/BIOS sees a drive, but your fdisk does not show  a 1TB drive, just flash drive.

You may need to use Windows tools to make repairs. Boot-Repair is primarily for Linux, and can only do some minor fixes to Windows. For chkdsk or defrag and many other Windows issues, you must use your Windows repair flash drive or installer with repair console.

---

### Post by ambograeme3257 on 2019-07-01
Thanks oldfred, that will be the plan for tomorrow.

Am I right in thinking there is no way of recovering data from the HDD using ubuntu live?

Specifically, my good lady is desperate to get her stored logins from Firefox on the HDD.

I guess if there are only windows methods I could be screwed?? 

My knowledge is minimal, but is there any way of creating a mirror of the affected HDD (say on standalone HDD) and access it on a laptop via USB??

---

### Post by oldfred on 2019-07-01
Only if some way to mount drive.

Then various tools to repair disk, but often Windows tools work better on Windows NTFS partitions.

You can see if Disks & upper right corner icon & Smart Status shows drive. And if so if "good" or "bad". It can run many tests, but all I know is passed or not.

Also if drive seen, then testdisk may show partitions or deeper search show files. Or photorec to scan driver for files, but only by type/extension. Some have posted that Windows scan tools do work better on NTFS, but many tools are not free.

---

