---
title: "What is the glib c?"
date: 2011-03-08
forum: Server Platforms
---

### Post by BDaughtry on 2011-03-08
We are considering using Ubuntu server as a plat form for an erp software we are purchasing. The erp software company wants to know what the glib c is so that they can tell us if their sofware will work. Can anyone tell me what the glib c is? I have not downloaded it yet. Thanks

---

### Post by dtfinch on 2011-03-08
It's the standard C library that almost all programs written in C/C++ depend on. The Windows semi-equivalent would be msvcrt*.dll.

Running "ldd --version" should print your glibc version, or you can find the file beginning with "libc-" in /lib. On my 10.04 servers it prints "ldd (Ubuntu EGLIBC 2.11.1-0ubuntu7.6) 2.11.1", so I have glibc 2.11.1.

---

