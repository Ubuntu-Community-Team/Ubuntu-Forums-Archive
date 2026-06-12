---
title: "Dummy output"
date: 2019-04-08
forum: Ubuntu/Debian BASED
---

### Post by sergey91 on 2019-04-08
I have asus laptop,  some time after installation ubuntu 18.10 my sound disappeared and now I see "Dummy output" on sound output device.
I tried to change kernels, it helped me for the first restart, after second restart got dummy output again.
If I try connect any earphones its dont work and I still have no sound.

---

### Post by yancek on 2019-04-08
Try running the commands below consecutively, then post any output you get from either/both commands:

> aplay -l
sudo lspci -v | grep -A7 -i "audio" 

Neither command will 'fix' anything, the only purpose is to get info on your sound so that others familiar with these problems might be able to help.

---

### Post by sergey91 on 2019-04-10
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
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
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 130
    Memory at df328000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

---

### Post by sergey91 on 2019-04-13
[COLOR=#000000]bump[/COLOR]

---

