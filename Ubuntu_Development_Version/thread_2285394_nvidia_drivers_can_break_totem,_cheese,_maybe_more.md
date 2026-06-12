---
title: "nvidia drivers can break totem, cheese, maybe more.."
date: 2015-07-05
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-07-05
Seen while using nvidia drivers on a **mobile** gpu (GT 755M), no clue if it affects desktop cards.
(- tmp workaround is setting an env of CLUTTER_BACKEND=x11
[https://bugs.launchpad.net/ubuntu/+source/clutter-1.0/+bug/1471586](https://bugs.launchpad.net/ubuntu/+source/clutter-1.0/+bug/1471586)

---

### Post by dino99 on 2015-07-06
i've received two new clutter files (1.6.2-1) which now let totem opening without error; but got other troubles: nautilus now makes gnome-shell crashing each time you try switching to an other workplace. So the apps using clutter seems needing a rebuilt.

---

### Post by ventrical on 2015-07-06
There are issues with cheese/nvidia and unity.

```

Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)

```

---

