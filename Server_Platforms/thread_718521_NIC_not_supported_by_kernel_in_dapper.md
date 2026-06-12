---
title: "NIC not supported by kernel in dapper"
date: 2008-03-08
forum: Server Platforms
---

### Post by Rich99 on 2008-03-08
I have a server running dapper, and want to move it to new hardware, a dell T105 to be precise.  I imaged the server across, but the nic isn't recognised.  pcilist shows:
Ethernet controller: Broadcom Corporation Unknown device 165a 

I gather the nic (a Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express) is supported in newer kernels, but for ease of security updates I don't really want to compile & maintain my own kernel.  Is there an easier option to get the nic working?

---

### Post by Petersonz on 2008-03-13
You should be able to compile the driver as a module and not have to recompile the kernel.

Broadcom has source drivers available.

Should be as simple as:

download broadcom drivers

apt-get install kernel-devel

to get kernel headers for compiling

make && make install to compile module and install.

I did this routine with Intel source drivers for e1000 and it worked fine. Didnt take a kernel recompile.

---

### Post by nanog on 2008-04-19
just upgrade to hardy
and sudo modprobe bnx2

---

