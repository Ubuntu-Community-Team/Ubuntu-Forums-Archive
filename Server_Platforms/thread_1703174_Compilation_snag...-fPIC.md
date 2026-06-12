---
title: "Compilation snag...-fPIC?"
date: 2011-03-08
forum: Server Platforms
---

### Post by djmikepic on 2011-03-08
Hi,

I'm attempting to compile HP Seagull (in-case anyone else may be :D) and I've hit a problem during the make phase. I'm running a 64 bit server and the problem appears to be 32 bit related. Can someone help? Listed below is some quick system info and the related error message. I wasn't able to attach the file due to invalid format so I've provided a link from my personal site.

[email]mpark@psp6wshm01:/etc/seagull.svn.LINUX[/email]$ uname -a
Linux psp6wshm01 2.6.35-27-server #48-Ubuntu SMP Tue Feb 22 21:53:16 UTC 2011 x86_64 GNU/Linux


[email]mpark@psp6wshm01:/etc/seagull.svn.LINUX[/email]$ sudo ./build.ksh -target all
[System  : LINUX]
[Archi   : X86_64]
[Mode    : RELEASE]
[Name    : seagull]
[Version : 1.8.2]

[Begin Makefile generation phase]
make: Nothing to be done for `all'.
[End Makefile generation phase OK]

[Begin compilation phase]
[Generating file seagull]
make[1]: Entering directory `/etc/seagull.svn.LINUX'
make[1]: `/etc/seagull.svn.LINUX/build-1.8.2/seagull' is up to date.
make[1]: Leaving directory `/etc/seagull.svn.LINUX'
[Generating file libtrans_ip.so]
make[1]: Entering directory `/etc/seagull.svn.LINUX'
[Compiling library-trans-ip/C_TransIP.cpp]
[Linking /etc/seagull.svn.LINUX/build-1.8.2/libtrans_ip.so]
/usr/bin/ld: /etc/seagull.svn.LINUX/work-1.8.2/C_RegExp.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/etc/seagull.svn.LINUX/work-1.8.2/C_RegExp.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [/etc/seagull.svn.LINUX/build-1.8.2/libtrans_ip.so] Error 1
make[1]: Leaving directory `/etc/seagull.svn.LINUX'
make: *** [all_libtrans_ip.so] Error 2

File = [C_RegExp.o]("http://silenceprohibitedrecordings.com/files/C_RegExp.o")

---

