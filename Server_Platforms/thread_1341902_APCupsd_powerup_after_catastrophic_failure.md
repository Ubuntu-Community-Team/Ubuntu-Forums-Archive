---
title: "APCupsd powerup after catastrophic failure"
date: 2009-11-30
forum: Server Platforms
---

### Post by mrzaius on 2009-11-30
I live in Kathmandu, Nepal where catastrophic multiple-hour power failures are sadly the norm, due to rolling blackouts. I've got a 220v USB APC Back-UPS 800 RS connected to a PC running apcupsd which shuts down cleanly. The desktop is set up to automatically power up when the PSU loses power and then has power restored.

The final hurdle I have yet to surmount is this:

A: When the shutdown is complete and the UPS completely loses its charge the UPS itself shuts down. When power is restored.... nothing happens. The UPS and PC remain offline.

B: When the shutdown is complete, but power is restored before the UPS shuts itself off.... nothing happens. The PC remains offline.

How do I go about having:

A: The UPS turn itself back on when power is restored (this would fix most of the problem)

and B: Have the UPS kill power to all ports and restore them afterwards, triggering the PC's BIOS setting for automatic power on. (I understand that this is less likely to be possible, but it'd sure be nice.)

(Mods: If this is the wrong forum, feel free to move this post.)

---

