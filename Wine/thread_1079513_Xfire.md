---
title: "Xfire"
date: 2009-02-24
forum: Wine
---

### Post by neilzomg on 2009-02-24
Hey all, just tried installing xfire heres what it looks like 
[[IMG]http://img16.imageshack.us/img16/7323/xfire.th.png[/IMG]](http://img16.imageshack.us/my.php?image=xfire.png)

any ideas there?

---

### Post by BoneSmash on 2009-02-24
That is a known bug and the only way to fix it at the moment is to use native Windows .dll files.  Check out Xfire in the Wine AppDB.

---

### Post by Poyntz on 2009-06-08
Also try the latest version. That bugs not present. But there are a heap of other bugs.
Please download xfire.msi from [http://www.xfire.com](http://www.xfire.com), then use wine to open it.
- should install fine, no errors

also, you'll need to use wine tricks to download some things
sh winetricks ie6 &&
sh winetricks comctl32 &&
sh winetricks comctl32.ocx &&
sh winetricks allfonts

Once you've installed it, my tutorial might help with using it without it crashing. Try here: [http://ubuntuforums.org/showthread.php?t=1181645&highlight=xfire](http://ubuntuforums.org/showthread.php?t=1181645&highlight=xfire)

All the best

---

