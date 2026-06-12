---
title: "Wake-up screensaver using mouse?"
date: 2014-04-01
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-04-01
I find that using either the standard GNOME DE (gnome-shell) or the new GNOME Classic sessions that even when the screen-lock is set to off the user must press Esc to exit the screensaver.

Is there a setting to change this behavior so just mouse movement wakes the screen?

---

### Post by GeorgeVita on 2014-04-01
Hi,
using today's live, gnome-classic, touching touchpad turns on screen, two-finger scroll upwards unlocks the screen (like a smart phone ...). Possibly this works rolling mouse wheel (if any).

---

### Post by kansasnoob on 2014-04-01
> **GeorgeVita said:**
> Hi,
using today's live, gnome-classic, touching touchpad turns on screen, two-finger scroll upwards unlocks the screen (like a smart phone ...). Possibly this works rolling mouse wheel (if any).

Nope, the only thing that exits the screensaver is pressing Esc.

---

### Post by kansasnoob on 2014-04-02
Bump :biggrin:

---

### Post by GeorgeVita on 2014-04-03
(bumping by asking more info)

Hi kansasnoob!

I am using an updated live UbuntuGnome 14.04 and I cannot find the actual "screensaver" and its settings ...

The closest setting is: Menu Applications > System Settings > Brightness and Lock > "Turn screen off when inactive for:"
Choosing "1 minute" I tested that "wake-up" from "screen off" can be done as I mentioned to my previous post (scrolling upwards via touchpad) and also pressing any key (not only ESC), rolling upwards the wheel of a mouse or dragging the whole screen (left click and move) upwards.

I also installed via terminal gnome-screensaver but unfortunately no "settings page" found!
Finally, searching the net, I read about [bug#994612]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/994612")

Am I missing something or you mean something else? Are you using an installed UbuntuGnome which has more options than the live version (from daily .iso) or you are talking about a different screensaver?

---

