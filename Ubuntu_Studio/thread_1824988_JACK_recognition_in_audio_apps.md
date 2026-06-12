---
title: "JACK recognition in audio apps"
date: 2011-08-14
forum: Ubuntu Studio
---

### Post by musicman99 on 2011-08-14
Hi folks,

have a weird problem here that I haven't recognized before at all.

System:
Lenovo T400
Aboganis lowlatency kernel 3.0.0-8
UbuntuStudio Natty, 11.04, all Audio, Studio Apps (Ardour, etc.)
FFADO (from UbuntuStudio)
JACK (from UbuntuStudio)
Presonus FP10

- JACK (QjackCtl) with firewire driver starts without problems
- Pulseaudio deactivates as it should
- Interfaces i/o are recognized in the connection window
- 2ms latency at 96kHz without xruns. :P

But ...
- Any other application out of the multimedia suite doesn't recognize an already running JACK server!
   - Ardour says "cannot connect to JACK"
   - QSynth says "cannot start JACK" and doesn't work as result
   - In VLC you cannot even select JACK as audio device, Jack plugin is installed ...
   - Meterbridge flickers for some milliseconds and disappears

Could somebody tell me what is wrong here?
Any configuration that I have missed?

Thanks for your help!

Benjamin

Please ignore the HW/SW details below

---

