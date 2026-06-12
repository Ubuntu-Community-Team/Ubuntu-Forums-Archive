---
title: "Combat Mission Barbarossa to Berlin"
date: 2006-03-01
forum: Wine
---

### Post by kudu on 2006-03-01
I got this game to run but it's another one with sound issues. Has anyone else gotten this puppy working ? Is there a sound fix ?

I want to experiment with jackd. How do you set it up to work with cedega ? Anyone done this already ? Appreciate some help!

kudu...out

---

### Post by Bokonon on 2007-06-22
Any chance on posting how you got that far?  I am happy with no sound...better than no game.

I am interested in all 3 of the classic CM games.

---

### Post by Cannaregio on 2007-11-25
> **Bokonon said:**
> Any chance on posting how you got that far?  I am happy with no sound...better than no game.

I am interested in all 3 of the classic CM games.h 

Me too.
Bump.

Trying wine with CMBO (the older of the three CM) and it says could not initialize 3d graphic.

Any help?

---

### Post by Cannaregio on 2008-02-08
Bump

---

### Post by Vadi on 2008-02-08
Tried with the latest wine version?

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Cannaregio on 2008-02-09
> **Vadi said:**
> Tried with the latest wine version?

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Yep, I have the 9.54 already.
Screen comes up black. No graphic. 
"Could not initialize 3dGraphics"

Anyone can help?

Here the relevant messages:
```
.wine/drive_c/Program Files/Combat Mission 2$ wine CombatMission2.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x34f710,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d7:IDirect3DImpl_7_CreateDevice (0x2ce0030): Only one Direct3D device per DirectDraw object supported
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

---

### Post by Cracauer on 2008-05-20
You need Cedega.

I also had to use the non-cd patches last time I tried.

The sound is a little goofed up, I didn't notice it's really bad.

---

### Post by Cannaregio on 2008-11-23
Ok, I managed it, had to use cedega, alas, wine as per november 2008 is still not able to run CMBB ([combat mission barbarossa to berlin]("http://www.battlefront.com/products/cmbb/cmbb.html"), the best combat mission of them all).
Everything works, graphic, music and all.
Incredible game/simulation, as old as the cuckoo, yet still the best tactical/strategic game/simulation on this planet. 
You'll enjoy playing it for [COLOR="#0000ff"]years[/COLOR] (not weeks, not months... this is as additive as software can be and you can spend a life studying [a bazillion of different tactical and strategical related advice]("http://www.battlefront.com/community/forumdisplay.php?f=42"))

Here is a short -hope complete- HOW-TO
----------------------------------------------------
How to run CMBB in GNU/Linux

1 ) Obtain cedega 6.0.2 total and cedega 6.0.5 engine

for instance:
[COLOR="Blue"]TransGaming_CEDEGA_v6.0.5_Pro.ra[/COLOR]r 

2 ) Install cedega 6.0.2 for debian
[COLOR="#0000ff"]cedega-small_6.0.2_all.deb[/COLOR]

3 ) now launch cedega from transgaming --> cedega

4 ) choose transgaming --> install local update

5 ) navigate to the cedega 6.0.5 engine
```
cedega-engine-6.0.5-local-update.i386.cpkg
``` and install it (takes only half a second)

6 )Insert the CMBB disk or launch a virtual iso 

7 ) choose install, create a game folder and navigate to the [COLOR="#0000ff"]setup.exe[/COLOR] (installation file) in the CMBB disk

8 ) Install CMBB as you would do in windows (takes very long)

9 ) Now get the no-cd patch from the web

10 ) Copy the patched file [COLOR="#0000ff"]CombatMission2.exe[/COLOR] to the CMBB folder inside .cedega/c_drive/Program Files/Combat Mission 2 overwriting the original CombatMission2.exe (or save first a copy of the original CombatMission2.exe if you so prefer)

11 ) Launch Combat Mission from Cedega

12 ) When presented with the graphic display [COLOR="#0000ff"]BE CAREFUL[/COLOR]: the maximum proposed resolution might push some of the commands too much over the lower edge of the screen, so be prepared, if this should happen, to delete the file
[COLOR="Blue"]Combat Mission BB Prefs[/COLOR] 
and restart cedega-CMBB again, choosing aslightly lower resolution.


That's it... uff!

---

