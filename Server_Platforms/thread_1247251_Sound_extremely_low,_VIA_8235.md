---
title: "Sound extremely low, VIA 8235"
date: 2009-08-22
forum: Server Platforms
---

### Post by weryl on 2009-08-22
Hi,

I have an Averatec laptop i want to use as a media player (using MPD) but the sound output I get is way too low to be any useful. I installed alsamixer and set everything to 100% (PCM, master, etc) but even then the sound is barely audible when I stick my ear to the speaker.

Here's what I get when I type "cat /proc/asound/cards":
```

1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                     VIA 82XX modem at 0xe000, irq 22

```

"aplay -l":
```

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I read some stuff about adding a line in /etc/modprobe.d/alsa-base.conf but that didn't work out for me (also it was for an Intel card, not mine). I'm running Ubuntu Server 9.04 from a fresh install (this afternoon) and I updated it an hour ago. I only install MPD, some python librairies and a custom daemon that allows me to whisper some music for now...

---

### Post by weryl on 2009-08-23
bump

Actually I thought about install the desktop edition instead and then deactivating gdm and every other useless service. I know the sound used to work on Ubuntu and I don't think the problem comes from the hardware. Think that'd work?

---

### Post by weryl on 2009-08-23
bump again
its important :)

---

