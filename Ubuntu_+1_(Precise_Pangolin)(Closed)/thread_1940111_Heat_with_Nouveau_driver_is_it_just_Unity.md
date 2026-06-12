---
title: "Heat with Nouveau driver: is it just Unity?"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kaldor on 2012-03-13
For the first time on this PC, Nouveau is perfectly usable and ready for my laptop's needs (I can even do some light 3d gaming on the 8400m- awesome). The only issue that's still annoying to me is the heat. I've posted here about it before during the 11.10 and 12.04 development.

However, I've been testing out GNOME fallback mode and GNOME Shell. So far, the temperatures seem to be idling at between 45 and 60 degrees celcius. This is on par with the NVIDIA blob on Ubuntu 10.04. 

This computer has been running for the last hour or so on GNOME Shell:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.0°C  (crit = +120.0°C)
temp2:        +57.0°C  (crit = +120.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +65.0°C  (high = +100.0°C, crit = +110.0°C)

```

That's a far cry from the typical 75+ that I see on Unity (along with the loud fans).

So now I'm thinking that the problems with heat might be related to Unity. Unity 2d is also affected. My temperatures on Unity tend to gradually increase until it hits 90 degrees and I need to boot it down. I was thinking that it was due to the lack of power management on Nouveau, but it seems to be working just find on non-Unity desktops.

Any other users having heat problems when using Unity? Which driver? Anything weird when running *top*?

---

