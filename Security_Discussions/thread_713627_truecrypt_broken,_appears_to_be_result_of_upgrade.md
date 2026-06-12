---
title: "truecrypt broken, appears to be result of upgrade"
date: 2008-03-02
forum: Security Discussions
---

### Post by cworley420 on 2008-03-02
I get the following error when mounting a truecrypt FS

FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module

I think after upgrading some kernel related packages the truecrypt modules are no longer loaded with the new kernel.  I tried reinstalling truecrypt expecting it to config itself with the new kernel.

Has anyone expereinced this after ubuntu updates?  This happend a while ago so, i don't remeber exactly what updates it was, its an assumption that the updates caused the problem.

-chris worley

---

### Post by chewearn on 2008-03-03
I have only experience this after a distribution update, like edgy to feisty, and feisty to gutsy.

Haven't seen broken truecrypt with normal kernel update.

The new truecrypt v5a is supposed to be kernel independent.  If you have 32-bit ubuntu, you can download the deb file from the website.

---

### Post by cworley420 on 2008-03-05
Thank you, i was reinstalling version 4.3 which i downloaded some time back.  After getting the latest v5.0 and installing it, I can now mount my truecrypt FSs


thanks'
-chris worley

---

