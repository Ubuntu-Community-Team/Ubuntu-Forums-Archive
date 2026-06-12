---
title: "Can I add new .deb into main reposity?"
date: 2005-06-11
forum: Repositories &amp; Backports
---

### Post by Marcel Firlej on 2005-06-11
Hi.

I build some Ubuntu packages and I have question now.

I build "Kadu" for Ubuntu (most popular in Poland, polish talk messanger - languages support: polish, english and some more). Kadu is in Debian repository but not working with Ubuntu, 'cose dependencies are too high. My packages working with Ubuntu at all :D

What I must do, to add that packages into Ubuntu server?  For all Ubuntu users?
I will makeing new versions of Kadu for Ubuntu...

(My packages must be accept by Kadu team first  :grin: )

What do you think  :-?

---

### Post by maspro on 2005-06-11
:) 

I think you need to request this kind of stuff through the Ubuntu development team. And I guess that they wanna test it first, so don't get your hopes up to high. If they approve then I guess that they will upload the package for your to the appropriate repositories.

---

### Post by az on 2005-06-11
You want to backport it.

Whatever is in debian sid in a few months from now will be in Universe for Breezy.  So if it is in Debian, it will be in Breezy.  It will not go into main unless  Canonical has a good reason to put it there.  Talk to them.  Good Luck.

[http://ubuntuforums.org/guides.php](http://ubuntuforums.org/guides.php)

---

### Post by jdong on 2005-06-11
#ubuntu-devel would probably be your best bet for quick developer contact.

---

### Post by Mez on 2005-06-12
actually - #ubuntu-motu will be better, seeing as it will proably go in universe instead of main

---

### Post by az on 2005-06-12
[QUOTE=Mez]actually - #ubuntu-motu will be better, seeing as it will proably go in universe instead of main[/QUOTE]

Ask MOTU to include a package that is going to be imported anyway?

(For those who are scratching their heads, MOTU = Masters Of The Universe;  They are the team of workaholics that try to maintain the thousands of Universe packages that are maintained by the thousands of debian developers)

---

