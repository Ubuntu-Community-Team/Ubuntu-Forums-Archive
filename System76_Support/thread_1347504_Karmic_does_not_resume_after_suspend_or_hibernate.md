---
title: "Karmic does not resume after suspend or hibernate"
date: 2009-12-06
forum: System76 Support
---

### Post by mgaz on 2009-12-06
Using a Karmic 64 bit on a bonp2 system from System76.com

When Ubuntu suspends to disk, it does not resume back and the screen stays black.

When resuming from a Hibernate, the screen stops at the message "Please wait" and does not resume further

---

### Post by thomasaaron on 2009-12-07
1. Did you do the online upgrade from 9.04?
2. If you go to System > Admin > Hardware Drivers, is your nVidia driver activated?
3. Did you run your System76 driver and reboot?

---

### Post by mgaz on 2009-12-07
1. It is a fresh install from 9.10 without any upgrade
2. No proprietary Driver is in use in my system
3. The Driver installation succeeded, When running the driver and clicking on install or restore, the procedure just times out and I have logged another ticket for this.

Since the driver does include only an addition for the finger device, I was not after getting the driver installed correctly.

Please let me know, if you need more information

---

### Post by thomasaaron on 2009-12-08
The problem *could* be the lack of the nVidia driver. Please try enabling it via System > Admin > Hardware Drivers. Then reboot your system. Then see if it will suspend.

---

