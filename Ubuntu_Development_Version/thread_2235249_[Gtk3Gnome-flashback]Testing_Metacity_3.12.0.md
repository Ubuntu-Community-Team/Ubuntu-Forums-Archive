---
title: "[Gtk3/Gnome-flashback]Testing Metacity 3.12.0"
date: 2014-07-19
forum: Ubuntu Development Version
---

### Post by tista on 2014-07-19
Hi all flashback lovers,

I've uploaded metacity-3.12.0 to my ppa:
[Lazulum PPA]("https://launchpad.net/~tista/+archive/ubuntu/lazulum?field.series_filter=utopic")
This is based on the Gnome Git codebases:
[https://git.gnome.org/browse/metacity/log/]("https://git.gnome.org/browse/metacity/log/")

[[img]http://s24.postimg.org/cu5n74v1d/Screenshot_from_2014_07_20_09_37_14.jpg[/img]](http://postimg.org/image/cu5n74v1d/)

And now I'm testing it with some visual enhancement patches... Still it would lead rendering performance degradations a bit compared with Gtk2 old one, but I suppose it would be acceptable in daily use.;)

My patchworks:
**#1. Expose drop-shadow beneath Gnome-Panel**
I really want this feature whenever theme designers want to employ a 'gradation' panel surface, and even if it was rendered with 'flat-colored' surface. This patch might cause misleadings in some other "dock" states, but metacity already has new state "HAVE_SHADOW".

**#2. Stop ugly gray start-up fullscreen**
It sometimes might be nice, for example, when kicking metacity after Gnome3 plymouth theme was shown. But the others, it would be so ugly appearance. 

**#3. HUD style Alt-Tab popup**
In case of Gnome-Shell, it was rendered as semi-transparent HUD style and I like that. It would be eye-friendly in both cases that Gtk3 theming had a light background or dark one.
[[img]http://s18.postimg.org/9qzoqhpsl/Screenshot_from_2014_07_06_16_13_45_2.jpg[/img]](http://postimg.org/image/9qzoqhpsl/)

Native code changes:
**#1. Stop exposing 'window-preview' on tab-popup**
Because of codes of cairo/gtk3, metacity 3.12 decided to stop showing window-preview thumbnails on Alt-Tab popup. Today popup was shown with only Icons and Apps Title. I could succeed to revive those thumbnails with some patches, but it makes slower so much to show it up, so I purged that patch.

Anyway I wish Utopic had metacity 3.12 as a stock... ;)

Best Regards,
Tista

---

### Post by muktupavels on 2014-07-20
Window preview in tab-popup was changed to icon preview two month after 2.34.13 release. It was not part of porting to GTK+ 3.

Metacity 3.12 most likely will be available in Utopic, but that will cause problems. When metacity will be available then gtk-window-decorator (from compiz) will lose metacity theme support falling back to cairo theme. To restore theme support gtk-window-decorator must be ported to GTK+ 3.

---

### Post by tista on 2014-07-20
Thanks Alberts for your correct info !! :)

Then I didn't know that problem of compiz because I had not been using compiz for many years, and I'm not sure those devs could solve to port Gtk3 into gtk-window-decorator or not, so should I file the wishlist to launchpad untill feature-freeze has come?

Best Regards,
Tista

---

### Post by muktupavels on 2014-07-20
I have started work on GTK+ 3 port for gtk-window-decorator. So I think there is no need to create wishlist in launchpad.

---

