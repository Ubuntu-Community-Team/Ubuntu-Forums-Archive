---
title: "VMPlayer 4.0.3 Ubuntu 12.01 i3 Intel Graphics 3D Acceleration Issue"
date: 2012-08-18
forum: Virtualisation
---

### Post by emist on 2012-08-18
Hello gents,

I've been having an odd issue with 3D acceleration in my vmware guests.  I'm running ubuntu in my host and I have installed the intel driver for the integrated graphics in my i3 chip.  

glxinfo | grep direct returns "direct rendering: Yes"

glxgears returns an fps in sync with my monitor's refresh rate when synced to the refresh rate, and about 6,000 fps when unsynced. I've ran tremulous in my linux host and confirmed that 3d accel was working fine there as well.

After installing vmware tools and directx 9.0c in my Windows XP guest, running dxdiag/Display shows that DirectDraw is enabled (and works fine), but Direct3 is "not available."  

For whatever reason, clicking "Detect display" in windows makes it show an extra display (even though I only have one). 

In my windows 7 guest I have neither DirectDraw nor Direct3D showing as enabled.  And it also shows the two monitors even though I have a single one. 

Does anyone have any suggestions as to what could be wrong?

Thanks,

emist

---

### Post by emist on 2012-08-18
Couldn't figure out whats wrong with vmware.  But installed virtualbox and using the same vmware images 3d acceleration is working fine.

---

### Post by dcstar on 2012-08-30
> **emist said:**
> Couldn't figure out whats wrong with vmware.  But installed virtualbox and using the same vmware images 3d acceleration is working fine.

Then **Mark the Thread**.

---

