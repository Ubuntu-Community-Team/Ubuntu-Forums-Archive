---
title: "Uninstalled tar (OOPS!)"
date: 2010-07-27
forum: Server Platforms
---

### Post by roboteti on 2010-07-27
So, I just got a really awesome ubuntu 9.10 VPS. I got it all setup and working, then (not thinking) removed tar because it seemed to be working incorrectly and I wanted to reinstall it. Of course, as I'm sure all of you know, dpkg relies on tar, and I don't have developer tools installed, so I'm kind of stuck right now.

Can you help?

---

### Post by Bachstelze on 2010-07-27
32 or 64 bit?

---

### Post by roboteti on 2010-07-27
Wow, that was fast. 64 bit

---

### Post by Bachstelze on 2010-07-27
[http://iori.fkraiem.org/stuff/tar](http://iori.fkraiem.org/stuff/tar)

Copy into /bin, that should at least let you reinstall the package properly.

---

### Post by roboteti on 2010-07-27
Perfect. Thanks!

---

### Post by srnk on 2010-12-15
Is there a tar binary for 32 bit ubuntu 9.04

---

### Post by sisco311 on 2010-12-15
Welcome to the forums!


[tar 1.20-1 for 32-bit](http://ompldr.org/vNmt2bg/tar)

---

### Post by srnk on 2010-12-15
Thanks sisco311. It worked :D

---

