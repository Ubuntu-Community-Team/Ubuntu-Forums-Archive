---
title: "Nautilus: sets it's own window placement"
date: 2017-05-28
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-05-28
In comparison to every other app which uses the window manager.

Every time nautilus closes it writes a custom window placement geometry to dconf. (based on position at close.
 There is an option to use the "Default" value which seems to use the wm. However this only works one time per set/reset, when nautilus is closed it  writes a custom (current value) again.

---

### Post by Frogs Hair on 2017-05-28
Are you using Gnome or Unity ? I'm in Gnome Wayland at the moment and Nautilus opens in the top left corner no matter where it's closed .

Edit: In Unity,Nautilus opens in the last location used as you described.

---

