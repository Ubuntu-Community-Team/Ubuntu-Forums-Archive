---
title: "Language packs under office 2007?"
date: 2009-02-22
forum: Wine
---

### Post by ownaginatious on 2009-02-22
Hey guys,

I finally managed to get office 2007 installed in Ubuntu under WINE after upgrading to the newest beta version, as instructed on the WINE website. Anyway, everything works pretty well (exceptions being equation editor and the help, which I don't really care about anyway). Now the only think I need is to install the German language pack for school.

The problem I'm having is that when I go to install it, it tells me that I don't have office installed; probably a problem with detecting the wine registry, or something.

Has anyone had experience with this and devised a work around? Any help would be greatly appreciated.

Thanks, 

Dillon

---

### Post by NightMKoder on 2009-02-22
> **ownaginatious said:**
> Hey guys,

I finally managed to get office 2007 installed in Ubuntu under WINE after upgrading to the newest beta version, as instructed on the WINE website. Anyway, everything works pretty well (exceptions being equation editor and the help, which I don't really care about anyway). Now the only think I need is to install the German language pack for school.

The problem I'm having is that when I go to install it, it tells me that I don't have office installed; probably a problem with detecting the wine registry, or something.

Has anyone had experience with this and devised a work around? Any help would be greatly appreciated.

Thanks, 

Dillon

First, to get equations working you just need to add one dll override (usp10.dll). Note this is the equation tools, not equation editor: [http://ubuntuforums.org/showthread.php?p=6673381](http://ubuntuforums.org/showthread.php?p=6673381) .

As for the language pack, I remember there was a way to do it by extracting the language pack to your CD root and then installing it from office setup. Here: [http://www.codeweavers.com/compatibility/browse/group/?app_id=2630;tips=1](http://www.codeweavers.com/compatibility/browse/group/?app_id=2630;tips=1) .

Also, you may need to override riched20 to get the language settings dialog to work: [http://bugs.winehq.org/show_bug.cgi?id=15269](http://bugs.winehq.org/show_bug.cgi?id=15269) .

Tell us how it goes.

---

### Post by bornakke on 2009-03-11
Wow it actually works! Have been looking for something like this for a year now - and the solution was so simpel! Just worked! Thank you! :KS

---

