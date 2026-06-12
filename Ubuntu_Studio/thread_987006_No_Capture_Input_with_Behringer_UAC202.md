---
title: "No Capture Input with Behringer UAC202"
date: 2008-11-19
forum: Ubuntu Studio
---

### Post by Tashi on 2008-11-19
Hi all

I have a Behringer UAC202 Audio Interface. In alsamixer I see only the output, but no capture input. Same in gnome mixer. I also hear no sound from the input.
I read many user are successful with this audio interface. I test it in Ubuntu 8.04 and 8.10. 

In the systemlog I found the following entry. Maybe this has a relation.


 pulseaudio[6487]: alsa-util.c: Cannot find fallback mixer control "Mic".

my output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Any help is really appreciated.

---

### Post by Tashi on 2008-11-21
bump

---

### Post by Tashi on 2008-11-21
The capture input works now. I think I had some configurations problems with jack.

---

