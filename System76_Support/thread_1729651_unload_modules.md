---
title: "unload modules"
date: 2011-04-15
forum: System76 Support
---

### Post by reid_rsv869 on 2011-04-15
Anyone know how to unload modules?  I have tried: sudo modprobe -r  whateverthename....

but I get this error:  FATAL: Module ieee1394 is in use.

I have tried from the usual CLI but have also tried logging off, then changing desktops (alt-ctl-F1) but I get the same error.

thoughts welcome.

Reid

---

### Post by isantop on 2011-04-15
Hi Reid.

Why are you trying to unload the module? It looks like a firewire module, so make sure there are no firewire devices plugged in when you try the modprobe command.

---

