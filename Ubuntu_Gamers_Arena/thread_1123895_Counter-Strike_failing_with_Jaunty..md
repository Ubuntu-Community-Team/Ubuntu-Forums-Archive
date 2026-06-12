---
title: "Counter-Strike failing with Jaunty."
date: 2009-04-12
forum: Ubuntu Gamers Arena
---

### Post by connorh123 on 2009-04-12
Hey guys, so I recently installed Jaunty Jackalope, but the game Counter-Strike, doesn't work.
However, it did work in Hardy Heron (8.04), so I might just switch back. There's also a problem with the sound whenever I turn it on. It makes a crackle sound, then it doesn't work anymore.

---

### Post by Psyphre on 2009-05-01
same, worked perfect in intrepid, but crashed within a minute when playing in jaunty :(

---

### Post by CharmyBee on 2009-05-01
Did you run winecfg and checked the audio tab? Try driver emulation

---

### Post by Psyphre on 2009-05-02
Ive got it working!

There are 2 issues that can cause it.

1) Audio issues. To elminate this as a possible problem, set "-nosound" as the launch property of CSS in steam. If it still crashes with no sound then this isnt the problem. If it stop crashing, then your gonna have to play around with your sound settings in wine. Either try what CharmyBee suggested, or in my case I set it to OSS rather than alsa and it works perfect.

2) Font issues. A fix is to set hl2.exe to run in win98.

I just did both and it works 100%.

---

### Post by CharmyBee on 2009-05-02
> **Psyphre said:**
> 2) Font issues. A fix is to set hl2.exe to run in win98.

Steam wouldn't like that.

---

### Post by Psyphre on 2009-05-02
> **CharmyBee said:**
> Steam wouldn't like that.

No it doesnt, which is why u set hl2.exe to run at win98. That way steam runs in xp mode, and CSS in 98.

Its working for me. Absolutely perfectly, infact I've been playing for 2 hours online today.

---

### Post by connorh123 on 2009-05-02
Okay, so this works for 1.6 and CSS I'm assuming?
Sorry, didn't add I was using 1.6.
EDIT: My hl2.exe was already at 98. And where do I set that -nosound?

---

### Post by Psyphre on 2009-05-02
sorry wasnt aware it was 1.6, i assumed source.

Im not sure how useful my suggestions will be, but if you want to give it a try anyway.

To disable sound open steam, and right click on counterstrike, then properties, then launch options.

Type in "-nosound"

You can type in other commands, i find that windowed mode works better for me than fullscreen. My current launch options are:

"-dxlevel 80 -windowed -height 1440 -width 900"

---

### Post by CharmyBee on 2009-05-02
of course, sound is a critical essential part of the game; without sound, you'd stink at CS.
Try -wavonly, see if that helps. I **think** the engine has a WAVE mix fallback for when DirectSound can't initialize or doesn't exist.

---

### Post by Psyphre on 2009-05-03
> **CharmyBee said:**
> of course, sound is a critical essential part of the game; without sound, you'd stink at CS.
Try -wavonly, see if that helps. I **think** the engine has a WAVE mix fallback for when DirectSound can't initialize or doesn't exist.

Oh definetly, its pointless without sound, but he's just doing it to see if it stops crashing. If it does, then we know its sound thats causing it and he just needs to try the different sound options to see if that helps. If no sound still causes crashing then we know its not sound at all thats the issue and can rule it off.

---

### Post by connorh123 on 2009-05-03
Nothing. About 5 minutes in, it just stopped and I shut down my computer manually.

---

### Post by Psyphre on 2009-05-03
> **connorh123 said:**
> Nothing. About 5 minutes in, it just stopped and I shut down my computer manually.

I assume this is with no sound right?

So then its obviously not a sound issue. Since your playing 1.6 instead of source I'm afraid I may not be able to help much. Do you use an ATI card? I was looking in the wine databse and apparently ati seems to have an issue with random crashes/freezes.

---

### Post by connorh123 on 2009-05-03
Yeah, ATI Radeon 7500.
Yes, it has happened before, and you may be right about that. Even when CS was working fine, it would sometimes crash.

---

