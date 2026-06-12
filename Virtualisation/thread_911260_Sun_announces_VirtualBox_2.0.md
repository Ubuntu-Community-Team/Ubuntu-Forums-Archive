---
title: "Sun announces VirtualBox 2.0"
date: 2008-09-05
forum: Virtualisation
---

### Post by jespdj on 2008-09-05
[Sun announces VirtualBox 2.0](http://www.sun.com/aboutsun/media/features/2008-0904/index.jsp)

One major new feature is support for 64-bit guest operating systems. See the [list of new features and changes]("http://www.virtualbox.org/wiki/Changelog").

---

### Post by Dark Hornet on 2008-09-05
This is great news....can't wait to get home to try it out....

---

### Post by xebian on 2008-09-05
The 64bit guest feature doesn't seem to work.  Keeps telling me it's only i586 cpu.  Maybe Sun release info is premature.

---

### Post by dark_phantom on 2008-09-06
> **xebian said:**
> The 64bit guest feature doesn't seem to work.  Keeps telling me it's only i586 cpu.  Maybe Sun release info is premature.

Obviously I don't know your system setup, but the manual specifies the requirements in order to run 64 bit guests.

> 
Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems, under the following conditions:
   1. You need a 64-bit processor with hardware virtualization support (see chapter 1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10) and a 64-bit host operating system.
   2. You must run a 64-bit version of VirtualBox on that OS (Windows Vista, Linux or OpenSolaris). This can then run both 32-bit and 64-bit VMs; a 32-bit VirtualBox can only run 32-bit VMs, regardless of the hardware.
   3. You must enable hardware virtualization; software virtualization is not supported for 64-bit VMs.

Note: On most systems, the hardware virtualization features first need to be enabled in the BIOS before VirtualBox can use them.

There is no specific setting to enable 64-bit support for a guest. If the above conditions are met (in particular, if hardware virtualization is enabled), 64-bit support is available, and you can simply install a 64-bit operating system in the guest.

Warning: You should enable the I/O APIC for virtual machines that you intend to use in 64-bit mode. This is especially true for 64-bit Windows VMs.  See chapter 3.7.1.2, “Advanced” tab, page 45. In addition, for 64-bit Windows guests, you should make sure that the VM uses the Intel networking device, since there no 64-bit driver support for the AMD PCnet card; see chapter 6.1, Virtual networking hardware, page 72.


---

### Post by NullHead on 2008-09-06
Anyone gotten intrepid ibex alpha5 to work under virtualbox yet?

---

### Post by esac on 2008-09-07
If only they could fix their shoddy networking support for bridged networking. NAT simply does not cut it.

---

### Post by markba on 2008-09-08
> **NullHead said:**
> Anyone gotten intrepid ibex alpha5 to work under virtualbox yet?

This problem (in the kernel) should be solved in intrepid alpha-6 (September 18th):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067)

---

### Post by xebian on 2008-09-08
> **dark_phantom said:**
> Obviously I don't know your system setup, but the manual specifies the requirements in order to run 64 bit guests.

Got it figured out from the vbox forums. Because it's a new feature Vbox should have provided up front instructions how to set it up.  Thanks anyway.

---

### Post by xebian on 2008-09-08
> **NullHead said:**
> Anyone gotten intrepid ibex alpha5 to work under virtualbox yet?

It's a hit and miss.  On some days, Xubuntu will work, or Kubuntu does but not the others.

But for todays' build - 9/8/2008, looks like they work on vb 2.0

---

### Post by NullHead on 2008-09-08
> **xebian said:**
> It's a hit and miss.  On some days, Xubuntu will work, or Kubuntu does but not the others.

But for todays' build - 9/8/2008, looks like they work on vb 2.0

Beg your pardon, I had no idea they did daily builds? Is that what I'm interpreting form your sentence? That was exactly what I was wishing they did for alpha-beta-rc stuff :D

---

### Post by xebian on 2008-09-08
> **NullHead said:**
> Beg your pardon, I had no idea they did daily builds? Is that what I'm interpreting form your sentence? That was exactly what I was wishing they did for alpha-beta-rc stuff :D

Where have you been all these years?  You need to get out of that 'narrow' aperture sometimes.  :)

cdimages.ubuntu.com in case you haven't heard of Google yet.:)

---

### Post by NullHead on 2008-09-09
It's down :( 

I'll keep my eyes peeled for its re-opening though :D

---

