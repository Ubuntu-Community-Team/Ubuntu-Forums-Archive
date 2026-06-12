---
title: "Trying to get IOMMU to work"
date: 2018-11-19
forum: Virtualisation
---

### Post by andrew187 on 2018-11-19
Hi,

I have been trying to get passthrough to work, but I am not having any luck. I was hoping that someone here could help.
The  reason is, I have wanted to run Windows 98 SE for a while to play some  old games and mess around with the "Intel book" by B. Brey.

I  can get Win 98 to install and run if I change the Domain in the XML from  KVM -> QEMU. However, no networking with QEMU. BTW, it will not  finish starting up (Stops at a black screen with a flashing cursor) with  Domain = KVM.
I have tried F8 -> Step-by-step but that doesn't work.

So I figured I would use passthrough.

I have the following in my grub file:
```

GRUB_CMDLINE_LINUX="intel_iommu=on"

```

When I run: 
```

dmesg | grep -e DMAR -e IOMMU
[    0.000000] DMAR: IOMMU enabled

```

All I get is that one line. 

Also if I:
dmesg | grep "Virtualization Technology for Directed I/O"

I do not get anything.
Does that mean that IOMMU is not supported?

My laptop Spec:
HP Envy M6
CPU: i7 3632QM
RAM: 16Gb

Xubuntu 18.10

Any help would be appreciated.
Kind regards.

---

### Post by QIII on 2018-11-19
Hello!

It might be helpful for those wishing to provide support to explain exactly what you want to pass through.

---

### Post by andrew187 on 2018-11-20
Ah, sorry about that.

The network card would be nice. I am ok with the video cards resolution.
From the little I know, the line that say's " Kernel driver in use: r8169" should say something like " Kernel driver in use: vfio-pci"...I think.
```

07:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 2000 [size=256]
    Memory at 61404000 (64-bit, prefetchable) [size=4K]
    Memory at 61400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

Edit:
When I enter the command:
find /sys/kernel/iommu_groups/ -type l

I don't get anything.
([http://vfio.blogspot.com/2014/08/iommu-groups-inside-and-out.html](http://vfio.blogspot.com/2014/08/iommu-groups-inside-and-out.html))

---

### Post by andrew187 on 2018-11-20
All good, I found the answer.

I had VMX (aka VT-x) but did not have VT-d (Virtualization Technology for Directed I/O, Intel's version of AMD's IOMMU (input/output memory management unit)).
My CPU spec: [https://ark.intel.com/products/71458/](https://ark.intel.com/products/71458/)
```


[LIST]
[*]Intel® Virtualization Technology (VT-x)                            Yes
[*]Intel® Virtualization Technology for Directed I/O (VT-d)      No
[/LIST]


```

The link below helped with my understanding of the technology. Talk about acronym craziness.
[https://en.wikipedia.org/wiki/X86_virtualization](https://en.wikipedia.org/wiki/X86_virtualization)

---

