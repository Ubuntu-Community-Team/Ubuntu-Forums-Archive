---
title: "Axiom 25 connection issue"
date: 2012-07-07
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-07-07
Ok, so I have a Axiom 25 keyboard controller that I would like use it connecting it with JACK and record in Ardour. I'm just not sure how to hook it up. I'm aware how to make a basic connection In JACK, I've done it with my Fast Track. I'm not sure if I use the USB cable that came with the keyboard controller, or use the MIDI to USB cable I have. 

Any help would be greatly appreciated. I apologize ahead of time if this is redundant, and if there are any forums like this please feel free to forward them to me. 

Thanks

---

### Post by jejeman on 2012-07-07
I hope that you want to record MIDI messages since it is only controller.

If you have Ardour 3 you can work with MIDI.

You can use USB cable, check out if it registers it as MIDI device
```
amidi -l
```
if not, then use MIDI to USB cable.

In order to connect ALSA MIDI and JACK MIDI (ALSA and MIDI tabs in Qjackctl) you need a bridge program a2jmidid.

---

