---
title: "KVM or Xen for GPU pass-through?"
date: 2012-11-25
forum: Virtualisation
---

### Post by DuckHook on 2012-11-25
For years I've used VirtualBox to successfully run XP and Vista clients on my Ubuntu box, and am considering taking the next step to either Qemu/KVM or Xen. Have always toyed with the idea, but never made the switch because VirtualBox is so easy to use whereas KVM has always suffered from the typical Linux obscurity/learning curve. Reason: AFAIK VirtualBox is a type 2 virtualizer which runs on ring 1 whereas KVM and Xen are type 1 virtualizers running on ring 0. This allows KVM and Xen to at least theoretically pass through PCI devices to the virtualized client, thus bypassing the translation layer that type 2 virtualizers like VirtualBox must use. At least, this is what I've been able to gather from Wikipedia and some research on the net. I may be totally off base here and spouting meaningless nonsense.

My goal is to pass through client video demands to physical hardware rather than the emulated virtual graphics adapter. I understand that Xen now does this (with a lot of blood, sweat and tears), but wonder if KVM is there yet (or will ever be). I also have the impression that KVM is more tightly tied into the Kernel than Xen and runs faster (with the important exception of graphics). I assume I'm not the only one interested, as one of the biggest attractions of virtualization for the average user is running Windows games in a VM without having to sacrifice major gaming features or video performance. My knowledge at this point is all full of holes and second-hand, and I welcome enlightenment from the assembled gurus here.

So my question is actually twofold:

1. Is my understanding of type1/ring0 vs type2/ring1 correct? And if so,

2. Which is the better virtualizer for graphics pass-through? KVM or Xen?

---

### Post by heiko_s on 2013-01-19
Just saw your post - hope the answer is still relevant.

1. Generally speaking yes. KVM and Xen are hypervisors that work directly on the bare-metal hardware. They sit in between the operating system(s) (e.g. Linux) and the hardware.

2. Xen was the first to adopt VGA passthru and is constantly improving on it. Most of the VGA passthru success reports are from Xen users, though some KVM users have succeeded too.
As it stands now, Xen has by far better documentation on that subject.

You should be aware that the right hardware is absolutely critical to implement GPU passthrough! This means VT-d (IOMMU) support in both the CPU and the motherboard, as well as a compatible graphics card. In most cases AMD will be the better choice for a graphics card.

Here some references:
[http://wiki.xen.org/wiki/Xen_VGA_Passthrough]("http://wiki.xen.org/wiki/Xen_VGA_Passthrough")
[http://wiki.xen.org/wiki/XenVGAPassthroughTestedAdapters]("http://wiki.xen.org/wiki/XenVGAPassthroughTestedAdapters")

A how-to for Linux Mint - should work similarly for Ubuntu:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013")

An Ubuntu-based how-to: [http://gro.solexiv.de/2012/08/pci-passthrough-howto/]("http://gro.solexiv.de/2012/08/pci-passthrough-howto/")

For Fedora:
[http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine")

This should get you started.

---

