---
title: "Updating vanilla kernel with Grsecurity"
date: 2016-02-15
forum: Security
---

### Post by sabina2 on 2016-02-15
Hello !

I tried to patch a vanilla kernel with Grsecurity for my Ubuntu 14.04.3 LTS lately. I installed and run 4.3.4-grsec then 4.3.5-grsec in place of my Ubuntu's 3.19.0 series. It works well but needs a few improvements with .config as it still breaks a few things while Paxtest also finds some unprotected areas. 

I am wondering how much time I can wait until I need to patch and to install a new stable vanilla kernel from kernel.org ? The last stable 4.3.5 has been released on January 31st, so 2 weeks ago. As my kernel is patched with Grsecurity, I would like to know if I must upgrade to each new 4.3.* release or if I can wait a few more weeks. I guess it also depends on the changelog (small corrections vs critical vulnerabilites) but I am not skilled enough to read and understand the changelogs. I also would like to compare how many times the 3.19.0 series is automatically updated on my Ubuntu with how many times I would need to patch, compile and install by myself a vanilla kernel in the same range of time. 

Thanks in advance !

---

### Post by sabina2 on 2016-02-16
Up !

Is this topic in the right forum, or should I post it in the Ubuntu development version forum ?

---

### Post by vince-vlara on 2016-02-19
> **sabina2 said:**
> I am wondering how much time I can wait until I need to patch and to install a new stable vanilla kernel from kernel.org ?

If you intend to keep up to date with Grsecurity you will primarily be tracking their updates and not kernel.org.

If the current Grsecurity testing patch is for kernel 4.3.5 the next one could be for 4.4.2 or something in between or after.

---

