---
title: "safe to delete old kernals from /boot?"
date: 2007-03-04
forum: Server Platforms
---

### Post by golfing22 on 2007-03-04
Hello everyone,
I made a mistake when I setup my server, becuase I only allocated 100mb to /boot, and now it's completely full.  It's going to be hard to resize that partition becuase it's in a software raid array.  I'm currently using kernal 2.6.17-11 but there are a lot of files for kernal 2.6.17-10.  Would it be safe for me to delete all the 2.6.17-10 files???

```
root@gameserver:/boot# ls -l
total 15025
-rw-r--r-- 1 root root  287964 2006-12-05 17:50 abi-2.6.17-10-server
-rw-r--r-- 1 root root  287726 2007-02-01 15:14 abi-2.6.17-11-server
-rw-r--r-- 1 root root   74847 2006-12-05 16:41 config-2.6.17-10-server
-rw-r--r-- 1 root root   74781 2007-02-01 14:06 config-2.6.17-11-server
drwxr-xr-x 2 root root     448 2007-01-04 19:50 grub
-rw-r--r-- 1 root root 5850009 2007-02-22 22:50 initrd.img-2.6.17-10-server
-rw-r--r-- 1 root root 3944448 2007-03-01 22:24 initrd.img-2.6.17-11-server
-rw-r--r-- 1 root root   94600 2006-10-20 07:44 memtest86+.bin
-rw-r--r-- 1 root root  728652 2006-12-05 17:50 System.map-2.6.17-10-server
-rw-r--r-- 1 root root  729806 2007-02-01 15:14 System.map-2.6.17-11-server
-rw-r--r-- 1 root root 1636374 2006-12-05 17:50 vmlinuz-2.6.17-10-server
-rw-r--r-- 1 root root 1636264 2007-02-01 15:14 vmlinuz-2.6.17-11-server

```

Thanks for the help,
golfing22

---

### Post by solar george on 2007-03-04
You can use apt to remove the old kernels

---

### Post by golfing22 on 2007-03-04
do you know what that command would be by chance?

---

### Post by solar george on 2007-03-04
Do 
```
apt-get remove linux-image-2.6.17-10-server
```

---

### Post by ianare on 2007-03-07
Just a friendly warning: I had the distupgrade 6.10 -> 7.04 crash and burn due to my /boot partition being full (I only had 64 MB total). I had to install from scratch, this time not giving /boot a seperate partition.

---

