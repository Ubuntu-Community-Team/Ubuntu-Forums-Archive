---
title: "Gnome 3 themes (no Gnome tweak)"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by forcecore on 2012-03-19
Is there some more themes that can be installed and will appear on Appearance selection on 12.04.

---

### Post by forcecore on 2012-04-04
Currently looks like only Gnome 3 official theme that appears in theme selection, anyone knows more themes for 12.04 that can work without Tweak Tool? Just like 11.04 and before that native theme selection worked.

---

### Post by jbicha on 2012-04-04
The theme switcher in System Settings is hard-coded to only support Ambiance, Radiance, Adwaita (included in gnome-themes-standard), and GNOME's accessibility themes (low, high, and high contrast-inverse).

---

### Post by forcecore on 2012-04-04
I am quite confused that why it is hardcoded, does it ever become dynamic like Gnome2 switcher was that did list and changed new installed themes?

---

### Post by jbicha on 2012-04-04
The code is a bit complicated since we're trying to keep the theme switching interface simple. Every GTK3 theme in the Ubuntu repositories should work in that dropdown, and if one doesn't (perhaps Xubuntu's  or Lubuntu's ?), then that's a bug and it's easy to fix.

Of course, merge requests are always welcome.

---

