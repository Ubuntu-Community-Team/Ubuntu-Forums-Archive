---
title: "Weirdness when installing Mate desktop environment"
date: 2018-04-24
forum: Ubuntu Development Version
---

### Post by sonsofblades on 2018-04-24
So, I decided to add a desktop environment to my current 18.04 installation: Mate. 

This decision was fueled in part by the fact that my child cannot seem to navigate Gnome easily, so I figure Mate, with it's much clearer labeling, would be much easier. Took a quick look around, and found it should a fairly simple process, but required me to swap to the lightdm. No big deal. 

```
sudo apt install tasksel
``` 

```
sudo tasksel install ubuntu-mate-desktop
``` About 8 minutes later (after selecting lightdm, and letting it install), I rebooted, and was greeted by the extremely green login screen. 
Cool, logged in. So, first thing I go to check out was the menu. Something is amiss. The Ubuntu Software Center was completely gone. 

Um... WHAT~! <----first immediate reaction. 

Just to be clear, I checked everything else. It seems that Mate was completely and correctly installed, Libreoffice was installed, and the standard media stuff was installed, but for some inexplicable reason, the main GUI package manager supplied with Ubuntu had been removed. 

Back to the Terminal.

```
sudo apt install synaptic
```

Well, whaddya know.... 

So that's my story. And heads up, if you decide to install the Mate DE in Ubuntu. 

Also, my Steam shortcuts are gone from the menu, but that's not a big problem.

---

### Post by kerry_s on 2018-04-24
your child couldn't navigate the big buttons in gnome & you think menus is going to make it easier?

you could have just used extensions like dash-to-panel or just put what he uses right up front on the desktop.

whatever, hope it works out, mate is a very good setup on it's own, with options in mate tweak to look like other desktop styles. like all linux it's very customizable to your needs.

---

