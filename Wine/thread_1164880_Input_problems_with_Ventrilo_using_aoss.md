---
title: "Input problems with Ventrilo using aoss"
date: 2009-05-20
forum: Wine
---

### Post by moomba89 on 2009-05-20
I've had vent 3.0.4 installed through wine for a while and have been using it to listen to raid conversation on WoW etc quite well, but recently I decided to add a microphone and, after trying many different configurations, I believe I'm experiencing a not-so-common problem:

OK, so my winecfg settings are to use OSS and driver emulation
I run vent after having killall'd pulseaudio
Running pulseaudio without aoss lets me configure my mic and have it work successfully through Monitor, BUT as I connect, I get an error mentioning that my input is already in use (even though it quite clearly isn't).

This problem would usually be fixed by running wine through aoss (unless I'm mistaken), so I then run it through aoss only to find that the input is not recognised at all (not through any of the given devices); monitor picks up 'Abs Zero'. The output sound works, but input is completely useless.

I've tried this set up with alsa, oss, with pulseaudio still enabled, pulseaudio disabled, and each of the input devices with each. I can't think of anything else to try and I would greatly appreciate your ideas.

Thanks :)

---

