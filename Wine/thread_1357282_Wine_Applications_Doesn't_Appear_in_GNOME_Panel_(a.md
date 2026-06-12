---
title: "Wine Applications Doesn't Appear in GNOME Panel (aka The Start Menu)"
date: 2009-12-17
forum: Wine
---

### Post by KcLKcL on 2009-12-17
Well, This is my problem:

I installed a program (anything), it should make a start menu entry and normally Wine should make a shortcut in the "Applications>Wine>Program" right? This Wine doesn't make it. It's installed but the menus doesn't show up...

Any idea?

---

### Post by Rmantingh on 2009-12-17
Initially you probably will find some shortcuts under section "Other" in your menu but if you log out and log in again then they can be found under the Wine menu (no longer under Other).
Also see [http://ubuntuforums.org/showthread.php?t=131551](http://ubuntuforums.org/showthread.php?t=131551) for how Wine uses your Desktop to put .desktop and .link files on.
I must admit it is all very confusing.

---

### Post by KeLa on 2009-12-17
I've noticed that after installation of win program and if there is no icon under wine you have to start menu editor and go and look there under wine and the icon if icon is listed there just close the editor and then it's on the menu.
I think this has to be some sort of refresh problem in menu system.

---

### Post by KcLKcL on 2009-12-17
Wait, I **figured it out**

I revert the Panel (Right Click>Edit Menus>Revert)

It **solves** my problem

Thanks for your suggestions :)

---

