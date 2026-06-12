---
title: "Crash accessing Home of another user"
date: 2021-04-05
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-04-05
On my PC I have some different users. If from one user I try to access the Home directory of a different user I enter the password and then I have a crash.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1922548](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1922548)

---

### Post by TheFu on 2021-04-05
> **corradoventu said:**
> On my PC I have some different users. If from one user I try to access the Home directory of a different user I enter the password and then I have a crash.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1922548](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1922548)

It shouldn't crash, but ubuntu did announce that user HOME directories would be locked down by default with this release. The error should just be a permission denied error.  [https://ubuntu.com/blog/private-home-directories-for-ubuntu-21-04](https://ubuntu.com/blog/private-home-directories-for-ubuntu-21-04)  I'm not a fan of using setfacl ... ever. Permissions that are hidden suck.

---

### Post by corradoventu on 2021-04-05
Yes, user HOME directories are now private and therefore a password is required to access it, but it should not crash.
Did You look to the screenshot attached to my bug?

---

