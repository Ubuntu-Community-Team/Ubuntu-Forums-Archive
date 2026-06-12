---
title: "Should ATI users go Aiglx or XGL?"
date: 2006-08-29
forum: The Cafe
---

### Post by NoTiG on 2006-08-29
im kind of out of the loop sorry. BTW i have a mobility radeon 9600

---

### Post by gruvsyco on 2006-08-29
It depends on if your card is supported by fglrx and your stance on the whole X thing.

OS politics aside... I have XGL running on Dapper and AIGLX running on Edgy.  I have some issues with the AIGLX setup interfering with Blender on redrawing the screen.  As far as Compiz goes though, performance seems to be about equal for that which I have running.

To run XGL, I think you will need to run ATI's binary driver while, AIGLX to my knowledge does not yet work with ATI's binary although it may soon (or has very recently).

---

### Post by ricesteam on 2006-08-29
I'm interested in this as well: Does ATi work with AIGLX yet?

Edit, just found this: @ [http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx)

> 
**Known to not work**

ATI: Radeon 9500 through X850 (r300 and r400 generations). Some issues with rectangular textures may be fixed in new DRM CVS, need to verify.

ATI: Rage 128. Looks like driver locking issue.

ATI: Mach64. No DRM support in Fedora, still insecure.

Matrox: MGA G200 to G550. Needs at least a driver update to fix DRI locking. PCI cards probably have other issues as well.

nVidia: Any. No open DRI driver. Closed driver support coming soon though.

3dfx: Voodoo 1 and 2. No DRI driver.

ATI: Radeon 8500 through X850 with the closed fglrx driver. Uses an ancient version of the DRI driver API that can't work with the new driver loader. No ETA on closed driver support.

Anything without a free 3d driver. 



---

### Post by atrus123 on 2006-08-29
My ATI card only works with the binary driver.

This means, since AIGLX requires the xcomp* extension (or whatever it's called), I have no choice but to use XGL, considering that that extension will not work at all with the binary driver.

---

### Post by Corvillus on 2006-08-30
With a 9600, definitely XGL. AIGLX only works well with open source drivers, and the 9600 doesn't support 3D acceleration on open source drivers. XGL should work though.

---

### Post by prizrak on 2006-08-30
I would say generally XGL is better than AIGLX. The former is an actual OpenGL based X server that will free up your CPU. You don't have to run Compiz on top of it if you don't want all the effects that will take up your resources. AIGLX is meant for nothing but eyecandy, it is a Xorg extension that will make pretty transitions but will still use CPU.

---

### Post by NoTiG on 2006-08-30
thanks for the input guys. going XGL and binary drivers

---

### Post by MaximB on 2006-09-11
what about ATI radeon 9800 ?
XGL or AIGLX ?

---

### Post by nirudha on 2006-09-12
Hi Max,

I think you can probably gather as much from the previous post.. but anything over 9500 (inclusive I think) you should be going for XGL running on top of the xorg X server. This is how I run my 9800XT.

There is however a big downside with this setup. You lose the ability to run 3d apps, e.g. Google Earth, Blender, etc. Actually there is a hack to make them run on an alternative display number. Did this but didn't like the way it worked. You also lose accelered video which is a bigger negative for me. What I do is have two sessions setup which lets me choose what I want. So if I want to show some of the advancements coming to Linux GUI's I can show it to my friends but for day to day work I use the non XGL session. You can find planty of how to's on this by looking for "start-compiz.py" on this forum or at compiz.net

Try it out. Hope for new AIGLX supporting ATI drivers or alternatively the replacement X server, XGEL?

Cheers!

p.s. you may want to install the elinks text web browser before you start playing with this stuff. so if you mess up the GUI you can still have web access to find a fix.

---

### Post by horatiub on 2006-09-17
I have an ATI Mobility X600.

Should I go with XGL or AIGLX?

Thank you

---

