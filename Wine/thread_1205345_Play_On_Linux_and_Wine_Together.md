---
title: "Play On Linux and Wine Together"
date: 2009-07-05
forum: Wine
---

### Post by zephyrcat on 2009-07-05
I currently have Steam working with a plain Wine install, but I am curious about trying Play On Linux to see if it works better.

Since Play On Linux is Wine-based, though, does anyone know how having two copies of Steam installed (one through Play On Linux and one through standard Wine) will work? I don't want to mess up what I already have working.

Thanks!

---

### Post by cogadh on 2009-07-05
PlayOnLinux is not really Wine based, it is just a front end GUI for Wine. You can run POL and Wine simultaneously, just make sure you don't have POL install anything in your existing .wine directory (make it use a separate Wine prefix).

---

### Post by ackanao on 2009-07-06
You could use "WineImport" plugin for POL to import your current Steam setup into POL - It's available on POL's download page.

Also, POL comes with some Steam POL scripts so you can try them too.

POL can't mess up your Wine installation so you don't have to worry about that.

About Steam: It will work better with POL only if you know that there's some Wine version that works better with Steam. Other than that, there's no difference at all. 

POL is just a few python scripts here and some shellscripts there to make Wine easier to use... Nevertheless it is one of the most useful frontend for Wine I've seen - it allows you to have as many different versions of Wine and wineprefixes as you want.

---

