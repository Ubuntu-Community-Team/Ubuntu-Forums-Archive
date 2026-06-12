---
title: "Does Ubuntu not work with KVM?"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-24
I just checked some nVidia settings after hooking up 3 PCs to a KVM and got this error.

Also .. I am using a Zonet KVM 4port 3304.

  I am assuming  of course this is just standard loopback and nVidia settings is right to report noScanOut

---

### Post by effenberg0x0 on 2011-11-24
> **ventrical said:**
> I just checked some nVidia settings after hooking up 3 PCs to a KVM and got this error.

Also .. I am using a Zonet KVM 4port 3304.

  I am assuming  of course this is just standard loopback and nVidia settings is right to report noScanOut

I tried it a month ago or so. The problem was that, by default, we have no more xorg.conf and I had to put together a basic xorg.conf for it work (just identify the device, monitor, horiz/vert refresh, serverlayout, etc).

---

### Post by ventrical on 2011-11-24
Thanks for your response!

---

### Post by cariboo on 2011-11-24
I use an older D-Link 4 port PS/2 KVM, I had it connected to a 19" CRT, that was never detected properly, so every time I installed a new version, I'd have to create a new xorg.conf file, with the proper horizontal and vertical refresh rates. With an LCD connected, the generic xorg.conf file seems to work OK.

---

### Post by ventrical on 2011-11-24
Thanks for your response also.  I am running 2 towers and a desktop ATM for testing Precise. It is convenient because I can switch back and forth to test different video adapters and 32/64bit systems without running through the squirell cage :)

  I do notice also that 'monitor detection' is a big reason why some installs will quit right on the spot.

 Thanks again.

---

