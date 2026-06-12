---
title: "Extrascreenular 3D interface"
date: 2008-08-26
forum: The Cafe
---

### Post by zmjjmz on 2008-08-26
So here's the idea:
Combine Camspace (a Linux version of course, it won't be out yet), Compiz w/Anaglyph, Freewins, and Wiimote headtracking, OnBoard (a virtual keyboard for Linux), and 3D (the red and green kind) glasses with that IR thing mounted on them, and MPX.
What you would get is window management with your hands or other flat, brightly colored objects (responsibility: Camspace) that pops out at you _and_ follows your head.
With multiple hands. (maybe MPX/Camspace could have one digit == one mouse?)
And a virtual keyboard that pops out at you too. (OnBoard + Freewins [when they get Input Redirection working]).

So it's a bit futuristic, but if Freewins can get Input Redirection working and the Camspace people make their code OSS and have a Linux version that's compatible with MPX, we could have a really awesome extrascreenular interface.

---

### Post by klange on 2008-08-26
This is why I wrote the Wiimote headtracking plugin (which should work with a really old version of the Wiimote interface plugin, I don't know if the new "version 2" of the Wiimote plugin sends out the right data) in the first place.

Anaglyph needs some hacks to actually work in 3d space (it fakes it at the moment). You also need to remove some restrictions that have recently been placed in Freewins to keep it from rendering when the screen is transformed (or you can't use Wiitrack).

And input redirection itself already works and has been somewhat tested (it's an old and buggy patch, but otherwise working).

---

### Post by zmjjmz on 2008-08-27
Uh, bump?

---

