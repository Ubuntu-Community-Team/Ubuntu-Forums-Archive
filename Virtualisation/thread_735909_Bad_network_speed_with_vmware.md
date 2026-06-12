---
title: "Bad network speed with vmware"
date: 2008-03-26
forum: Virtualisation
---

### Post by y0dase on 2008-03-26
Hello!

I recently installed a windows 2008 sever with vmware, using Ubuntu 7.10 as guest os. First I had some problems getting the vmxnet driver to load, but after removing the pcnet32 (?!) it seems to load just fine. 
[46975.936429] Found vmxnet/PCI at 0x1424, irq 17.
[46975.936725] vmxnet: numRxBuffers=(100*24) numTxBuffers=(100*64) driverDataSize=9000
[46975.940462] eth0: vmxnet ether at 0x1424 assigned IRQ 17.

But the speed are the same as it was before installing the vmxnet driver?!
I'm getting 4-8 mb/sec to my guest (ubuntu) and 20-25 mb/sec to the host. 
When i run htop i can see that the cpu is working at near 100% (2.4 ghz btw). Guessing the vmxnet driver arent working as it's supposed to?
Anyone else experiencing this?

Regards
y0da

---

### Post by beatbros on 2008-03-26
Hi,
did you install vmware server 2 beta  or 1.05?

Only vmware 2 (wich is in beta) has support for windows 2008 as host.
The old 1.05 seems to be really problematic on Windows server 2008.

Here's the community link with problems already addressed and so on:

[http://communities.vmware.com/community/beta/server2.0](http://communities.vmware.com/community/beta/server2.0)

---

### Post by y0dase on 2008-03-26
Oh.. didn't think of that :). I'm using 1.0.5, downloading the beta now.. keep your fingers crossed :P

---

