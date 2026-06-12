---
title: "change PAM's encryption from MD5 to SHA?"
date: 2009-08-11
forum: Security
---

### Post by l3git.h4cker on 2009-08-11
I have Ubuntu 8.04 LTS server, and was wondering how to change PAM and the way it encrypts /etc/shadow's passwords from MD5 to SHA.

Is this possible?  If so, how might I do this?

EDIT -> nvm, I found out how to use blowfish

---

### Post by cdenley on 2009-08-12
SHA-512 support in PAM was not present until ubuntu 8.10.
[http://ubuntuforums.org/showthread.php?t=924435&page=2](http://ubuntuforums.org/showthread.php?t=924435&page=2)

---

