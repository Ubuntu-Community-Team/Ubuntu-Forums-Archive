---
title: "Any suggestions to make Fallout 3 more stable?"
date: 2009-10-11
forum: Wine
---

### Post by MetroidJunkie2008 on 2009-10-11
After patching Wine 1.1.30 and Fallout 3 runs. Using a mod, I bypassed the infant stage to avoid the engine hanging at that spot but, when I try to enter the next room, the Vault Atrium, it crashes with a "This program has made a fatal error and needs to be shut down", the kind of crap it would give an unpatched version while starting up. 

    I already followed the steps in Winehq, including regedit directx, downloading dlls, patching, etc. and nothing seems to work. If that one room of the vault works, surely that means the graphical engine itself is operationable?

---

### Post by roob85 on 2009-10-12
i have the same problem with fallout3 crashing when your an infant...what mod did you use to bypass this?

---

### Post by MetroidJunkie2008 on 2009-10-12
[http://www.mediafire.com/?jwxn4hk9bj0](http://www.mediafire.com/?jwxn4hk9bj0)

Since I couldn't find it, I uploaded it to a file host for you. It bypasses infant stage, taking you straight to gender, name, face, SPECIAL, and skills. Still can't get into the Atrium yet, though, it gives the same crash that an unpatched wine would get at start.

---

### Post by MetroidJunkie2008 on 2009-10-18
I just tried teleporting to Megaton, it crashed with that. Any suggestions to get Fallout 3 beyond the first Vault room?

---

### Post by beastrace91 on 2009-10-18
Tried other versions of Wine?

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

~Jeff

---

### Post by MetroidJunkie2008 on 2009-10-18
Any wine versions, in particular, you'd recommend for Fallout 3?

---

### Post by Progressive on 2009-10-19
True, performance can vary greatly between different versions of WINE. The latest version of WINE, 1.1.31 lists a bunch of DX10 improvements, and 1.1.32 will be out in 4 days with even more 3D improvements.

Though, one thing I notice is that when using linux or WINE, people are quick to blame either Linux or WINE even when it might be the fault of something else.... the game, drivers, etc.

Drivers
-------

Maybe you already have the latest drivers for your video card, but I'm sure others reading this thread might not. Phoronix is the best place to check for that.


Patching
--------

Also, do you have the latest official game patch from Bethesda?

[http://fallout.bethsoft.com/eng/downloads/updates.html](http://fallout.bethsoft.com/eng/downloads/updates.html)


Tweaking
--------

Furthermore, some of the issues can probably be fixed by tweaking the game engine itself:

[http://www.tweakguides.com/Fallout3_1.html](http://www.tweakguides.com/Fallout3_1.html)


FallOld
---------

The good people of Oldblivion have made a project known variously as FallBack, FallOld, and OldFallout.

[http://www.oldblivion.com/sm/index.php?topic=5831.msg69573#msg69573](http://www.oldblivion.com/sm/index.php?topic=5831.msg69573#msg69573)

Since WINE works much better with older versions of DirectX and Shader Model, using this hack should give added stability.

[http://www.oldblivion.com/sm/index.php?topic=5828.msg71249#msg71249](http://www.oldblivion.com/sm/index.php?topic=5828.msg71249#msg71249)

Looks like there may have been more work done in the past year since that stuff was written.... one guy called Permalite claims to have made some extra progress on the shaders, but I couldn't find any links to his work. That said, those guides seem to be enough to get something mostly working.


Nif Optimization
---------------

There is another cool performance improvement that worked with Oblivion, and it seems new versions of the program list Fallout 3 as supported. This is mostly for a framerate boost

[http://cs.elderscrolls.com/constwiki/index.php/Nif_Optimization](http://cs.elderscrolls.com/constwiki/index.php/Nif_Optimization)

(be sure to make backups of the original NIF files, but if it works it can provide a performance boost with no quality loss)

---

### Post by MetroidJunkie2008 on 2009-10-20
[http://www.fallout3nexus.com/downloads/file.php?id=8992](http://www.fallout3nexus.com/downloads/file.php?id=8992)


 I think I found a solution, this skips you right to the exit, the capital wasteland's working great so far. Thanks for the performance boosting mod, though, I'll have to grab it. :)

---

