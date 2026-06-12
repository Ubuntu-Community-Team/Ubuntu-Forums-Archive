---
title: "wineserver -k  , okay?"
date: 2009-01-20
forum: Wine
---

### Post by zami on 2009-01-20
When a program under Wine crashes, freezes, etc, but is "stuck" on the desktop, and "wineboot" does nothing, is 

wineserver -k 

appropriate to use?

It works but I don't know why or remember where I even read that command - it may have been in a "please don't ever use this" type post!  Anyhow it works but I don't want to completely break my Wine setup.

Any info on this command?  Is it "safe" ?

-zami

---

### Post by cogadh on 2009-01-20
Perfectly safe to use in most circumstances. All it does is kill the current wineserver session, which will force your locked up app to close. The only problem it might cause is file saving issues. If your app locks while writing to a particular file, like a game writing to a save file, using "wineserver -k" could corrupt that file.

---

### Post by zami on 2009-01-20
cogadh,
thanks so much!

-zami

---

