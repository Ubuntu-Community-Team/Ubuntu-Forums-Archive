---
title: "Ubuntu and server virtualization"
date: 2012-06-05
forum: Server Platforms
---

### Post by MadsRC on 2012-06-05
I have a question for all of you Ubuntu Server people.

I want a setup like this:
2 physical server, one running unRAID and one running as a VM Server (Running a Ubuntu 12.04 server & an pfSense firewall.

What is the best way to achieve VM Server?
From what I can see there's a few alternatives (They all feature VMWare, as that is what I want to work with)
1: Install & run VMWare's server OS (Would be the best solution, but my 2 NIC's aren't supported so would need new hardware)
2: Install Ubuntu and run VMWare Server as a service on that.

Does anyone have an experience with option 2? I don't suppose the performance would be different from option 1 and 2, since a base Ubuntu Server install wouldn't be a performance eater.

Any input?

---

### Post by spynappels on 2012-06-05
There will be a performance hit to option 2, but without knowing the hardware specs of the physical server, it is hard to be precise.

I've found it easier to source some Intel NICs and run ESXi than to add the extra level of complexity of an OS and VMware as a service. It is also easier to administer an ESXi host, can be done even through SSH/CLI.

All in my opinion of course, but I have used both options.

---

### Post by MadsRC on 2012-06-05
So, you would be going for something like a vSphere server?

---

### Post by rubylaser on 2012-06-05
> **spynappels said:**
> There will be a performance hit to option 2, but without knowing the hardware specs of the physical server, it is hard to be precise.

I've found it easier to source some Intel NICs and run ESXi than to add the extra level of complexity of an OS and VMware as a service. It is also easier to administer an ESXi host, can be done even through SSH/CLI.

All in my opinion of course, but I have used both options.

+1 to ESXi with VT-D passthrough.

---

### Post by Cheesemill on 2012-06-05
> **MadsRC said:**
> 2: Install Ubuntu and run VMWare Server as a service on that.

Don't use VMware Server.

It is no longer being developed or supported.
[http://www.vmware.com/products/server/overview.html](http://www.vmware.com/products/server/overview.html)

Either use vSPhere Hypervisor (ESXi) or install a headless VirtualBox Server.

---

### Post by MadsRC on 2012-06-05
VT-D ? Is that so that a 2 virtual machines can share 1 physcial cpu?

---

### Post by rubylaser on 2012-06-05
From Wikipedia...
> An input/output memory management unit (IOMMU) enables guest virtual machines to directly use peripheral devices, such as Ethernet, accelerated graphics cards, and hard-drive controllers, through DMA and interrupt remapping. This is sometimes called PCI passthrough.[31] Both AMD and Intel have released specifications:
AMD's I/O Virtualization Technology, "AMD-Vi", originally called "IOMMU".[32]
Intel's "Virtualization Technology for Directed I/O" (VT-d).[33] Included in most but not all Nehalem based processors.

This will allow you to pass through the nics directly to Pfsense rather than using a virtual nic.  Another common use is passing through an HBA for a storage server.

---

### Post by MadsRC on 2012-06-05
Okay, so it's going to be a ESXi/VSphere server then.

Currently the server consists of:
P5G41T-M LX Motherboard (LGA775)
Pentium Dual Core SLA8X (2.2GHz) (A friend offered me a Pentium Quad Core - Still waiting for the spec's on it)
40GB IDE HDD (With more to come)
6GB RAM
PCI Network Card

So 2 NIC's but neither of them are supported in ESXi... So new NIC's are needed.

VT-D, how can I know if it is supported? Is it a feature in the NIC's or?

---

### Post by rubylaser on 2012-06-05
The processor needs to support it first and then the motherboard.  That processor does not support [VT-D]("http://ark.intel.com/products/33925/Intel-Pentium-Processor-E2200-(1M-Cache-2_20-GHz-800-MHz-FSB)") or VT-X that you'll need to run 64bit guests on ESXi (you should be able to run 32 bit guests though).

---

### Post by MadsRC on 2012-06-05
Thank you :) I'll wait till my friend gives me some info on his spare Quad Core CPU and see if that supports it, if not, then I guess I'll find another solution to running multiple virtual servers.

---

### Post by rubylaser on 2012-06-05
No problem.  If it's a Core2Quad era processor, you should be fine for VT-X and if it's a Q9550, it will even support VT-D.

---

