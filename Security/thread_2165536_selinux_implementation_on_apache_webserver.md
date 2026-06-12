---
title: "selinux implementation on apache webserver"
date: 2013-08-05
forum: Security
---

### Post by learnbash on 2013-08-05
Hello folks,

Please is there anyone can tell me, how i can secure/implement selinux on my webserver where apache is running.

---

### Post by samiux on 2013-08-05
> **learnbash said:**
> Hello folks,

Please is there anyone can tell me, how i can secure/implement selinux on my webserver where apache is running.

To make it simple and easy management, I suggest "AppArmor".

Samiux

---

### Post by CharlesA on 2013-08-06
> **samiux said:**
> To make it simple and easy management, I suggest "AppArmor".

Samiux

Agreed. If you really want to use SELinux, you'd need to move to a RH-based distro. SE Support on Debian/Ubuntu is tricky at best.

---

