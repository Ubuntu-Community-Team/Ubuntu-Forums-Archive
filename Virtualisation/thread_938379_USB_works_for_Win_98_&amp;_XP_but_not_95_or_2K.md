---
title: "USB works for Win 98 &amp; XP but not 95 or 2K?"
date: 2008-10-04
forum: Virtualisation
---

### Post by Blueshell on 2008-10-04
I can't get USB devices to be noticed by virtualized Win 2K or 95, but the same devices in the same VMware session -are- noticed by 98 and XP!  (I'm most interested in getting the 2K case working.)

I'm running Dapper with VMware 1.0.3 build-44356.

For example:  I have a Garmin GPS and a Dallas iButton reader; one's plugged directly into the machine, and the other goes through a hub (but the behavior is independent of where they're plugged in).  Plugging in the Dallas reader requires me to rmmod ds9490 (I presume; I haven't tried it -without- rmmoding), whereas the GPS doesn't require me to do anything to the kernel at all.  Both devices show up no problem in the VM -> Removable Devices -> USB tab once the respective guests are resumed (otherwise, of course, the RD tab is grayed out and I can't select it), but only in the 98 and XP guests.  The 95 and 2K guests, in the very same VMware window, -don't-:  the USB tab just says "Empty".

How can this even happen?  I would have thought that the VMware host wouldn't care -what- guest it's running as far as letting me even connect a USB device to it, but somehow it knows and fails.

I've tried suspending all the machines, shutting down VMware, and restarting VMware and unsuspending; no change.  I also tried powering the 2K guest off and on; no change.

Any ideas?  Thanks.

---

