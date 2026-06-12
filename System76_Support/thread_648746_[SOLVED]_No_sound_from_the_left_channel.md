---
title: "[SOLVED] No sound from the left channel"
date: 2007-12-24
forum: System76 Support
---

### Post by asmiller-ke6seh on 2007-12-24
There seems to be a bunch of folk who experienced the same problem that I experienced (and resolved) today, on a variety of hardware, across multiple versions of Ubuntu.

I found that by opening the ALSA Mixer (the volume control that can be accessed by double clicking on the speaker icon in the panel), muting my FRONT speakers, and then unmuting them, my left speaker came back on right away, No idea why this happened.

I have a Serval Performance (SERP2) with Intel HDA (Realtek ALC883) sound subsystem operating under Gutsy Gibbon with all updates applied and the System 76 driver (version 2.1.3).

---

### Post by thomasaaron on 2007-12-24
Sounds like a bug either in ALSA or the Sound Control program.
Glad you figured it out, though.

---

