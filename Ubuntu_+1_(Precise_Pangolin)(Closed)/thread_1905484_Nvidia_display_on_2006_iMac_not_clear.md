---
title: "Nvidia display on 2006 iMac not clear"
date: 2012-01-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by felixdzerzhinsky on 2012-01-06
**This has turned out to be a hardware problem. The bad picture quality occurs with OS X as well.**

My 2006 iMac has very poor graphics. I have nvidia-current installed. The best way I can describe it is that the screen seems to be covered in tiny squares. Not sure if that will be visible

Nvidia X Server Settings is detecting my Intel iMac 24 inch as an Apple Color LCD 1920x1200.

From lspci -v 
```

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=128M]
	Memory at c8000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at 2000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

```

Is there something else I can do to improve the graphics quality? It used to be good on 10.04.

---

### Post by xyzzyman on 2012-01-07
Not coming through on your screenshot.

---

### Post by ronacc on 2012-01-07
try hand installing the 290.10 driver from nvidia directly . Last time I did a new install of precise ( last week ) jockey (dkms) actually was trying to install the 173 driver on my 7600gs system even though I had specified  nvidia-current .

---

### Post by felixdzerzhinsky on 2012-01-08
> **ronacc said:**
> try hand installing the 290.10 driver from nvidia directly . Last time I did a new install of precise ( last week ) jockey (dkms) actually was trying to install the 173 driver on my 7600gs system even though I had specified  nvidia-current .

I ended up with a Black screen of death. No idea how to proceed. Would it be possible for someone to provide me with a working xorg.conf file for the iMac 24 inch.

---

