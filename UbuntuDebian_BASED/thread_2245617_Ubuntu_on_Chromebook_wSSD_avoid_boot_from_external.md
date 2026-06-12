---
title: "Ubuntu on Chromebook w/SSD: avoid boot from external HDD"
date: 2014-09-24
forum: Ubuntu/Debian BASED
---

### Post by jbeale on 2014-09-24
I just got a new Acer C720 Chromebook with 32 GB SSD, and installed chrubuntu. 
```
user@chrubuntu:~$ uname -a
Linux chrubuntu 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

I have connected an external USB HDD for additional storage space. When I reboot the system, first I have to type CTRL-L to start the Ubuntu boot, and then it tries to boot from the external drive (which is not bootable) and then it says "no boot media found", rather than trying the internal SSD.  I have to go into the boot menu and manually select the second item on the list to boot, which is the SSD.

Is there any way to avoid this manual intervention every time?

---

### Post by TheFu on 2014-09-25
Yes, but you need to void the warranty to accomplish it.  Search for how to always force legacy boot on the C720.

BTW, I have one too - but it is Ubuntu-only now. No Chrubuntu, no chromeos.

---

### Post by howefield on 2014-10-27
Thread moved to the "Ubuntu/Debian BASED" forum.

---

