---
title: "Starcraft 2 in Ubuntu 10.10"
date: 2010-10-20
forum: Wine
---

### Post by Spectre5 on 2010-10-20
Hello,

I installed Starcraft 2 on my computer a long time ago while running Ubuntu 10.04.  Everything was great - it worked right out of the box on the first try (I did the mmdevapi=disabled audio fix).  I've never had any problems with it and EVERYTHING worked - campaign, multi-player, battle.net, chats, etc, etc.

However...this past weekend I upgraded my system to Ubuntu 10.10.  Now I have major audio problems and Starcraft also crashes every time I exit the game (regardless of what compatibility mode it is in).  The audio will usually begin to work when the game starts, but has a bad crackling sound to it.  It sometimes stays like that, or sometimes just suddenly stops playing any sound/music at all.

I've tried everything I can think of.  I've tried every compatibility mode.  I re-installed the game with PlayOnLinux and I used numerous different versions of Wine from there.  I've tried setting the sound to ALSA, OSS, and esound.  I've tried changing the default bitrate, in-game options, etc, etc...nothing has worked.

If I start the game, I can minimise it and start the sound preferences and it does correctly show the game in the "applications" tab and with audio being on.

My system is Ubuntu 10.10, nVidia 9500 GT (with the latest drivers).

lspci -v shows the following for my audio:
```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I've looked through countless posts on google, ubuntuforums, and one the wine appdb.  Any other ideas???  I'll post back if I find a solution...

---

### Post by beastrace91 on 2010-10-21
I didn't see it listed in your post, have you tried settings the option in your audio tab from "hardware" to "emulated"?

~Jeff

---

### Post by Spectre5 on 2010-10-21
> **beastrace91 said:**
> I didn't see it listed in your post, have you tried settings the option in your audio tab from "hardware" to "emulated"?

~Jeff

Hi, thanks for the suggestion, but I have tried that as well!  Any other ideas??

---

### Post by Spectre5 on 2010-10-22
I made the following changes:

PlayOnLinux advanced wine configuration -> multisampling = enabled (reduces the audio stutter for me)
PlayOnLinux wine configuration -> Audio -> esound
PlayOnLinux wine configuration -> Windows Mode -> Windows 7
PlayOnLinux wine version -> 1.1.40 (1.2* and 1.3* version give graphics problems...but didn't in Ubuntu 10.04)

HOWEVER....after restarting my computer, the audio problem is back!!! I checked and multi-sampling is still enabled...but at least the graphics problem is still "solved."  I still get a crash on every exit as well.

---

### Post by beastrace91 on 2010-10-22
Highly recommend you try crossover games... It supports SC2 very well.

~Jeff

---

