---
title: "Samba not using full hard drive space"
date: 2017-01-28
forum: Server Platforms
---

### Post by agentkibble on 2017-01-28
I currently have Ubuntu Server 16.04 with Samba installed. I have a brand new 4TB hard drive partitioned and formatted to fat32, mounted to /Share. On my windows 10 PC I mapped the share to Z: but it only says 1.63 TB free of 1.63 TB. I loaded up a Ubuntu VM and mounted the share and it's only showing 1.8 TB Free. How can I make Samba use the full size of the disk?

---

### Post by wildmanne39 on 2017-01-28
*Thread moved to **Server Platforms for better support**.*

---

### Post by darkod on 2017-01-28
1. Why is the disk formatted as fat32?

---

### Post by agentkibble on 2017-01-29
Because at the time when I was formatting I saw Fat32 and it said it would work with both Linux and windows, didn't realize at the time that that would stop me from using the entire disk. Formatted as NTFS and it's all good now, can access the full 4 TB.

---

### Post by darkod on 2017-01-29
When the disk is in a linux server you should use a linux filesystem, not fat32 or ntfs. The statement that ntfs is read by both linux and windows is usually for external disks that you move between different computers and you connect to both linux and windows computers.

Samba will take care to offer the shares to windows clients and using ext4 will also work and is recommended. The windows clients don't care about the filesystem, they see the samba shares.

In any case, if you want to keep ntfs and consider this closed please mark the thread solved. You can do that in Thread Tools above the first post.

---

