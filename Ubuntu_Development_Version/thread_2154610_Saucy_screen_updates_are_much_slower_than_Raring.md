---
title: "Saucy screen updates are much slower than Raring"
date: 2013-06-15
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2013-06-15
For various reasons I rarely post here now but I'm doing so as I'm not too happy with Kubuntu 13.10. I've always been able to use the development version of **Kubuntu** as my main installation since version 11.04 but for me Kubuntu 13.10 is not running too well. The degradation in performance started a couple of weeks ago.

 The PC that I'm now using has **Intel** graphics and I've upgraded from Raring and installed afresh twice using different hard drives but I'm seeing the screen updates to be very much slower compared to Raring. The difference is very noticeable when switching workspaces and resizing applications. For now I've abandoned Saucy and reverted to Raring. There have been some updates in the -proposed repository that have specifically referred to the slow updating of the display in Ubuntu/Unity but installing those hasn't helped.

   Yesterday I installed the KDE version of Fedora 18, which I later upgraded to Fedora 19 which is currently at the beta stage of development. Apart from one application which wouldn't start due to a dependency problem that will no doubt be fixed shortly I found Fedora 19 to be rock solid with the screen updating at the speed I would expect.

   Any comments? I've spent too long using Ubuntu and its various flavours to simply jump ship. I really do need to find a fix or flag a fixable bug as in just seven months time Raring's support will have ceased. :(

---

### Post by VMC on 2013-06-15
I've had video issues also. I'm using nouveau. Check you home .xsessions errors, also check "/var/log/Xorg.0.log". 
My main issue is extreme long time between boot and when a desktop is presented. I'll wait until beta before I file a log.
It appears to be improving.

---

