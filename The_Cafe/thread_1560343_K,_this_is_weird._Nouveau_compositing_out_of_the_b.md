---
title: "K, this is weird. Nouveau compositing out of the box??"
date: 2010-08-24
forum: The Cafe
---

### Post by murderslastcrow on 2010-08-24
I don't know what's going on. This is confusing.

So I have this NVIDIA card that worked with nouveau, but of course no compositing, on Ubuntu 10.04. So I slap Kubuntu Maverick Meerkat on a CD, and as soon as I go to try it, all the compositing effects are automatically enabled, including window previews. I'm not talking about the non-composited effects that are always present and quite nice (like widgets always supporting transparency, animations, glowing, etc. that occurs without compositing), I'm talking the real deal.

So I have to conclude one of three things.

1. The NVIDIA binaries are loaded by default on the LiveCD. This seems unlikely.
2. Maverick's KDE has a built-in software rendering version of Kwin.
3. Nouveau is included, with preliminary compositing support, in Maverick.

This is just weird. Anyone have any clues, or tried it themselves? I don't get how the driver could've loaded without ever being installed if it's the proprietary one. Also, I don't think it's the proprietary one, as some effects like wobbly windows are saying they are having issues being enabled, as they weren't before with the proprietary driver. I also have a very fast system which should be able to handle that, even off of a CD.

I'm intrigued. If this is working so well already, I think the NVIDIA proprietary drivers will soon be just as good as the ATi ones.

---

### Post by Mmmbopdowedop on 2010-08-24
> **murderslastcrow said:**
> <snip>I think the NVIDIA proprietary drivers will soon be just as good as the ATi ones.

I don't know about the rest, but the nVidia drivers at the moment from their site are already awesomenly good. 

And from experience, far better than any ATI.

---

### Post by murderslastcrow on 2010-08-24
Well, after installing Kubuntu Maverick, I can indeed confirm that there are no proprietary drivers installed on my computer, at all. All open, all working with compositing.

It's a tiny bit sluggish, but nothing that would interfere with regular use. I wonder if this will work for PowerPC computers, like a G4 iMac? That would be freaking amazing, as KDE 4 is much nicer than Aqua in Tiger, at least.

This is awesome, you guys. HOLY CRAP! It's open. This is... so cool. Lol.

But I had no idea Gallium and all that would be enabled by default. Maybe it's just KDE 4 using software rendering. I guess I should try it with vanilla Ubuntu as well to confirm it.

Still, this is good news.

---

### Post by murderslastcrow on 2010-08-24
Lol, I figured more people would find this news exciting for some reason. Well, I suppose if open drivers providing appropriate performance is now becoming commonplace, it's all the better for us. :D Now all we need is some way to get wireless drivers and firmware open and present in the kernel (Broadcom, basically).

Then Linux will by and large work 'out of the box' on pretty much everything.

---

### Post by lovinglinux on 2010-08-24
Great news.

Now they just need to make flash work without eating CPU cycles like that green little monster from Ghostbusters.

---

### Post by Simian Man on 2010-08-24
Like usual Ubuntu is 6 months behind Fedora :).

---

### Post by Ctrl-Alt-F1 on 2010-08-24
> **Simian Man said:**
> Like usual Ubuntu is 6 months behind Fedora :).
Yeah, current releases of Fedora already have 3d support in Noveau.

---

