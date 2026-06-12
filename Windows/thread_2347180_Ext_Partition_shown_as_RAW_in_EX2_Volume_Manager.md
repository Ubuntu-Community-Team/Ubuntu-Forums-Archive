---
title: "Ext Partition: shown as RAW in EX2 Volume Manager"
date: 2016-12-22
forum: Windows
---

### Post by arashk on 2016-12-22
Hi there,
By Minitool Partition Wizard, I created  one ext4 partition on a 55mb memory card. On the Minitool it does not have drive letter and cannot be assigned one.
On EX2 Volume Manager (Ext2Fsd-0.68) it is recognized as "RAW" (not as ext4). I tried ext2 and the same problem happened.

Do you have any idea why and how to solve it?

---

### Post by howefield on 2016-12-22
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2016-12-22
I've never use 'Minitool Partition Wizard' but I suppose it is windows software as your refer to 'drive letters'.  Windows default systems are incapable of recognizing/reading/writing to Linux filesystems and will not assign them a drive letter.  This is by design of microsoft.  If you go to Disk Management in windows, you will see something like 'healthy partition' at best and nothing more detailed about the partition.

---

### Post by arashk on 2016-12-22
> **yancek said:**
> I've never use 'Minitool Partition Wizard' but I suppose it is windows software as your refer to 'drive letters'.  Windows default systems are incapable of recognizing/reading/writing to Linux filesystems and will not assign them a drive letter.  This is by design of microsoft.  If you go to Disk Management in windows, you will see something like 'healthy partition' at best and nothing more detailed about the partition.

It is a Windows software.
Windows is incapable but it has been claimed that "Ext2Fsd" and "EX2 Volume Manager" enable Windows to recognize/read/write to Linux filesystems.
The problem posed in the first post is [COLOR=#ff0000]**not that Windows is incapable**[/COLOR], **but [COLOR=#33cc66]that why a partition ext4-formatted by Minitool is RAW in EX2 Volume Manager[/COLOR]**.

---

### Post by yancek on 2016-12-22
A "default" windows system is not capable of reading/writing a Linux filesystem as I indicated above.  If you have third party windows software to do this, then I think your best option is to contact the developers of EX2 Volume Manager as to why it doesn't perform as expected.  Good luck with it.

---

### Post by arashk on 2016-12-23
I solved the problem.

---

