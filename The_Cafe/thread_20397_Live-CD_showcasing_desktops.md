---
title: "Live-CD showcasing desktops?"
date: 2005-03-16
forum: The Cafe
---

### Post by RadixLecti on 2005-03-16
Hi,

I was wondering, has anyone heard of a Live-Cd with the main purpose of showcasing different desktop environments? I thought it'd be nice if I could just pop in the cd, reboot and try different desktops without having to install them. 

So, are there any live-cd's like that out there?

Thanks.

---

### Post by BWF89 on 2005-03-16
I think on SLAX you can choose your preferred desktop enviroment. I think it's KDE but you can choose the Windows, Unix, or OSX look. Or mabye that was FreeBSD Live CD. I don't remember.

---

### Post by RadixLecti on 2005-03-16
[QUOTE=BWF89]I think on SLAX you can choose your preferred desktop enviroment. I think it's KDE but you can choose the Windows, Unix, or OSX look. Or mabye that was FreeBSD Live CD. I don't remember.[/QUOTE]
 I was thinking of getting to choose Gnome, KDE, XFCE, enlightenment and so on... like a desktop environment demo.  Would be nice with a live-cd that has the lesser known/used desktops.

---

### Post by bored2k on 2005-03-16
[QUOTE=RadixLecti]I was thinking of getting to choose Gnome, KDE, XFCE, enlightenment and so on... like a desktop environment demo.  Would be nice with a live-cd that has the lesser known/used desktops.[/QUOTE]
 Knoppix has several environments. It doesn't have Gnome though :( [maybe Knoppix dvd has it] .

---

### Post by BWF89 on 2005-03-16
Hire a programmer to make you a live cd.

---

### Post by jdong on 2005-03-16
Find the DVD version of Knoppix (Bittorrent) -- it has everything you want!

---

### Post by RadixLecti on 2005-03-16
[QUOTE=jdong]Find the DVD version of Knoppix (Bittorrent) -- it has everything you want![/QUOTE]
 Hehe,
That seems to be easier said than done.

---

### Post by jdong on 2005-03-16
yeah, no kidding!


Then again, Mandrake users have the "mklivecd" scripts, where you customize a Mandrake 10.x install just the way you like it, issue "mklivecd", and get an instant ISO. That's what PCLINUXOS is based off.


Speaking of PCLOS, if it's still like preview 6-ish, there should be both KDE and GNOME (relatively new versions), so that you can demo both. Knoppix/Kanotix will sport most of the other WM's, so just those two can showcase A LOT.

---

### Post by RadixLecti on 2005-03-17
[QUOTE=jdong]yeah, no kidding!


Then again, Mandrake users have the "mklivecd" scripts, where you customize a Mandrake 10.x install just the way you like it, issue "mklivecd", and get an instant ISO. That's what PCLINUXOS is based off.


Speaking of PCLOS, if it's still like preview 6-ish, there should be both KDE and GNOME (relatively new versions), so that you can demo both. Knoppix/Kanotix will sport most of the other WM's, so just those two can showcase A LOT.[/QUOTE]
 Sounds good. Thanks for the info. I've been trying to get my dad interested in Linux, that's the biggest reason to want to have one of those live-cd's... So he can find a desktop he would be comfortable with.

---

### Post by britbrian on 2005-05-18
My mklivecd experience for making a desktop showcase

I've remastered PCLinuxOS preview8 & 8.1 a few times now after doing my fav upgrades. My best remaster includes KDE3.4, Gnome (mixed 2.8 & 10) many office apps OOo1.3, KOffice & Gnome Office. Ofcourse to keep the iso <~650MB, I uninstalled much unwanted stuff until the df command reports ~1.8G space is used for /.
PCLinuxOS requires 256MB to boot and my remasters can just about do so, only after following some tips to exclude unneeded accounts & apt caches plus cleaning up included user accounts.

Alas Gnome is much less supported in PCLinux and the preferences window is broken  ](*,) . The Gnome ver of plastik theme is good but not as attractive as the excellent clearlooks theme.

XFce was recently added to PCLinux repos so I installed it and used the plugins to merge the separate panel & task tray into one bottom panel looking just like a typical KDE/Win98 panel. However the autohide panel sometimes doesn't unhide so you have to restart it.

Since XFce only adds about 6MB IIRC, It would be easy to add XFce, IceWM & Fluxbox also to a KDE/Gnome showcase and keep most Office apps  minus unwanted stuff.

If you want to try it out, search forum posts for mklivecd on pclinuxonline.com for tips.

Happy remastering  :-)

---

### Post by tread on 2005-05-21
I am trying to do a live dvd for just this purpose, and it seems to be shaping up ok. My biggest problem at the moment is that the default user automatically gets logged into gnome .. I checked the gdm config files and those say no to automatic login. The second problem is separating the menus .. currently all kde applications show up in the gnome menu. But I'll try to fix these .. I'll post again if I succeed.

---

