---
title: "Disk Partition and Disk Format Please Help"
date: 2008-07-11
forum: Windows
---

### Post by macnyak on 2008-07-11
TO ALL UBUNTU, KUBUNTU, LINUX USERS and WINDOWS USERS:


A pleasant day to all...


I just want to ask about disk partitioning...and disk FORMATS


Well, for my experienced with Windows XP (bootable CD) a hard drive can be partitioned then it needed to be formated before the OS is installed..

In Windows XP you just have to **Press** letter **C** to create a partition and **Press** letter **D** to delete a partition..

Then in the following setup you will be asked what FORMAT you will use FAT or NTFS, Quick or Normal..

I am told that NTFS is much better that FAT, is that true?

Here's my questions,.. Kindly answer it coz I'm not well inclined with Ubuntu yet. 


- How to partition a Hard Drive if I will use Ubuntu or Kubuntu Live CD?

- What disk FORMAT does Ubuntu or Kubuntu use? How to Format a disk?

- If I partition a Hard Drive with a Windows XP bootable CD and Formatted it with NTFS,.. Can I install Ubuntu or Kubuntu in it? (not a dual boot only single OS)

- If I already have a PC with Ubuntu or Kubuntu installed in it, then if I both a new Hard Drive and if that Hard Drive is NTFS formatted.. Will Ubuntu or Kubuntu OS detect my new Hard DRive? or Will I be able to open the hard drive and copy paste or explore its contents?

- Does Ubuntu or Kubuntu Hard Drives called Drive C:, Drive D:, Drive E:,  and so fort like in Windows?

- Is it possible to PARTITION a Hard Drive and have Different FORMATS in it? like NTFS and the FORMAT that Ubuntu uses (I'm sorry I don't know what Format Ubuntu uses)

- If I dual boot 1 XP and 1 Ubuntu,.. then I use different FORMATS,.. NTFS for XP and FOrmats the other for Ubuntu,.. If I boot my pc on XP mode will I be able to see the contents of the Other drive with Ubuntu (copy some files in it and paste it in my XP NTFS format hard drive) and vice versa,.. If I boot my PC on Ubuntu mode will I be able to check the contents of the other drive with NTFS format?

please help me with this,.. and i'm sorry if im not good in english 

Thanks a lot and GOD bless to everyone...

---

### Post by LaRoza on 2008-07-11
> **macnyak said:**
> 
Well, for my experienced with Windows XP (bootable CD) a hard drive can be partitioned then it needed to be formated before the OS is installed..

Yes, any storage media has to have a format to be used. An unformated disk is like a blank piece of paper (or ones with random marks and letters scattered about). A formatted disk is like paper with ordered letters that can be read.

> 
In Windows XP you just have to **Press** letter **C** to create a partition and **Press** letter **D** to delete a partition..
I don't know about that, there is a lot more to formatting and partitioning than that. Windows is so restrictive.

> 
I am told that NTFS is much better that FAT, is that true?
NTFS is a journalling file system and supports larger files and partitions than FAT32. FAT32 is only good for flash drives and such.

> 
- How to partition a Hard Drive if I will use Ubuntu or Kubuntu Live CD?

You have several options. One is that it will do it for you, one option will wipe the entire disk, and one will resize the Windows partition (you tell it how much) and automatically set up a dual boot.

> 
- What disk FORMAT does Ubuntu or Kubuntu use? How to Format a disk?
Use the default, EXT3. There are many formats it can use, and they are options for manually setting it up, but I don't think you have a reason to do that.

> 
- If I partition a Hard Drive with a Windows XP bootable CD and Formatted it with NTFS,.. Can I install Ubuntu or Kubuntu in it? (not a dual boot only single OS)
Yes, The Windows partition can be resized. Windows will use NTFS and Ubuntu will be using EXT3. 

> 
- If I already have a PC with Ubuntu or Kubuntu installed in it, then if I both a new Hard Drive and if that Hard Drive is NTFS formatted.. Will Ubuntu or Kubuntu OS detect my new Hard DRive? or Will I be able to open the hard drive and copy paste or explore its contents?
Yes, Ubuntu can read and write to NTFS without trouble.

> 
- Does Ubuntu or Kubuntu Hard Drives called Drive C:, Drive D:, Drive E:,  and so fort like in Windows?
No. Windows does that because DOS did that. DOS does that because a pre-MS-DOS OS called CP/M did. (C: is named after CP/M). In *nix systems, everything is a file. So the partitions will be mounted under a directory, by default the partitions label, but you can change that.

> 
- Is it possible to PARTITION a Hard Drive and have Different FORMATS in it? like NTFS and the FORMAT that Ubuntu uses (I'm sorry I don't know what Format Ubuntu uses)
Yes, you can more than one partition and they can be different formats.

> 
- If I dual boot 1 XP and 1 Ubuntu,.. then I use different FORMATS,.. NTFS for XP and FOrmats the other for Ubuntu,.. If I boot my pc on XP mode will I be able to see the contents of the Other drive with Ubuntu (copy some files in it and paste it in my XP NTFS format hard drive) and vice versa,.. If I boot my PC on Ubuntu mode will I be able to check the contents of the other drive with NTFS format?

Sort of. Windows by itself can't read EXT3, but you can get a driver for it, or you can do what I do and create a three new partitions. Shrink the Windows partition to a size where it is half full, create an EXT3 partition the same size, great a 512 MB partition (Swap) and then use the rest for storage. This may be a little complicated though for someone not used to doing it (it is easy in practice)

See for guides: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

