---
title: "grub-pc upgrade error"
date: 2010-12-22
forum: Server Platforms
---

### Post by BlackDex on 2010-12-22
Hello there,

I have 2 web servers which i just did an apt-get upgrade on.
And now i get the following error back.

```
$ sudo dpkg --configure -a
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
```

What can i do to fix this problem?

---

### Post by BlackDex on 2010-12-23
bump

---

### Post by coiske on 2011-03-18
Did you ever figure this out?  Just got the same error on an upgrade, and I'm scared to reboot (lest I end up with a nonfunctional Grub).

---

