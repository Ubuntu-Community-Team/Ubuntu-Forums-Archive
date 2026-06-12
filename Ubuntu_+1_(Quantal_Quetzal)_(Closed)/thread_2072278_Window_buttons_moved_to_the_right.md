---
title: "Window buttons moved to the right"
date: 2012-10-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ocwo92 on 2012-10-17
I couldn't wait until Quantal was out of the last beta so I installed it. Beyond an nVidia glitch, I have only one problem: the window buttons (minimize, maximize, and close) have moved back to the right hand side of the window, and I can't get them moved to the left.

I've tried with ubuntu-tweaks, and I've tried to enter "close,minimize,maximize:" in the "button_layout" field in gconf-editor's apps/metacity/general tab, but to no avail.

How do I move the buttons back to the left hand side?

---

### Post by mc4man on 2012-10-17
You can read thru here (gconf is on the way out
[http://ubuntuforums.org/showthread.php?p=12294114#post12294114](http://ubuntuforums.org/showthread.php?p=12294114#post12294114)

---

### Post by stinkeye on 2012-10-17
...or in terminal
```
gsettings set org.gnome.desktop.wm.preferences button-layout close,minimize,maximize
```

---

### Post by ocwo92 on 2012-10-17
> **mc4man said:**
> (gconf is on the way out

Yes, that solved my problem (well, actually I used the terminal version in the second reply).

I was already a bit skeptical of dconf to begin with when I realized that gconf-editor has been uninstalled during the upgrade.

---

