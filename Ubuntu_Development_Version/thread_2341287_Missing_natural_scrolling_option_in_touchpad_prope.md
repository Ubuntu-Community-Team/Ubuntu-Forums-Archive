---
title: "Missing natural scrolling option in touchpad properties"
date: 2016-10-26
forum: Ubuntu Development Version
---

### Post by Yahoé on 2016-10-26
Hello all,

I don't know if this is related to using zesty, but the natural scrolling option has disappeared from the touchpad properties and I have lost system-wide natural scrolling, quite annoying.

xinput list-props returns:

libinput Natural Scrolling Enabled (274):    0
libinput Natural Scrolling Enabled Default (275):    0

Any easy fix?

---

### Post by jbicha on 2016-10-26
Please file a bug. I think that issue affects Ubuntu 16.10 also. If you're using Unity, I recommend

```
ubuntu-bug unity-control-center
```

---

### Post by jbicha on 2016-10-26
As a workaround, install dconf-editor and look in /org/gnome/desktop/peripherals/touchpad and /mouse

Note that unity-control-center currently uses the older /org/gnome/desktop/peripherals/touchpad **scroll-method** and ignores these newer settings: edge-scrolling-enabeld, natural-scroll. two-finger-scrolling-enabled. GNOME does the opposite.

---

### Post by jbicha on 2016-10-26
Hmm, maybe this is the old [bug 1132063]("https://launchpad.net/bugs/1132063") .

---

### Post by mc4man on 2016-10-26
> **Yahoé said:**
> 
xinput list-props returns:

libinput Natural Scrolling Enabled (274):    0
libinput Natural Scrolling Enabled Default (275):    0

Any easy fix?
Well by default _Ubuntu_ wouldn't be using libinput yet (thru xserver-xorg-input), still on synaptics
Did you manually switch to xserver-xorg-input-libinput or by some other means?

If so maybe try removing it & installing xserver-xorg-input-synaptics & a reboot

---

### Post by mc4man on 2016-10-28
It  does  appear Ubuntu-Gnome went to xserver-xorg-input-libinput which apparently doesn't work well with dconf settings & likely System Settings is neutered. (gnome mantra of limit things they know better than mere users..
One could try to alter thru conf files or just return to xserver-xorg-input-synaptics
(hopefully Ubuntu doesn't move to libinput unless it becomes user gui serviceable

info, ect.
[https://wiki.archlinux.org/index.php/Libinput](https://wiki.archlinux.org/index.php/Libinput)
Though another missing/ignored option, same idea...
[https://ask.fedoraproject.org/en/question/89443/how-to-enable-touchpad-edge-scrolling/](https://ask.fedoraproject.org/en/question/89443/how-to-enable-touchpad-edge-scrolling/)

---

### Post by Yahoé on 2016-11-03
Somehow I found xserver-xorg-input-libinput installed! Removed it.

---

### Post by Yahoé on 2016-11-03
> **Yahoé said:**
> Somehow I found xserver-xorg-input-libinput installed! Removed it.

I ended up not removing xserver-xorg-input-libinput because that wouild have also removed xserver-xorg-input-all
I took the dconf-editor approach where in /org/gnome/desktop/peripherals/mouse I set Natural scrolling to True (it was already done for the touchpad).
It all seems fixed now

---

