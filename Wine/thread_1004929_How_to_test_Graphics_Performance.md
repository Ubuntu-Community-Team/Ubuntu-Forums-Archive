---
title: "How to test Graphics Performance"
date: 2008-12-07
forum: Wine
---

### Post by xarte on 2008-12-07
With appearance/visual effects set to 'none' and the ATI drivers enabled via Hardware Drivers, graphics seem to be running fine. 

However, before I go through the laborious process of installing Warcraft and hours of updates (no, I didn't copy them onto a disk first... I'm an idiot...), I'd like to check whether the graphics are going to display.

I'd prefer not to install a game as I want to keep my disk as clean as possible.

Is there some way I can evaluate my graphics card performance?

thanks,

Helen

---

### Post by asdfoo on 2008-12-07
> **xarte said:**
> With appearance/visual effects set to 'none' and the ATI drivers enabled via Hardware Drivers, graphics seem to be running fine. 

However, before I go through the laborious process of installing Warcraft and hours of updates (no, I didn't copy them onto a disk first... I'm an idiot...), I'd like to check whether the graphics are going to display.

I'd prefer not to install a game as I want to keep my disk as clean as possible.

Is there some way I can evaluate my graphics card performance?

thanks,

Helen

no, not without asking someone with the same setup, driver version, video card and warcraft version to test for you.

especially more so, since ati is such hit and miss compared to nvidia.

---

### Post by hikaricore on 2008-12-07
Mind you this isn't actually a reliable graphic benchmark, but you could try running
**glxgears** from a terminal window to see if the gears rotate smoothly and that
the FPS output is relatively steady.

The output will look something like this:

> [hikaricore@devistate:~ (300.4 Mb)]$ glxgears
[B]36099 frames in 5.0 seconds = 7215.242 FPS
35518 frames in 5.0 seconds = 7103.516 FPS
36386 frames in 5.0 seconds = 7272.217 FPS
35553 frames in 5.0 seconds = 7107.525 FPS[/B]


Notice how the rates are pretty steady.
Again this isn't a true benchmark but it will give you a rough idea.

I get between 50 and 120 FPS ingame on my nvidia card.

---

### Post by sellwowgold2 on 2008-12-07
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com),[sell ffxi gil](http://www.virdeal.com),[sell maple story mesos](http://www.virdeal.com),[sell gaia gold](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

### Post by xarte on 2008-12-08
Thanks for that, Hikari. Hmm.... I'm getting around 1230 FPS... roughly 1/7th of your performace, something like 7 to 20 FPS ...not promising, but then my daughter is currently on the Mac and it's running 20 FPS ingame. Possibly there's some ways to tweak performance that I haven't worked out yet. I'm pretty sure I turned off pixelshading... though that might have been on the previous install.

Well I guess I might as well give it a go, I never use up all my download limit... 

even if I can get it playable enough for dithering around and checking mail, I can kick the kids off the Mac for instances.

I'm having so much fun with Ubuntu on this old laptop that I'm fairly sure that when I get a new machine after Christmas, I'll run Linux on it. It'll be nice to run it on decent new hardware - but I'll be sure to make sure the graphics card is Linux-friendly!

---

### Post by hikaricore on 2008-12-08
glxgears fps are not an onpar ratio to ingame fps.
I just said to look for a steady rate and no studdering in the animation. :)

Let us know how the game works out for you, it may suprise ya.

---

### Post by xarte on 2008-12-08
ah. ok, good. I'll let you know. No stuttering - a good sign. A little variation, but mostly steady.

(Is that the monkey from 'The Hunger' in your avatar?)

---

