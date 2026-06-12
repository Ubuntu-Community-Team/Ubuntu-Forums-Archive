---
title: "[SOLVED] VirtualBox installed - No more video card"
date: 2008-03-12
forum: Virtualisation
---

### Post by DamonChyld on 2008-03-12
I just installed VirtualBox (not yet loaded an OS on it) and when I restarted after uncommenting the "Magic to make /proc/bus/usb work" entries I discovered that my video card was kaput.

If I go into preferences>appearance and set visual effects to custom I get the "Desktop effects could not be enabled" popup.

Restricted device manager says that my ATI accelerated graphics driver is enabled but not in use. I tried disabling/enabling it but it didn't change. 

lshw (Note display:1 UNCLAIMED)
```
*-display:1 UNCLAIMED
description: Display controller
product: RV370 [Radeon X300SE]
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@0000:01:00:1
version: 00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0

```

xorg
```
Section "Device"
Identifier            "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
Driver                "fglrx"
Busid                 "PCI:1:0:0"

```

How would I go about fixing this?

---

### Post by wormser on 2008-03-12
I am not good with xorg.conf but I have the same video card.  I do not know if it will help but here is my xorg.conf.  

```
Section "Device"
	Identifier	"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
EndSection
```

lshw
```
 *-display
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx

```

---

### Post by DamonChyld on 2008-03-12
Thanks wormser, but this is the desktop version of the x300, not the laptop/mobility :)

---

### Post by DamonChyld on 2008-03-12
Why is it that the simplest solutions sometimes evade us? Uninstalled/reinstalled and video card is working. I am a little concerned that it's still listed as unclaimed in lshw but...?

---

