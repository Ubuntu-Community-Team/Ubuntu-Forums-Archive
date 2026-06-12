---
title: "How does Linux affect XP files on a dual-boot system?"
date: 2006-05-28
forum: The Cafe
---

### Post by cnbiz850 on 2006-05-28
I don't know if this is a valid question.  I thought that Linux wouldn't affect Xp files.  But some problems with the XP makes me wonder.

Not long after I installed Ubuntu (Dapper) on the laptop with XP as dual-boot, it seems all files on the XP are read-only (When using the XP).  I even have problems running some programs as the datafiles are read-only.  It's XP Home edition.  I tried to logon to the single user mode of the XP to re-configure file permissions and ownership.  Seems it did something, but the fact that files are read-only didn't change afterwards.  Basically, I can't make the system perform normally.  I don't know if it was hit by some malware or not and I know that anything is possible on the XP.  But one  thing I start to wonder is whether Linux could have caused it.  Part of my fstab is as follows.  Can't anyone help explain anything about this problem?

$ more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0       1
/dev/hda2       /media/hda2     ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda5       /media/sda5     ext3    defaults        0       0
/dev/hda4       none            swap    sw              0       0

---

### Post by lucia_engel on 2006-05-28
This is quite normal and it's not a malware problem.

Linux only support reading NTFS partitions. Though there is an experimental program going on that tries to write to it, I don't recommend it. So, assuming you have XP installed with NTFS filesystem, you won't be able to write to it.
If you want to share files between linux and XP, use the FAT filesystem as this is the only reliable way.
There's also a Windows program called Ext2fs (?) that allows XP to read and write to the linux partition but it won't retain the permissions and ownership stuff, so stick with FAT.

---

### Post by cnbiz850 on 2006-05-28
[QUOTE=lucia_engel]This is quite normal and it's not a malware problem.

Linux only support reading NTFS partitions. Though there is an experimental program going on that tries to write to it, I don't recommend it. So, assuming you have XP installed with NTFS filesystem, you won't be able to write to it.
If you want to share files between linux and XP, use the FAT filesystem as this is the only reliable way.
There's also a Windows program called Ext2fs (?) that allows XP to read and write to the linux partition but it won't retain the permissions and ownership stuff, so stick with FAT.[/QUOTE]


Thanks for the response, but sorry it didn't address my problem.  When I said files read-only, I meant that on the XP they appear read-only.

---

### Post by lucia_engel on 2006-05-28
oh sorry about that, I should learn to read more carefully :p

That's a weird problem, don't know how to fix it.

---

### Post by skyshark88 on 2006-05-28
Not from ubuntu, it can't change the files to an ntfs filesystem or the properties........

---

### Post by cnbiz850 on 2006-05-28
[QUOTE=skyshark88]Not from ubuntu, it can't change the files to an ntfs filesystem or the properties........[/QUOTE]

Doesn't Ubuntu make them all read-only for itself and then in turn they become read-only under XP as well?    In the fstab, I need to set umask=0222 to NTFS partitions.  Doesn't that cause anything to XP?
What about on FAT?

---

### Post by blastus on 2006-05-28
[quote=cnbiz850]Doesn't Ubuntu make them all read-only for itself and then in turn they become read-only under XP as well?[/quote]

No. NTFS file permissions are not used in Linux. Linux mounts partitions using mount points. Mount points have permissions associated with them and they have nothing to do with the permissions of the directories/files in the file system. XP mounts partitions also, but the way it assigns mount points (C:, D: etc...) is pretty much hard coded and permissions are not associated with mount points.

> In the fstab, I need to set umask=0222 to NTFS partitions. Doesn't that cause anything to XP?

No.

> What about on FAT?

I'm not sure. If you experience some goofiness with permissions on a FAT32 partition in Linux (for example, some directories/files mysteriously become read only after mounting the partition), you may have to use the chmod command to fix the problem. The only thing you should be using FAT32 for is to move files between Windows and Linux.

---

### Post by alexrizzi01 on 2008-01-02
I have the same problem (with XP Professional).
My situation is this:
2 partition (both ntfs) used by XP, the first for the system files (disk C), the second for data files (disk D)
3 partition with Linux.

Now I know that I can use fat32 in the XP data files partion (disk D) and do not share at all the XP system files (disk C), this will be the perfect final solution.

But ... is there any known way to make XP work again (e.g. I cannot add new printer since it says I do not have the permission to write somewhere, even if I'm an administrator), without re-installing it?

Thanks for any suggestion and help

---

### Post by az on 2008-01-02
> **alexrizzi01 said:**
> 
But ... is there any known way to make XP work again (e.g. I cannot add new printer since it says I do not have the permission to write somewhere, even if I'm an administrator), without re-installing it?

Thanks for any suggestion and help

I doubt the the problem has anything to do with installing Ubuntu.  Something other than the Ubuntu installer created that problem.

Now, that doesn't mean that you can't Install Ubuntu, browse your Windows partition and much tings up "by hand", but that the partitioning and installing of Ubuntu besides Windows does not cause what you are describing.

---

