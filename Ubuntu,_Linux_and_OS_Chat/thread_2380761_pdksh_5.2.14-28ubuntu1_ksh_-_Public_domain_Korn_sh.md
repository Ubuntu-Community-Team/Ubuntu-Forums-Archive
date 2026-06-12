---
title: "pdksh 5.2.14-28ubuntu1 ksh - Public domain Korn shell"
date: 2017-12-21
forum: Ubuntu, Linux and OS Chat
---

### Post by rmstock2 on 2017-12-21
I created a new pdksh package for the  ksh - Public domain Korn shell 
for Ubuntu 16.04 from a old mandriva 2007.1 SRPM package,  which one 
should be able to compile without any problems on modern linux distro's 
with newer gcc versions.  Two adjustments were made : inside siglist.sh 
: sort +2n +0n is replaced with sort -k3n -k1n and inside several c 
files shprintf(newline); becomes shprintf("%s", newline); to prevent 
the -Werror=format-security errors from happening.
In addition an other patch was created to pass the preprocessor
difficulties on Ubuntu 16.04 when using gcc version 5.4.0 20160609 
(Ubuntu 5.4.0-6ubuntu1~16.04.4). The resulting ksh shell seems
to pass the smell test and IBM torture tests :

[IMG]https://i.imgur.com/1ieieLt.png[/IMG]


```
$ ls -l /bin/ksh
-rwxr-xr-x 1 root root 236088 dec 18 02:55 /bin/ksh
$ ldd /bin/ksh
        linux-vdso.so.1 =>  (0x00007ffed7766000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc43c97c000)
        /lib64/ld-linux-x86-64.so.2 (0x00005575b218d000)
$

```

when comparing this to bash :


```
$ ls -l /bin/bash
-rwxr-xr-x 1 root root 1037528 mei 16  2017 /bin/bash
$ ldd /bin/bash
        linux-vdso.so.1 =>  (0x00007ffcb9751000)
        libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007f45e0c3c000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f45e0a38000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f45e066d000)
        /lib64/ld-linux-x86-64.so.2 (0x000055ebcbb83000)
$ 



```if this package is of use, you can make it permanent with synaptic, to
prevent the pdksh (migration edition) and mksh MirBSD Ksh from getting
installed :


[IMG]https://i.imgur.com/wq91H0A.png[/IMG]


Download is at 
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/)
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1.debian.tar.xz](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1.debian.tar.xz)
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1.dsc](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1.dsc)
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1_amd64.build](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1_amd64.build)
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1_amd64.changes](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1_amd64.changes)
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1_amd64.deb](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14-28ubuntu1_amd64.deb)
[ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14.orig.tar.gz](ftp://ftp.crashrecovery.org/pub/linux/pdksh/DEB/ubuntu1604/pdksh_5.2.14.orig.tar.gz)

In case DNS for ftp.crashrecovery.org is blocked,  ftp.crashrecovery.org  currently  points to ip 77.174.144.88

---

### Post by oldos2er on 2017-12-22
Not a support request, moved to Ubuntu, Linux, & OS Chat.

---

