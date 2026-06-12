---
title: "Gpu Acceleration Failing? Drivers?"
date: 2020-02-27
forum: Virtualisation
---

### Post by localmana88 on 2020-02-27
So basically i have 2 nvme disks in my computer
In one i have Windows 10
And in the other one i installed ubuntu yesterday(was unused some time)

I install vmware workstation pro 15.5 in ubuntu and open a windows 7 x64 guest VM, when trying to do the same i do with Windows 10 host(open a game) it fails, and the VM is the same
Gpu acceleration or vmware tools is failing, how i can check what is and solve?

The VM is the same in both hosts

hardware: **My hardware:**
**CPU: Ryzen 7 2700 not OC**
**GPU: Gigabyte GV-N107TWF2-8GD GeForce GTX 1070 Ti 8GB GDDR5 **
**Motherboard: Asus PRIME X470-PRO AMD AM4 X470 ATX**
[B]Disks: 2x Samsung 970 EVO (In one Windows 10 in other one Ubuntu 18.04)
[/B]
**RAM: F4-3200C16D-32GTZA**

---

### Post by rbmorse on 2020-02-27
Did you install the package: 

open-vm-tools

from repository? This takes the place of installing the O/S specific VMtools package into a virtual machine like you have to do on a Windows host.   The Open-VM-tools package should be installed all virtual machines properly shut down to powered off state and the Workstation host program not running.

Once that is done, you should be able to start Workstation, fire up the virtual machine and enter the graphics section of virtual machine settings.  Make sure hardware acceleration is enabled.

---

### Post by CelticWarrior on 2020-02-28
Even with hardware acceleration the game may fail. Most demanding games don't work in a VM because they don't recognize the virtual GPU. They should work with GPU passtrough though.

---

### Post by localmana88 on 2020-02-28
> **CelticWarrior said:**
> Even with hardware acceleration the game may fail. Most demanding games don't work in a VM because they don't recognize the virtual GPU. They should work with GPU passtrough though.

This isnt true atleast for my case
Cause when doing exactly the same with Windows 10 x64 Pro Host, i get different result(Game goes 45/50 fps witouth lag and witouth bugs) But when trying with ubuntu, i get error

---

### Post by localmana88 on 2020-02-28
> **rbmorse said:**
> Did you install the package: 

open-vm-tools

from repository? This takes the place of installing the O/S specific VMtools package into a virtual machine like you have to do on a Windows host.   The Open-VM-tools package should be installed all virtual machines properly shut down to powered off state and the Workstation host program not running.

Once that is done, you should be able to start Workstation, fire up the virtual machine and enter the graphics section of virtual machine settings.  Make sure hardware acceleration is enabled.

no i did no install nothing gonna try again installing those, what i have to do, install open-vm-tools and reinstall windows 7 vm and tools? any specific configuration for tools in workstation?

---

### Post by localmana88 on 2020-02-28
i will edit OP with this too but here is my hardware, if someone knnows if i have to install something

the other obvius option is too pasthroug gpu to vm but i want to use that as last resource before trying everything

[B]My hardware:
[/B]
[B]CPU: Ryzen 7 2700 not OC
[/B]
**GPU: Gigabyte GV-N107TWF2-8GD GeForce GTX 1070 Ti 8GB GDDR5 **
**Motherboard: Asus PRIME X470-PRO AMD AM4 X470 ATX**
[B]Disks: 2x Samsung 970 EVO (In one Windows 10 in other one Ubuntu 18.04)
[/B]
**RAM: F4-3200C16D-32GTZA**

---

### Post by CelticWarrior on 2020-02-29
> **localmana88 said:**
> no i did no install nothing gonna try again installing those, what i have to do, install open-vm-tools and reinstall windows 7 vm and tools? any specific configuration for tools in workstation?

You shouldn't need to reinstall the VM, just change the VM's settings to enable acceleration after installing the package recommended in the other post. Again, I don't know VMware but those settings should be easy to find

---

### Post by localmana88 on 2020-02-29
> **rbmorse said:**
> Did you install the package: 

open-vm-tools

from repository? This takes the place of installing the O/S specific VMtools package into a virtual machine like you have to do on a Windows host.   The Open-VM-tools package should be installed all virtual machines properly shut down to powered off state and the Workstation host program not running.

Once that is done, you should be able to start Workstation, fire up the virtual machine and enter the graphics section of virtual machine settings.  Make sure hardware acceleration is enabled.

Install this package + reboot solved my issue

---

