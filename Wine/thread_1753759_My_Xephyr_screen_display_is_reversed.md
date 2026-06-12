---
title: "My Xephyr screen display is reversed"
date: 2011-05-09
forum: Wine
---

### Post by Old Newville on 2011-05-09
Hi,

I'm trying to run an old 256-color Disney game using Wine, but the game won't load. I get an error message that the game only runs in 256 colors. Working from the WineHQ website, I'm trying to find a work-around using Xephyr. I'm running Ubuntu 10.04 on a Dell Dimension 4600 with an Acer 20-inch monitor.

To bring up the display, I enter the following code:
[INDENT]```
Xephyr :1 -ac -screen 640x480x8 &
DISPLAY=:1 xterm
```[/INDENT]However, when the Xephyr screen comes up, the display is turned around, as if you were seeing it in a mirror. When I move the mouse to the left, the cursor moves to the right. Letters are turned around backwards.

I've found no references to this problem anywhere -- not on Google or on this forum -- but I'm hoping someone can help!

Thanks.

---

