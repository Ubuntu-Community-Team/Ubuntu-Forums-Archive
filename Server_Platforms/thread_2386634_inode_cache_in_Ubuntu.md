---
title: "inode cache in Ubuntu"
date: 2018-03-08
forum: Server Platforms
---

### Post by davidpsv17 on 2018-03-08
Hi,

I have an Ubuntu Xenial Server with different processes, each day  more or less at the same hour I receive an alert that the number of  inodes is very high. This check looks at /proc/sys/fs/inode-nr and if  the first number (number of inodes the system has allocated) is greater  than 4888985, send an alert. Now, I'm resolving this doing a drop_caches  with: "sync; echo 2 > /proc/sys/vm/drop_caches" but I would like to  know which process is using all these inodes, it could be possible?

  
Thanks!!

---

### Post by slickymaster on 2018-03-08
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2018-03-09
What do 
**df -h**
and 
**df -i **
show?
Running out of inodes on a file system doesn't happen much, unless there are 500K tiny files or the file system is small.  I've run out on a few systems - they were running ruby blog software with lots and lots of "gems" installed.  Since inodes are set at file system creation time, the solution is to move some files to a new file system.  If you use LVM, it might be possible to shrink the file system and LV, then create another LV with 100x more inodes on the freed space, then move the most offending files over.

For ext4 file systems, you can see the file system characteristics with **tune2fs**.

Running out of inodes is a hassle.

---

