---
title: "Issues with a few WINE games."
date: 2009-06-20
forum: Wine
---

### Post by Cadeyrn on 2009-06-20
I'm running 64-bit WINE 1.1.20-23 (depending on what fix I'm trying now, but 20-23 all act the same on my computer) on x64 Jaunty. Guild Wars works in every way possible besides the fact that it crashes when it begins to load any area, rendering it unplayable. STALKER, upon launch, gives me the WINE version of the popular Windows error, "<app name> has encountered a serious problem and needs to close." The only x32 packages I'd need for x64 WINE that I don't have are the build dependencies, which are useless right now because I'm not trying to compile x32 WINE. Plus my computer isn't able to install them for some glitchy unknown reason.

Before reading the output of my problems, I believe my problem is related closely to the fact that Steam through WINE and its apps randomly stopped having any sound at all, ever, with ALSA and OSS.

The STALKER Terminal output, from launch to error message, is this:

```
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x113fd8 0
fixme:heap:HeapSetInformation 0x110000 0 0x32f990 4
```

The Guild Wars Terminal output from launch to crash is much longer, so it's an attachment.

EDIT: By myself I've managed to fix many games. Only these two are left, but they may not be because I can't test them with the changes I've made until tonight.

---

### Post by Cadeyrn on 2009-06-23
And still nobody cares. No matter, because I switched to CrossOver and now every game works. I guess the problem was WINE is horrible on x64 systems while CrossOver is not...

---

### Post by regor210 on 2009-06-23
You could try install them using PlayOnLinux.
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by Talorgan on 2009-10-12
> **Cadeyrn said:**
> And still nobody cares. No matter, because I switched to CrossOver and now every game works. I guess the problem was WINE is horrible on x64 systems while CrossOver is not...

I have the 64 bit version of Ubuntu 9.04 installed at the moment and experiments with Wine are bearing little resemblance to the results reported at WineHQ. Maybe I should try the 32 bit version?

---

### Post by NightMKoder on 2009-10-12
Probably not - there is no 64 bit version of wine, when you're on x64 and running wine, you're just running it in 32-bit mode. It's most likely your drivers/settings and has nothing to do with wine itself.

On a sidenote, if you're using proprietary video drivers (as you should be), you have to install 32-bit versions as well.

---

### Post by DarkeKun on 2009-10-12
> **Cadeyrn said:**
> And still nobody cares. No matter, because I switched to CrossOver and now every game works. I guess the problem was WINE is horrible on x64 systems while CrossOver is not...

I've tried to make it work with CrossOver, but, no luck... can't install *reason* its the pylotro for Dungeons and Dragons Online, and I got no sound, and, how do I run pylotro with a program as CrossOver?

---

### Post by Talorgan on 2009-10-17
> **NightMKoder said:**
> Probably not - there is no 64 bit version of wine, when you're on x64 and running wine, you're just running it in 32-bit mode. It's most likely your drivers/settings and has nothing to do with wine itself.

On a sidenote, if you're using proprietary video drivers (as you should be), you have to install 32-bit versions as well.

... so 64 bit may be the problem indirectly, via unavailability of drivers?

---

### Post by beastrace91 on 2009-10-17
> **Talorgan said:**
> ... so 64 bit may be the problem indirectly, via unavailability of drivers?

Not necessarily - what type of GFX card do you have? What driver version and how did you install said driver?

~Jeff

---

### Post by Talorgan on 2009-10-20
You could be on to something here.

I did the:

sudo lshw -html >> info.html

... thing, and the "display" box is white with not much info in it, where most of the boxes are yellow. It simply lists "ATI Technologies" and "VGA compatible controller" which sounds kinda generic.

When I installed the 64 bit distro a box offered to install display drivers and I accepted. The quality of the display improved dramatically after I had done that but I suspect that you are about to tell me that I don't have the right video drivers installed?

The card is an ATI Radeon HD 4770.

---

### Post by NightMKoder on 2009-10-20
Then your biggest problem is your video card. ATi 3d drivers are just bad on linux. You have the right drivers (fglrx from ATi themselves I assume), but they just don't work as well as they should and crash frequently.

---

### Post by Talorgan on 2009-10-24
Thanks for your reply. At least I now know what the problem is.

Given that some of the programs I want to try in Wine don't need 3D graphics I wonder if I should just remove the graphics card.

---

