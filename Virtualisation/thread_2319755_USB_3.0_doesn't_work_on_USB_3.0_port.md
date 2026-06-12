---
title: "USB 3.0 doesn't work on USB 3.0 port"
date: 2016-04-06
forum: Virtualisation
---

### Post by galapogos on 2016-04-06
Hi,

I have a Ubuntu 14.04 LTS 64-bit guest VM on a Windows 10 Pro host on VMWare Workstation 12 Player. The system is a Dell XPS13 2016 laptop. I'm having trouble using an external USB 3.0 hard drive on Ubuntu. I get the following error message when I connect the device.
> The device was unable to connect to its ideal host controller. An attempt will be made to connect this device to the best available host controller. This might result in undefined behavior for this device.

lsusb shows the following:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lspci shows the following USB modules:
```

02:00.0 USB controller: VMware USB1.1 UHCI Controller (prog-if 00 [UHCI])
	Subsystem: VMware Device 1976
	Physical Slot: 32
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at 2080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
02:03.0 USB controller: VMware USB2 EHCI Controller (prog-if 20 [EHCI])
	Subsystem: VMware USB2 EHCI Controller
	Physical Slot: 35
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at fd5ef000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

```
I don't see any USB 3 controller.





The device works in Windows.

I seem to recall having a similar problem with the same external drive on another Ubuntu 14.04 LTS 64-bit desktop that I had - the drive would work on the desktop's USB 2.0 ports, but not on the USB 3.0 ports. However, in that instance, lsusb at least showed the device, and the USB 3.0 modules were correctly detected, so I'm not sure if in this case it's a Ubuntu problem or a VM problem.

Any ideas? Thanks.

---

### Post by galapogos on 2016-04-06
OK, so I enabled USB 3.0 in the VM settings, and now everything works. Silly me.

---

