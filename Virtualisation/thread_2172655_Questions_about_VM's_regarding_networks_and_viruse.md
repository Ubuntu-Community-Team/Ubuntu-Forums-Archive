---
title: "Questions about VM's regarding networks and viruses"
date: 2013-09-05
forum: Virtualisation
---

### Post by Wiking on 2013-09-05
[COLOR=#323232][FONT=verdana]**Networking**
Do Virtual Machines Behave the Same as a regular PC on a network? What are the differences between a virtual machine on a network and a regular machine on a network?
[/FONT][/COLOR][COLOR=#323232][FONT=verdana]
I also noticed the VMware network adapter in the control panel. Doesn't the VMWare adapter have to use the network card of the machine thats running the VM in order to send packets and datagrams trough the wire?[/FONT][/COLOR][COLOR=#323232][FONT=verdana]
[B]
Viruses[/B]
How safe is it to open an infected file on a virtual machine? Is there a chance that the computer hosting the VM will get infected?[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]What if it's a plug and play malware that can be transferred by USB key? Wouldn't both the host computer and the VM machine become infected if you plug in a USB stick to the computer that is running the Virtual Machine?[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]thanks[/FONT][/COLOR]

---

### Post by Habitual on 2013-09-06
> **Wiking said:**
> [COLOR=#323232][FONT=verdana]How safe is it to open an infected file on a virtual machine? Is there a chance that the computer hosting the VM will get infected?[/FONT][/COLOR]

Up until "lately", NO, not possible, but Never says 'never' as they say. Given enough time and resources, and the motivations of evil do-ers, it will be possible at some point in the future. IMHO.

---

### Post by houstonbofh on 2013-09-06
> **Wiking said:**
> [COLOR=#323232][FONT=verdana]**Networking**
Do Virtual Machines Behave the Same as a regular PC on a network? What are the differences between a virtual machine on a network and a regular machine on a network?[/FONT][/COLOR]
Depends on your virtual network.  If you have your VM software set up for bridging, the guest machine will look totally real to the network, and the only clue will be MAC addresses. (Unless you change them)
> **Wiking said:**
> [COLOR=#323232][FONT=verdana]
I also noticed the VMware network adapter in the control panel. Doesn't the VMWare adapter have to use the network card of the machine thats running the VM in order to send packets and datagrams trough the wire?[/FONT][/COLOR]
Yes, but it uses it through an abstraction layer, the VMware adapter.
> **Wiking said:**
> [COLOR=#323232][FONT=verdana][B]
Viruses[/B]
How safe is it to open an infected file on a virtual machine? Is there a chance that the computer hosting the VM will get infected?[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]What if it's a plug and play malware that can be transferred by USB key? Wouldn't both the host computer and the VM machine become infected if you plug in a USB stick to the computer that is running the Virtual Machine?[/FONT][/COLOR]
The USB device will be either read by the guest or the host.  Both can not open it at once.  (OK, they can, but not in most configurations)  Also, there is no good cross platform malware, so the host and guest need to be on the same codebase.  But, if a virus is network transferable, a guest can transfer it to any other compatible machine, virtual or otherwise.

---

### Post by 1clue on 2013-09-06
> **Wiking said:**
> [COLOR=#323232][FONT=verdana]**Networking**
Do Virtual Machines Behave the Same as a regular PC on a network? What are the differences between a virtual machine on a network and a regular machine on a network?
[/FONT][/COLOR][COLOR=#323232][FONT=verdana]

If you use bridged networking they're essentially indistinguishable from regular computers.

> 
I also noticed the VMware network adapter in the control panel. Doesn't the VMWare adapter have to use the network card of the machine thats running the VM in order to send packets and datagrams trough the wire?
[/FONT][/COLOR][COLOR=#323232][FONT=verdana]

Yes, the VMware adapter needs to use the physical hardware as long as the host it's contacting is not another VM on the same host.

> 
** Viruses**
How safe is it to open an infected file on a virtual machine? Is there a chance that the computer hosting the VM will get infected?[/FONT][/COLOR]


This is a complicated question.  Is the host running Windows?  Is the guest running Windows?  Is the [s]virus[/s] (let's just call it malware) malware designed for the hardware and/or software it's running on?

I suppose it's possible for malware to check for the presence of virtualization and find an exploit that way, but it's difficult for me to imagine malware in the guest infecting the host, unless there is some sort of application or data sharing going on.  Of course if you're sharing something then there's a possibility of an exploit.

> 
[COLOR=#323232][FONT=verdana]What if it's a plug and play malware that can be transferred by USB key? Wouldn't both the host computer and the VM machine become infected if you plug in a USB stick to the computer that is running the Virtual Machine?[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]thanks[/FONT][/COLOR]
If the malware on the stick could exploit a real host of the same type, then it can exploit the VM.  Depending on how the driver for virtualization works, it's possible that the host could be infected as well as whatever VM you connected it to.

---

