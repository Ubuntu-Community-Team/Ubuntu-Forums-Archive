---
title: "Help with Pangolin Touchpad on Fedora"
date: 2011-08-05
forum: System76 Support
---

### Post by rgheck on 2011-08-05
I'm trying to get Fedora running on a new panp8 Pangolin. The only sticking point is the touchpad. I've looked at what the System76 drivers do here, which is install a new version of the kernel module psmouse.ko, but I cannot get this to compile properly. Everything is find until I get "MODPOST 0 modules".

I wonder if someone could tell me exactly what changes were made to elantech.c here, preferably by posting a patch against whatever kernel this code came from.

Speaking of which: Doesn't doing things this way mean improvements to the kernel's mouse code are always being over-written?

---

### Post by isantop on 2011-08-05
Which version of the driver are you looking at? Systems that are up to date should be running the latest kernel, which includes the fixed code. I don't think the driver is doing anything with the mouse stuff anymore.

Would it be possible to try the latest mainline kernel, instead Fedora's? It may include the patched code as well.

---

### Post by rgheck on 2011-08-06
That was the latest driver, and I'm using a 2.6.40 kernel. The problem turns out to be that the Fedora kernel doesn't compile the PS/2 mouse driver as a module. So the solution was to recompile the kernel, using the altered elantech.{h,c} files. That worked.

I've reported this on the Fedora bug tracker.

---

