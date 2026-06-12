---
title: "PCI Passthrough / Intel Graphics Issue"
date: 2017-03-11
forum: Virtualisation
---

### Post by droofe on 2017-03-11
Hello World!

I'm working on my new PC Build. Right now, I have Ubuntu Server 16.10 installed on top of

- Intel 7700k (yes it supports VT-d)
- 32 GB Ballistic DDR4 RAM
- 300GB Intel SSD for boot
- ASUS Z270 Mark 2 Motherboard
- Nvidia MSI Gefore 1070 Graphics Card

I'm trying to set up PCI passthrough so that I can use Windows 10 as a gaming PC as a VM. I've followed several tutorials about getting IOMMU and PCI passthrough setup. My computer has two use cases right now and I'm not sure what is causing this.

1.) Intel Graphics with NVIDIA Card in PCI Slot
When I boot the computer with the NVIDIA card in, the intel graphics cannot support more than 1072*768 graphics, and virt-manager says that my host does not support PCI-Passthrough, which I dont believe because obviously the OS can't get full access to the features of the processor. I feel like something about passing the NVIDIA card to vfio is causing the OS to not properly initialize the intel drivers.

2.) Only Intel Graphics Attached
The PC boots perfectly and opens a full 1920x1080 screen to the desktop.

If you need me to drop any configs please let me know. I'd really love to get this to work and drop my findings into a blog post for the future.

Thanks for your help!,
droofe

---

### Post by Delvien on 2017-03-15
You'll want to make sure virtualization support AND Vt-d is enabled in the bios, often times they are in separate options and sections (doesn't make sense, I know) 

Have you blacklisted nouveau, nvidia (and all variants)? 

Have you enabled your IOMMU groups in the kernel cmd part of grub?

In my experience, just because a board says it supports VT-d and IOMMU doesn't mean it can pass through GPUs.

Edit: Did you select the default graphics boot device to the igpu (intel) ?

---

