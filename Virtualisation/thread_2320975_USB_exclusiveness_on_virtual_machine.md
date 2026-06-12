---
title: "USB exclusiveness on virtual machine"
date: 2016-04-19
forum: Virtualisation
---

### Post by itzik-istartup on 2016-04-19
Hello Ppl,

I would like to ask if there is a way to assign a USB port to be used exclusively on a Virtual machine running windows on a Ubuntu host.

Specifically i'm trying to do some modification to a smartphone bootloader connected to usb. the tools require windows machine which i have only on a VM and it seems that the host OS (ubuntu) is interfering.

Thanks in advance.

---

### Post by SeijiSensei on 2016-04-19
If you are using VirtualBox, you must [use the version provided by Oracle]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") and install the [Extension Pack]("https://www.virtualbox.org/wiki/Downloads") to enable USB support.  You'll have to [create a USB "filter"]("https://www.virtualbox.org/manual/ch03.html#idp46640731855648") as well.

---

### Post by itzik-istartup on 2016-04-19
Thanks SeijiSensei, what about vmware?
also on the host (ubuntu) side, is there a way to unload the driver for a specific usb device?

---

### Post by MAFoElffen on 2016-04-19
In VMWare- Ensure the VM has a "USB Controller" present in settings, and that you configure the support capability for it. The VM is limited to the capabilities of the client's host's "physical" capabilities.

At least for USB host-VM passthrough, how and what follows on vSphere clients, follows suit for the rest of their products (from what I've seen):
> 
How USB Device Passthrough Technology Works
The USB controller is the USB hardware chip that provides USB function to the USB ports that it manages. USB controller hardware and modules that support USB 3.0, 2.0, and USB 1.1 devices must exist in the virtual machine. Two USB controllers are available for each virtual machine. The controllers support multiple USB 3.0, 2.0, and 1.1 devices. The controller must be present before you can add USB devices to the virtual machine.
You can add up to 20 USB devices to a virtual machine. This is the maximum number of devices supported for simultaneous connection to one virtual machine.


---

### Post by itzik-istartup on 2016-04-19
Thanks [COLOR=#000000]*MAFoElffen!*[/COLOR]

---

### Post by SeijiSensei on 2016-04-20
> **itzik-istartup said:**
> Thanks SeijiSensei, what about vmware?
also on the host (ubuntu) side, is there a way to unload the driver for a specific usb device?

In Linux most drivers are implemented as kernel modules.  You can see all the currently installed modules with the command "lsmod".  You can remove a specific module with "sudo rmmod modname" or "sudo modprobe -r modname".

---

