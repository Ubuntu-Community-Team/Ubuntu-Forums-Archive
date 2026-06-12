---
title: "Virtualization Issue with new Lemur 7"
date: 2017-02-03
forum: System76 Support
---

### Post by p4tr0kl0s on 2017-02-03
Recently received my new Lemur in the mail, and am having trouble getting VirtualBox to run a 64-bit Windows 7 machine.  VirtualBox is telling me that VT-x is disabled, which my research leads me to conclude is untrue.  There is no BIOS option for VT-x, but lscpu tells me I have it.  Anybody else have trouble getting a 64-bit system to run?  Apologies in advance if this is strictly a VirtualBox issue and not an issue with the machine.  Specs and error message below:

My machine:

Lemur (Lemu7)
Intel i7 cpu
16gb memory
Ubuntu 16.10

VirtualBox Error Message:
 VT-x is disabled in the BIOS for all CPU modes (VERR_VMX_MSR_ALL_VMX_DISABLED)
 

[TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] [FONT=monospace]NS_ERROR_FAILURE (0x80004005)[/FONT]
[/TD]
[/TR]
 [TR]
 [TD] Component: 
[/TD]
 [TD] ConsoleWrap
[/TD]
[/TR]
 [TR]
 [TD] Interface: 
[/TD]
 [TD] IConsole {872da645-4a9b-1727-bee2-5585105b9eed}
[/TD]
[/TR]
[/TABLE]

Thanks!

---

### Post by DuckHook on 2017-02-04
I have never owned or used a System76 machine but I would be knocked-over shocked if your BIOS does not have a VT-x option. In some BIOSes it's not called VT-x, but something else. You should read through the documentation that came with your laptop to find the setting that allows HW virtualisation.

It is true that VBox will not run without this setting enabled. Not only VBox, but other VM technology like KVM, XEN, VMWare, all of them. They all need access to the CPU virtualisation hooks. I don't know of a single manufacturer who ships a machine without VT-x, and especially a Linux vendor, since VMs are practically ubiquitous in Linux. You are just overlooking a BIOS setting that may be under another name, or hidden deep within some submenu.

Note: VT-x is Intel terminology. AMD calls theirs AMD-V. BIOS manufacturers call them something else yet again. Since System76 is basically an OEM that is rebranding someone else's laptop, it could be called anything.

---

### Post by april-system76 on 2017-02-20
Hello! The Lemur 7 certainly supports VT-x (and VT-d), however a BIOS issue caused VT-x to be disabled by default. We'll be issuing a BIOS update for all Lemur 7 customers shortly, but in the meantime you can open a support case at system76.com and we'll get you squared away if this is time sensitive. Otherwise, we are expecting to package and ship the Lemur 7 BIOS within the week.

---

### Post by smd3 on 2017-03-02
I installed the bios update this evening, then Virtualbox, and Windows 10.  Everything is working great on my Lemur 7!

---

### Post by april-system76 on 2017-03-08
Just a quick update, we'll be sending out the updated BIOS to affected Lemur 7 owners shortly.

---

### Post by smd3 on 2017-03-08
I updated my firmware last week, and now have Virtualbox and Windows 10 running great.

---

