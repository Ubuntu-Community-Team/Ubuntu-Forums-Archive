---
title: "Does anyone else's laptop do this?"
date: 2009-04-09
forum: The Cafe
---

### Post by tom66 on 2009-04-09
When power is removed, the speakers click loudly. Originally I thought it might have something to do with a relay in the laptop switching (power control), but it seems to be dependant on volume. I have a Dell Studio 15, though I noted this odd behaviour also happened with a Dell Inspiron 1300 I owned for a good few years. I have not noticed this behaviour with other laptops running Ubuntu, but those are few and far between for me.

---

### Post by kevin11951 on 2009-04-09
happens to me too...

---

### Post by zekopeko on 2009-04-09
report a bug

---

### Post by Martin Marshalek on 2009-04-09
Mine does this too, and it's a Compaq...

Apparently this is relatively normal as it is not brand-specific.

---

### Post by tom66 on 2009-04-09
I think it's a hardware issue. I'm not sure if it doesn't happen on Windows, because I've only ever used Windows to get Ubuntu on this PC. I didn't notice it on Windows XP on my previous laptop, however the clicking only started happening later. (I also, rarely used XP on that laptop.) It is of course possible this is an Ubuntu thing, because I would have updated Ubuntu. I wonder what's causing it. Some kind of state change in the sound system based on power (power-saving modes?)

---

### Post by lisati on 2009-04-09
I've never noticed until now. (2 x Toshiba)

Just tried it and there was a definite click, nearly missed it due to the volume of the TV

---

### Post by Stupendoussteve on 2009-04-09
Is this click you're talking about separate from the sound effect that Gnome-power-manager makes around the same time it dims the screen? (Which is not a bug, or an issue, just a wav)

If that's the sound you're hearing, you can disable it by right clicking the battery icon, going to Preferences > General and unchecking the "Use sound to notify" thing.

If you want to hear the sound, it is at /usr/share/gnome-power-manager/gpm-unplugged.wav

---

### Post by tom66 on 2009-04-09
Shouldn't it be more of an informative sound then... a ding (yes, Windows comes to mind here), or a beep, would be better. Click sounds like a hardware problem, and is weird and doesn't really say anything. I found out it doesn't click when I turn this off, so something to do with this. But why is AC removal triggering an error?

---

### Post by Stupendoussteve on 2009-04-09
It's not triggering an error, the dialog is just badly worded. It also makes a sound when the battery is critical. It's just a sound affect it makes when you unplug the system, just like any other generally useless sound effect.

If you write over that .wav file with any other .wav, it will play that instead.


I never thought it sounded like a hardware error. It sounds like someone snapping their finger, and hardware errors don't generally come out of the speakers.

---

### Post by tom66 on 2009-04-09
Interesting. 

I think it sounds like a spark jumping somewhere or some kind of relay switching and I will post a bug suggesting it be changed. 

Thanks all.

---

### Post by doorknob60 on 2009-04-09
No, but that's because the only laptops I have run Debian and Arch, so I guess it's part of Ubuntu's default configuration, from reading the replies anyways. My laptops are an ancient Compaq ("Designed for Windows 98") that runs Debian Lenny with LXDE, and my parents' pretty recent HP laptop (about a year or two old) running Arch with Gnome.

---

### Post by SomeGuyDude on 2009-04-09
HP dv6000 series, Arch64, no problem with speaker clicks.

---

