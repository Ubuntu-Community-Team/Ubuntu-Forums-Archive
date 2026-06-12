---
title: "No Sound Ubuntu Studio 14.04"
date: 2015-01-27
forum: Ubuntu Studio
---

### Post by leegold on 2015-01-27
Hi,

Tried everything I can think off and recommended with web searchs. I have no sound. I've tried the usual things maybe I missed trying something...

I can give any info needed about the laptop and the config - I'd really like to fix it.

Win7 dual boot sound works OK. Ubuntu Studio very fast - like it a lot.

Weird...two vol controls one in the panel proper and in the indicator area on the panel. Tons of controls regarding sound (to be expected), checked it all, a bit confusing...


$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Thanks.

---

### Post by leegold on 2015-01-27
Fixed it. Did "alsamixer" in the terminal and unmuted "S/PDIF" didn't see this in the GUI controls from the desktop panel. Now sound works. So the terminal control of the alsamixer seems better for trouble shooting. Isn't S/PDIF and optical in/out? Or maybe it just started working automagically - at least it works now.

---

