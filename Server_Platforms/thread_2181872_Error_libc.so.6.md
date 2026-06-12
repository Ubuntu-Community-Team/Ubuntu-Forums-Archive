---
title: "Error libc.so.6"
date: 2013-10-19
forum: Server Platforms
---

### Post by kwN7kft on 2013-10-19
Hi there,

Every command that I Type i get the following error.

ls: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

I think symbolic link was damaged or deleted is there anyway in recovering it ?

Thnaks in advanced.

---

### Post by steeldriver on 2013-10-19
Hmm... that's going to be tricky since almost every binary is going to dynamically link to libc. You could try using busybox - it provides minimal versions of most commands and (I think) is statically linked

```
$ **busybox** find /lib -name 'libc[.-]*' -exec **busybox** ls -l {} \;
```

If that finds the broken link you should be able to use busybox ln -s to recreate it. Otherwise you will need to use a live CD/USB I think - either to fix the link or chroot and reinstall the libc6 package.

---

### Post by hawkmage on 2013-10-19
As steeldriver said it is going to be difficult doing much of anything, not even busybox will work without libc.so

Here are the linked libs for busybox:
```
hawkmage@ubuntu:~$ ldd /bin/busybox
       linux-vdso.so.1 =>  (0x00007ffff3eee000)
       libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f8ad2a84000)
       /lib64/ld-linux-x86-64.so.2 (0x00007f8ad2e23000)
```

About the only thing I can think of doing is to boot of a live CD/DVD of Ubuntu and mount the drive and fix the issue.

---

### Post by steeldriver on 2013-10-19
strange... I get

```

$ ldd /bin/busybox
    not a dynamic executable

$ file /bin/busybox 
/bin/busybox: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), **statically linked**, for GNU/Linux 2.6.24, BuildID[sha1]=0xcd1f26d962ba4460c5239a401d0568c6f2fded27, stripped

```

---

### Post by Bashing-om on 2013-10-19
@ et all;
Same same as steeldriver for my output:
> 
sysop@1304mini:~$ ldd /bin/busybox
        not a dynamic executable

sysop@1304mini:~$ file /bin/busybox 
/bin/busybox: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, for GNU/Linux 2.6.24, BuildID[sha1]=0x0fc88573a7b858ab9dfe424dc398ef95092d07e7, stripped
sysop@1304mini:~$ 


Interested in seeing the solution.

[INDENT][INDENT]in the process of learning
[/INDENT][/INDENT]

---

### Post by hawkmage on 2013-10-19
Oops, I logged into a Debian box that used to run Ubuntu.

---

