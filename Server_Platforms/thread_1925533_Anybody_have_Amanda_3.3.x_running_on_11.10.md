---
title: "Anybody have Amanda 3.3.x running on 11.10 ?"
date: 2012-02-14
forum: Server Platforms
---

### Post by Zapisto on 2012-02-14
Hello,

Just upgrade from amanda server 2.6.1 to 3.3.x
on ubuntu 11.10 

all was going ok until i start play with amchek,  firt, it give error for amflush still running.
when i try amcleanup  i got:
> Segmentation fault

in the log :

> Feb 13 14:48:01 orion kernel: [11638.594686] amcleanup[23694]: segfault at 8 ip 006053e9 sp bffc1720 error 4 in libConfig.so[601000+23000]

then now amcheck is giving me :
> Amanda Tape Server Host Check
-----------------------------
Holding disk /Data2/Amanda: 148700 MB disk space available, using 148600 MB
amcheck-device terminated with signal 11Server check took 0.241 seconds

in the log i have :
> Feb 13 14:49:17 orion kernel: [11714.402564] amcheck-device[23732]: segfault at 8 ip 007e73e9 sp bfa46510 error 4 in libConfig.so[7e3000+23000]

so i think the two issue migth be related

any helps will be appreciated
thanks

---

