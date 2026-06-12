---
title: "Ubuntu lucid produces broken initrd"
date: 2010-11-23
forum: Server Platforms
---

### Post by pvh513 on 2010-11-23
I maintain a server which initially had karmic installed and was recently upgraded to lucid. The root filesystem is installed on a RAID5 with a 3ware 9650 controller. Ever since the upgrade, lucid has been producing broken initrd images. The symptom is that during the boot, the system will claim that it cannot find the root filesystem. The workaround I found is to boot into a *karmic* rescue system and force a rebuild of the initrd. Then the system will boot fine until some update causes another rebuild of initrd and the whole cycle starts again. I have looked at the working and broken versions of initrd and found that in the broken versions some of the libraries are located under /lib64 rather than /lib (and this is the *only* difference). To be more precise, in a working initrd, /lib64 only contains ld-linux-x86-64.so.2 and all other libraries are in /lib. In a broken initrd, /lib and /lib64 contain the following:

```
# ls -l lib64/
total 3028
-rwxr-xr-x 1 root root  136936 2010-11-23 16:38 ld-linux-x86-64.so.2
-rw-r--r-- 1 root root  126536 2010-11-23 16:38 libblkid.so.1
-rw-r--r-- 1 root root   14584 2010-11-23 16:38 libcom_err.so.2
-rwxr-xr-x 1 root root 1572232 2010-11-23 16:38 libc.so.6
-rw-r--r-- 1 root root  121592 2010-11-23 16:38 libdevmapper.so.1.02.1
-rw-r--r-- 1 root root   14696 2010-11-23 16:38 libdl.so.2
-rw-r--r-- 1 root root  207240 2010-11-23 16:38 libdmraid.so.1.0.0.rc16
-rw-r--r-- 1 root root   28072 2010-11-23 16:38 libe2p.so.2
-rw-r--r-- 1 root root  184144 2010-11-23 16:38 libext2fs.so.2
-rw-r--r-- 1 root root   76696 2010-11-23 16:38 libproc-3.2.8.so
-rwxr-xr-x 1 root root  135745 2010-11-23 16:38 libpthread.so.0
-rw-r--r-- 1 root root   31744 2010-11-23 16:38 librt.so.1
-rw-r--r-- 1 root root  117592 2010-11-23 16:38 libselinux.so.1
-rw-r--r-- 1 root root  244576 2010-11-23 16:38 libsepol.so.1
-rw-r--r-- 1 root root   47048 2010-11-23 16:38 libudev.so.0
-rw-r--r-- 1 root root   19008 2010-11-23 16:38 libuuid.so.1
# ls -l lib/
total 2284
drwxr-xr-x 3 root root    4096 2010-11-23 16:38 firmware
-rwxr-xr-x 1 root root   72048 2010-11-23 16:38 klibc-usBAintlt99f0TITo98H_trqH2c.so
-rwxr-xr-x 1 root root 1572232 2010-11-23 16:38 libc.so.6
-rw-r--r-- 1 root root   14696 2010-11-23 16:38 libdl.so.2
-rw-r--r-- 1 root root  217568 2010-11-23 16:38 libfuse.so.2
-rw-r--r-- 1 root root  266616 2010-11-23 16:38 libntfs-3g.so.75
-rwxr-xr-x 1 root root  135745 2010-11-23 16:38 libpthread.so.0
-rw-r--r-- 1 root root   31744 2010-11-23 16:38 librt.so.1
drwxr-xr-x 3 root root    4096 2010-11-23 16:38 modules
drwxr-xr-x 3 root root    4096 2010-11-23 16:38 udev

```So some libraries are present both in /lib and /lib64 (not sure why, they are identical) while others are only in /lib or /lib64. I *assume* that only /lib is seen by the loader, causing binaries that need libraries that are only in /lib64 to fail to load.

So I have a good idea what is going wrong here, but I don't know how to fix this. Does anybody know what the proper fix for this problem would be?

---

