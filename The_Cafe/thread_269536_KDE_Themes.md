---
title: "KDE Themes"
date: 2006-10-01
forum: The Cafe
---

### Post by Pyro MX on 2006-10-01
My question is simple: How can I make KDE or GNOME theme? Do you have any good tutorials about KDE and GNOME theming? I have been searching the web for a while and it seems I'm plain unlucky, either I find outdated files or... nothing. If you have anyhting, it would be nice! Thanks!:)

More KDE than GNOME (found a couple of things on GNOME, but nothing on KDE)

---

### Post by Bloodfen Razormaw on 2006-10-01
KDE themes are really Qt themes.  Read Trolltech's Qt documentation for that.  They are shared libraries that are loaded by Qt, and such you have all the the power you want.  Themes are only KDE-specific if you use functions from kdelibs in your code.  To load the Qt theme you can use KControl or qtconfig.

GNOME themes, likewise, are really GTK+ themes, which are, just like Qt, shared libraries.  You program them, compile them, and so on.  The one major difference between Qt and GTK+ themes is terminology.  In GTK+, the above is called a theme *engine*.  The theme itself is a gtkrc file that will tell GTK+ what theme engine to use, and also what colors to use (this is responsible for the misconception on this forum that KDE themes are harder to install than GNOME themes, since the GNOME themes on gnome-look.org are really just different color schemes for theme engines you must already have installed; KDE does color configuration separately from the theme).

[http://doc.trolltech.com/](http://doc.trolltech.com/)
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)
(The easiest way though is to start with a common theme and modify it; this is how many common themes are created.)

---

### Post by Pyro MX on 2006-10-01
Thanks! I'll check that out!

---

### Post by mcduck on 2006-10-02
> **Bloodfen Razormaw said:**
>  In GTK+, the above is called a theme *engine*.  The theme itself is a gtkrc file that will tell GTK+ what theme engine to use, and also what colors to use (this is responsible for the misconception on this forum that KDE themes are harder to install than GNOME themes, since the GNOME themes on gnome-look.org are really just different color schemes for theme engines you must already have installed; KDE does color configuration separately from the theme).
well, actually you can do far more than just decide the colors when doing a gtkrc file to make a GTK theme. Depending on the engine(s) you choose to use, you can at least configure sizes and spacings of elements and widgets, and often you also have some choises for different styles of widgets and menus etc..

And then there's engines like pixmap, that let you use whatever pictures you have to build your theme. 

So even if you don't make your own GTK engine, gtk themes are more than just color schemes for the same theme.

---

### Post by ComplexNumber on 2006-10-02
> My question is simple: How can I make KDE or GNOME theme? Do you have any good tutorials about KDE and GNOME theming? I have been searching the web for a while and it seems I'm plain unlucky, either I find outdated files or... nothing. If you have anyhting, it would be nice! Thanks!
there are lots of tutorials and links to tutorials about gnome theming here:
[http://gnomethemes.org/forum/](http://gnomethemes.org/forum/)


i don't know if there are any good kde theming tutorials for kde/qt. the only one i could find dates back to 2001, so its somewhat out of date lol:
[http://dot.kde.org/987013890/](http://dot.kde.org/987013890/)
good luck.




[quote=Bloodfen Razormaw]this is responsible for the misconception on this forum that KDE themes are harder to install than GNOME themes, since the GNOME themes on gnome-look.org are really just different color schemes for theme engines you must already have installed; KDE does color configuration separately from the theme[/quote]
thats total tripe. its not where the misconception is. there is no miconception at all. kde themes ARE much harder to install...and thats a fact. 
in gnome, the icons go in /usr/share/icons(or /home/username/themes)  and the themes go in /usr/share/themes(or /home/username/.themes). the only thing whcih needs compiling are the engines, and they go in /usr/lib/gtk-2.0/engines. all thats necessry is untarring the tarballs and placing them in their respective locations. as mcduck says, the gtkrc file does a lot more than control the colour scheme, they also control widget size/placements/features etc.

in kde, everything is spread out all over the place, and the styles and many of the win decs need compiling (many of which fail to compile). there are several components to a kde 'theme' - the kth file(its actually a compression file) which is the equivelent of the index.theme and gtkrc file in gnome. this specifies what icons, style, windecs, colour scheme, and screensaver to use for a particular theme, together with specifying the widgets features/size/placements/etc. the styles are the equivelent of gnome's theme-engines.  the styles go in /usr/share/apps/kstyle/themes, usr/lib/kde3, and usr/lib/qt-3.3/plugins/styles. the windecs are the equivelent of metacity theme. then theres the colour scheme.

---

