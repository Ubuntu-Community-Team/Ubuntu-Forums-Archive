---
title: "Any way to throttle the speed of a virtual CPU?"
date: 2008-01-21
forum: Virtualisation
---

### Post by Paul Miller on 2008-01-21
I'm looking for an emulator or virtualizer that allows me to set the speed of the virtual CPU.  For example, if I'm running on a 3.0 ghz P4, I might want to throttle my virtual CPU to, say, 500 mhz.  The reason I'm looking for this feature is to do some performance testing for some software on slower machines than I have access to. :-)

Is there any open source product out there that has this feature?

---

### Post by dark_phantom on 2008-01-22
I'm interested in something similar, I want to assign more cpu time to a VM.  If there's a way, I would like to know.

---

### Post by Paul Miller on 2008-01-22
Oh, increasing the priority of the virtualizer app is easy: just use the renice command in combination with sudo.  Be careful, as this could cause your "real" Ubuntu install to freeze up as the kernel allocates a majority of the processor to your VM.  Check out man renice.

This is quite different from what I want.... I want to be able to throttle my virtual CPU down in a controlled manner.  That is, if I'm starting with a 3ghz system, I'd like to be able to tell Virtualbox (or whatever) to run at the speed of a 1ghz system, for instance.

---

### Post by RIchard James13 on 2008-01-23
Found a link to a patch on the QEMU FAQ that slows down the emulator
[http://lists.gnu.org/archive/html/qemu-devel/2006-11/msg00275.html]("http://lists.gnu.org/archive/html/qemu-devel/2006-11/msg00275.html")
I have not tried it myself. There also might be patches for other emulators?

---

