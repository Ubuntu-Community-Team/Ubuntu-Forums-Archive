---
title: "Fail2Ban; the md5 module is deprecated"
date: 2009-12-05
forum: Security
---

### Post by dark_templar on 2009-12-05
Hi folks,

Has anyone seen this this error pop when installing fail2ban in karmic?:

 DeprecationWarning: the md5 module is deprecated; use hashlib instead import md5

---

### Post by tubbygweilo on 2009-12-05
Looks like it may well relate to bug [#323270]("https://bugs.launchpad.net/subvertpy/+bug/323270").

---

### Post by dark_templar on 2009-12-05
Thanks,

It looks like it. I will install python 2.5 on it and point fail2ban to 2.5 instead of 2.6.

---

### Post by dark_templar on 2009-12-05
It seems that md5 is also deprecated in 2.5.

I will try to import md5 into the library I guess.

---

### Post by falconindy on 2009-12-06
The program still runs, correct? This isn't something you need to worry about fixing. It's up to the developer of the program to change it. 

A library or function being deprecated means that while its still available for use, there's been a replacement implemented that you should be using instead. On a long enough time line, the functionality will be removed from, in this case, Python.

---

### Post by dark_templar on 2009-12-07
Thanks. Yes it is working.  I checked the logs and everything looks normal apart from that.

---

