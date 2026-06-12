---
title: "Counter-Strike Source"
date: 2009-10-31
forum: Wine
---

### Post by BarfBag on 2009-10-31
Ubuntu 9.10, Karmic Koala (64 Bit)
WINE 1.0.1
Intel Core 2 Quad (2.66 GHz)
4 GB DRR2 RAM
EVGA nVidia GeForce 9800 GT (1 GB GDDR3 VRAM)

Hey, guys.  I'm having some really annoying problems with Counter-Strike Source.  There's no reason it shouldn't run, as it ran fine on my previous PC.  I just built this one a couple of days ago, and I'm having trouble.

1.  It will only run in a virtual desktop.  If it is not in a virtual desktop, it hangs at loading the menu.

2.  Sound doesn't work.  I have tried both ALSA and OSS.

3.  If I enter a server, it crashes shortly after.  It's also real slow, which puzzles me, as my old PC was a third of the power of this one and it ran flawlessly.  Proprietary video drivers are installed.

Anybody know how to fix these things?

---

### Post by beastrace91 on 2009-10-31
I'd be willing to bet your Wine version is the culprit here! Try updating to the latest (1.1.32 as I write this) or if those do not work I know personally I have had good luck running CSS on Wine 1.1.28

Also be sure to check the link in my sig for suggestions on performance optimizations :)

~Jeff

---

### Post by BarfBag on 2009-10-31
Thanks for the reply!  I upgraded my version of WINE, and all of the problems listed were fixed.  However, a new problem has arisen.  Whenever I exit the game, it restarts X.  Is there an explanation for this?

---

### Post by beastrace91 on 2009-11-01
I would again bet this is a result of the Wine version. Try running it under 1.1.28 or .29 and see if the X restarting issue on exiting persists.

~Jeff

---

