---
title: "Ubuntu removed some menu icons"
date: 2009-09-03
forum: The Cafe
---

### Post by wildman4god on 2009-09-03
in the menu bar and right click menu's some of the icons are missing this makes the menu look unfinished, I heard this was part of gnome's new policy on menu icons, but my question is why now the menu's look ugly and hacked together, boot up ubuntu 9.10 alpha 5 to see what I mean. Does anyone know if ubuntu is going to address this?

---

### Post by pastalavista on 2009-09-03
The icons may be turned off. Check gconf-editor in /desktop/gnome/interface

[Press alt-f2 and enter "gconf-editor" (no quotes) and navigate to Desktop > Gnome > Interface] Make sure the entry "menus_have_icons" is checked.

---

### Post by Tibuda on 2009-09-03
They (Gnome) have only changed the default. I like it.

> **pastalavista said:**
> The icons may be turned off. Check gconf-editor in /desktop/gnome/interface

[Press alt-f2 and enter "gconf-editor" (no quotes) and navigate to Desktop > Gnome > Interface] Make sure the entry "menus_have_icons" is checked.

Or System > Prefs > Appearence > Interface > Show menu icons.

---

### Post by wildman4god on 2009-09-03
thanks it worked. :D

---

