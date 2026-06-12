---
title: "Ventrilo Server 2.1.2 start problem!"
date: 2008-11-17
forum: Server Platforms
---

### Post by juncha on 2008-11-17
Hi, im new at Ubuntu forums, but not new at Debian OS :P

I have edited param.h and changed USER_HZ to 1500 HZ before compiling my kernel, and now my ventrilo server won't start cause of that. Can I edit sysconfig and change it back to 1000 HZ or i must compile my kernel again? I'm running Ubuntu 8.04.1 

Here is a detailed error message:

ERROR: sysconf reported an _SC_CLK_TCK higher then 1000. 1500 to be precise.

Thanx :lolflag:

---

### Post by juncha on 2008-11-18
Nevermind I have recompiled my kernel to 1000HZ and it's fine, thank you anyway though.

---

