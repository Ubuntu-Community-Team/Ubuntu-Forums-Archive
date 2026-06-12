---
title: "gnome classic"
date: 2019-04-12
forum: Ubuntu Development Version
---

### Post by ping-wu on 2019-04-12
I have 19.04 (fully updated) on two machines, one (automatically) shows a gnome classic on log-in, the other does not.

These two machines have identical installation procedures.

? ? ?

BTW I really like gnome classic even when I have a relatively powerful machine (Ryzen 7 + RX550 + 16 GB DDR4)!

---

### Post by Frogs Hair on 2019-04-12
I think you can enable the bottom panel as in the classic session from the tweak tool. I have seen this session appear before on though only on an upgrade.

---

### Post by kansasnoob on 2019-04-12
I was just testing that session in Disco and assume that it still requires the installation of the package 'gnome-shell-extensions' from the repos. I encountered a login screen bug though:

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1824588](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1824588)

I'm guessing that may be hardware related? Regardless because of that bug I can't be 100% certain that package is still required but I know it was previously. That "classic" session should not be confused with the flashback session which uses gnome-panel.

---

### Post by ping-wu on 2019-04-13
I use flashback (alternatingly with ubuntu desktop) 18.04.x when gnome classic is (or at least was) essentially unworkable.  With 19.04, the situations seem to have reversed.  For machines that do not (automatically) make gnome classic available during log in, I couldn't find a way to install it.

---

### Post by mc4man on 2019-04-13
gnome-shell classic is in the **gnome-shell-extensions** package.

---

### Post by ping-wu on 2019-04-14
> **mc4man said:**
> gnome-shell classic is in the **gnome-shell-extensions** package.

The gnome classic desktop I got from installing the **gnome-shell-extensions** package turned out to be functionally very different from the "automatically installed" (really don't know what this means) version.  The icons are all screwed up (black and white).  But mostly, the gnome terminal is essentially unusable (screen disappeared but reappeared every time I entered a character, like a black and white neon light).

---

