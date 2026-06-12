---
title: "Mint Menu package"
date: 2008-01-18
forum: Ubuntu Brainstorm
---

### Post by Faolan84 on 2008-01-18
so i just downloaded the source to mintmenu, from Linux Mint 4.0 and compiled it into a binary for amd64 users. I have to say it's not too shabby although I think it needs some work and a little Ubuntu-fication, but needless to say I really think this belongs in the next LTS release (but maybe not as default, just there as an option).

It has very minimal dependencies, only Python and python-gtk2, and python-glade2. All the Mint specific stuff could easily be taken out. I've also provided the source so we can all have at it.

---

### Post by steeleyuk on 2008-01-18
Wasn't the SUSE menu put up for inclusion into GNOME but rejected for usability reasons? I know that the Linux Mint menu is similar so unless it gets included in GNOME by default, I don't think we're going to see it in Ubuntu.

That said, I do like those menus. Some people say they're too Windows-like but they're very neat and tidy.

---

### Post by caryb on 2008-01-18
Any pictures?


Cary

---

### Post by perlluver on 2008-01-18
This is the mint menu.

---

### Post by 23meg on 2008-01-18
Could you post the source URL, and/or file a needs-packaging bug?

---

### Post by Faolan84 on 2008-01-18
Well like i said earlier, it may not be a good idea to make it the default menu, but it certainly is better than slab and it's a choice for those who like those types of menus. It's all about choice and making that choice easy for the user without overwelming them. Some like SLAB, for others theres Mint Menu, and still there's the good ole Gnome Bar and old style "Windows" type gnome menus.

---

### Post by smartboyathome on 2008-01-18
I would say include it, but don't make it default. IMO it is nice, but it isn't as usable according to HIG as GNOME's menu.

---

### Post by mabovo on 2008-01-18
I had once installed it from OpenSuse packages but I don't remember where I got them. 
Anyway it has the same design as KDM4 menu very interesting not so user friendly but I agree to have it as an option in Ubuntu.

---

### Post by kevykev on 2008-01-18
Why is the architecture on the deb file amd64, could it be repackaged as architecture=any?

---

### Post by Faolan84 on 2008-01-28
Kevykev, I guess you are right. I did provide the source so you could always try it. I have been quite busy with my own project lately. I might do it when I have some free time. Thanks for the tip.

---

