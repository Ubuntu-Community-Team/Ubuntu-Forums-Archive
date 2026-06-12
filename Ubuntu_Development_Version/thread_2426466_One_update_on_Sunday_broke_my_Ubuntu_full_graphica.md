---
title: "One update on Sunday broke my Ubuntu full graphical boot"
date: 2019-09-09
forum: Ubuntu Development Version
---

### Post by amano on 2019-09-09
I can only enter Eoan via the safe-mode in GRUB. Plymouth isn't displayed anymore and the display goes black otherwise. 

Any ideas?

```
lspci  -v -s  $(lspci | grep ' VGA ' | currently t -d" " -f 1)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 35) (prog-if 00 [VGA controller])
	Subsystem: ASRock Incorporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: i915
```

---

### Post by amano on 2019-09-11
Hmm. False alarm. It might have to do with some small sheet of plastic that stuck in my HDMI port. Strange.

---

