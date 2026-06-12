---
title: "Ubuntu 16.10 virtualbox guest additions 5.1.6 removal from standard installation"
date: 2016-10-24
forum: Virtualisation
---

### Post by bugrider2 on 2016-10-24
Installed Ubuntu 16.10 Desktop 64bit as a guest in Virtualbox 5.1.8.
After standard installation from iso with auto updates from network, kernel has Virtualbox 5.1.**[COLOR=#ff0000]6[/COLOR]** guest additions modules installed:

[B][COLOR=#0000ff][FONT=courier new]modinfo vboxguest
filename:       /lib/modules/4.8.0-26-generic/kernel/ubuntu/vbox/vboxguest/vboxguest.ko
version:        5.1.6_Ubuntu r110634
license:        GPL
description:    Oracle VM VirtualBox Guest Additions for Linux Module
author:         Oracle Corporation
srcversion:     D95A5FA0DB511CEC415F6E7
alias:          pci:v000080EEd0000CAFEsv00000000sd00000000bc*sc*i*
depends:        
intree:         Y
vermagic:       4.8.0-26-generic SMP mod_unload modversions [/FONT][/COLOR][/B]

Note that this is some special Ubuntu kernel flavour. It is NOT from any package listed in Synaptic / apt.

It is also impossible to update this to 5.1.8 using the Virtualbox guest additions iso image. The installer from the iso will report success, but the mod remains at 5.1.6.
Hence some functionality is lost, due to version mismatch.

I could not find any hint on how to remove the 5.1.6_Ubuntu mod from the kernel.

**Anybody got a clue on how to remove this?**

---

### Post by ajgreeny on 2016-10-24
As you have downloaded and installed the extensions package from Oracle in your VBox manager, (I presume you have done this?), have you tried going to the Devices menu in your guest and clicking on the "Insert guest additions CD image" to mount the guest additions image in the guest.

After doing that you need to run the VboxLinux.run file which is in that iso guest image file, in a root terminal which is often easiest done by simply dragging the .run file from the file manager into the terminal.

Incidentally I had several problems with VBox 5.1 series so went back to the 5.0 version, 5.0.26 at present, which works faultlessly.

---

### Post by bugrider2 on 2016-10-24
> **ajgreeny said:**
> As you have downloaded and installed the extensions package from Oracle in your VBox manager, (I presume you have done this?), have you tried going to the Devices menu in your guest and clicking on the "Insert guest additions CD image" to mount the guest additions image in the guest.

Yes, of course. As I wrote in my original post:
> **bugrider2 said:**
> It is also impossible to update this to 5.1.8 using the Virtualbox guest  additions iso image. The installer from the iso will report success,  but the mod remains at 5.1.6.

More specifically:
[LIST]
[*]The 5.1.6_Ubuntu version of the Virtualbox guest additions modules comes preconfigured with the kernel and is present after the Ubuntu install procedure (and without ever seeing any Virtualbox 5.1.6 on the host, because as I wrote: The Ubuntu OS install was already under Virtualbox 5.1.8). 
[*]There is no package that relates to these 5.1.6_Ubuntu modules, which could be uninstalled using synaptic or apt. 
[*]Installing the Virtualbox 5.1.8 guest additions from the respective Virtualbox guest additions iso image actually sudo runs without any errors (and running an uninstall later also does not report any errors), but after the installation, modinfo still reports version 5.1.6_Ubuntu. 
[/LIST]

I believe the preconfigured 5.1.6_Ubuntu modules are taken from
**[FONT=courier new] /lib/modules/4.8.0-26-generic/kernel/ubuntu/vbox/[/FONT]**
and below and makefiles are in
**[FONT=courier new] /lib/modules/4.8.0-26-generic/build/ubuntu/vbox/[/FONT]**
and below.
But hey, any digging below synaptic is currently over the top for me.

My position is that if the Virtualbox guest additions come preconfigured with the kernel, there should be a way to remove them.
The problem was never present in any previous Ubuntu release (or lets say: At least I never noticed any problem. (And yes: I DO (and DID) check the modinfo after any guest additions install - but up to now I never did this BEFORE installing them!))

So again:
**Anybody presenting a method to get rid of the 5.1.6_Ubuntu modules would be highly welcome.**

---

### Post by &amp;KyT$0P# on 2016-10-24
[This thread]("https://ubuntuforums.org/showthread.php?t=2329454") sounds like the 16.04 version of the same problem, maybe you can come up with a similar solution for 16.10?

---

### Post by bugrider2 on 2016-11-30
It seems that the problem disappeared with VirtualBox 5.1.10.
The  guest additions installer of version 5.1.10 recognizes that the  vboxguest module originated from the linux kernel extra image. It then  presents a warning. Ignoring this warning and continuing to execute the  installer then correctly installs the 5.1.10 guest additions.

---

