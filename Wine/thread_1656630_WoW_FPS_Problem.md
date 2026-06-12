---
title: "WoW FPS Problem"
date: 2010-12-31
forum: Wine
---

### Post by sylosis on 2010-12-31
Hi, i am experiencing low FPS in World of Warcraft.

I am using 10.04 LTS and wine version 1.2 with a GeForce 9500 GT card with the proprietary drivers.

If someone can tell me how to get the terminal output i can give you that.

I get around 15-25fps in most areas which is fine but it gets annoying when in the more populated areas as it drops to around 2-5fps. Whereas in windows i used to get around 50-60fps.

I have everything set on the lowest settings in the ingame settings, but if you look at the following picture, you will see that the game doesnt allow me to select anything higher.

[http://oi53.tinypic.com/2w22d5u.jpg](http://oi53.tinypic.com/2w22d5u.jpg)

Also, when i press 'play' on the launcher, the sound plays fine, but after that, i get no ingame sound, this isn't too much of a problem as most of the sounds annoy me anyways, but if its an easy fix then i might aswell ask.

any help is appreciated, thankyou

---

### Post by ronnielsen1 on 2010-12-31
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

Have you done the tweaks suggested at winehq?

---

### Post by sylosis on 2010-12-31
Yes i have tried all the things that apply to me but none of them helped, even using opengl didnt increase fps at all :(

---

### Post by disabledaccount on 2010-12-31
- Disable compiz/desktop effects.
- Check if hw acceleration is working: >glxinfo | grep render
- Verify if your results in Unigine, glxgears, etc. are comparable to others
- Update wine to newest version - v1.2 is very old.
- Disable debugging in wine: >export WINEDEBUG=-all
- Try different registry settings, gfx-related (direct3D, opengl, X11)

---

### Post by sylosis on 2011-01-01
hey thanks for the reply

1. disabled it and got a slight fps increase, nothing major though just 1-2 fps

2. direct rendering: Yes
OpenGL renderer string: GeForce 9500 GT/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

3. not sure what you meant by this one, im not too good with ubuntu.

4. i went to upgrade it from the wine site and it says 1.2 is the most recent stable version, the later version is still beta. should i install the beta?

5. + 6. again im not too sure what you meant by these.

cheers

---

### Post by Tweak42 on 2011-01-01
I *think* if you launch the game using the Launcher.exe it doesn't use opengl (or it didn't for me the the past) so I always launch the game directly using "wine Wow.exe -opengl" just to be sure.

What version nvidia drivers are you running?
Have you tried running the game in windowed or windowed (fullscreen) mode?

You can try out wine 1.3 to see if it makes any difference, but Wow performance has been pretty close between stable and developer versions.  Developer versions tend to be for stability, graphical bug fixes and support for newer hardware but that sometimes introduces new bugs.

---

### Post by cwwilson721 on 2011-01-01
1.3 works perfectly fine for WoW Cata. I've been running it since it became available

Look at the wine website for how to add 1.3 to your system.

As for low FPS, it's a combo of MANY things:

A 9500GT is NOT a good card for games. The amount of data it can pump out is almost too low, even for WoW (Which, by the way, is getting more and more graphics heavy EVERY patch. My FPS on a 9600GSO-768MB/AMDx2/4GB went from 60-70 to 45-55 from WotLK to Cata. And my 9600GSO has WAY more memory path width(192 vs 128 ), ROPs, and cuda cores(96 vs 32) than your 9500GT).

Another bottleneck is memory. A min amount to even THINK of running WoW/wine is 2GB, 4GB REALLY makes a difference.

And your CPU is THE biggest bottleneck (after graphics). Even though WoW is a "single core 32bit app" it is such a resource hog that at a min, you should have a 2core, and more cores are even better. A quad-core will make things run MUCH better. And Ghz helps.(Guess what my NEXT upgrade will be? A mobo and 6+ core 3+Ghz CPU)

So, in conclusion, your FPS with a 9500GT is NOT going to be high. And if you have a dualcore or less CPU, even lower, and lower memory, even less.

Hope this explains things a bit.

---

### Post by sylosis on 2011-01-01
Thanks for the reply,

i have 4GB RAM so that shouldn't be a problem, my CPU is very old, single core, its just awful. however in windows i got 50fps easily in the major cities/sanc's so i figured theres no need to upgrade it.

i do however realise that wine will not be the same as running it in windows, do you think a CPU upgrade would drastically improve the fps?

cheers

---

### Post by sylosis on 2011-01-01
sorry tweak42 didn't see your post, i tried it in windowed mode and it didnt make much of a difference

i am using 'NVIDIA accelarated graphics driver (version current)(recommended)'

and i will give 1.3 a try and let you know

cheers

---

### Post by cwwilson721 on 2011-01-01
If you want as much FPS as you can, turn down EVERYTHING. NO AA, no shadows, close view distance, EVERYTHING.

Then, turn things up a bit at a time, until you get a happy medium between FPS and "eyecandy" (When I raid, my view distance is low, but I have my particles on medium. I'd rather have higher DPS than having LK look good...)

---

### Post by disabledaccount on 2011-01-01
> **sylosis said:**
> 3. not sure what you meant by this one, im not too good with ubuntu.

4. i went to upgrade it from the wine site and it says 1.2 is the most recent stable version, the later version is still beta. should i install the beta?

5. + 6. again im not too sure what you meant by these.

cheers3. There is Unigine demo/benchmark available both for windows (wine) and for linux. glxgears is standard test application for opengl (not a benchmark really, but gives some overview about opengl 3D performance)
4. I've observed better performance with new wine (1.3+) in many games, so i recommend to upgrade it. Besides, in case of wine "stable" means it passes every cross-platform tests, not that it is stable in every game or programm.
5, 6: You should read wine documentation - most important settings are stored in registry. Registry settings are described here:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)
but its worth to mension, that descriptions here are not completely in sync with newest versions of wine.

---

### Post by Tweak42 on 2011-01-01
> **sylosis said:**
> sorry tweak42 didn't see your post, i tried it in windowed mode and it didnt make much of a difference

i am using 'NVIDIA accelarated graphics driver (version current)(recommended)'

and i will give 1.3 a try and let you know

cheers

It sounds like you are using a older Nvidia driver that shipped with your distro, installed with the "Additional Drivers" app.  If you don't have a Nvidia settings application in your "Administration" menu like pictured here: [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html) setup the PPA in the guide and update your drivers to the latest (260.19.29 as of this writing).

The PPA site for the latest nvidia driver is here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

And while you are at it you can also also add the ubuntu wine ppa for wine 1.3:
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

