---
title: "Ubuntu Mate Top Panel Icon Sizes"
date: 2015-07-02
forum: Ubuntu Development Version
---

### Post by Alan F on 2015-07-02
Ubuntu Mate 15.10, fully undated with Marco Window Manager.

See attached screenshot showing top left corner of screen. The top panel size is set to minimum (24).

To my eyes the added Application shortcut icons are too big and spaced too close together. I have hunted throughout the system and dconf to try to find out how to make these smaller and spaced further apart, to no avail.

Is this possible? Can anyone help?

---

### Post by kerry_s on 2015-07-02
if you look in the icons, you'll see like 16,22,24,32,etc...
so using a 24 pixel panel is most likely using a 24 size icon, try making the panel 25 or 26 for extra spacing. you could also go into the launcher properties & manually select the icon, that way you get the size you want. you could also try selecting a svg icon which can scale to any size.
you can use separators for between the icons for space.

i'm not currently using mate, i just installed something else today(elementary os). i used the osx(Cupertino? in 15.10, it was eleven in 15.04) type setup in mate tweak on mine. eventually i just swapped to xfce4-panel.

---

