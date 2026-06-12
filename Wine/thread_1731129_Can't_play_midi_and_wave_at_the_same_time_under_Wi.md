---
title: "Can't play midi and wave at the same time under Wine"
date: 2011-04-16
forum: Wine
---

### Post by ubnewbie2 on 2011-04-16
I am trying to get some music software (Band in a Box and Real band) working, but I am fairly sure it's a more general problem.

I have selected ALSA as the sound driver in winecfg.  Midi devices and wave devices are all available, but if I run an app that uses the midi devices, other apps using wave, stop working.   In the case of Band in a Box, which uses both, the midi stuff works fine (playing using Timidity), but the wave stuff is silent.

If I click on "Test Sound" in winecfg, while a midi program like BIAB is running, the button stays depressed (with no sound) until I quit Band in a Box, the the sound plays releasing the winecfg button - so it was stalled trying to play the sound.

---

### Post by cogadh on 2011-04-19
The problem is likely a limitation of ALSA and your sound hardware. If your sound hardware is not a "full hardware" sound card (i.e. some of the processing is handled by the drivers and not just the hardware alone), then ALSA is usually limited to a single stream at a time. Supposedly there are ways to configure ALSA to get around it, but I've never had any success with them. You should check the ALSA Wiki for more information.

---

### Post by ubnewbie2 on 2011-04-20
It is a proper hardware sound card, but, it could also be a limitation of the way the windows/wine drivers interact with ALSA.

I think I'll be going back to running it under VMWare player.

---

