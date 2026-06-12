---
title: "Smallest ubuntu host for vmware workstation?"
date: 2009-07-29
forum: Virtualisation
---

### Post by Hydex on 2009-07-29
Hello,
I would like to host VMWare Workstation on a linux host, and thought of ubuntu. 
Thing is I only need the most basic functions on the host as the final user would exclusively use one of his VMs to work, so ideally it would only display to the user the shortcuts to launch the needed VM to the user and would only contain the needed libraries to run VMWare Workstation.
Is it possible to reduce the size of an ubuntu distrib so it would fill my needs? 


In fact I discovered Ubuntu JeOS but it is mainly for guest usage , so I was wondering if the same kind of distrib existed for host usage.

Thanks!

---

### Post by jocampo on 2009-07-29
You mean, he will seat on same Ubuntu host and use the virtual machine? hmmm... what's the purpose of the Virtual Machine? I suggest the following

1.Install Ubuntu Server (use less resources and more powerful, especially if you don't add the GUI)
2.Install Vmware or VirtualBox
3.Instruct the user to connect via ssh (from his current Windows client or whatever he's using now) and use the virtual machine.

As an alternative (with VirtualBox) you install the guest on top of Ubuntu, and run it on Full Screeen; he/she won't notice is running a virtual machine on top of a real Linux box. ;-)

---

### Post by Hydex on 2009-07-29
> **jocampo said:**
> You mean, he will seat on same Ubuntu host and use the virtual machine? hmmm... what's the purpose of the Virtual Machine? I suggest the following

1.Install Ubuntu Server (use less resources and more powerful, especially if you don't add the GUI)
2.Install Vmware or VirtualBox
3.Instruct the user to connect via ssh (from his current Windows client or whatever he's using now) and use the virtual machine.

As an alternative (with VirtualBox) you install the guest on top of Ubuntu, and run it on Full Screeen; he/she won't notice is running a virtual machine on top of a real Linux box. ;-)

Thanks!
For security reasons I need to have two VMs on a workstation, each connected to a particular network (and virtual desktop) using rdp - yes it is really heavy, blame the specs... 

A user should not be able to do much on his comp if not using one of the VM.

Anyway your idea is good, but I would need to upgrade... Ubuntu Server + Win/normal ubuntu + two (or more) VMs will kill a lambda desktop workstation, won't it?

---

### Post by stlsaint on 2009-07-29
depends on specs of your computer! powerful cpu with more ram  will handle more!!

---

### Post by Hydex on 2009-07-30
> **stlsaint said:**
> depends on specs of your computer! powerful cpu with more ram  will handle more!!

Sure, but it's not easy to ask our clietns to change all their computers :P
I'd rather use one host only, but ubuntu seems quite big for that function :/

---

