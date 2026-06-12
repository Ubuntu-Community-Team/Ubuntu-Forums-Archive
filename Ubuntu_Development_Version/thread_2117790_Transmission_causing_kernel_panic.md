---
title: "Transmission causing kernel panic"
date: 2013-02-19
forum: Ubuntu Development Version
---

### Post by kimr1508 on 2013-02-19
I have upgraded Xubuntu 12.10 to raring, but I experience that when starting Transmission it results in a kernel panic after some random number of minutes.

The issue only happens with kernel 3.8. If I boot with kernel 3.5 everything works fine.

I use the wl-driver for Wifi.

Has anyone else experienced this problem?


Thanks in advance,
Kim

---

### Post by dino99 on 2013-02-19
if you install transmission-dbg, then run it from the terminal to get the output logged into a .txt file; that will help to fix the issue when reporting

```
sudo transmission > panic.txt
```

---

### Post by kimr1508 on 2013-02-22
I have installed transmission-dbg and tried to run:

transmission-gtk > debug-transmission.txt (with and without sudo)

but nothing is logged to the file.

I have also updated to kernel 3.8.0-6 and created a new user for test purposes, but the kernel panic can still be reproduced.

Is there another way to log some usefull debug information? Currently my best input is a screenshot of the kernel paninc taken with my phone.


Best wishes,
Kim

---

### Post by dino99 on 2013-02-22
you can also use tee:

Example: $   ls 2>&1 | tee text.txt

---

### Post by kimr1508 on 2013-02-23
Thanks I'll try it out and do some more testing when the new kernel updates arrive.


Best wishes,
Kim

---

### Post by kimr1508 on 2013-02-24
After some searching in the bug reports on launchpad this issue might be related to the broadcom wl module and not Transmission.

There are several reports about wl causing kernel panic and system freezes:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/292450](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/292450)

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1098225](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1098225)

Hope a fix will be released since it could affect a lot of people. 


Best wishes,
Kim

---

