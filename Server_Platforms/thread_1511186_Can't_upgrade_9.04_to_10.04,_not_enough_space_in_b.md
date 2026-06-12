---
title: "Can't upgrade 9.04 to 10.04, not enough space in /boot"
date: 2010-06-16
forum: Server Platforms
---

### Post by v0idnull on 2010-06-16
/boot is filled with what seems to be legacy stuff:

-rw-r--r-- 1 root root 3549936 2009-04-16 23:57 vmlinuz-2.6.28-11-server
-rw-r--r-- 1 root root 3540112 2009-09-09 09:13 vmlinuz-2.6.28-15-server
-rw-r--r-- 1 root root 3540496 2009-11-11 07:11 vmlinuz-2.6.28-16-server
-rw-r--r-- 1 root root 3540464 2009-12-01 16:21 vmlinuz-2.6.28-17-server
-rw-r--r-- 1 root root 3540432 2010-03-12 02:05 vmlinuz-2.6.28-18-server
-rw-r--r-- 1 root root 3541232 2010-05-26 21:35 vmlinuz-2.6.28-19-server

as an example, do I need all these files for older kernels or are they safe to delete?

---

### Post by snowpine on 2010-06-16
It is okay to delete older kernels, I like to keep the current one plus one older one as a backup. I recommend removing them using the package manager (rather than simply deleting the files) and I also recommend a fresh reinstall of 10.04 rather than a sequential 9.04->9.10->10.04 upgrade. :)

Another solution to consider is to simply increase the size of your /boot partition.

---

