---
title: "LTSP thin client graphics not found"
date: 2010-02-21
forum: Server Platforms
---

### Post by map7 on 2010-02-21
I'm using Ubuntu 9.10 with the LTSP packages installed and I have an Intel  motherboard with Atom chip model: D945GCLF2D as my thin client.  This comes with an Intel GMA 950 as it's graphics chip.  This does not get recognised when booting as a PXE thin client.

It does work however on the Ubuntu 9.10 32bit livecd, I can use glxgears and compriz straight from the live cd.  The only way I can get the system to boot as a thin client into the GUI is to set XSERVER=vesa in my lts.conf but then I cannot enjoy the full potential of my graphics card.

When typing in lspci -v on the live cd which works I see that it's using the intelfb driver.  This is not included on my client build, how do I include this driver module as part of my client build?  Is it just a certain package I have to install?  I have the xorg-server-intel package already installed, so it's not that.

```

Here is the lspci -v output about the video card:
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 90200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 20e0 [size=8]
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	Memory at 90280000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: intelfb
	Kernel modules: intelfb

```

---

