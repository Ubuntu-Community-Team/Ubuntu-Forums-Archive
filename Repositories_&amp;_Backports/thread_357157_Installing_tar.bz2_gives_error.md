---
title: "Installing tar.bz2 gives error"
date: 2007-02-09
forum: Repositories &amp; Backports
---

### Post by magichsjx on 2007-02-09
[B]Hello
when i go to install a tarball tar.bz2 package i get the following error does anyone have any idea?

> 
~$ tar jxf swiftfox-1.5.0.7-pentium3.tar.bz2

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors


especially this line seems to be the cause:

> 
bzip2: Inappropriate ioctl for device
Input file = (stdin), output file = (stdout)

if anyone can tell me what is wrong with my repos or sources list or anything else i would appreciate it. ty.:( [/B]

---

### Post by mlind on 2007-02-11
try to download the file again, it's probably just corrupt download.

---

