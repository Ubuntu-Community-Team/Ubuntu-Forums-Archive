---
title: "VirtualBox video card Windows 95/98"
date: 2014-10-20
forum: Virtualisation
---

### Post by lovehart942 on 2014-10-20
Hello, ):Pyes you. I am trying to get a diffrent Video card in VirtualBox for Windows (95/98). I know the  VirualBox Virtualize HardWear And It already has a Virtual video card for It (defalt manly VGA) But I need to know how to change it (for more colors) *wine cant run the programs well so need to run it on VirtualbBox using Windows 95/98*.  So how do I change the video card?

---

### Post by CharlesA on 2014-10-20
You can't change what video card virtualbox presents, but you could try increasing the video memory. If you are running a Windows 95 or 98 VM, you probably doesn't need much.

---

### Post by lovehart942 on 2014-11-04
Why can't I change the video card? Virtual box can Virtualize Hardware. (By the way I use Ubuntu 14.04, didn't mention that last time)      And how whould increasing memory help?

---

### Post by SeijiSensei on 2014-11-04
VirtualBox presents a virtualized video adapter to the VM.  The virtual machine does not talk directly to the video hardware. Same is true for networking.  The VM sees a virtual Intel gigabit Ethernet adapter regardless of the actual hardware on the machine.

As Charles says, increase the video memory to 64M or 128M.  You should also install the "Extension Pack" as described on the VirtualBox website since it has some proprietary driver extensions that can help with some video adapters.

---

### Post by QIII on 2014-11-04
Just as clarification if there is any misunderstanding.

It's not that VBox *can *virtualize hardware.  It *does *virtualize hardware.  But it virtualizes the specific hardware as determined by its developers.  You cannot, for instance, decide that it should virtualize an ATI card and flip a switch somewhere.

To do something like that you would need a KVM (Kernel-based Virtual Machine) along with Spice to (more or less) communicate directly with your graphics hardware.  Be advised, however, that setting up this sort of thing is not exactly trivial and sometimes using Spice can frustrate your host OS's use of the resource.

VirtualBox is simply not that sophisticated.

---

### Post by lovehart942 on 2014-11-15
So is spice and KVM an extension for Virtual Box or another virtualizing program?

---

### Post by TheFu on 2014-11-15
For simplicity, KVM is like virtualboxmanage.
There are a few "hypervisors" for Linux. It is best to only install 1 of these at a time.
* virtualbox
* vmware player
* vmware workstation
* Xen
* KVM
* LXC (which can be installed with any of the others)

The last 3 do not ahve a built-in GUI, but for Xen and KVM, using the virt-manager tool does provide a similar GUI experience as the virtualbox GUI does. Xen an KVM and LXC are designed for servers, so running them local is not assumed.

Spice is a remote desktop method and I think it is currently only available through KVM. I found it too much trouble for the performance and completely lacking in security (unless we add a VPN). There are many remote access methods, some are easy, some are secure, some are efficient and others are not.

If you want to dedicate a specific video card to a guest OS, this is non-trivial and only works with very specific hardware (GPU, BIOS, MB, CPUs), with very specific kernels, and with very specific guestOSes.  I'd guess fewer than 0.5% of all people using virtualization in the world have gotten that to work. There is a thread here about it, if you want to read more and see how few people got it working.

---

