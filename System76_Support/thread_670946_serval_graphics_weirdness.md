---
title: "serval: graphics weirdness?"
date: 2008-01-18
forum: System76 Support
---

### Post by icewater on 2008-01-18
hello Systen76   -

i have a serval that i bought about a year ago, and there seems to be something wrong with the graphics.

the areas that should be white pixels are, instead, yellow. if i start firefox, the screen is distorted and jittery - the content inside the firefox window is completely unreadable.  if i open GIMP, the tool dialogs are unreadable unless i grab them with an alt-click and move them.

is this a known issue?  could it be hardware?  how should i proceed?

i have a conference in March and must have this issue resolved by then.


thanks!

---

### Post by thomasaaron on 2008-01-18
Which Serval do you have? (The System76 driver will tell you.)

That's pretty weird. It could be hardware related. Have you made any configuration changes that might have affected your graphics? Or downloaded any software that matches the time the problem started?

ALSO, make sure your graphics driver in /etc/X11/xorg.conf is set to nvidia.

EDIT-----
Burn an Ubuntu CD and run memtest. I just fixed a discoloration problem a couple of days ago by replacing a memory card. Weird.

---

