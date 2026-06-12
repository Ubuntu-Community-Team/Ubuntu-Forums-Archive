---
title: "Logitech USB headset and Ventrilo"
date: 2009-08-01
forum: Wine
---

### Post by Saturate2009 on 2009-08-01
Okay, so, I've been trying to convert totally to Ubuntu, but a few things are driving me freaking insane.  I've tried every post about logitech USB headsets to get them to work and none of the fixes have even worked for me.  I managed to get WoW working fine, except for the annoyance of no hardware cursor, but that's a blizzard problem, not a linux problem.  Anyway, any help with my headset is appreciated, I'll go ahead and list what I've done below, along with what I'm running.


Jaunt-9.04 64 bit
Wine- Current Version
Ventrilo - Current version 32 bit.
Logitech USB headset.  It's the kind you plug into the USB box, it's analog/USB

What have I done?  Well...

asoundconf list

the results are 
Nvidia
Headset


Sadly, I can still hear some things through the headset randomly when I use Ubuntu.  Sometimes it directs system sounds there.. almost like it's mirroring, it's quite odd.  

Under Wine/Audio Config

I have "ALSA" checked, but when I drop down each tree, only two "Defaults" are listed.  Pretty sure one should be USB...   I can't run Ventrilo in OSS, or WoW in OSS, because that defy's the purpose of me even being on one while USING the other.  After this I am completely lost, I'm going to tinket and attempt to fix it somehow.  Any walkthrough, tip, even a nudge in the right direction would be helpful.

EDIT: I followed the Cmedia fix, I can now talk through my microphone, but the sound in ventrilo comes through my speakers.  I also still can't use ALSA, two Nvidia setups are under ALSA.

Thanks.

---

