---
title: "Peggle: Black Screen, crashes, can only hear sound"
date: 2009-03-24
forum: Wine
---

### Post by blazemore on 2009-03-24
When I load Peggle Deluxe, or Peggle Nights trials, I see the entry on the application switcher, I can hear the Pier Gynt suite, but I can't run the game. The desktop becomes unresponsive, as if the window is invisible and not responding, and I have to restart X.

This is with or without Compiz, and I've also tried using Crossover Games.

EDIT: Output from the terminal is this, repeated over and over, so I know it's a display problem:
```
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @0! (XRandR)

```

---

### Post by blazemore on 2009-03-25
anyone?

---

### Post by xzero1 on 2009-03-25
Kill emerald & Compiz -- use Metacity window manager with GTK window decorator.  Is your display capable of 800x600 resolution or 1600x1200?

---

### Post by blazemore on 2009-03-26
I fixed it by running in a virtual desktop

---

