---
title: "How to uninstall wine"
date: 2010-11-14
forum: Wine
---

### Post by cookie6 on 2010-11-14
Hello, I was searching how to uninstall wine, and came up with this code to uninstall: sudo apt-get remove --purge wine

But, when I put the code in, this happens. (Look at screen shot)
It says its not installed, but its still in the menu. [ATTACH]175638[/ATTACH] [ATTACH]175640[/ATTACH]

---

### Post by [Shawn] on 2010-11-14
Have you tried ```
sudo apt-get remove wine
``` ?

---

### Post by _outlawed_ on 2010-11-14
> **'[Shawn] said:**
> Have you tried ```
sudo apt-get remove wine
``` ?

He had already uninstalled it, just the menu entries are still there.

I don't think wine uninstall triggers the menu scripts to run, so it sticks the entry in there. You can always right click -> Edit Menus -> delete the Wine folder that way.

---

### Post by howefield on 2010-11-14
Looks like you are using the wrong package name.

---

### Post by Hippytaff on 2010-11-14
Also you might need to use the full name ie Wine-1.2.3
or it could be that you need to use a capital W (linux is case sensitive) :-)

---

### Post by howefield on 2010-11-14
Probably wine1.2 or if you are using the Wine development release wine1.3

---

### Post by cookie6 on 2010-11-14
> **_outlawed_ said:**
> He had already uninstalled it, just the menu entries are still there.

I don't think wine uninstall triggers the menu scripts to run, so it sticks the entry in there. You can always right click -> Edit Menus -> delete the Wine folder that way.

Thanks! Problem solved! :) Its gone like a fart in the wind! :lolflag:

---

