---
title: "LibAdwaita and GTK4 themes support"
date: 2022-04-11
forum: Ubuntu, Linux and OS Chat
---

### Post by tea for one on 2022-04-11
If you are aware of the contretemps concerning the use of themes in future versions of Gnome, you may be interested in this [https://www.gnome-look.org/p/1214931](https://www.gnome-look.org/p/1214931)
Not only does the theme support libadwaita and gtk4, it also allows the user to create their own accent colour and the text highlighted by the accent colour.

The script (generate-color-theme) on the website will need three packages which may not be automatically installed.
[LIST]
[*]inkscape
[*]optipng
[*]sassc
[/LIST]
I&#8217;ve installed the package and played around with the theme generator while testing Ubuntu 22.04 with Gnome 42.
It looks like a promising development.

---

### Post by Claus7 on 2022-04-20
Hello,

very interesting: I wanted to change the headerbars of gtk4 applications, in order to be close with the rest of the non gtk4 apps of the theme chosen. Checking this link of yours I was able to find out that I could copy the gtk.css file (and optionally assets folder) from a desired theme, change the @define-color headerbar_bg_color from the gkt.css file and place it under the folder /home/*username*/.config/gtk-4.0. The changes take place immediately.

Regards!

---

