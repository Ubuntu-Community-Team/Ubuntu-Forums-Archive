---
title: "Gnome 3.8 jerky and choppy radeon 4250"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by DisappearingOak on 2013-03-18
Gnome 3.2 and 3.4 had acceptable performance (using 'radeon') but 3.6 had slightly jerky animations and now installing 3.8 beta from the PPA on raring, it seems it is very slow, jerky and unusable. Setting Clutter Vblank to none improves performance but still very choppy and annoying, Anyone know anything about this?

Radeon 4250 on AMD's 880g chipset

---

### Post by dino99 on 2013-03-18
if the hardware does not support 3D, then performance cant be expected.

---

### Post by DisappearingOak on 2013-03-18
The hardware and driver both are 3d acceleration enabled. it runs win 7 super fast, cinnamon and the latest unity (did have some problems with slow compiz effects before but new version is fast) run fine.  GS did run fine in 3.2 and 3.4.!! It is only the newer versions which have problems. What is happening here?

---

### Post by zika on 2013-03-18
> **DisappearingOak said:**
> Gnome 3.2 and 3.4 had acceptable performance (using 'radeon') but 3.6 had slightly jerky animations and now installing 3.8 beta from the PPA on raring, it seems it is very slow, jerky and unusable. Setting Clutter Vblank to none improves performance but still very choppy and annoying, Anyone know anything about this?

Radeon 4250 on AMD's 880g chipset
Do You, by any chance, have file /etc/X11/xorg.conf? If You do, just move it to, for example /etc/X11/xorg.conf.zika and restart X... If that does not help, simply move xorg.conf.zika back to xorg.conf...

---

### Post by DisappearingOak on 2013-03-18
Nope. no xorg.conf here. Unity running great with direct rendering enabled as glxinfo says.

---

### Post by DisappearingOak on 2013-03-27
You know. This is very frustrating. I had tested Gnome 3.7.3 and even that was running smooth. Why do they add such regressions. Setting GLAMOR acceleration helps in 3.8 but workspace bar, etc and dragging windows to workspaces is still very choppy and I still perceive some lag. This is just plain horrid.

---

