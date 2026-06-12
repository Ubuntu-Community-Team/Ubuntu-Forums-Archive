---
title: "gtkperf in precise testing multiple DE's"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by buzzmandt on 2012-04-07
laptop 2.4 ghz amd64 bit, 4 gig ram, intel graphics

Just for those who are curious, like I was.  The lower the number the better/faster gtkperf finished.

KDE kwin no effects 13.01
KDE kwin full effects 19.76
Gnome (gnome-shell) 13.11
Gnome Classic with effects 15.52
Gnome Classic w/out effects 8.97
Openbox 6.17
Ubuntu Unity 3d 18.76
Ubuntu Unity 2d 14.03


Just out of curiousity ran DDO under openbox and it was very fast but it's not the de (wm) for me lol

I've always been a fan of kde but always turn off effects before starting any games.  I've been playing with all these sessions looking for something new, unity seems a bit sluggish to me still, even more so than kde with effects.  I'm sure they'll improve on that.  Still trying to figure out how to make icons in g-shell on the desktop without logging into gnome classic to do so lol.  for now i'm still DE hopping lol

---

### Post by lucazade on 2012-04-07
> **buzzmandt said:**
> laptop 2.4 ghz amd64 bit, 4 gig ram, intel graphics

Just for those who are curious, like I was.  The lower the number the better/faster gtkperf finished.

KDE kwin no effects 13.01
KDE kwin full effects 19.76
Gnome (gnome-shell) 13.11
Gnome Classic with effects 15.52
Gnome Classic w/out effects 8.97
Openbox 6.17
Ubuntu Unity 3d 18.76
Ubuntu Unity 2d 14.03


Just out of curiousity ran DDO under openbox and it was very fast but it's not the de (wm) for me lol

I've always been a fan of kde but always turn off effects before starting any games.  I've been playing with all these sessions looking for something new, unity seems a bit sluggish to me still, even more so than kde with effects.  I'm sure they'll improve on that.  Still trying to figure out how to make icons in g-shell on the desktop without logging into gnome classic to do so lol.  for now i'm still DE hopping lol

gtkperf was not updated to gtk3 so these results are no more so significant...
it would be interesting to know how the combination of gtk3 stack / unico gtk3 engine / light-themes and the DE in use perform.

---

### Post by fjgaude on 2012-04-07
Just add a data point or two using gtkperf:

Unity 3D : 4.76
Unity 2D : 3.56

Running low-power Sandy Bridge Intel CPU (2.5GHz to 3.6GHz) as shown in my signature, 8GB SDRAM at 2133MHz, Corsair SSD.

Over the last year my box has gone from about 12 under Unity 3D now down to 4.76 sec. It's fast simply using the integrated CPU graphics.

Whether gtkperf has been updated or not I'm satisfied with the video quickness and likely the Intel drivers.

---

### Post by zika on 2012-04-07
And the fastest (at my place) FluxBox... ;)
Faster (even) than OpenBox...

Update:
I've got a sort of puzzling result:
(Measured in FluxBox, both through LighDM and startx)
If I put /etc/X11/xorg.conf as simple as:```
:~$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection
```I get gtkperf score ~6.8.
If there is no xorg.conf in /etc/X11 I get score of ~4.2...

---

