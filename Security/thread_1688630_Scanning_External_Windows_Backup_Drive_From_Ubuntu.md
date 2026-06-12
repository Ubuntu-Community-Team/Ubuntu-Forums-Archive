---
title: "Scanning External Windows Backup Drive From Ubuntu"
date: 2011-02-15
forum: Security
---

### Post by steveone on 2011-02-15
Hey guys. This is my first post. I hope this the correct location. I've been struggling with the problem of scanning an external drive that is used to store the backup from a Windows 7 machine. The Windows 7 machine was infected but the user continued to backup to the external drive. He has since formatted his machine and reinstalled Windows 7, but now he would like restore whatever he can from the backup on the external drive. I've been attempting to scan the external drive for viruses using ClamTK by connecting it to my laptop running Ubuntu 10.04, but it has not worked. There is supposed to be about 10 gigs of backed up data, but I haven't seen any. I don't know why it is not mounted. If anyone can share their wisdom with me to resolve this problem it would be much appreciated. Thanks in advance.

---

### Post by gordintoronto on 2011-02-15
Please give us details of the external drive: brand and model.

Is it a USB drive? I always follow this sequence: connect the external drive to my PC, then turn its power on. It has always appeared as an icon on my desktop. I've used a few external drives.

---

### Post by booshire on 2011-02-15
lsusb will show you if it is connected. It should mount to /media by default on a desktop install. Also make sure it is working on another machine. If all else fails, sometimes you can pop the drive out and bypass USB all together.

---

### Post by steveone on 2011-02-16
> **gordintoronto said:**
> Please give us details of the external drive: brand and model.

Is it a USB drive? I always follow this sequence: connect the external drive to my PC, then turn its power on. It has always appeared as an icon on my desktop. I've used a few external drives.
Thank you for replying. I apologize for the lack of detail. The drive model is: WD My Book 1110.  It is connected via USB. The Smart Status is unsupported. Maybe that's the problem. Please let me know if this helps. I've tried shutting down and booting with the drive connected. Unfortunately, that did not make a difference. Thanks again.

---

### Post by steveone on 2011-02-16
> **booshire said:**
> lsusb will show you if it is connected. It should mount to /media by default on a desktop install. Also make sure it is working on another machine. If all else fails, sometimes you can pop the drive out and bypass USB all together.
Thank you for your reply. lsusb returns- Bus 001 Device 002: ID 1058:1110 Western Digital Technologies, Inc. In disk utility the Smart Status is unsupported. I've tried to scan the drive from my Macbook Pro as well with the same results. I just thought it was a short coming of the Mac.

---

### Post by steveone on 2011-02-16
Ok guys. I was able to resolve the problem. The problem was that Western Digital has a password lock feature on the drive. I had to connect the drive to a Windows machine, which I did using VMWare. Once it was connected I had to remove the security feature by entering the password for the lock and then remove the password protection. The drive was definitely infected. It started chewing up drive space like crazy but I managed to get that part of it done. Once the password protection was removed I connected the drive to my laptop running Ubuntu and it mounted right away. I am scanning the drive as I write this. Thanks again guys for your ideas. I hope this will help anyone else who may run across this issue.

---

