---
title: "StarCraft under Wine unbearably slow"
date: 2009-02-22
forum: Wine
---

### Post by Aikon- on 2009-02-22
Hi all,

I am trying to get StarCraft (specifically, BroodWar) working on my desktop and/or laptop, preferably the former.

The problem on my desktop (AthlonXP 2500+, ATI Radeon 9600xt) is that the game is effectively frozen if I let Wine try to draw full-screen. If I use winecfg to emulate a virtual desktop (i.e. play in windowed mode), I can at least get around in the game, but my CPU is spiked and it is horribly slow -- so much so that when playing on b.net, people quit any game I join almost immediately.

I tried adding the DirectDrawRenderer 'opengl' key, however all I get is a flickering white screen when I try to run SC/BW. This happens in both windowed and full-screen modes.

This computer should be more than capable of playing SC; a couple of years ago I had it playing WoW at almost the same speeds as under Windows. Any help with getting this working would be greatly appreciated =)

-Aikon

---

### Post by NightMKoder on 2009-02-22
From Wine's AppDB for Starcraft ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=149):](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149):)

> 
Cure for slowness

If the game runs slow on your machine then look at [this page]("http://wiki.winehq.org/UsefulRegistryKeys")

Use the key "DirectDrawRenderer" and add that to your registry with the value "opengl"; you may also need to add the key "RenderTargetLockMode" with the value "readtex".

(Found under HKEY_CURRENT_USER/Software/Wine/Direct3D using regedit)

If the above trick does not work, or causes your Starcraft to crash on launch:

- Remove the DirectDrawRender registry entry.
  - Use your Wine Configuration utility to set Emulate Virtual Desktop to on, resolution 640 x 480. 


See if any of that helps.

---

### Post by Aikon- on 2009-02-22
> **NightMKoder said:**
> From Wine's AppDB for Starcraft ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=149):](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149):)



See if any of that helps.

Thanks, but as you can see from my original post, I have already tried these and am still experiencing unbearably slow performance.

-Aikon

**Edit:** maybe it wasn't clear, but I also set the target lock mode to readtex when setting DD renderer to opengl.

---

### Post by YokoZar on 2009-02-22
This is a fairly well-known problem in Wine caused by the lack of something called a DIB Engine.  Interestingly, this is the same reason why AutoCAD still doesn't work - we fix StarCraft, and all of a sudden an engineering drawing program starts working as well.


Anyway, the DIB Engine has been a long project in Wine that's still being worked on.  One reason it's been so long is that the engine itself needs to be nearly perfect before it can be included at all, otherwise there will be huge regressions in already working (albeit slow) applications like StarCraft.

---

### Post by bmitov on 2009-04-08
Any idea when the DIB engine is going to be finished?

Cause SC is just really "laggy" in game, not as smooth as if it were run on Windows.

---

### Post by TheBuzzSaw on 2009-04-08
You might consider using Virtual Box, though it takes more time to configure.

---

### Post by asdfoo on 2009-04-08
The slowness is also probably reflected by your computer specs somewhat too.  I see reports on the Wine AppDB where no slowness is mentioned.  ati 9600 is quite old, I got rid of my ati 9800 three years ago and went with nvidia which is much better for Wine

---

