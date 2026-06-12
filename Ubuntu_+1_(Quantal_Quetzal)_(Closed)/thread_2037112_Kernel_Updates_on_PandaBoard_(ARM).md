---
title: "Kernel Updates on PandaBoard (ARM)"
date: 2012-08-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jholewinski on 2012-08-03
I'm trying out Ubuntu Server 12.10 Alpha 2 on a PandaBoard and kernel updates do not seem to be succeeding.  After installation, I had kernel 3.4.0-201, and an 'apt-get upgrade' installed kernel 3.4.0-204.  But the system still boots into kernel 3.4.0-201.

The new kernel is visible in /boot on the root partition, but does not appear to have been copied to the FAT32 partition used for u-boot.


My /boot:

```
jholewinski@panda01:/media/tmp$ ll /boot
total 25629
drwxr-xr-x  2 root root    1024 Aug  3 14:54 ./
drwxr-xr-x 22 root root    1024 Jun 26 22:24 ../
-rw-r--r--  1 root root  605411 Jun  5 11:45 abi-3.4.0-201-omap4
-rw-r--r--  1 root root  621026 Jul  9 12:05 abi-3.4.0-204-omap4
-rw-r--r--  1 root root     301 Aug  3 13:55 boot.script
-rw-r--r--  1 root root  103258 Jun  5 11:45 config-3.4.0-201-omap4
-rw-r--r--  1 root root  104868 Jul  9 12:05 config-3.4.0-204-omap4
lrwxrwxrwx  1 root root      26 Aug  3 14:48 initrd.img -> initrd.img-3.4.0-204-omap4
-rw-r--r--  1 root root 6027051 Aug  3 14:23 initrd.img-3.4.0-201-omap4
-rw-r--r--  1 root root 6000343 Aug  3 14:54 initrd.img-3.4.0-204-omap4
lrwxrwxrwx  1 root root      26 Aug  3 14:10 initrd.img.old -> initrd.img-3.4.0-201-omap4
-rw-------  1 root root 2064129 Jun  5 11:45 System.map-3.4.0-201-omap4
-rw-------  1 root root 2061998 Jul  9 12:05 System.map-3.4.0-204-omap4
lrwxrwxrwx  1 root root      23 Aug  3 14:48 vmlinuz -> vmlinuz-3.4.0-204-omap4
-rw-------  1 root root 4354064 Jun  5 11:45 vmlinuz-3.4.0-201-omap4
-rw-------  1 root root 4293816 Jul  9 12:05 vmlinuz-3.4.0-204-omap4
lrwxrwxrwx  1 root root      23 Aug  3 14:10 vmlinuz.old -> vmlinuz-3.4.0-201-omap4
```


My FAT32 u-boot partition (mounted at /media/tmp):

```
jholewinski@panda01:/media/tmp$ ll /media/tmp
total 20564
drwxr-xr-x 5 root root    1536 Dec 31  1969 ./
drwxr-xr-x 3 root root    1024 Aug  3 14:59 ../
-rwxr-xr-x 1 root root     201 Aug  3 15:01 boot.sck.mybak*
-rwxr-xr-x 1 root root     224 Aug  3 15:01 boot.scr*
-rwxr-xr-x 1 root root     201 Aug  3  2012 boot.scr.bak*
-rwxr-xr-x 1 root root     152 Aug  3 15:00 boot.script*
drwxr-xr-x 2 root root     512 Aug  3 13:49 .fseventsd/
-rwxr-xr-x 1 root root   34312 Jun 27 02:41 MLO*
drwxr-xr-x 4 root root     512 Aug  3 13:49 .Spotlight-V100/
drwxr-xr-x 2 root root     512 Aug  3 13:49 .Trashes/
-rwxr-xr-x 1 root root    4096 Aug  3 13:49 ._.Trashes*
-rwxr-xr-x 1 root root  248536 Jun 27 02:41 u-boot.bin*
-rwxr-xr-x 1 root root 4354128 Aug  3  2012 uImage*
-rwxr-xr-x 1 root root 4354128 Aug  3  2012 uImage.bak*
-rwxr-xr-x 1 root root 6027115 Aug  3  2012 uInitrd*
-rwxr-xr-x 1 root root 6027050 Aug  3  2012 uInitrd.bak*
```


The boot.scr file was updated (I had to re-build it to enable the serial console), but not uImage/uInitrd.

Is this a bug, or do the uImage/uInitrd files need to be hard-created now?  I seem to remember this being done automatically in 12.04.

---

