---
title: "[SOLVED] Problems migrating shadow file from SuSE 9.3 to Ubuntu Server x86_64"
date: 2008-05-23
forum: Server Platforms
---

### Post by seabra on 2008-05-23
Hi

 I just migrated a server from SuSE 9.3 to Ubuntu Hardy Heron.
 I copied users from old shadow file to the new file the users can't login.
 I guess this has to do with the way users passwords are encrypted in SuSE and in Ubuntu.  
Any ideias how I can solve this problem??

Kind Regards,

 João Seabra

---

### Post by RealPSL on 2008-05-25
You are definitely on the right path. By default SuSE encrypts file using a blowfish algorithm. Ubuntu is probably expecting DES or MD5 depending on whether you have changed the configuration. ```
man shadow
``` provides tips on determining which algorithm is in use. I am not sure how to convert from blowfish though I have only seen SuSE use that algorithm in my experience.

---

### Post by seabra on 2008-05-28
libpam-unix2 - Blowfish-capable PAM module
This solved the problem

---

