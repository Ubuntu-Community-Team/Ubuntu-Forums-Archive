---
title: "Sound issues in vbox"
date: 2009-11-06
forum: Virtualisation
---

### Post by Warthaug on 2009-11-06
I am not able to get sound to work, despite working my way through several suggestions I've found here and on the vbox forums.  I was hoping by describing what I've done here someone can tell me what I've done wrong.

I'm running vbox 3.0.10 in ubuntu 9.10, 64bit. I installed winXP SP3 as a guest, installed guest addons, and then updated winXP with all current updates.  Despite that, I have no sound.

On the end of the host machine I've tried all four sound options available to me (null, oss, alsa and pulse), as well as tried switching the audio controller (AHC and soundblaster). None of that resolved the lack of sound.

I think the problem lies at the guest end. When I open the control panel in XP, and then open the sound dialogue, the sound dialogue states that no audio device is installed (regardless of whether I have AHC or soundblaster selected as the audio controller). If I open the device manager I either have an unrecognised device (if I'm using AHC as the audio controller) or no sound device listed at all (if soundblaster is selected).

That said, when I look in the guest addons folder on the XP machine there are no drivers for sound - while there are .inf files for video, mouse and other features.

Anyone know how to fix that?

Thanx

Bryan

---

