---
title: "Screen Problems (Shifted to the left)"
date: 2008-11-14
forum: Server Platforms
---

### Post by Nigraffle on 2008-11-14
I just finished installing Ubuntu 8.10 Server Edition on my PC.  
I'm rearing to go, when my system boots up, and the left half inch of everything is cut off.  I have Ubuntu on two other systems, but this is my first time setting up a server, so I'm not particularly crafty with the CLI, so I decided to ask (and hopefully not waste your time) before seriously messing with anything.

The specs for my monitor and computer are at the following sites - 
[http://www.dell.com/downloads/us/products/optix/gx270_spec.pdf](http://www.dell.com/downloads/us/products/optix/gx270_spec.pdf)
[http://www.kdsusa.com/K2237mdwb.asp](http://www.kdsusa.com/K2237mdwb.asp)

and it's hooked up via VGA, if that's any help.  So, any ideas on how I'd fix it?  Thanks in advance.

   -Adam

---

### Post by Tomatz on 2008-11-14
Change your **refresh rate** in *system, preferences, screen resolution*. Just go up in **small steps** until it corrects itself and **dont go over 75** (just to be safe) ;)

Mine does this also.


[Edit] duh CLI

Hmmm not sure how to do this as you obviously dont have an xserver. Can you move the screen H position with the monitor menu options?

---

### Post by MJN on 2008-11-14
Most (all?) LCD monitors have an auto-configure option - available either via a dedicated hardware button or an option in the setup menu. Try this as one of adjustments it makes is that concerned with screen geometry (and positioning).
 
The resulting settings will usually be set for that specific resolution and refresh rate hence you might need to repeat the process when using another resolution/refresh (only once though).
 
You ought to do this anyway to ensure optimum clarity and sharpness.
 
Mathew

---

### Post by Nigraffle on 2008-11-17
*face-palm*  Thanks.  I feel like an idiot :P  Changing the screen settings worked like a charm.

---

