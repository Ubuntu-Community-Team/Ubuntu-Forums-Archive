---
title: "problem with wireless interface with virtualbox 4.1.6"
date: 2011-12-18
forum: Virtualisation
---

### Post by jamesbon on 2011-12-18
I use Ubuntu 11.04 amd64 version.

MY wireless card a broad com chipset following
```
14e4:4315
```

things have worked fine until I created a guest OS in Virtualbox.To the guest I used bridged netwroking mode and since I use wireless card the Virtualbox got connected to the wireless interface and created a bridge over there.Upto here things are smooth the guest has access to internet as well and some one from within the lan can do an SSH to the guest OS.

The problem starts now after some time of working the wireless on the host machine disconnects.Rebooted the host OS but the connectivity of host finished.Reinstalled the```
 b43-installer
``` no success.

Renamed the VirtualBox guest OS folder to a different location
i.e.
```
mv /home/rin/VirtualBox VMs/**Windows** /home/rin/VirtualBox VMs/**KWindows**

```
Rebooted the host machine.
Got wireless back on track.

Again tried to use guest so

```
mv /home/rin/VirtualBox VMs/**KWindows** /home/rin/VirtualBox VMs/**Windows**

```

switched on the virtual machine in Virtual Box again after some time the connectivity of host is in problem.SO have to disable the networking option for VirtualBox guest machines.
Could this probably be a bug?

My OS: Ubuntu 11.04
VirtualBox version : 4.1.6

---

