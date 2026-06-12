---
title: "LightDM and Ubuntu Unity Greeter don't load with GRSecurity and PaX Linux kernel"
date: 2013-07-03
forum: Security
---

### Post by Leslie Dorner on 2013-07-03
I downloaded a vanilla Linux kernel 3.2.47 amd64 and I downloaded the GRSecurity Linux kernel patch for this specific version. I followed Insanity Bit's guide: 1. [http://www.insanitybit.com/2012/05/31/compile-and-patch-your-own-secure-linux-kernel-with-pax-and-grsecurity/](http://www.insanitybit.com/2012/05/31/compile-and-patch-your-own-secure-linux-kernel-with-pax-and-grsecurity/). I did not check partially restrict all non-root users in GRSecurity and I did not check restrict mprotect() in PaX. I saved my custom configuration settings and I compiled my Linux kernel 3.2.47 amd64. Then, I installed it. I was able to boot into the GRSecurity Linux kernel, but I get a low graphics mode warning and I can't select to drop into a shell in the menu system. So, I type CTRL + ALT + F2 to get TTY2 and I log in using my Administrator account. Then, I type sudo service lightdm restart. I get the Ubuntu Unity Greeter and LightDM works properly. I log in normally and I'm in Ubuntu Unity. I type CTRL + ALT + F2 and I log out of TTY2. I press CTRL + ALT + F7 and I resume using Ubuntu Unity.

How do I fix this problem so that when I select the GRSecurity Linux kernel, I can boot directly to the Ubuntu Unity Greeter and log in normally?

Thanks.

---

