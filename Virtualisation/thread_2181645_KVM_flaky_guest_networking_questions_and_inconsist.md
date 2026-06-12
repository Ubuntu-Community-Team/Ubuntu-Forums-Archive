---
title: "KVM: flaky guest networking questions and inconsistent shutdown behavior"
date: 2013-10-18
forum: Virtualisation
---

### Post by arinekhen on 2013-10-18
Hi. I'm about a year into learning about KVM, and am running several production web servers with it. I have two identical x86 64-bit hosts running 12.04LTS, a primary and a secondary for redundancy. My four guests are also 12.04LTS, and they exist on both hosts, but are only in operation on the primary host. I have a single virbr0 serving all guest virtio nics. Traffic is low enough that I've had no issues with all traffic being on a single physical nic. I have three things I need to ask for help with.

First, one of my guests is configured with two virtual nics. This guest does not always become available on the real network upon reboot. It's always available by name and real IP from it's host, but sometimes it takes several reboots (or just waiting for ten-fifteen minutes) before it is available on the real network. The other three guests have a single virtual nic and have never behaved this way, so I assume I've done something wrong with the dual nic setup. Since it doesn't fail every time, I've had trouble figuring it out. Any suggestion on where to be looking?

Second, all of my guests are inconsistent when I SSH into them to shut them down with sudo poweroff. Even though the terminal session closes, sometimes nothing at all actually happens, and I have to log back in and try again. I shut them down this way because selecting the machine in virt-manager and choosing "shutdown" never works. Any ideas?

My last question is about tying guest virtual nics to physical ones. I have four nics on the hosts, so there's no reason I have to run all traffic through one. If performance ever becomes an issue, I'd like to establish an affinity for a physical nic for each guest. I did try it once - I created a new guest in virt-manager and configured the nic to use eth1-macvtap. when the guest came up, all networking on the host ceased. When I shutdown the guest, it recovered. What is the correct way to do this?

Thank you!

---

### Post by KillerKelvUK on 2013-10-21
Hi, have you installed the acpid package on your guests?  I believe this is needed for the reboot/poweroff, certainly power management using virt-manager won't work without it?

For your networking, please can you paste back a copy of your host /etc/network/interfaces file so we can take a look at your bridge and ip setup?

---

### Post by TheFu on 2013-10-23
I think you need VT-d support in hardware. Do you have that?

If you can clearly describe all the physical and logical networking, we should be able to help. Without that, any advice will be half-assed. ;)
The exact hardware involved for the networking is critical - not all switches and routers are created equal.

---

### Post by KillerKelvUK on 2013-10-25
> **TheFu said:**
> I think you need VT-d support in hardware. Do you have that?

If you can clearly describe all the physical and logical networking, we should be able to help. Without that, any advice will be half-assed. ;)
The exact hardware involved for the networking is critical - not all switches and routers are created equal.

VT-d support for what?  I was under the impression this allowed almost seemless passthrough for PCI devices e.g. gfx, telephony cards, raid etc.

Linux Bridge can bond a physical NIC to a virtual NIC, am doing this on my setup which isn't fully VT-d.

---

