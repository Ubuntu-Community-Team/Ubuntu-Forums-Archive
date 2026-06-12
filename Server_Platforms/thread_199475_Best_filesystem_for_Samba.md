---
title: "Best filesystem for Samba"
date: 2006-06-18
forum: Server Platforms
---

### Post by mssever on 2006-06-18
Once I get Samba up and running, I'll be using it in part as a fileserver for WinXP machines. I may also access it from Linux. Which filesystem would be ideal to use on my share partition? ext3 or ntfs?

---

### Post by tkiesel on 2006-06-18
If you'll be using the Linux computer as the fileserver, I suggest ext3 or another Linux compatible file system.  Linux can't write files to ntfs yet, so you'd run into some snags there.  (Actually, Linux can write to ntfs with the right software, but it experimental and buggy. ;) )

Rock on,
-T

---

### Post by mssever on 2006-06-18
[QUOTE=tkiesel]If you'll be using the Linux computer as the fileserver, I suggest ext3 or another Linux compatible file system.  Linux can't write files to ntfs yet, so you'd run into some snags there.  (Actually, Linux can write to ntfs with the right software, but it experimental and buggy. ;) )

Rock on,
-T[/QUOTE]
Does Ubuntu have problems with NTFS, then? I've done a fair amount of NTFS work from several live CDs, most notably Adios, which is RedHat-based. I haven't tried using (or formatting) NTFS from Ubuntu, though.

I guess my main concern is file permissions (since Linux and NTFS handle them completely differently).

---

### Post by LordHunter317 on 2006-06-19
All Linux has problems with NTFS.  Those rescue cds use special tools and tricks.

---

### Post by imagine on 2006-06-19
Creating, moving, resizing and reading is possible with NTFS partitions. But writing is buggy, you shouldn't try that.

And for a Linux system you should obviously chose a Linux filesystem, like ext3, xfs, reiserfs and so on. Certainly not NTFS. Who gave you that idea?

---

