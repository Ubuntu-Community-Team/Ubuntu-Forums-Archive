---
title: "Suspend idon't work"
date: 2018-08-31
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-08-31
In most cases you don't need to suspend on a desktop.
In my case I want to run Civ4 with Steamplay. Civ4 works fine, but I'm not able to load a saved game. Because of this I want to  use suspend to turn of the computer.
To do a suspend click the window key, type suspend and start suspend.
The computer shuts down and the power button starts blinking.
When I return from suspend mouse, keyboard and monitor isn't working. The only alternative is to press the power button to turn off the computer.
There is a bug report on Ubuntu 18.04 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950).

---

### Post by P-I H on 2018-08-31
I enabled "Global C-state Control" in bios, which fixed the suspend problem. This was turned off to prevent freezes in gnome-shell, but these don't happen frequently.
Back from suspend I'm able to continue a CIV4 game.

---

