---
title: "Autoupdate 10.10 server sigfault"
date: 2010-10-27
forum: Server Platforms
---

### Post by gzipper on 2010-10-27
Hi.
I have the 10.10 server and I made the (bad) choice of using auto updating the system with security updates. Choice were made from the installatoin. Now I get sigfaults from unattended-upgr.
Following from messages:
```
 kernel: [458262.341340] unattended-upgr[8057]: segfault at 0 ip 002d3770 sp bfcb9c98 error 4 in libc-2.12.1.so[25f000+157000]
```
System
```
 uname -a
Linux server 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux

```
I believe I got the libc pkg updated but the error were there before that update. Any got ideas on a fix or what to do?

---

### Post by mdavids on 2010-12-13
Any news on this? I have the exact same problem om my two Maverick machines.

---

