---
title: "missing 300 GB on a External HDD with NTFS, still factory formated"
date: 2018-09-23
forum: Windows
---

### Post by aryell-linx on 2018-09-23
I'm missing ~300 GB on a External HDD with NTFS 3TB drive, still factory formatted. I've seen this before, it sometimes happens with all NTFS filesystems I've had, does not matter what brand of hard drive it is, (also internal or external). My question is should I delete system volume information folder with a live distro of ubuntu. Because in my experience the only way to fix this problem is to format the drive again. And also, get this, M$ support said kind of the same thing, but did just talk to a low level employee, not a actual technician. If I just delete the contents of the drive normaly or move all the files that I can to some other storage media, the missing space is still seen as missing. I think there are a lot of log files leftover or something, do not know for sure. Restore Points are disabled so no luck there. I'm using windows 10 at the moment.
   Any one experience this kind of thing before ?
 If anyone need other info or clarification on this problem pls ask, right now I'm going to -- copy -- the files to internal HDDs and delete some of the bloat from sys vol info folder in the hopes that the filesystem will survive on the external drive, but I am hoping for a more elegant solution.

---

### Post by jeevanthanal on 2018-09-24
you just install gpart and check the drive,

---

### Post by oldfred on 2018-09-24
You have GB versus GiB, you have format and you have journal with all newer file systems, both NTFS & ext4.

Linux also reserves 5% for superuser which with new very large drives may be too much or not required for data only partitions. But you still are responsible for managing use.
Also NTFS likes 30% free space. At 10% free you have little space for it to do a defrag.

       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.

---

