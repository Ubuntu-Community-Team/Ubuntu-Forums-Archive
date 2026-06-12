---
title: "No Sound on Acer VW237Q Monitor"
date: 2019-05-04
forum: Ubuntu/Debian BASED
---

### Post by M4rotku on 2019-05-04
Hello all,

I bought this monitor to use with a new System76 Meerkat machine, running Pop!_OS.  It has built-in speakers, but I can't get them to work.  The monitor is connected via HDMI cable.  

In the sound menu, I can see a device for output:  HDMI / DisplayPort - Built-in Audio.  But when I select it and try to test the speakers, no sound is produced.  :confused:

I have already gone into alsamixer, unmuted all of the options, and turned the volume to 100.  I have also tried adjusting the settings in pavucontrol to make sure that nothing is muted.  Here are the results from lspci and aplay:

```

lspci -v | grep -A6 Audio
00:1f.3 Audio device: Intel Corporation Device 9dc8 (rev 30) (prog-if 80)
	Subsystem: Intel Corporation Device 2074
	Flags: bus master, fast devsel, latency 32, IRQ 151
	Memory at c0b20000 (64-bit, non-prefetchable) [size=16K]
	Memory at 404ab00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC233 Analog [ALC233 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


If anyone has advice on how to get the speaker to produce sound, it would be greatly appreciated.

Thanks!
Joe

---

### Post by wildmanne39 on 2019-05-04
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

