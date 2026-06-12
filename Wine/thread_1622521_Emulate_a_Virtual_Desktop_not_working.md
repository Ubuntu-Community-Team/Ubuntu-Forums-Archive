---
title: "Emulate a Virtual Desktop not working?"
date: 2010-11-15
forum: Wine
---

### Post by Zenmij on 2010-11-15
Hello,

I've tried a few older games through wine just lately which need to be in a virtual desktop. I know these games work well in wine for other users, but they still want to run fullscreen. This ends up being a black screen and in the case of Bridge Commander, flickering between a window and fullscreen 4 or 5 times then black.

I have to kill the process, and when I return to the desktop, its in 600x800 resolution. I then have to logout of my user session because the screen is too full and hard to navigate :S.

First time I noticed this happen is after Ubuntu could not detect my display and asked me to use the Nvidia settings program - any chance that could be at the root of it?

Many Thanks.

---

### Post by Sugi on 2010-11-15
Have you tried using emulate desktop environment [Emulate a Virtual Desktop] within wine configure? EXMAPLE: Terminal > winecfg

or running the comment for virtual desktop?
Terminal > wine explorer /desktop=TEST,800x600 game.exe

Btw, I had this same problem with StarCraft 1 and incorrectly shutting down the application which would cause my main resolution to get stuck at 640x480. :S

I hope this has helped some,
Sugi

---

### Post by Zenmij on 2010-11-16
Thanks for the reply Sugi.

I tried [Emulate a Virtual Desktop] in winecfg, but something overrides it, and the game still plays in fullscreen.

Any other ideas?


Thx.

---

### Post by Soulcage on 2010-11-17
Emulate virtual desktop requires all .exe files to close if this doesn't happen normally you can force it by ```
wineserver -k
``` into a terminal.

---

### Post by Sugi on 2010-11-22
Have you tried the terminal command?  That should help.

Sugi

---

