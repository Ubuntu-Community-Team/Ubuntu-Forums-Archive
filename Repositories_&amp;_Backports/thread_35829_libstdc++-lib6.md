---
title: "libstdc++-lib6"
date: 2005-05-20
forum: Repositories &amp; Backports
---

### Post by bularsson on 2005-05-20
Hi everybody,

I've installed Hoary recently (switching from Mandrake LE - it sucks). When I tried to install Maple 9, it complains that libstdc++-libc6.1-1.so.2 is missing . I've been looking at the repositories for this library without success. Could somebody tell me which package I should install??

Thanks a lot,

Bularsson.

---

### Post by bularsson on 2005-05-20
Hello to myself,

I think I've solved the problem. I've installed libstdc++2.10-glibc2.2 and symlinked 
libstdc++-3-libc6.2-2-2.10.0.so to libstdc++-libc6.1-1.so.2. Now Maple 9 is willing to install.

B.

---

### Post by csocean on 2008-05-29
could you let me know how you did that?  I'm in the same boat I think ;)

---

