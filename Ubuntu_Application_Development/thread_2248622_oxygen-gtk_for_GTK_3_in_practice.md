---
title: "oxygen-gtk for GTK 3 in practice"
date: 2014-10-15
forum: Ubuntu Application Development
---

### Post by red_hax0r on 2014-10-15
I don't know if anyone else has noticed this, but the Gtk 3 oxygen-gtk theme makes the statusbar too large in KDE.  The Gtk 2 oxygen-gtk looks fine with KDE.  This has been a problem for at least a few years.  I've noticed this developing in PyGObject and in C.  I don't how to edit themes, but I don't know what difference it would make since my program would be distributed on different computers.  This looks like just another reason not to use gtk+ for my projects anymore.  

Gtk 3 theme:
[IMG]http://i47.photobucket.com/albums/f166/red_hax0r/gtk3-kde_zpsebf64ae7.png[/IMG]

Gtk 2 theme:
[IMG]http://i47.photobucket.com/albums/f166/red_hax0r/gtk2-kde_zpsae7e6f40.png[/IMG]


Note:
The code is exactly the same for both except for the modules used.

Edit: I tried other themes with the same result. Just noticed it in the image comparison, but it looks all widgets are affected.  Perhaps this is a new padding feature of Gtk 3 I am unaware of?  Must be KDE related because the usual styles in GNOME don't do that.

---

