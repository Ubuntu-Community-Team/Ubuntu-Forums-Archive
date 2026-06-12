---
title: "Removing MS Office After Uninstalling Wine"
date: 2010-11-16
forum: Wine
---

### Post by tacantara on 2010-11-16
I recently removed Wine from my computer.  I had originally installed it so I could run MS Office.  It was working for me for a couple of weeks, then I started getting errors while working with MS Word documents.  I couldn't save, print, etc. without getting the "unexpected error - must shut down MS Word" error.  It was stuck in some kind of loop, which required me to force-close it, else it would keep opening up to a new blank document.

The Wine folder is still showing in my Main Menu, because when I removed Wine, it didn't remove the MS Office package.  Which directory should I be looking for to remove MS Office?  I can't seem to track it down.  I'm not critically short on disk space, but I don't want to wait until that point to try and remove software that I'm not using.

---

### Post by Soulcage on 2010-11-16
If that is all you had / have installed then you can run ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*

``` to basically make wine a fresh install.

---

### Post by tacantara on 2010-11-16
Thanks :)  That seems to have done the trick.

---

