---
title: "Wonky Window Decorations &amp; Settings in Kubuntu Dailies/Alpha2"
date: 2015-01-25
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2015-01-25
Anyone else seeing window decoration and color issues in Kubuntu 15.04? 

In the last several days straddling the Alpha2 release, every daily I've tried, as well as the Alpha2 image, shows a black panel where you would expect to see alternative window decorations. (SystemSettings->ApplicationStyle-WindowDecoration).

Window decorations also sometimes go missing, following no obvious pattern.

The Breeze decorations are blue, too.  Shouldn't they be a dark gray, or has a change happened? 

Breeze is the only option in "Look and Feel". Hope this does not mean the actual release will not offer Oxygen, as well.

(Also, is there going to be a breeze-gtk-config package to cajole GTK apps to look appropriate, as is done with the oxygen-gtk-config tools?)

---

### Post by xc3RnbFO8P on 2015-01-25
It is a mess...
this green color is from my own color scheme 008080 and getting new stuff doesn't work.

[[img]https://farm8.staticflickr.com/7417/16367165975_cbdac376b9_z.jpg[/img]](https://flic.kr/p/qWj1dP)

[[img]https://farm8.staticflickr.com/7439/16365441121_7f09afa585_z.jpg[/img]](https://flic.kr/p/qWaatX)

[[img]https://farm8.staticflickr.com/7394/16179598628_200239e6ec_z.jpg[/img]](https://flic.kr/p/qDJEZ3)

---

### Post by buzzingrobot on 2015-01-28
No change with today's (28 Jan) daily.

---

### Post by Rog131 on 2015-01-28
(at here)

**Look And Feel**

The 'Look and Feel' option needs the bit and the pieces from the Oxygen and the Breeze. The Breeze was the only option until I installed more Oxygen packages.

Installing: kde-style-oxygen-qt4, plasma-theme-oxygen, oxygen-cursor-theme

[IMG]http://i.imgur.com/p56Yyuv.jpg[/IMG]

**Black box - window decorations**

[img]http://i.imgur.com/qATjrxF.png[/img]

This seems to be a compositor/KDE system Settings problem. A workaround is to go to the 'Compositor' settings and shuffle the rendering backend.

[img]http://i.imgur.com/BxlLXGV.png[/img]

After the restart of the system settings the window decoration options are there.

[img]http://i.imgur.com/lc6rRUu.png[/img]

---

### Post by buzzingrobot on 2015-01-28
Thanks!  I think, though, I'll wait to do another physical install until the daily is using 5.2 instead of the beta. Shouldn't be long.

---

### Post by ventrical on 2015-01-30
I'm really surprised at the new touch and feel of kubuntu daily-live.

---

### Post by buzzingrobot on 2015-01-30
> **ventrical said:**
> I'm really surprised at the new touch and feel of kubuntu daily-live.

Ah! I see you have blue Breeze window decorations, too.:p  They should be dark gray. At least, they have been all along.  Selecting a new color scheme doesn't change the colors. 

The Breeze window decorations are too large -- too much depth, too slab-like -- for my tastes, so I'll be looking for a way to make them thinner. (Seems to be a trend.  I see lots of new flat themes with these oversize slab decorations.)

I like the overall design.  The default icons and the overlay line used to designate the active window in the panel don't thrill me.

---

### Post by Rog131 on 2015-01-31
**Plasma 5.2 Errata**

Known issues: [https://community.kde.org/Plasma/5.2_Errata](https://community.kde.org/Plasma/5.2_Errata)


> ...Selecting a new color scheme doesn't change the colors.

Seem to work at here.

[img]http://i.imgur.com/3n69WJV.gif[/img]


> ...The Breeze window decorations are too large -- too much depth, too slab-like -- for my tastes, so I'll be looking for a way to make them thinner.

The border size has own setting and the titlebar is following the button size.

[img]http://i.imgur.com/ce5ABon.png[/img]

---

### Post by buzzingrobot on 2015-01-31
> **Rog131 said:**
> **Plasma 5.2 Errata**

Known issues: [https://community.kde.org/Plasma/5.2_Errata](https://community.kde.org/Plasma/5.2_Errata)


Thanks. I eventually found that icon on the decoration.  At the smallest border size, the Breeze decoration is still too thick for my tastes.  The display in that panel remained flaky, as well.

Colors:  Breeze decorations turned blue after selecting an Oxygen color scheme and did not return to the dark grey on selecting a Breeze scheme.

If Oxygen returns in 5.3, or someone themes Breeze to considerably reduce the depth of the decorations, I'll take another look.

---

### Post by marco-parillo on 2015-02-01
I saw [this]("https://www.kubuntuforums.net/showthread.php?67338-Window-decorations-in-Kubuntu-15-04-Alpha-and-Plasma-5-5-2") on KFN

> [h=2]Window decorations in Kubuntu 15.04 Alpha and Plasma 5 [5.2][/h][COLOR=#000000][FONT=sans-serif][INDENT]It seems that the recent update of Kubuntu 15.04 Alpha 2 broke window decorations for some (including me):

[http://askubuntu.com/questions/57634...rations/580290]("http://askubuntu.com/questions/576340/kde-plasma-5-upgrade-has-removed-my-window-decorations/580290")

I fixed like this:

[FONT=monospace]$ sudo dpkg-reconfigure kwin
dpkg-reconfigure: kwin is broken or not fully installed
$ sudo apt-get install kwin
....[/FONT]

And probably Kubuntu 15.04 Beta will fix it too.

BTW, congrats on Plasma 5. It's amazing.[/INDENT]
[/FONT][/COLOR]


---

### Post by Rog131 on 2015-02-04
Earlier:

> (Also, is there going to be a breeze-gtk-config package to cajole GTK apps to look appropriate, as is done with the oxygen-gtk-config tools?)

Maybe - maybe not:  Bug 343555 - Breeze support for gtk2 and gtk3 - [https://bugs.kde.org/show_bug.cgi?id=343555](https://bugs.kde.org/show_bug.cgi?id=343555)


About the Breeze window decoration 'tallnes': Breeze windec wastes vertical space - [https://forum.kde.org/viewtopic.php?f=285&t=121334](https://forum.kde.org/viewtopic.php?f=285&t=121334)

The Breeze window decoration titlebar is using the button size and the caption font size to scale the titlebar. There is also an option to edit the Breeze window decoration. The 'breezebutton.cpp' is telling:

> scale painter so that its window matches QRect( -1, -1, 20, 20 )
this makes all further rendering and scaling simpler
all further rendering is preformed inside QRect( 0, 0, 18, 18 )

A quick test with the vanilla Breeze window decorator and a smaller version:

[img]http://i.imgur.com/v7eNpUb.gif[/img]

---

### Post by buzzingrobot on 2015-02-04
> **Rog131 said:**
> 
Maybe - maybe not:  Bug 343555 - Breeze support for gtk2 and gtk3 - [https://bugs.kde.org/show_bug.cgi?id=343555](https://bugs.kde.org/show_bug.cgi?id=343555)


That's a depressing thread to read, speaking as a user. I don't blame either KDE or Gnome for doing what they wish with their projects. It's naive, though, to think, if they're thinking this,  that Gnome users will flock to KDE just because GTK apps look bad in the the new design, or vice versa.

---

