---
title: "Gnome-Panel is spamming syslog with Y-axis alllocation mismatches on Gnome Flashback"
date: 2018-08-08
forum: Ubuntu Development Version
---

### Post by Smask on 2018-08-08
I'm seeing lot of these:

```
gnome-panel[2799]: gtk_widget_size_allocate(): attempt to underallocate [COLOR=#00ff00]GtkMenuBar[/COLOR]'s child [COLOR=#00ff00]GtkMenuItem[/COLOR] 0x[COLOR=#40e0d0]55f712bd64d0[/COLOR]. Allocation is [COLOR=#ff0000]161x24[/COLOR], but minimum required size is [COLOR=#ff0000]161x29[/COLOR].
```

Repeat this line with different contents where coloured.

I guess I'll experience glitches like these during the Gnome 3.28 to 3.30 transition period. And yes, I've got proposed enabled.

---

### Post by muktupavels on 2018-08-10
That is bug / problem in gnome-panel! Please report it here - [https://gitlab.gnome.org/GNOME/gnome-panel/issues](https://gitlab.gnome.org/GNOME/gnome-panel/issues).

---

### Post by Smask on 2018-09-14
Marking this problem as solved since gnome-panel upgraded to v3.30

---

