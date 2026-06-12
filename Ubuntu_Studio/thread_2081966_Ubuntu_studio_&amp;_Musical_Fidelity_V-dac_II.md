---
title: "Ubuntu studio &amp; Musical Fidelity V-dac II"
date: 2012-11-08
forum: Ubuntu Studio
---

### Post by Kuki23 on 2012-11-08
Hi,
I'am new in Linux, and my question is, how to config my DAC, in mixer and player, to get bit perfection sound

Thanks

---

### Post by CrocoDuck on 2012-11-10
Hi. Dunno much about converters. Are you already managed to make it work? When using a new device the first step I make is to plug it and check his functionality by launching jack. If things go wrong then you have to go through trouble shooting. So:

Plug your device
Start Qjackctl
Press the setup button, go to input/output device options, press the > button and select your device for output.
Come back to main window and press start.

If you can find your device and jack can be started, then you'll have to set sample rate and frames/period to best performances.

If you are not interested in using jack maybe the best way is to open a terminal and type:

```
alsamixer
```select the device with the F6 key, F3 for output controls, have a look around with arrows (F1 for help). Repost here if you can't choose your dac.

---

