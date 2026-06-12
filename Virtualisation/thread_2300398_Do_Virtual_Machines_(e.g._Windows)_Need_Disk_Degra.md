---
title: "Do Virtual Machines (e.g. Windows) Need Disk Degragging?"
date: 2015-10-25
forum: Virtualisation
---

### Post by Ian_Scott on 2015-10-25
I use Windows VM on a number of Linux notebooks and have wondered if these need or benefit from the typical need to defragment NTFS drives on the host OS. The Linux host is usually Ext4 and this doesn't need fragmenting as far as I know but the Windows VM will use NTFS as a format. Does this need fragmenting or does the host Linux EXt4 format already take care of that?

Also I wonder why Microsoft doesn't use their ExFat format on any of Vista. windows 7, 8, 8.1 and certainly not even on the prematurely released and problematic w10 (as I found the hard way and ditched for Linux;)) Obviously a copy cat version responding to Linux' Ext3/4, but does Microsoft not trust their ExFat format sufficiently to make use of it as standard?

---

### Post by ian-weisser on 2015-10-26
No benefit to most users by defragging the host ext3/4.
Yes benefit to some user by defragging guest NTFS.
Ext3/4 filesystems fragment *differently* than NTFS. Fragmentation in ext3/4 becomes a significant issue only when disk usage is almost full.

---

### Post by afz12 on 2015-10-26
Thanks ian-weisser

You have misunderstood - these VM are windows and use NTFS not Ext4. The host is Ext4 but my question regards the guest. Does the windows VM guest using NTFS need defragging or does the host EXt4 that runs it cover this already?

---

### Post by CharlesA on 2015-10-26
Most newer versions of Windows defrag automagically.

---

### Post by afz12 on 2015-10-26
Thanks CharlesA. I thought my question was simple enough but seems to have caused confusion. Whether Windows 8 or 10 auto degrag is irrelevant. My question is, to repeat, does a virtual windows machine need to use de-fragmentation when it runs on a Linux host file system that does not - e.g. ext4? I prefer any answers that reply to this question as I am sure readers viewing this post must understand. Alternatively, perhaps my question has no answer?

---

### Post by CharlesA on 2015-10-26
Assuming you are using KVM to run the VMs, the "hard drive" Windows sees is just a huge file on the EXT partition. You could defrag that from the host but it shouldn't be needed.

Windows files on the virtual drive will fragment, but I don't think it will cause a big issue. Defrag it inside Windows if you want, but I don't think you will see much of a performance increase.

---

### Post by afz12 on 2015-10-27
Thanks CharlesA

I suspected this and have never seen any obvious disk speed improvement (using Virtualbox, different versions) but this would probably need a detailed measurement with a stopwatch! However I have found that windows bleachbit.exe and ccleaner.exe both provide a "wipe free space" and when I saved the resulting VM to USB disk, the file size is much smaller. In one example, a dynamic XP VM started at ~25 GB when saved but dropped down to ~8 GB after I ran the wiper and saved to disk again. Since then I had wondered about defrag and if the way a virtual disk is managed either aligns its structure with the host file system e.g. EXt4 or if it is detached and independent. Anyway, just an idle curiosity

---

### Post by CharlesA on 2015-10-27
In that case, you defrag the files to get everything into nice chunks and then zero the free space out to shrink the VHD. I don't think that works with anything except dynamically-sized drives, though. [https://blogs.oracle.com/virtualbox/entry/how_to_compact_your_virtual](https://blogs.oracle.com/virtualbox/entry/how_to_compact_your_virtual)

---

