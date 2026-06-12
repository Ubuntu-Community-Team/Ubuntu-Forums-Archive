---
title: "i386 under lucid on Oracle VirtualBox (Host: precise) using old libc"
date: 2014-04-10
forum: Virtualisation
---

### Post by LGI-MP on 2014-04-10
I'm trying to run a very old program that is already pre-compiled for i386 and was having no success running it on my x86_64 system, even with ia32-libs.  I installed Oracle VirtualBox and installed the following image on it:

[http://old-releases.ubuntu.com/releases/10.04.3/ubuntu-10.04.4-desktop-i386.iso](http://old-releases.ubuntu.com/releases/10.04.3/ubuntu-10.04.4-desktop-i386.iso)

The package requires libc/libm version 5 which I was unable to find in any Ubuntu version.
I found a CentOS RPM package for libc-5.3.12-31.i386 and used Alien to convert this to .deb format.  I then installed this, created a conf file in /etc/ld.so.conf.d to add the installed path into my library path, ran ldconfig an verified that the entry was operating. Running ldd shows the libraries are found
ldd /usr/bin/blast/blastp: 
    linux-gate.so.1 =>  (0x00c29000)
    libm.so.5 => /usr/i486-linux-libc5/lib/libm.so.5 (0x00bab000)
    libc.so.5 => /usr/i486-linux-libc5/lib/libc.so.5 (0x0089b000)

uname -m:
i686

uname -a:
Linux virtbox 2.6.32-57-generic #119-Ubuntu SMP Wed Feb 19 01:04:55 UTC 2014 i686 GNU/Linux

file /usr/bin/blast/blastp:
/usr/bin/blast/blastp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped

ls -la /usr/bin/blast/blastp:
-rwxr-xr-x 1 root root 436096 1998-02-05 09:59 /usr/bin/blast/blastp
(same permissions for directories /usr/bin and /usr/bin/blast)

/usr/bin/blast/blastp:
bash: /usr/bin/blast/blastp: No such file or directory

ld /usr/i486-linux-libc5/lib/libm.so.5:
ld: warning: cannot find entry symbol _start; not setting start address
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__isnanl'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__isnan'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `errno'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__isinf'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `___brk_addr'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__environ'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__getfpucw'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `atexit'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__isinfl'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `__errno_location'
/usr/i486-linux-libc5/lib/libm.so.5: undefined reference to `raise'

Is there a mismatch between the i686 kernel and the 386 executable? the 486 libc?  What else do I need to do?  Is there a different Ubuntu or Debian system I should be using as my base?

---

### Post by lukeiamyourfather on 2014-04-10
If I'm not mistaken that would be circa 2000, which predates all versions of Ubuntu. You might want to try a very old distribution like Debian 3.0 (Woody) or Red Hat Linux 7 (not to be confused with Red Hat Enterprise Linux).

---

### Post by LGI-MP on 2014-04-16
> **lukeiamyourfather said:**
> If I'm not mistaken that would be circa 2000, which predates all versions of Ubuntu. You might want to try a very old distribution like Debian 3.0 (Woody) or Red Hat Linux 7 (not to be confused with Red Hat Enterprise Linux).

Thanks for the tip. I had some difficulties installing Woody (although I believe I know how to address that issue now), but was eventually able to install Fedora Core 1.  I THOUGHT I had the issue solved, as ldd&file output looked logical, but now I get segfaults in the offending program.

Here is my current status:
ls -la /lib/lib?.so.5
lrwxrwxrwx  1 root root 34 Apr 11 00:47 /lib/libc.so.5 -> /usr/i486-linuxlibc5/lib/libc.so.5
lrwxrwxrwx  1 root root 34 Apr 11 00:46 /lib/libm.so.5 -> /usr/i486-linuxlibc5/lib/libm.so.5

[matt@localhost vbox]$ ls -la /usr/i486-linuxlibc5/lib/*
lrwxrwxrwx  1 root root      14 Apr 11 00:44 /usr/i486-linuxlibc5/lib/libc.so.5 -> libc.so.5.4.38-rwxr-xr-x  1 root root 1820567 Oct  8  1997 /usr/i486-linuxlibc5/lib/libc.so.5.4.38
lrwxrwxrwx  1 root root      13 Apr 11 00:44 /usr/i486-linuxlibc5/lib/libm.so.5 -> libm.so.5.0.9
-rwxr-xr-x  1 root root   75525 Oct  8  1997 /usr/i486-linuxlibc5/lib/libm.so.5.0.9

ldd /usr/bin/wublast/blastp
        libm.so.5 => /lib/libm.so.5 (0x40013000)
        libc.so.5 => /lib/libc.so.5 (0x4001c000)

sudo /sbin/ldconfig -v | grep libc.so
        libc.so.6 -> libc-2.3.2.so
        libc.so.6 -> libc-2.3.2.so
        libc.so.6 -> libc-2.3.2.so

I'm confused as to why ldconfig doesn't see the so.5 entries. Explicitly adding /usr/lib and /lib to the ld.so.conf file does gives the following errors on ldconfig invocation:
 /sbin/ldconfig: Path `/lib' given more than once
/sbin/ldconfig: Path `/usr/lib' given more than once

file /usr/bin/wublast/blastp
/usr/bin/wublast/blastp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped

/usr/i486-linuxlibc5/lib/libc.so.5.4.38: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped

sudo ldd /usr/i486-linuxlibc5/lib/libc.so.5.4.38
        statically linked

sudo ld /usr/i486-linuxlibc5/lib/libc.so.5.4.38
ld: warning: cannot find entry symbol _start; not setting start address

ld /lib/libm.so.5
ld: warning: cannot find entry symbol _start; not setting start address
/lib/libm.so.5: undefined reference to `__isnanl'
/lib/libm.so.5: undefined reference to `__isnan'
/lib/libm.so.5: undefined reference to `errno'
/lib/libm.so.5: undefined reference to `__isinf'
/lib/libm.so.5: undefined reference to `___brk_addr'
/lib/libm.so.5: undefined reference to `__environ'
/lib/libm.so.5: undefined reference to `__getfpucw'
/lib/libm.so.5: undefined reference to `atexit'
/lib/libm.so.5: undefined reference to `__isinfl'
/lib/libm.so.5: undefined reference to `__errno_location'
/lib/libm.so.5: undefined reference to `raise'


uname -a
Linux localhost.localdomain 2.4.22-1.2199.nptl #1 Wed Aug 4 12:21:48 EDT 2004 i686 i686 i386 GNU/Linux

uname -m
i686

---

