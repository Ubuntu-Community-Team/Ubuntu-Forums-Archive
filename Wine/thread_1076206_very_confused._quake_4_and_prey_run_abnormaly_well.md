---
title: "very confused. quake 4 and prey run abnormaly well."
date: 2009-02-21
forum: Wine
---

### Post by d3drocks on 2009-02-21
hey,
Ive disscussed this on the 3DRealms forums a bit, and no one seems to know why this happens.
it seems games running ID Technology get a performance boost when in wine, in comparison to their native linux versions, and being run in windows. my older PC could only run prey on medium, and would get an OK framerate when in windows. I put it in wine, and it could run the game on ultra, with a few settings lowered due to my videocard.
Quake 4 did the same thing, (and so did doom 3 as well).
I've no idea why this happens, and am interested if anyone else knows.

---

### Post by Ferrat on 2009-02-21
> **d3drocks said:**
> hey,
Ive disscussed this on the 3DRealms forums a bit, and no one seems to know why this happens.
it seems games running ID Technology get a performance boost when in wine, in comparison to their native linux versions, and being run in windows. my older PC could only run prey on medium, and would get an OK framerate when in windows. I put it in wine, and it could run the game on ultra, with a few settings lowered due to my videocard.
Quake 4 did the same thing, (and so did doom 3 as well).
I've no idea why this happens, and am interested if anyone else knows.

Sounds like (what I call) a fake FPS boost, WINE not having everything implemented skips some calls, specially with the "WINEDEBUG=-all" so it just ignore it and move on = no real action, and doing nothing is faster than anything else :P 
In many ways this stuff is more or less useless but you won't really get all the effects etc that you think you get, since wine uses the same OpenGL calls just converted from Direct3D there is no way that you get a "real" boost in FPS.
EDIT:
Well in theory it could be that the Linux version very unoptimized and that slows it down but that sounds unlikely.

---

### Post by d3drocks on 2009-02-21
> **Ferrat said:**
> Sounds like (what I call) a fake FPS boost, WINE not having everything implemented skips some calls, specially with the "WINEDEBUG=-all" so it just ignore it and move on = no real action, and doing nothing is faster than anything else :P 
In many ways this stuff is more or less useless but you won't really get all the effects etc that you think you get, since wine uses the same OpenGL calls just converted from Direct3D there is no way that you get a "real" boost in FPS.
EDIT:
Well in theory it could be that the Linux version very unoptimized and that slows it down but that sounds unlikely.


actually, in prey's case, it could be likely that the port sucks, as the guy who did is aparently known for not even finishing that stuff. as for quake 4 and doom 3, ID Software seems to always hire geniuses (I believe john Carmack was the guy who did the first side scroller on pc) so i dont think thats something they would skip over.

and if wine is just skipping rendering calls, i dont see much of a difference in the graphics (its the litte things maybe?), but even if it is just a framerate boost, its nice to have nonetheless.

---

### Post by Dizzle7677 on 2009-02-21
> **d3drocks said:**
> and if wine is just skipping rendering calls, i dont see much of a difference in the graphics (its the litte things maybe?)
 
Simple answers:
1.Could be something else other than the rendering engine - sound(ALSA/OSS) versus the wine Directsound implementation.
2.OpenGl<->OpenGL32
3.Nothing is 'skipped', unless your hardware doesn't support a certain GL extension - which is something entirely different.

---

