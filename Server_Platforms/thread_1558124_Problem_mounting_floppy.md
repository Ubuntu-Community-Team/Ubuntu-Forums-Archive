---
title: "Problem mounting floppy"
date: 2010-08-21
forum: Server Platforms
---

### Post by edkasky on 2010-08-21
I have Ubuntu Server 10.04.1 LTS installed on a Dell PE 2600 and it&#347; running great.  However, I have a habit of wanting to make an emergency boot floppy - just in case.

Whatever I try, I cannot get the floppy to mount.  I can access it using command line utilities to format it etc., but it just will not mount.

Most recently, I installed fdutils and when I do a - sudo fdmount - the error is fdmount (/dev/fd0): Can't access /fd0: No such file or directory
which is not true: brw-rw---- 1 root floppy 2, 0 2010-08-21 14:28 /dev/fd0
Plus I am formating and creating file system (msdos and ext2) to fd0 successfully.

I have done a bit of searching and the errors lead me to the possibility that the kernel may not have been compiled with the floppy driver.  Can this be possible?  If not, then I have tried about 10 different ways to format and mount the silly thing and am about to give up.

Ed

---

