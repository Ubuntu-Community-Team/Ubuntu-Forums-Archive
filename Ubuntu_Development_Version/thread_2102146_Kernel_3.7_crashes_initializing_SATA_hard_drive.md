---
title: "Kernel 3.7 crashes initializing SATA hard drive"
date: 2013-01-06
forum: Ubuntu Development Version
---

### Post by kyleabaker on 2013-01-06
I've noticed for some time now that I was unable to boot successfully using Kernel 3.7. My system hard drive is connected via IDE, whereas my extra internal is connected via SATA.

Out of luck, I attempted to boot into Kernel 3.7 while my extra (SATA, EXT 3, 1 TB) hard drive was disconnected and it booted successfully. I've confirmed by connecting the hard drive that it fails.

With the hard drive connected, the latest Kernel I'm about to use is Kernel 3.5. I'd like to resolve the issue. Where should I begin looking? How can I obtain the full logs from an unsuccessful boot?

Thanks!

EDIT:
I'm seeing the same thing that **fdm** is seeing [here](http://ubuntuforums.org/showthread.php?t=2085789&page=4) (but that thread isn't specific to the issue).

---

### Post by ronacc on 2013-01-06
since I have a mixed system both ide and sata internal drives I have been unable to boot ANY 3.6 or 3.7 kernel ( 3.8rc1 works good ) , it seems that the system is freezing BEFORE logging is started , I never get any log files from failed boots , only successful ones with either 3.5 or 3.8 kernels .

---

### Post by kyleabaker on 2013-01-06
You're suggesting that this issue is resolved with Kernel 3.8? Will 3.8 be the default for Ubuntu 13.04?

---

### Post by ronacc on 2013-01-06
3.8 resolves it for me (and others with the same problem ) see here [http://ubuntuforums.org/showthread.php?t=2097058](http://ubuntuforums.org/showthread.php?t=2097058) . . 3.8 is supposed to be the kernel for raring release I believe .

---

