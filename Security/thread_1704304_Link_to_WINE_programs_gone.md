---
title: "Link to WINE programs gone"
date: 2011-03-10
forum: Security
---

### Post by dpatel on 2011-03-10
Hi - after reading Bodhi's Ubuntu security sticky, I removed the links between WINE and the various folders. However, I've lost the menu items for my programs. 

The menu no longer has MS Office in there and the only way to launch these is to do into .wine and launch it from there.

How can I bring back these links?

---

### Post by DanneStrat on 2011-03-15
> **dpatel said:**
> Hi - after reading Bodhi's Ubuntu security sticky, I removed the links between WINE and the various folders. However, I've lost the menu items for my programs. 

The menu no longer has MS Office in there and the only way to launch these is to do into .wine and launch it from there.

How can I bring back these links?

When you remove all the symlinks that point outside of the 

".wine" directory then "wine" will be confined to that folder. 

That means that all the files will stay in the ".wine" directory.

It's a trade between security vs usability.

You could however recreate the menu shortcuts manually

by doing the following:

Go into System > Preferences > system menu (or something similar)

In the right menu category, make a new launcher.

In the command box type

```
wine "C:\program files\executablename.exe"
```

Replace "executablename" with the name of your executable.


Good luck.

---

