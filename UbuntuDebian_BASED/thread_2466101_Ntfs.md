---
title: "Ntfs"
date: 2021-08-19
forum: Ubuntu/Debian BASED
---

### Post by aramrahgozar on 2021-08-19
Hi
I have 3 disks in my system and all of them formatted NTFS. I want to install Neon KDE beside my windows in Disk number 1. Also I'm a data holder. Now I want to use linux but download my files on Disk number 2. (NTFS formatted)
Is it safe to write on NTFS partition in linux as much as windows? (Data corruption)
Should I install NTFS-3g or native driver is good?
Should I disable hibernate and fast boot in windows and Neon KDE?

---

### Post by coffeecat on 2021-08-19
*Thread moved to **Ubuntu/Debian Based** sub-forum.*

---

### Post by guiverc on 2021-08-19
If you are using NTFS partitions for any OS and sharing the disk, all hibernation should be avoided (which includes windows fastboot).

I don't know KDE Neon well (it's build on an older Ubuntu LTS base (eg. 20.04 uses Qt 5.12.8 LTS, KF 5 5.68 etc), but with many of the toolkits & libraries changed from  the LTS versions to short-lived so a later KDE can be used; so it's neither a Ubuntu LTS product nor Ubuntu *stable* either, but bits of both), but it's still a GNU/Linux.

I've installed GNU/Linux before on systems using NTFS partitioning; and the system running as a form of persistent *live* with the save file being saved on the NTFS partition (I was allowed & expected to store files there). I had to do it as I didn't then own the hardware (and did **not**want to use windows), and I'd not recommend it. I'd recommend a full install on a POSIX *native* file-system so all meta data is valid & you'll have less problems and greater flexibility (*no upgrades issues etc*).

Sharing data - yep you can.   Two rules
- don't hibernate
- don't use windows 10 fast boot (*it doesn't leave a clean file system on the disk, as an unclean file-system with some details in the fastboot file is faster to boot from; just dangerous if another OS is used*)

In truth I've **many** times hibernated on one, booted into the other (GNU/Linux; Ubuntu, Debian etc) and then written files on the NTFS without issues... but I **always** consider what I was doing in windows at the time, and where on the *file-system* I'll be writing to and make an educated guess that it's safe before hand (*what are the chances that part of the disk may have been cached by windows etc*); and should my calculation be wrong, how messed up will the *file-system* be?  if I've any doubt I just don't hibernate & reboot.  How knowledgeable are you on OS *theory* & file-systems, that will dictate if you can do this calculation; but be cautious & always have good backups of anything you value.  (*Note:  with hibernating here, I'm not talking about windows 10 fastboot*). 

I'd suggest installing your GNU/Linux (*KDE Neon or whatever you like*) on its own partition, using at least the minimum disk size suggested (*I have no idea; Ubuntu Desktop says 25GB but you need to adjust with how you'll use it; my use needs a little more, most can get by on less*) and yes you can share data, but I'd recommend avoiding hibernate and **NOT** use windows 10 fastboot.

---

### Post by TheFu on 2021-08-19
ntfs and ntfs-3g packages/drivers are synonyms. They are the same.

Because NTFS is a foreign, reverse engineered, file system, it will never be as safe as using a native file system.  When/if corruption happens, you'll need to hope that Windows can resolve that.

I have 1 NTFS partition on 1 disk, only because a hardware device that writes to disk supports only NTFS or FAT32 and no other file systems.  About once every 30-60 days, I find that disk is corrupted and needs to be reformatted as NTFS.  I don't think it is Linux causing it, but I cannot say that with 100% assurance.  

Lots of people use NTFS for data to be shared between Linux and Windows. I haven't noticed too many complaints here about that, but honestly that isn't in my skill set so I don't watch these forums for those issues.  Search the forums, see who had corruption with NTFS. Did they solve it or did they lose data?

BTW, I would say the same about many native Linux file systems too.

Backups are always a good idea for anything you don't want to lose, regardless of the OS or the file system.

---

### Post by aramrahgozar on 2021-08-20
> **TheFu said:**
> ntfs and ntfs-3g packages/drivers are synonyms. They are the same.

I have 1 NTFS partition on 1 disk, only because a hardware device that writes to disk supports only NTFS or FAT32 and no other file systems.  About once every 30-60 days, I find that disk is corrupted and needs to be reformatted as NTFS.  I don't think it is Linux causing it, but I cannot say that with 100% assurance.  

Lots of people use NTFS for data to be shared between Linux and Windows. I haven't noticed too many complaints here about that, but honestly that isn't in my skill set so I don't watch these forums for those issues.  Search the forums, see who had corruption with NTFS. Did they solve it or did they lose data?

Backups are always a good idea for anything you don't want to lose, regardless of the OS or the file system.

I appreciate your help
Problem is I can't check all downloaded files for not being corrupted. Also It isn't possible to backup 50TB data. I need them written correctly.
I notice a few corrupt file topics but most of the related to hibernate.

---

### Post by aramrahgozar on 2021-08-20
> **guiverc said:**
> 

I've installed GNU/Linux before on systems using NTFS partitioning; and the system running as a form of persistent *live* with the save file being saved on the NTFS partition (I was allowed & expected to store files there). I had to do it as I didn't then own the hardware (and did **not**want to use windows), and I'd not recommend it. I'd recommend a full install on a POSIX *native* file-system so all meta data is valid & you'll have less problems and greater flexibility (*no upgrades issues etc*).


I'd suggest installing your GNU/Linux (*KDE Neon or whatever you like*) on its own partition, using at least the minimum disk size suggested (*I have no idea; Ubuntu Desktop says 25GB but you need to adjust with how you'll use it; my use needs a little more, most can get by on less*) and yes you can share data, but I'd recommend avoiding hibernate and **NOT** use windows 10 fastboot.


I want to use linux as main OS, But I don't want change my disks format because if I counter problems I've more skill in windows than linux to repaire disks. POSIX isn't what I need.

---

### Post by TheFu on 2021-08-20
> **aramrahgozar said:**
> I appreciate your help
Problem is I can't check all downloaded files for not being corrupted. Also It isn't possible to backup 50TB data. I need them written correctly.
I notice a few corrupt file topics but most of the related to hibernate.

If you can't backup the data, then it really isn't important.

The only file system that will actually validate the files written actually arrive on the disk is ZFS and only if ECC RAM is used.  No ext4, not xfs, and certainly NOT NTFS.

Update: 
From [https://en.wikipedia.org/wiki/Zfs#Features](https://en.wikipedia.org/wiki/Zfs#Features)
> ZFS always stores checksums separately from the data they verify, improving reliability and the ability of scrub to repair the volume. ZFS also stores multiple copies of data&#8212;metadata, in particular, may have upwards of 4 or 6 copies (multiple copies per disk and multiple disk mirrors per volume), greatly improving the ability of scrub to detect and repair extensive damage to the volume, compared to fsck.
scrub checks everything, including metadata and the data. The effect can be observed by comparing fsck to scrub times&#8212;sometimes a fsck on a large RAID completes in a few minutes, which means only the metadata was checked. Traversing all metadata and data on a large RAID takes many hours, which is exactly what scrub does.

To get anything like ZFS data integrity provided, we have to use something like RAID5 + par2 files.  Most of the time, the trivial error correction built into modern HDDs will catch issues, but not always and not after years of not being exercised.  Something like **badblocks** can be used to toggle bytes, then restore the data previously there, which will certainly exercise the hardware fully.  This is not automatic and running badblocks with the wrong options can easily wipe all data.

---

### Post by hk42 on 2021-08-20
A trick to mainly use NTFS partitions is to make backups of the Linux file system as archives.
Thus you preserve ownership and attributes.
Making and restoring archives needs to keep free-space on the Linux partition.

---

### Post by DuckHook on 2021-08-20
> **TheFu said:**
> If you can't backup the data, then it really isn't important.

The only file system that will actually validate the files written actually arrive on the disk is ZFS and only if ECC RAM is used.  No ext4, not xfs, and certainly NOT NTFS.
+1 to TheFu's observations.

As to OP's comments:
> **aramrahgozar said:**
> …I can't check all downloaded files for not being corrupted. Also It isn't possible to backup 50TB data. I need them written correctly…
It is not only possible to backup 50 TB of data, but it is done all the time in the enterprise environment. My data is 5 TB: it is not only backed up, but mirrored. 5 TB is conceptually no different than 50 TB except by way of scale. Moreover, I assume that 50 TB is mostly media files that never change, in which case, a differential backup is not that taxing.

TheFu's comments are accurate: trying to ensure "data integrity" without backups is like trying to ensure household financial integrity without insurance. If you are unwilling to insure a piece of property, it cannot be that important. Likewise, if you are unwilling to back up a piece of data, it cannot be that important.

This should actually give you some clarity as to how to approach backups. In my case, I do not bother backing up my media files and rely on two separate mirrors to provide me with sufficient redundancy. On the other hand, I have differentiated my truly critical files and back those up religiously. They are only a small fraction of my total data and are not difficult to back up.
> **aramrahgozar said:**
> I want to use linux as main OS, But I don't want change my disks format because if I counter problems I've more skill in windows than linux to repaire disks. POSIX isn't what I need.
If you insist on using NTFS, then I would suggest that you stay with Windows. Running NTFS with Linux, especially given your aversion to backups, is just asking for trouble. Another analogy: you are basically insisting on driving a BMW using Ford parts. Linux is going far above and beyond its duty to accommodate Windows users by making NTFS accessible, but NTFS:
[LIST]
[*]remains an accommodation only, not a duty,
[*]is foreign to Linux and is therefore unreliable,
[/LIST]
Your insistence on marrying Linux with NTFS and additionally demanding high data integrity is simply not feasible. You can have only two of the three—not all of them:
[LIST=1]
[*]Linux + data integrity requires ext4 or ZFS
[*]Windows + NTFS is a unified OS with the tools needed to solve the inevitable breakages and can be considered reasonably reliable
[*]Linux + NTFS may be more versatile, but is half man–half horse and cannot be made reliable
[/LIST]
It's your choice to make, but don't ask for the impossible.

---

