---
title: "Why does Ubuntu Studio use alacarte instead of menulibre?"
date: 2016-02-22
forum: Ubuntu Studio
---

### Post by yoshii on 2016-02-22
I am wondering why Ubuntu Studio uses alacarte instead of menulibre?  
I know that Xubuntu now uses menulibre and after trying it out, it does seem less buggy and a bit more straightforward.  
Are there any plans to change this in future versions of Ubuntu Studio?

---

### Post by ipatrol on 2016-05-17
Because there's an unresolved bug with either Ubuntu Studio, menulibre, or XFCE that causes it to destroy all the Studio menu entries.
[https://bugs.launchpad.net/menulibre/+bug/1430571](https://bugs.launchpad.net/menulibre/+bug/1430571)

---

### Post by yoshii on 2016-05-17
Ah, ok thanks, iPatrol.

---

### Post by stuart_brown2 on 2016-05-19
To start: this is not my "first cup of Ubuntu", I've been using it for nine years! In the last few days I have done four complete re-installs of Ubuntu Studio 16.04: twice on a 1TB external hard drive attached to an old Dell Latitude E6500 and twice on the 250GB internal HDD of the E6500. The system installed and was fully functional in all cases. In the cases of the two external HDD installations, I made no attempt to edit menus - I was checking other aspects of functionality. In the case of the first internal HDD installation (which I did when I was confident that it would do what I wanted it to do), I installed a necessary minumum of Windows applications using Crossover (version 13). I then edited the Ubuntu Studio menus using menulibre - and not only did it lose completely the Ubuntu Studio menu structure but also it seemed to duplicate various sub-menus. I then re-installed ubuntustudio-menu and ubuntustudio-default-settings and rebooted the machine, but the menu structure was still broken. I checked that this was so with both the default Whisker Menu and the alternative Xfce applications menu - it was (which to be fair was what I was expecting). I then used alacarte to attempt to mend the menu - which failed. I concluded that the menu config was completely zapped. Rather than mess around further, I have now reinstalled the entire system and my first action has been to de-install menulibre. I would not touch it with a bargepole. I may or may not install alacarte, but more probably I will edit the menus manually in the relevant system and user folders.

---

