---
title: "X2go Quality Settings Guide?"
date: 2016-12-22
forum: Server Platforms
---

### Post by mattlach on 2016-12-22
Hey all,

I usually tun all my servers command line only, but there are a few pieces of software I want running on my VM server that unfortunately require a GUI.  

My solution to this was to set up an LXC container with 16.04 server edition in it, install the base lxde without Xorg (don't want to waste that precious KVM/LXC RAM) in the container, as well as install the X2go daemon and manage it remotely on my workstation using the X2go client.

It was surprisingly much easier than I thought it would be to get it to work, but I'm stuck on the quality settings.

The default setting appears to be 16M Jpg, which if I google it, some suggest uses way too much bandwidth.   (doesn't look like it to me)  I still found text quality to annoy me.   So I switched to nopack (which I assume is just rawimage data).  I think this looks better, but I am not sure, it's subtle. I expected this to have a huge bandwidth impact, but it doesnt appear as if it does.  It seems to stay at only ~60kb/s which is perfectly fine for gigabit LAN.  The difference with 16M PNG seems imperceptible compared to nopack, but the bandwidth use seems to stay approximately the same too?  The fonts are still not perfect for some reason, and kerning is awful, maybe I need to dig into LXDE's default font rendering settings or something)

Anyway, there are a ton of quality settings, and I'm not sure what they all mean.   Does anyone know where I might find more documentation regarding this?   Googling it, I have found surprisingly little.   Does anyone know where I might find more information regarding the differences between the settings.   I've tried to understand them just by name, like "16m jpg" but it is not clear to me what all of the different settings mean.

Any assistance appreciated.

---

### Post by mattlach on 2016-12-22
Actually, the bandwidth doesn't seem to change much regardless of what setting I choose.    I've just been closing the x2go client window, changing the setting and logging back in again, as I want to keep the session active and not kill the running processes.  Maybe I need to log out and log back in for the changes to take effect?

---

