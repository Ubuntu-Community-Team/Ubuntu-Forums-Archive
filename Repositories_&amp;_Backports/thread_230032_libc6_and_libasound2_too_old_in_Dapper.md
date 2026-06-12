---
title: "libc6 and libasound2 too old in Dapper"
date: 2006-08-05
forum: Repositories &amp; Backports
---

### Post by cookdav on 2006-08-05
When I try to install either JDK 1.4 or 1.5 on Dapper, it tells
me that libc6 and libasound2 are too ancient.  Here are the details:

Unpacking sun-j2sdk1.5 (from sun-j2sdk1.5_1.5.0+update07_i386.deb) ...
dpkg: dependency problems prevent configuration of sun-j2sdk1.5:
 sun-j2sdk1.5 depends on libasound2 (>> 1.0.11); however:
  Version of libasound2 on system is 1.0.10-2ubuntu4.
 sun-j2sdk1.5 depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing sun-j2sdk1.5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-j2sdk1.5

Is there a solution?

TIA...

    Dave

---

### Post by Jagot on 2006-08-05
Which repository is that version of Java coming from.  The version in the multiverse repo always works perfectly for me.  Enable multiverse, then:

```
sudo aptitude update
sudo aptitude install sun-java5-jdk
```

---

### Post by cookdav on 2006-08-05
The .DEB kit was built on a different Linux system.
(It must be picking up dependencies from THAT system...whoops.)

Yes, just installing package 'sun-java5-jdk' does indeed
solve it.  Many thanks!

---

