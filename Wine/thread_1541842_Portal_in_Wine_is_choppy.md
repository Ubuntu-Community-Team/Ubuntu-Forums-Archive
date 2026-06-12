---
title: "Portal in Wine is choppy"
date: 2010-07-29
forum: Wine
---

### Post by LunaticHiatus on 2010-07-29
So, I installed wine from the software center, used the OSS driver, installed the tahoma font, Installed steam, Downloaded portal, and ran it.

When there was no movement, the graphics looked fine. But as soon as I moved my character around. It would get really choppy. (lines and flat surfaces of black and white tearing threw)

So, I then added the ppa:ubuntu-wine/ppa to the software sources. It runs a LOT better now, but still kinda choppy. What could be the cause?

---

### Post by nhasian on 2010-07-29
hello LunaticHiatus,

what video adaptor do you have and which driver are you using?

---

### Post by LunaticHiatus on 2010-07-29
video adaptor?
Well, I am using a ati/amd proprietary FGLRX graphics driver

---

### Post by LunaticHiatus on 2010-07-29
bumpu

---

### Post by Jazzy_Jeff on 2010-07-29
It could be a problem with the ATI card. Driver support sucks for linux. One thing you might try is to disable visual effects. Right click on the desktop and click on Change Desktop Background. Then click on the Visual Effects tab and click on none. Hope this helps.

---

### Post by LunaticHiatus on 2010-07-29
since the graphics improved dramatically when I upgraded, I don't think its a driver issue. Perhaps something that needs to be tweaked in wine?

---

### Post by sandyd on 2010-07-29
> **LunaticHiatus said:**
> since the graphics improved dramatically when I upgraded, I don't think its a driver issue. Perhaps something that needs to be tweaked in wine?
try switching to opengl mode
ddr=opengl

and installing d3dx9/d3dx10 if you haven't done so already (if the game uses directx that is, ive never played portal)

---

### Post by LunaticHiatus on 2010-07-29
it uses DirectX 9.
is d3dx9 and d3dx10 in the repositories?

---

### Post by sandyd on 2010-07-30
> **LunaticHiatus said:**
> it uses DirectX 9.
is d3dx9 and d3dx10 in the repositories?

no, its in winetricks. however, winetricks is in the wine repository now, so just add the wine repository, upgrade wine, and install winetricks

---

### Post by nhasian on 2010-07-30
> **carlee said:**
> ive never played portal

thats a travesty.  At the 2008 Game Developers Choice Awards, Portal won Game of the Year, along with the Innovation Award and Best Game Design.

---

### Post by philinux on 2010-07-30
Move to Wine forum.

---

### Post by themusicalduck on 2010-07-30
In Steam, look under the games tab, highlight Portal and click Properties.

Somewhere in there should be "set launch options" or something like that. Click on that and put in ```
-dxlevel 81
``` (or 80, some people says 81, some 80, could try both.)

Hopefully that'll make the game run in directx 8 mode which is supposed to be smoother.

To be honest I never had much success running Portal in Wine, but using the dxlevel thing did seem to make some improvement.

---

### Post by sandyd on 2010-07-30
> **nhasian said:**
> thats a travesty.  At the 2008 Game Developers Choice Awards, Portal won Game of the Year, along with the Innovation Award and Best Game Design.
I unfortunately have the addiction of killing stuff. (Read Dead Redemption, SCII, BF2, COD:MW2.....)

---

