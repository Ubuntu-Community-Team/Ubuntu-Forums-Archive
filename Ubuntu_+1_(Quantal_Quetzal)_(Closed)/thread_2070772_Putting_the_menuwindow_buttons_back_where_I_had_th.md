---
title: "Putting the menu/window buttons back where I had them in 12.04."
date: 2012-10-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Sslaxx on 2012-10-13
12.10's GNOME fallback session has overwritten my changes to the window min/max/close buttons (putting them back to the left Mac-style) and this time it doesn't seem to be a Metacity key (the key it still there in Metacity).

Is there any way to change this?

---

### Post by mc4man on 2012-10-13
In dconf-editor > org.gnome.desktop.wm.preferences
It will appear to be set as you want but it's being overridden. So set to something else then reset to how you want.
Note that the "Set to Default" & 'Default:" are Not the same in use

Screen 1 - as normally seen
Screen 2 - after resetting off, then back to above

---

### Post by kprowell on 2012-10-16
Thanks!  That helped me a lot?  Question...  I know this isn't entirely a new thing (using dconf) but this looks a lot like a registry to me and that is a nightmare in Windows.

---

