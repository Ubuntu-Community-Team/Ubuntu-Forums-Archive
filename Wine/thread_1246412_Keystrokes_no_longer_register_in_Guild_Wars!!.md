---
title: "Keystrokes no longer register in Guild Wars!!"
date: 2009-08-21
forum: Wine
---

### Post by lockaar on 2009-08-21
_**EDIT: PROBLEM SOLVED!**_


I sure hope someone can help me with this one...

I installed Guild Wars using Wine 1.1.27, and graphical anomalies aside (horrible FPS) it was running, I could load into towns, type, everything.

Today I load it and for some reason, whenever I try to type (to login), no keystrokes register, but the cursor icon is flashing. The strange part of it is the strokes register in the background (desktop, or terminal) programs.

Ex: I insert 

```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dx8
```into the terminal in order to launch Guild Wars using DX8, and when I type my login name (game at full screen) the login name is typed into the currently open terminal window in the background!

EDIT: I have tried downgrading WINE to various different versions, all of which can run the program, but there is the same problem, none of keystrokes work in the program, they all go to whatever is open "behind" my game.

What would make the keystrokes not register with the open program? My mouse works fine.

Thanks

---

### Post by NightMKoder on 2009-08-22
stop.using.desktop.effects.

---

### Post by lockaar on 2009-08-22
I have tried disabling those (even uninstalled) and the problem is still present, i don't know why though.

_**EDIT: PROBLEM SOLVED!!**_

Yesterday when I was setting up WINE I had seen various posts recommending that I un-check the box that said "Allow the windows manager to control the window". That was causing my problems...I re-checked that box and now I'm in business!

Funny how something so simple can be overlooked.

---

