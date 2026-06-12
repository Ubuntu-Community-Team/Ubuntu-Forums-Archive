---
title: "GPU passtruouth dosen't work"
date: 2017-10-28
forum: Virtualisation
---

### Post by mantazasas on 2017-10-28
Hello i followed this tutorial: [https://medium.com/@calerogers/gpu-virtualization-with-kvm-qemu-63ca98a6a172](https://medium.com/@calerogers/gpu-virtualization-with-kvm-qemu-63ca98a6a172) step by step just i used virt-manager to create my vm but when i start vm with PCI host device(nvidia gf730) then monitor attached to this gpu shuts down (no signal) and pc just freezes. Can  someone help me with this issue?

---

### Post by fredwntr1 on 2017-10-29
What's your hardware specs? Does your cpu support virtual extensions? Also do you have more than one pci device  plugged in? Is the graphics card in it's own iommu group? Are you using uefi in the virtual machine ( because if your not and you are using Intel graphics as your primary display for Linux you will have freezing Also use the guide from the arch wiki it's a little more accurate [https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF](https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF)

---

### Post by mantazasas on 2017-10-30
hello my specs are gpu nvidia ge force 730 cpu   Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz also i using intel graphics as primary display so i cant have  gpu passtruouth?

---

### Post by ODTech on 2017-10-30
> **mantazasas said:**
> hello my specs are gpu nvidia ge force 730 cpu   Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz also i using intel graphics as primary display so i cant have  gpu passtruouth?


You can but there are two things you have to check first.

You will need to firstly make sure that your Geforce 730 has a uefi bios. All modern cards should have a uefi bios but on the off chance that it does not you can most likely update it. See link below where you can look up your card and possibly get a uefi bios for it.
[https://www.techpowerup.com/vgabios/](https://www.techpowerup.com/vgabios/)

If it turns out your card does not have a uefi bios and it's not possible to update it then you can still get the vm to run but you will have to patch the linux kernel with the i915 vga arbitration patch as a workaround to the vga bios issue. In this case you will also not be able to run the vm in uefi mode but will have to use the classic seabios.

Secondy you have to check if your graphics card is in it's own iommu group. See link below to a full guide for pci passthrough on the mint forum. One of the first steps is to check the iommu grouping. 
[https://forums.linuxmint.com/viewtopic.php?f=231&t=212692](https://forums.linuxmint.com/viewtopic.php?f=231&t=212692)
Mint is based on Ubuntu so the guide is safe to follow on your ubuntu system.

---

