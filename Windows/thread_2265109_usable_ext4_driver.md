---
title: "usable ext4 driver?"
date: 2015-02-12
forum: Windows
---

### Post by hako1 on 2015-02-12
I am using a multi-boot system with Ubuntu 14.04 as my main system.
From time to time, I need to run Windows 8.1 or Windows XP for some special tasks.
My data are on 3 NTFS partitions, I did not experience issues accessing them from Linux or Windows.
Except - NTFS gets slower with the time, needs defragmentation, occasionally.

So, I was contemplating to use ext4 for my data.
For access from Windows there are drivers like Paragon ExtFS or Ext2Fsd.
I have, for test, tried Paragon ExtFS (v2.73) with Windows 8.1, but the experience was devastating: While reading went ok, writing corrupted the ext4 file system. With some fsck work most data could be recovered, but the capacity of the partition decreased each time.
Maybe the actual Paragon ExtFS (v2.395) is better; but before I try, maybe some of you have already tried?
There is also Ext2Fsd, is that driver better?

If someone has experience with such a setup, please share.

---

### Post by lukeiamyourfather on 2015-02-12
There are a few options. In my opinion using a third party file system in Windows is the worst possible option. Linux has decent NTFS support via NTFS-3G. If using a Linux native file system a virtual machine could be used in Windows to mount and then share the drive with Samba. So it would show up like a network share to Windows even though it's a local drive. Another option would be to setup a file server or NAS to store data so it doesn't matter what operating system is used to access the data.

---

### Post by hako1 on 2015-02-13
> **lukeiamyourfather said:**
>  ... using a third party file system in Windows is the worst possible option...   Looks like you are right. I will stick with NTFS, even with occasional defragmenting.

---

### Post by egorks on 2015-10-06
> **hako1 said:**
> Looks like you are right. I will stick with NTFS, even with occasional defragmenting.

been using ext2fsd for years now (started with win7, latest 0.62 works well under win8.1)

never had a problem either with ext2 or ext3. have multiple partitions from 200G up to 3Tb. testing ext4 at the moment...

PS. wouldn't trust Paragon driver (or any of their software for that matter) in a million years. they never test their sw for bugs (completely destroyed data on one of partitions was enough for me)

---

