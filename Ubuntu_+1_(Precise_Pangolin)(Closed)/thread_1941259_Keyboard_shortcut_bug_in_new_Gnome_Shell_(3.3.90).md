---
title: "Keyboard shortcut bug in new Gnome Shell (3.3.90)"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-03-15
I can't seem to get any key combo to work for minimizing all windows. Is anyone else having this issue?

[edit: can't get a key combo to launch terminal either, but Alt-F2 works for running a program. Those are really the only ones I use.]

---

### Post by jbicha on 2012-03-15
I can fix the Ctrl+Alt+T bug as that's just setting a default value (Ctrl+Alt+T won't open the terminal in upstream GNOME or Fedora, etc.)

Unfortunately, Ubuntu's keyboard shortcuts panel in System Settings currently only sets the gconf shortcuts, but GNOME Shell 3.4 uses gsettings. You can use dconf-editor to manually set them. Look in org.gnome.desktop.wm.keybindings.

---

