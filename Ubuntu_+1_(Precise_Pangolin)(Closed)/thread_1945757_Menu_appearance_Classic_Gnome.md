---
title: "Menu appearance Classic Gnome"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Abandon on 2012-03-23
There is a difference in using Classic Gnome and Classic Gnome with effects. 

Without effects the menu looks good (screenshot 1)

[IMG]http://www.linuxweblogs.nl/Screenshot1.png[/IMG]

Classic Gnome with compzit gives a grey version of the menu

[IMG]http://www.linuxweblogs.nl/Screenshot2.png[/IMG]

You are looking at the Dutch translation for Applications | Locations

How do I get the good looking version (like Classic Gnome without compiz) in Classic Gnome with compiz?

---

### Post by mdurham on 2012-03-23
> You are looking at the Dutch translation for Applications | Locations
I don't have this entry, where exactly is it?

---

### Post by screaminj3sus on 2012-03-23
I noticed the same thing. Gnome classic (no compiz) looks fine, but with compiz the applications and places menu have the ugly grey text.

---

### Post by tista on 2012-03-23
> **Abandon said:**
> There is a difference in using Classic Gnome and Classic Gnome with effects. 

Without effects the menu looks good (screenshot 1)

[IMG]http://www.linuxweblogs.nl/Screenshot1.png[/IMG]

Classic Gnome with compzit gives a grey version of the menu

[IMG]http://www.linuxweblogs.nl/Screenshot2.png[/IMG]

You are looking at the Dutch translation for Applications | Locations

How do I get the good looking version (like Classic Gnome without compiz) in Classic Gnome with compiz?

Hi Abandon.

This seems a metacity bug...
Yeah metacity has only "minimal" compositor especially on panel appearances, so Compiz, Mutter, and any other truly "3D compositors" could improve exact theming on gtk3 for panel you know. ;) In other words, Metacity shows "wrong" foreground colour on it...

If you want to change this appearance, hack this file:
```
/usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css
```

Maybe Mutter would make sense to show correct appearances on gtk3 theming, so please check it out on mutter session as well...

Regards,
Tista.

---

### Post by screaminj3sus on 2012-03-24
This doesn't seem to be the only issue with gnome session with compiz enabled. The bottom panel themeing is messed up too (it looks fine with the no effects session).

I searched for a bug on this but didn't find anything (could just be me being horrible at searching :p) so I went ahead and created one:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/963908](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/963908)

---

