---
title: "ESXI-Server and client machine?"
date: 2010-03-24
forum: Virtualisation
---

### Post by themarker0 on 2010-03-24
Is there any ways i can use ESXI as a server, and a personal computer at the same time? I have a new machine, and it is very good, and i am thinking it would be a waste to just install windows 7 64 bit. (little of the hardware works under linux well) So i'd like to move my server onto it aswell.

---

### Post by TheFu on 2010-03-24
Sure, if you dual boot.  ESXi is a hypervisor. It takes over the system completely. There is no GUI on that same machine hardware, just a text interface. 
You can load Windows7 into a virtual machine under ESXi, then RDP into it from other machines on your network.

A different option is to load Windows7 on your new machine, then load VirtualBox and run your server under it as a VM. IMHO, VirtualBox isn't ready for production use, but if you are like me, you need to have 1 Windows machine that you can trust will have drivers available for pretty much any hardware you need.  I have many other machines that are pure Linux, but I retain 1 Windows7 machine running VirtualBox and both WinXP and Xubuntu VMs available under it ... er .... just in case.

Since I also run an ESXi server, I know that the VMWare GUI to manage it only runs (officially) under WinXP. It doesn't run under Windows7. There are hacks to get it running under Win7 or Vista.

---

### Post by codfather on 2010-03-25
You can also run ESXi from a usb stick, so you could have the best of both worlds, you would just have to re-boot your machine when you wished to change it's function. It would make sense to have two separate disks, one for the workstation side and one for the virtualization side, as  ESXi likes to grab all the disks you give it and format them as it's storage with vmfs.

Have you tried booting your machine with a Lucid Lynx beta CD to see how that works, as that would then give you the ability to use KVM as your hypervisor, which is extremely fast.

hth

Nick

---

### Post by themarker0 on 2010-03-25
I have not setup the machine yet, because i wanted to get this working. So there is no way to have it all running on one computer :/

---

### Post by TheFu on 2010-03-26
Yes, you can have it all running on 1 computer, just not with a local GUI.

Have you checked the ESXi will actually work on your machine? It is a little picky about disk and network controllers, IME.

---

### Post by themarker0 on 2010-03-26
> **TheFu said:**
> Yes, you can have it all running on 1 computer, just not with a local GUI.

Have you checked the ESXi will actually work on your machine? It is a little picky about disk and network controllers, IME.

Yes i made sure of that. So no GUI, that means no windows then?

---

