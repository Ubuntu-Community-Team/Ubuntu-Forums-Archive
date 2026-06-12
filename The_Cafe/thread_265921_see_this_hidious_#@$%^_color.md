---
title: "see this hidious #@$%^ color?"
date: 2006-09-26
forum: The Cafe
---

### Post by fuscia on 2006-09-26
[[IMG]http://img180.imageshack.us/img180/552/hidiousow6.th.jpg[/IMG]](http://img180.imageshack.us/my.php?image=hidiousow6.jpg)

how do i change it? i can change it by using different themes in gnome, kde and xfce, but in something like openbox, i don't know how to do it. gtk-theme-switch does *not* do it. who picked this color?](*,)

edit: i'm talking about that light gray that one might use to paint a hospital room.

---

### Post by K.Mandla on 2006-09-26
I've been using the [murrine configurator]("http://cimi.netsons.org/pages/murrine.php") to change the color schemes on those awful things. I also use the theme pack he has for download, either there or at gnome-look.org.

That is the only downside of openbox -- dealing with those ghastly color changes.

Also, are you starting gtk-theme-switch with *switch2*?

---

### Post by ComplexNumber on 2006-09-26
**fuscia**
do you have this file in your home directory:
.gtkrc-1.2-gnome2.

it should have a line in it like this:
include "/home/your-username/.themes/Bluecurve/gtk/gtkrc"

---

### Post by Kindred on 2006-09-26
That colour changes with the theme for me (I use gtk-chtheme), or in .gtkrc-2.0 which gtk-chtheme writes to.  Not sure what else to say...

---

### Post by IYY on 2006-09-26
gtk-theme-switch is for GTK1, gtk-theme-switch2 is for GTK2, which is what this app is. Anyway, it's easier to just run gnome-settings-daemon on startup and have all the Gnome settings work.

---

### Post by fuscia on 2006-09-26
a-bi, this is what i found...

[quote=".gtkrc-1.2-gnome2"]# Autowritten by gnome-settings-daemon. Do not edit

include "/home/fuscia/.gtkrc.mine"[/quote]

...which leads us to what IYY was saying...leaving me wondering "wtf are they talking about???" i am sooooooooooo f lost.

---

### Post by fuscia on 2006-09-26
> **Kindred said:**
> That colour changes with the theme for me (I use gtk-chtheme), or in .gtkrc-2.0 which gtk-chtheme writes to.  Not sure what else to say...

please accept this token of my gratitude...

[img]http://blantonsbourbon.com/CMS/images/stories/tasting.jpg[/img]


thanks to all for your help.

---

