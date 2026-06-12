---
title: "Filesystem worries"
date: 2009-09-16
forum: Server Platforms
---

### Post by fela on 2009-09-16
I just recieved my new 1TB backup drive for the home NAS server. It came formatted as FAT32 LBA, I have files over 4GB so of course I reformatted it. Here's the problem: I stupidly formatted it as XFS, now I'm reading on various places that power cuts can kill data on XFS partitions and I really want this data to be rock solid as it's a backup drive (right now everything in the home folder on the server is backing up, so I can't test its reliability yet).

**Do you think XFS is reliable enough or do you think it's a must to reformat it and re-backup all the data all over again?**

Another question about filesystems: I'm soon gonna reinstall the OS on the server (Debian instead of Ubuntu). I'm thinking ext3 right now as the filesystem for / (don't want a separate boot partition). I would use XFS but grub has problems with it. Do you think there's anything better than ext3 that's reliable and reasonably fast **with lots of apps accessing it at once?** It has to be GRUB compatible.

Cheers

---

### Post by geek-n-out on 2009-09-16
I no guru, but I have worked with alot of linux (different flavors) guys and have recently migrated entirely to Ubuntu for my home network.  I will say that ext3 is fast, but has no undelete options like ext2 had.  I ran into that during testing of my file servers at work. SOOOOO my point is if you are running backups like you should then ext3 would be awesome... :)  :lolflag:

---

### Post by fela on 2009-09-16
> **geek-n-out said:**
> I no guru, but I have worked with alot of linux (different flavors) guys and have recently migrated entirely to Ubuntu for my home network.  I will say that ext3 is fast, but has no undelete options like ext2 had.  I ran into that during testing of my file servers at work. SOOOOO my point is if you are running backups like you should then ext3 would be awesome... :)  :lolflag:

Thanks. I think I'll run ext3 as the / partition when I reinstall the OS (after it's finished backing up the 200GB+ of data currently on it). Right now ext3 is the / partition and it seems to be running OK.

---

### Post by geek-n-out on 2009-09-16
in my opinion ext3 runs great.  I other than that one time of lost data (did it on purpose) i haven't had any problems.  Good luck man.

---

### Post by scorp123 on 2009-09-16
> **fela said:**
>  I stupidly formatted it as XFS, now I'm reading on various places that power cuts can kill data on XFS partitions  Yes, especially if the file was open at the time. Then it *could* happen that the next time you boot up again the file all of a sudden has a length of zero bytes ... Which basically means whatever was inside that file is hosed. Too bad if it was something important ...

XFS is great for large files and that's what it was originally created for on those Silicon Graphics/SGI rendering machines ... But I would not use it without additional UPS units. A power outage in the wrong moment and XFS might hose your files.

Right now I have settled on **Ext4** ... It's faster than Ext3 but handles large files with speeds that are comparable to XFS.

> **fela said:**
>  Do you think XFS is reliable enough I use it on the job on my Linux servers. But there I have emergency power and what not ... At home? Nope. I would use something else. 

> **fela said:**
>  Do you think there's anything better than ext3 that's reliable and reasonably fast **with lots of apps accessing it at once?** It has to be GRUB compatible.  Ext4 ... Ubuntu 9.04 with Ext4 on / and /boot is fast like hell when booting. But then again Ext3 is better tested and has the reputation of being extremely reliable. Depends on what's more important to you.

So far I am quite happy with Ext4.

---

### Post by fela on 2009-09-16
Well I've gone with XFS for the backup, oh well I'll have to see if my files get hosed. Hope they don't but it is a backup drive so it's gonna be off most of the time. I'll make certain to always cleanly unmount it before I shut it off and at this part of town we never get any power cuts so all should be well :)

I'll go with ext3 for the filesystem on the server.

---

### Post by Nick Rhodes on 2009-09-23
EXT4 suffers from the exact same issues from power cuts as XFS (infact it was worse until patched around April IRC).
The issue is that a combination of delayed allocation and data in the write cache (which very frequently is written out of order) is lost and leaves the file system in an inconstant state, the meta data does not acuratly reflect the data.
Using write barriers to helps to ensure meta data is written at the correct times and improves things drastically.

The issue with data files being nulled upto incomplete writes during reboot was fixed mid-2007 ([http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F](http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F)).

At the moment I would trust EXT4 marginally less than XFS and both far less than EXT3.

I am using EXT4 on my laptop, but have also had XFS on (I did make sure my HDD supported write barriers), both have survived OS freezes without problem due to bad default Xorg configurations.

Cheers, Nick

---

### Post by scorp123 on 2009-09-23
> **Nick Rhodes said:**
>  The issue with data files being nulled upto incomplete writes during reboot was fixed mid-2007 ([http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F](http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F)).
 It still happens. I just recently answered to a thread were someone was complaining about losing files on XFS ...

[http://ubuntuforums.org/showthread.php?t=1025412](http://ubuntuforums.org/showthread.php?t=1025412)

---

### Post by fela on 2009-09-23
Thanks for all the posts. I've since reformatted my 1TB backup drive as ext3, and the server's 500GB disk was already ext3. They're the only two disks that have mission-critical data on them.

Just out of interest, does anyone know of these sorts of bugs on the HFS+ filesystem, and NTFS aswell? I seem to notice alot more bug reports on open source filesystems - I guess it's because they're easier to debug :lol:

---

### Post by Nick Rhodes on 2009-09-24
> **scorp123 said:**
> It still happens. I just recently answered to a thread were someone was complaining about losing files on XFS ...

[http://ubuntuforums.org/showthread.php?t=1025412](http://ubuntuforums.org/showthread.php?t=1025412)

Interesting, I know LVM does not support write barriers (correctly) which is required for safer unclean shutdowns and the inability to disable the write cache sure does not help.

Cheers, Nick

---

