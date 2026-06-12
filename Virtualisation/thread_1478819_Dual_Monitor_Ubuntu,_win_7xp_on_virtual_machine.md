---
title: "Dual Monitor Ubuntu, win 7/xp on virtual machine"
date: 2010-05-10
forum: Virtualisation
---

### Post by Prust on 2010-05-10
Hi,

     I've some graphical issues when using my vmware (player) installation. I'm working with CAD software on office pc and also sometimes on my personal notebook (If matters to giving some advices/tips).

     I get enough performance on notebook but on my office pc (which I'm using dual monitor and w/compiz) I can't solve lagging or flashing display issue. Specially when open my ArchiCAD... I've thought it was some OpenGL problems, and focus on display setting "Acceleration 3D", define 1 monitor and enough resolution etc.
     I try both of xp and 7, then i get much succesful results in xp

     I used VirtualBox first but I guess Vmware's OpenGL support is better. But vm software doesnt matter for me and I've only need use my ArchiCAD. Neither dual boot, nor Wine is my options, so i really appreciate your advices

thanks in advance...

_My Specs:
Q8400 Quad Core, Ati HD 4870, 2x2GB Kigston DDR2...

---

### Post by BobVila on 2010-05-11
> **Prust said:**
> Hi,

     I've some graphical issues when using my vmware (player) installation. I'm working with CAD software on office pc and also sometimes on my personal notebook (If matters to giving some advices/tips).

     I get enough performance on notebook but on my office pc (which I'm using dual monitor and w/compiz) I can't solve lagging or flashing display issue. Specially when open my ArchiCAD... I've thought it was some OpenGL problems, and focus on display setting "Acceleration 3D", define 1 monitor and enough resolution etc.
     I try both of xp and 7, then i get much succesful results in xp

     I used VirtualBox first but I guess Vmware's OpenGL support is better. But vm software doesnt matter for me and I've only need use my ArchiCAD. Neither dual boot, nor Wine is my options, so i really appreciate your advices

thanks in advance...

_My Specs:
Q8400 Quad Core, Ati HD 4870, 2x2GB Kigston DDR2...

If you're still using virtualbox, install the Guest Additions in Safe Mode. (3d acceleration only works on 32-bit guests). Also, I had abysmal Windows VM performance until I updated to a 2.6.32 kernel.

---

### Post by Prust on 2010-05-12
> **BobVila said:**
> If you're still using virtualbox, install the Guest Additions in Safe Mode. (3d acceleration only works on 32-bit guests). Also, I had abysmal Windows VM performance until I updated to a 2.6.32 kernel.

I tried it a while ago, uninstalled it then installed it in safe mode. Without "3D acceleration" guest desktop not lags much but in ArchiCAD results nearly same. I'm still using 2.6.31 and my ubuntu is 32bit therefore for my guest i choose 32 bit versions of XP/7.

Also I thought vmware's display support is better than vbox but eventualy faster one enough for me

---

