---
title: "CUPS blocked?  Executables won't run!"
date: 2010-05-04
forum: Security
---

### Post by LifeOnMars on 2010-05-04
I recently upgraded an Ubuntu server and now none of the CUPS executables under /opt/OpenPrinting-Gutenprint work!  Here are some of the things I've tried:

[FONT=Courier New]root$ cd /opt/OpenPrinting-Gutenprint/bin
root$ ./cups-calibrate
bash: ./cups-calibrate: Permission denied
root$ ldd ./cups-calibrate
/usr/bin/ldd: line 117: ./cups-calibrate: Permission denied
root$ file ./cups-calibrate
./cups-calibrate: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.15, dynamically linked (uses shared libs), not stripped
root$ uname -a
Linux ubuntu3 2.6.27-14-server #1 SMP Mon Aug 31 13:57:10 UTC 2009 i686 GNU/Linux
root$ ls -l ./cups-calibrate
-rwxr-xr-x 1 root root 26118 2010-02-25 10:59 ./cups-calibrate*
root$ strings ./cups-calibrate | grep '\.so'
/lib/ld-lsb.so.3
libpthread.so.0
libcrypt.so.1
libz.so.1
libcupsimage.so.2
libm.so.6
libc.so.6
root$ mount -l
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro) []
/dev/sda6 on /usr type ext3 (rw,relatime) []
/dev/sda12 on /opt type ext3 (rw,relatime) []
/dev/sda7 on /var type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
...
root$ cp ./cups-calibrate /usr/bin/cups-calibrate-TMP
root$ ldd /usr/bin/cups-calibrate-TMP
/usr/bin/ldd: line 117: /usr/bin/cups-calibrate-TMP: Permission denied
root$  /usr/bin/cups-calibrate-TMP
bash: /usr/bin/cups-calibrate-TMP: Permission denied
root$ cp /bin/df /opt/OpenPrinting-Gutenprint/bin/df-TMP
root$ /opt/OpenPrinting-Gutenprint/bin/df-TMP --version
df (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Written by Torbjorn Granlund, David MacKenzie, and Paul Eggert.
root$ service apparmor stop
Unloading AppArmor profiles : done.
root$ ./cups-calibrate
bash: ./cups-calibrate: Permission denied

[/FONT]
I've checked all the libraries in the `strings` output and they all `ldd` fine.  Any ideas?  This is truly frustrating!

---

### Post by cariboo on 2010-05-04
I just tried the cups-calibrate command as a regular user, to just to see if the command works, which it did. I have a Brother HLl5250 that used the openprinting repositories until the Lucid RC, when that repository was closed. It has now reverted to the Lucid repositories. Could there be a problem with the files from the openprinting repository?

---

### Post by tgalati4 on 2010-05-04
I have found that CUPS is closely tied to the kernel.  Change the kernel and guess what, CUPS breakage.  There is often a quick fix available and within a few days a CUPS update fixes whatever was borked.  I'm not familiar with openprinting, but you should file a bug describing what is not working.  Anything in /opt is a 3rd-party installation.  Ubuntu updates would most like break these 3rd-party installs anyway.

---

