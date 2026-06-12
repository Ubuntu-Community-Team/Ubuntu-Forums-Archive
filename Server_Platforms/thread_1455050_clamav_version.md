---
title: "clamav version"
date: 2010-04-15
forum: Server Platforms
---

### Post by nsnidanko on 2010-04-15
Hi, 
 
We are running clamav on 9.10 (with MailScanner)...
 
I upgrade our clam av from respiratory today and it is still showing old version..
 
When i do freshclam i get this:
 
Local version: 0.95.3 Recommended version: 0.96
 
[EMAIL="root@ares"]root@ares[/EMAIL]:~# ldd `which freshclam`
        linux-vdso.so.1 =>  (0x00007fff1c15e000)
        libclamav.so.6 => /usr/lib/libclamav.so.6 (0x00007f121d51d000)
        libz.so.1 => /lib/libz.so.1 (0x00007f121d306000)
        libresolv.so.2 => /lib/libresolv.so.2 (0x00007f121d0ed000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007f121ced1000)
        libc.so.6 => /lib/libc.so.6 (0x00007f121cb62000)
        libtommath.so.0 => /usr/lib/libtommath.so.0 (0x00007f121c946000)
        libltdl.so.7 => /usr/lib/libltdl.so.7 (0x00007f121c73c000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00007f121c52b000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007f121c327000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f121d7e9000)
 
Is there 0.96 available from respiratory? Or i have to install it manually from .deb package?

---

### Post by noway2 on 2010-04-15
The version in the repositories is 0.95.3.  While it is older, and yes it has reached the point where it 'complains', it is new enough to not be subject to the old version disabling that did / will take place.

---

### Post by nsnidanko on 2010-04-15
oh ok. I originally installed 0.95.3. I thought after going apt-get upgrade it will be upgraded to 0.96. This update apeared in respiratory few days ago, right after 0.96 officialy came out.
 
By the way today they stop releasing freshclam for anything older than 0.95.3
 
Regards

---

