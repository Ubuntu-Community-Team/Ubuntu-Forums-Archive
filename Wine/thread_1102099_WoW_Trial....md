---
title: "WoW Trial..."
date: 2009-03-21
forum: Wine
---

### Post by wolfyking2 on 2009-03-21
Ok, so I decided I would try the trial, because i've never played the game before.  Install went smooth, seems my card can handle the graphics, choosing the world is fine...but when I press 'New Character' it crashes.  I got it to the char creation once, but when I clicked on the class 'rogue' it crashed.  It was very specific, I had to do usa servers, shattered hell world, then it got to char creation, but it doesn't work anymore.  Help!

---

### Post by wolfyking2 on 2009-03-21
nvm, fixed it, but the game was too laggy too play.

---

### Post by khelben1979 on 2009-03-21
What are the computer hardware you are using with WoW? Also, are you using native graphic drivers?

---

### Post by stimpack on 2009-03-21
follow some of the guides about wow, WoW runs very nicely indeed.

---

### Post by hikaricore on 2009-03-21
You're going to need a decent Nvidia or at the very least an ATI card to run WoW properly.
If you have an integrated intel "video" chipset you're likely out of luck.

Using Nvidia or ATI be sure you have the latest proprietary drivers installed and that you are running the game in **OpenGL** mode!

---

### Post by khelben1979 on 2009-03-21
Check this out: [WoW Wiki]("http://www.wowwiki.com/Wine").

---

### Post by wolfyking2 on 2009-03-21
Yess, I have an intel card, and am running the game in openGL.

---

### Post by hikaricore on 2009-03-21
> **wolfyking2 said:**
> Yess, I have an intel card, and am running the game in openGL.

There's your problem, Intel is hit and miss with programs that require high end graphics under Linux.
Intel chipsets rely heavily on DirectX in the Windows environment and often have very lacking OpenGL support.
They share memory with the rest of the system so this is also an issue in some cases.
Some Intel users have luck running games in D3D mode (somehow) but this is strange because D3D mode is just converted to OpenGL via WINE, there is no real DirectX functionality under Linux.

Hope this explains things a little better.  By all means keep trying things, but you may just want to get a real video card.

---

