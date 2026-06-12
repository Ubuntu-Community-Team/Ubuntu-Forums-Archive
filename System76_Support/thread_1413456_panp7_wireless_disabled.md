---
title: "panp7 wireless disabled"
date: 2010-02-22
forum: System76 Support
---

### Post by cheriot on 2010-02-22
The wireless applet on the deskbar just says, "wireless is disabled". From lshw, I get the following:

> 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:9a:c3:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f0300000-f0301fff


Any suggestions on how I can get wireless going?

---

### Post by revlimiter on 2010-02-22
There's a function button. Fn-f11 or f12? I'm not sure. It's the one with the little wireless icon. Try hitting that.

---

### Post by cheriot on 2010-02-22
Thanks, that did it.

---

