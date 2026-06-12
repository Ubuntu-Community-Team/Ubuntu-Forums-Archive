---
title: "WMP 10 uninstall"
date: 2009-10-25
forum: Wine
---

### Post by PaulInBHC on 2009-10-25
I have 9.10 and wine 1.1.3 Tried to install wmp 10 and it failed. Now I can't get it to uninstall. I tried to install wmp 9 after using the wine uninstall program but 9 states that a newer version is already installed.

Ideas?

---

### Post by Toffeeapple on 2009-10-25
I don't know a clean way.... but uninstalling wine and then deleting all it's folders will do the trick but then that will also delete anything else you installed...

I've found that its always a good idea to install stuff in separate prefixes, that way if it all goes wrong its just a matter of deleting a folder.

If fiddling round scares you try playonlinux (it's a sort of front end for wine) every time you install something with that it gives you an option to put it in a separate prefix or select an existing one.

Also have you tried winetricks? it's handy for easily installing essential windows stuff.

---

### Post by PaulInBHC on 2009-10-25
Thanks for the tips. I'll mess with it next weekend.

I uninstalled wmp through wine, then saw it was still in the apps menu. Uninstalled wine through synaptic but the wine menu was still there and fonts were missing for webpages. Did a search here and tried a few terminal tips.

One doggone website with streaming audio won't work with 9.10 and I've tried everything except getting the dll's and such from windows.

---

### Post by sea_monkey987 on 2009-10-25
just delete the .wine folder in your user directory to reset the wine install (and remove WMP 10).  perhaps wmp can not be uninstalled normally since it's not once of those built-in installed programs in windows?

---

