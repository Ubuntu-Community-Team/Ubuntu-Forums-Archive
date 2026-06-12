---
title: "Devuan: no sound after distribution upgrade to Daedalus."
date: 2023-09-28
forum: Ubuntu/Debian BASED
---

### Post by maketopsite on 2023-09-28
```
$ alsamixer 
cannot open mixer: Host is down
$
```
```
# lspci -v
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 7 Series/C216 Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f7e10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
```

---

