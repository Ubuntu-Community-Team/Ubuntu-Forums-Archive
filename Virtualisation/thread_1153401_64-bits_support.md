---
title: "64-bits support"
date: 2009-05-08
forum: Virtualisation
---

### Post by fferreira on 2009-05-08
Hi,

I have a Intel T7100 processor. It is supposed to support the  Virtualization Technology and I have enabled it at the BIOS configuration.

I also have installed the Sun VirtualBox 2.2 under my fresh Ubuntu Jaunty. I am trying to install a Scientific Linux 5 (SL5) 64bits as a virtual machine, no success though. When I start to run the Installation Wizard of SL5 it appears the following message:

"Your processor doesn't support 64-bits. Install the 32-bits version"

What the f*** is wrong with that?

---

### Post by dcstar on 2009-05-08
> **fferreira said:**
> Hi,

I have a Intel T7100 processor. It is supposed to support the  Virtualization Technology and I have enabled it at the BIOS configuration.

I also have installed the Sun VirtualBox 2.2 under my fresh Ubuntu Jaunty. I am trying to install a Scientific Linux 5 (SL5) 64bits as a virtual machine, no success though. When I start to run the Installation Wizard of SL5 it appears the following message:

"Your processor doesn't support 64-bits. Install the 32-bits version"

What the f*** is wrong with that?

Some VM systems are 64-bit, some are not. VMWare Server installed on a 64-bit host supports 32 or 64-bit clients.

Do a search and find out what is supported.

---

### Post by veloce on 2009-05-12
My laptop supports VT, so I have moved to kvm.  All my vms on this machine are now 64bit.

---

### Post by bodhi.zazen on 2009-05-12
> **fferreira said:**
> Hi,

I have a Intel T7100 processor. It is supposed to support the  Virtualization Technology and I have enabled it at the BIOS configuration.

I also have installed the Sun VirtualBox 2.2 under my fresh Ubuntu Jaunty. I am trying to install a Scientific Linux 5 (SL5) 64bits as a virtual machine, no success though. When I start to run the Installation Wizard of SL5 it appears the following message:

"Your processor doesn't support 64-bits. Install the 32-bits version"

What the f*** is wrong with that?

You also have to activate this in VirtualBox

In the general tab, check off the "VT-x/AMD-V" box.

---

### Post by lukeiamyourfather on 2009-05-12
Make sure that the virtual machine profile is configured for a 64-bit guest operating system. From the VirtualBox GUI select the machine, click the settings button at the top, and then select Linux for the guest and Red Hat (64-bit) as the Linux version. Cheers!

---

