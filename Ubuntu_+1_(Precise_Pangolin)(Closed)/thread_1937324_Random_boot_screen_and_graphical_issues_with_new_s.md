---
title: "Random boot screen and graphical issues with new setup"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by daltonlaffs on 2012-03-07
So I got together some new hardware and installed 12.04 B1 (64-bit) with the Alternate disc, in order to use the encrypted LVM feature.

My vid card is the Nvidia GTS 450. When I first installed the encrypted LVM, it booted to an empty purple screen, then went black and stayed that way. However, I had a hunch and typed my password anyway. My hunch was correct -- the boot process wasn't showing anything on-screen for some reason, but I *was* able to put in my password, and when Unity took over, the graphics came back.

Installing the proprietary drivers didn't help with the invisible password entry screen. I started to experiment at this point and found some old script online called "fixplymouth", which had a useless but interesting effect -- now the boot process just stayed at that initial blank purple screen until I got to Unity, instead of going black.

Also worryingly, after I log into Unity, the background momentarily glitches up. It appears to be a random assortment of pixels, but sometimes I can make out vertical stripes in the patterns. It fixes itself after my desktop wallpaper loads.

I've also been noticing other small oddities. For example, sometimes when accessing a pulldown menu (right-click menus, etc), a selection of the left side will be invisible until I mouse near it.

The system seems stable otherwise, and I'm even capable of running some video games (Wine's compatibility with Steam games sure is amazing these days...) with absolutely no problems. However, Compiz occasionally crashes for no discernable reason, which probably has something to do with all this.

Anyone have any ideas what could have gone wrong here? :confused:

PS. The shutdown version of the "boot screen" shows up *sometimes*. Other times, it's just terminal output, and other other times, it's that weird purple screen again. Shutdown never fails, though.

PPS. My new CPU is an Intel i5 2500k, which has some integrated graphics. Could this have anything to do with these issues? Some kind of conflict?

PPPS. If I totally disable my internal graphics (but not my Nvidia card), I get a flashing _ and a black screen during the boot -- apparently an empty terminal display. So I think my earlier hypothesis that it has something to do with an integrated-versus-PCI conflict might have some merit; is there any way to force the loader to use my Nvidia card?

---

### Post by cariboo on 2012-03-07
Welcome to the joys of running a testing version, only a little over two weeks until Beta 2. :)

---

### Post by grahammechanical on 2012-03-07
The log in screen is controlled by something called LightDM. It seems that LightDM is not loading for some reason. Or may be not installed.

Synaptic Package Manager is not installed by default any more but you can install it from the software Centre and then use it to re-install LightDM and associated packages.

That might fix the issue about not having a log in screen. As for the graphical glitches between log in and the desktop loading, well that is another matter.

I have something similar. I though that it was due to my messing around with the LightDM background image settings by using something called Simple LightDM Manager. But the idea has now entered my head that I might need to go back to an earlier version of the Nvidia driver. There have been a few revisions of the Nvidia driver over the last few months.

As for the ghostly menus, I get that. It goes away once I start accessing the menus. It is something to do with Compiz. We have had several Compiz updates as well.

Regards.

---

### Post by daltonlaffs on 2012-03-07
I'm adding another odd observation to the main post: If I totally disable my internal graphics (but not my Nvidia card), I get a flashing _ and a black screen during the boot -- apparently an empty terminal display. So I think my earlier hypothesis that it has something to do with an integrated-versus-PCI conflict might have some merit; is there any way to force the loader to use my Nvidia card?

@cariboo907: Heh, that's the truth. Don't worry, I know this is the kind of thing I was signing up for when I put in the beta disc instead of the stable.

@grahammechanical: Actually, no, it's not LightDM I was talking about. When you use an encrypted LVM, as opposed to a normal Ubuntu install, you're *supposed* to get a password entry screen during the boot procedure, before LightDM starts. (LightDM itself is stuck in the encrypted partition.) LightDM works fine, although now that I think about it, those weird patterns emerge before and after I log in with LightDM.

---

### Post by ventrical on 2012-03-07
Welcome to the "bug of the century" :)

[http://ubuntuforums.org/showthread.php?t=1925194](http://ubuntuforums.org/showthread.php?t=1925194)

---

### Post by daltonlaffs on 2012-03-07
Huh, looks like I'm far from the only one experiencing *that* part, then. That implies that the weird patterns before and after LightDM login are irrelevant to my boot password issue.

That being the case, does anyone know of anything I could try to get the boot password screen to reveal itself?

---

### Post by alphacrucis2 on 2012-03-07
I get the graphic glitches too between login and the loading of the desktop. Appears to be something to do with the nvidia blob.

---

