---
title: "Ubuntu 10.04 LTSP and Intel atom thin client"
date: 2010-10-20
forum: Server Platforms
---

### Post by shineymart on 2010-10-20
Trying to connect an intel atom based TC which uses the Intel D945GSEJT
motherboard. We have several old AcerPower F1 PCs which connect OK but the
new TC doesn't provides a weird screen resolution at the LDM - 1152x864.
I've logged in and looked at the monitors section and it thinks there is a
laptop monitor for some reason in addition to an undetected monitor. If I
try to change anything I lose my mouse which is VERY strange.

If I boot 10.04 using a USB memory stick on the TC everything is fine - I
can get 1280x1024, the monitor is detected and all is well.

I've tried changing monitors, fiddling with lts.conf etc with no success.

For info, my current lts.conf is as follows

[default]
    X_NUMLOCK = True
    X_COLOR_DEPTH = 24
    LDM_DIRECTX = True
    X_MODE_0 = 1280x1024

# Acerpower F1
[acerf1]
    X_NUMLOCK = true
    X_COLOR_DEPTH = 24
    LDM_DIRECTX = True
    X_MODE_0 = 1280x1024
    X_HORZSYNC = 28-64
    X_VERTREFRESH = 43-60

Any ideas anybody?

Martyn

---

### Post by santhony on 2010-10-20
I've been trying to run the Intel Atom as a Fat Client.  I've been unsuccesful at adding the NVIDIA drivers to it thus far.....

---

### Post by shineymart on 2010-10-20
The TC in question has a standard Atom board as per the spec below

[http://www.intel.com/products/desktop/motherboards/D945GSEJT/D945GSEJT-overview.htm](http://www.intel.com/products/desktop/motherboards/D945GSEJT/D945GSEJT-overview.htm)

Surely this should 'just work' in LTSP.

---

### Post by santhony on 2010-10-20
I've been trying to run the Intel Atom as a Fat Client.  I've been unsuccesful at adding the NVIDIA drivers to it thus far.....

---

