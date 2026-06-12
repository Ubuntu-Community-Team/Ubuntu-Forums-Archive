---
title: "100% CPU usage with WoW"
date: 2010-03-08
forum: Wine
---

### Post by mludd on 2010-03-08
After not playing WoW for almost a year I decided to start playing again but I've run in to some issues with CPU usage that I'm hoping are due to a configuration error on my part (and not that WoW has gotten a lot more CPU intensive).

Basically I have a machine with an Athlon 64 3200+ (2GHz, Single core), 5 GiB of RAM and a GT 220 with 1024 MiB and just the login screen after starting Wow.exe makes the CPU usage hit ~85-90% and the sound makes popping noises due to buffer underruns (at least that's what the wine debugging printouts tell me is wrong with the audio output). When I last ran WoW under wine on this machine it had only 1 GiB of RAM and a GF7600 with 256 MiB of memory yet the CPU usage would normally be less than 75% in-game except in the "usual places" (Stormwind outside AH and similar hotspots) and now just logging in will peg the CPU at 100% pushing my framerate down to ~15-20 FPS.

The only 100% CPU usage issue I've been able to google is the alt-tab issue for Windows (where /console maxfps 0 is supposed to fix the issue, this does not appear to be my problem and the command in question does nothing).

I've tried re-nicing the process but it has done nothing to improve the situation.

Anyone who's had similar issues and found a solution?

EDIT: This is with the wine1.2 package in 9.10 but the same problem appeared with the regular wine package as well.

---

