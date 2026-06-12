---
title: "VirtualBox, Xorg, NVidia freezes after VBox upgrade"
date: 2009-09-11
forum: Virtualisation
---

### Post by the_maplebar on 2009-09-11
I recently upgraded from VirtualBox 2.1.4 to VirtualBox 3 and things run better and smoother most of the time except sometimes my VM will just freeze for a while.  It didn't do this with VirtualBox 2.  When it freezes Xorg is using 50%-60% of 1 core and VirtualBox has most of the rest.  Has anyone else seen this?  Is there something I can do to use VBox 3, it runs better when it doesn't freeze.

A little more details.  This is happening when I am running Worms World Party, using hardware 3D acceleration.  In VBox 3 it runs perfectly except when it freezes (Xorg + VBox have CPU maxed).  In VBox 2.1.4 it runs good but can get a little choppy.  I went back to 2.1.4 because it is usable and noticed that Xorg mostly stays below 10% CPU and spikes to 20%.  With VBox 3 Xorg stays about 20% and spikes to 60%.  My specs:

Ubuntu 8.10
VirtualBox 2.1.4 (PUEL) -> VirtualBox 3
NVidia Graphics driver Version 180

---

