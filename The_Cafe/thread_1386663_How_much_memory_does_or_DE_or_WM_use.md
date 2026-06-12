---
title: "How much memory does or DE or WM use?"
date: 2010-01-20
forum: The Cafe
---

### Post by stars on 2010-01-20
Please post your desktop environment and/or window manager's memory usage once it's loaded without other applications running. Thanks.

DE: Gnome
RAM: 92MB

---

### Post by Icehuck on 2010-01-21
> **stars said:**
> Please post your desktop environment and/or window manager's memory usage once it's loaded without other applications running. Thanks.

DE: Gnome
RAM: 92MB

Question is, can you get gnome down to 50 mb or less?

---

### Post by doorknob60 on 2010-01-21
I technically have 311 MB used right now, but that's the kernel making it useful (not sure how, but I know all my apps running is not much at all, I use Openbox) since I have 4 GB of RAM. My actual WM is using 1.1 MB of RAM, which is technically what you asked :P If you add Pcmanfm and Lxpanel total Lxtask says the three combines is about 9 MB. Those are the only programs running always.

---

### Post by markp1989 on 2010-01-21
well my desktop (xmonad) is using 65mb of ram at cold boot according to free -m, i dont know how much of that is being used xmonad thou

WM: xmonad 
programs: xsetroot to set the cursor , setxkbmap to set the keymap, and feh to draw the wallpaper, lxterminal

---

### Post by Techsnap on 2010-01-21
> Question is, can you get gnome down to 50 mb or less?

Yep the OP should try it. I have managed to do it.

---

### Post by stars on 2010-01-21
Techsnap, thanks for confirming Icehuck's ideal of using 50MB. What did you do to achieve that? I'm still new to gnome since I've always used mostly cli or box wm's in the past. So far, I've used sysv-rc-conf and removed most startup applications. What steps did you take to achieve 50MB?

---

### Post by Techsnap on 2010-01-21
Well the end result isn't particularly that nice considering you have to disable GTK themes and uninstall Nautilus. I can't recall exactly what  I did but I'll give it a go again this weekend perhaps.

---

### Post by hoppipolla on 2010-01-21
KDE 4
50 megabytes? :D






... they suspected nothing O.O

---

### Post by stars on 2010-01-21
Techsnap, if you find the time to do that it would be great. Box wm's really spoil a user I think since they're so light and easy to configure. I thought it would be fun to try a de for a change.

hoppipolla, haven't tried kde in ages, though many seem to like.

---

### Post by Techsnap on 2010-01-21
hoppipolla: I use KDE all the time, I have used KDE for 8 solid years on Linux but I've never got KDE 4 running in 50MB RAM, it's usually between 95 & 130MB. 

stars: Yeah I'll post here when I do.

---

### Post by K.Mandla on 2010-01-21
Musca and Xorg 7.3 will run in much less than 12Mb, before you start up a few windows.

[http://kmandla.wordpress.com/2009/09/02/unsolved-mysteries-x-in-1mb/](http://kmandla.wordpress.com/2009/09/02/unsolved-mysteries-x-in-1mb/)

Awesome and other tiling WMs take up tiny slivers of space. Screen and htop alone show memory use of around 9Mb total in use, in Debian.

---

### Post by squilookle on 2010-01-21
I'm using Gnome: 
Before starting X/Gnome I'm usually on about 17mb, with Gnome but nothing else started, its between 130 - 150mb.

---

### Post by hoppipolla on 2010-01-22
> **Techsnap said:**
> hoppipolla: I use KDE all the time, I have used KDE for 8 solid years on Linux but I've never got KDE 4 running in 50MB RAM, it's usually between 95 & 130MB. 

stars: Yeah I'll post here when I do.

hehe there is a CHANCE I may have made up that low memory usage! :D

I think my PC is actually sitting on rather high memory use at the moment but then I do have a lot open O.O

... across 6 desktops o.O

---

