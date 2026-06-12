---
title: "Problems with M-audio Delta66 in Ubuntu Studio"
date: 2008-08-10
forum: Ubuntu Studio
---

### Post by djpenguin on 2008-08-10
I'm having serious problems trying to use my delta 66 sound card under ubuntu studio.  The card is recognized, I can see all the control options under Envy24control, but when I send it signal at unity gain (0dB) on the inputs, it gets a pathetically weak input signal on all four analog inputs, even with the ADCs set to 100% volume.

The computer it's in is a dedicated recording machine that does not have a network/internet connection.

What's going wrong here?  Why can't I get decent signal levels through my card?

---

### Post by Stochastic on 2008-08-11
Most of the time this issue (on various cards) stems from low volume settings in alsamixer.  I've never worked with envy24control, so it may be a replacement for alsamixer, but it's worth a look.

---

### Post by djpenguin on 2008-08-11
Volume is at 100% in alsamixer and Envy24control.

---

