---
title: "USB Drive usage at the command line"
date: 2008-12-09
forum: Server Platforms
---

### Post by dpeters on 2008-12-09
How do I view and copy files from a USB drive and my home folder?
I have three books on linux and not one explains this simple operation. I already have plenty of information on mount points, device files, mounted devices, mounting, unmounting and changing permissions. Everything but what I'm looking for.

---

### Post by zwygart on 2008-12-09
Did you know the basic commands?
ls   : display the content of a directory
cd   : change directory
cd ..    : move up one directory
cd /     : goes at root directory
cp *source destination*     : copies files from source to destination
mkdir        : make directory

type help and you will see a list of commands
type help *command*  to have infos about the command

To access your drive, cd to your mount point  (usually /media/disk-1  or /mnt/disk-1)

ls /media    : you will see mounted media
ls /mnt      : they also may be there

cd /media/*name of dir*
ls          : You should see the content.

Are you sure you mounted correctly the drives?

---

### Post by dpeters on 2008-12-12
Problem solved.
Two problems surfaced.
Multiple partitions of a software RAID array gives a lengthy list of /dev/sda*, sdb* devices. Which were the two SATA hard drives. Inserting the thumb drive resulted in sdc and sdc1 in the list. I didn't catch the import of this being two partitions at first.
Secondly: After editing /etc/fstab and creating appropriate mount points in /mnt, I issued the mount -a and received file system errors. Then it dawned on me that I was using a U3 Thumbdrive (which has autoexecuting software in the first partition). This apparently is not recognized by the kernal nor the mount -a. (Though this does work on an Ubuntu Desktop system, 8.04)
Doing a manual mount of the second partition (sdc1)to the mount point (/mnt/usb1) and then "ls -l /mnt/usb1" yielded the list of files on the device.
Since these devices are commonplace I'm sure I am not alone.
Lesson learned: You can use the storage on these devices by just ignoring the 1st partition.

---

