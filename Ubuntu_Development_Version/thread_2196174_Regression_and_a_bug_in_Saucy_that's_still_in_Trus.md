---
title: "Regression and a bug in Saucy that's still in Trusty"
date: 2013-12-28
forum: Ubuntu Development Version
---

### Post by Mateusz Stachowski on 2013-12-28
I wonder does anyone else have a problem with Alt (Hold) not showing the menus on panel. This doesn't work for me in Saucy and in the daily images of Trusty and I remember that it worked in Raring so it looks like a regression.

I also discovered a bug that happens if I enable the magnifier plugin in CCSM and this too affects Saucy and Trusty. When I go into the spread of all windows with Super + W and then activate the window using Enter instead of mouse cursor I get a magnifier glass displayed on top of that window.

---

### Post by Mateusz Stachowski on 2013-12-28
The magnifier glass also shows after selecting a program with Enter in the Alt + Tab and Ctrl + Alt + Tab switcher.

---

### Post by grahammechanical on 2013-12-28
I do not know what you mean about Alt (hold) not showing the menus on the panel. I thought the sequence was Alt+F10 and to release Alt when an top panel drop down menu appears then we can use an arrow key to move back and forth across the the top with the menus dropping down. If I remember correctly, specific tests on Unity were run during the 13.04 development cycle. I ran those tests several times myself. The results were sent to the Unity developers directly,

Alt tap brings up the HUD. It always did and still does but Alt (hold) does nothing. The Keyboard Shortcuts overlay says Alt (hold) reveals the application menu. Well, it does not. So, I guess that you are right. Perhaps the use of the Alt key has changed but the information in the Keyboard Shortcuts overlay has not been edited. There have been changes to the shortcut keys before now.

Regards.

---

### Post by ventrical on 2013-12-28
> **grahammechanical said:**
> I do not know what you mean about Alt (hold) not showing the menus on the panel. I thought the sequence was Alt+F10 and to release Alt when an top panel drop down menu appears then we can use an arrow key to move back and forth across the the top with the menus dropping down. If I remember correctly, specific tests on Unity were run during the 13.04 development cycle. I ran those tests several times myself. The results were sent to the Unity developers directly,

Alt tap brings up the HUD. It always did and still does but Alt (hold) does nothing. The Keyboard Shortcuts overlay says Alt (hold) reveals the application menu. Well, it does not. So, I guess that you are right. Perhaps the use of the Alt key has changed but the information in the Keyboard Shortcuts overlay has not been edited. There have been changes to the shortcut keys before now.

Regards.


That is  what I got here . (all of the above)

---

### Post by Mateusz Stachowski on 2013-12-28
Alt (hold) should reveal the hidden global menu of a program. I don't think that the use of Alt key has changed so it is a bug.

---

### Post by mc4man on 2013-12-28
> **Mateusz Stachowski said:**
> Alt (hold) should reveal the hidden global menu of a program. I don't think that the use of Alt key has changed so it is a bug.

Seems to be broken for gtk3 apps, still works ok with gtk2 & qt4
(gtk3  apps that have menus in app window do work with alt(hold) + letter

---

### Post by Mateusz Stachowski on 2013-12-30
You are right the Alt (hold) works for qt4 programs with global menu and gtk3, gtk2 programs that have menu in window. I tested deadbeef the only program in my system that uses gtk2 and it didn't reveal the global menu.

I also discovered that Alt (hold) + letter will bring the menu in the window instead of the panel with gtk3 and gtk2 programs.

---

### Post by Mateusz Stachowski on 2014-01-01
Today I wanted to report those bugs but I turns out that they are already being reported by other users.

[https://bugs.launchpad.net/unity/+bug/1253642](https://bugs.launchpad.net/unity/+bug/1253642)   (Holding Alt does not reveal application menu on almost all software)

[https://bugs.launchpad.net/compiz/+bug/1195954](https://bugs.launchpad.net/compiz/+bug/1195954)   (Pressing 'Esc' or 'Enter' during Compiz Scenes toggles 'Magnifier' activation)

---

