---
title: "GPU Passthrough Need Help"
date: 2021-01-18
forum: Virtualisation
---

### Post by usr100101011 on 2021-01-18
Hi everyone, please I realy need help!

I followed this guid:
[https://www.server-world.info/en/note?os=Ubuntu_18.04&p=kvm&f=11](https://www.server-world.info/en/note?os=Ubuntu_18.04&p=kvm&f=11)

I have a HP Rackserver with a Nvidia Tesla K40 card and did following:

lspci -nn | grep -i nvidia
21:00.0 3D controller [0302]: NVIDIA Corporation GK110BGL [Tesla K40m] [10de:1023] (rev a1)

added GRUB_CMDLINE_LINUX="intel_iommu=on iommu=pt pci=realloc pci=nocrs rdblacklist=nouveau nouveau.modeset=0 pci-stub.ids=10de:1023"
in /etc/default/grub

made a new file:
/etc/modprobe.d/vfio.conf
and added:
options vfio-pci ids=10de:1023

than:
echo 'vfio-pci' > /etc/modules-load.d/vfio-pci.conf

and finaly:
reboot


Now when I do:
dmesg | grep -E "DMAR|IOMMU"
I get:
[    0.007430] ACPI: DMAR 0x00000000DF61FE80 000278 (v01 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.359433] DMAR: IOMMU enabled
[    0.683411] DMAR-IR: This system BIOS has enabled interrupt remapping
[    1.498193] DMAR: Host address width 39
[    1.498197] DMAR: DRHD base: 0x000000f7ffe000 flags: 0x0
[    1.498238] DMAR: dmar0: reg_base_addr f7ffe000 ver 1:0 cap c90780106f0462 ecap f0207e
[    1.498241] DMAR: DRHD base: 0x000000e7ffe000 flags: 0x1
[    1.498247] DMAR: dmar1: reg_base_addr e7ffe000 ver 1:0 cap c90780106f0462 ecap f0207e
[    1.498250] DMAR: RMRR base: 0x000000df7fc000 end: 0x000000df7fdfff
[    1.498252] DMAR: RMRR base: 0x000000df7f5000 end: 0x000000df7fafff
[    1.498254] DMAR: RMRR base: 0x000000df63e000 end: 0x000000df63ffff
[    1.498256] DMAR: ATSR flags: 0x0
[    1.498259] DMAR: ATSR flags: 0x0
[    1.498602] DMAR: dmar0: Using Queued invalidation
[    1.498615] DMAR: dmar1: Using Queued invalidation
[    1.503103] DMAR: Intel(R) Virtualization Technology for Directed I/O
[    1.831875] ata_piix 0000:00:1f.2: DMAR: 32bit DMA uses non-identity mapping
[    2.081389] ehci-pci 0000:00:1d.7: DMAR: Setting identity map [0xdf7fc000 - 0xdf7fdfff]
[    2.133679] ehci-pci 0000:00:1d.7: DMAR: 32bit DMA uses non-identity mapping
[    2.631651] uhci_hcd 0000:00:1d.0: DMAR: Setting identity map [0xdf7f5000 - 0xdf7fafff]
[    2.631671] uhci_hcd 0000:00:1d.0: DMAR: 32bit DMA uses non-identity mapping
[    2.632480] uhci_hcd 0000:00:1d.1: DMAR: Setting identity map [0xdf7f5000 - 0xdf7fafff]
[    2.632498] uhci_hcd 0000:00:1d.1: DMAR: 32bit DMA uses non-identity mapping
[    2.633227] uhci_hcd 0000:00:1d.2: DMAR: Setting identity map [0xdf7f5000 - 0xdf7fafff]
[    2.633245] uhci_hcd 0000:00:1d.2: DMAR: 32bit DMA uses non-identity mapping
[    2.634053] uhci_hcd 0000:00:1d.3: DMAR: Setting identity map [0xdf7f5000 - 0xdf7fafff]
[    2.634072] uhci_hcd 0000:00:1d.3: DMAR: 32bit DMA uses non-identity mapping
[   16.138327] hpsa 0000:05:00.0: DMAR: 32bit DMA uses non-identity mapping
[   17.461917] aacraid 0000:02:00.0: DMAR: Setting identity map [0xdf63e000 - 0xdf63ffff]
[   17.629606] aacraid 0000:02:00.0: DMAR: 32bit DMA uses non-identity mapping
[   75.656262] DMAR: DRHD: handling fault status reg 2
[   75.679287] DMAR: [DMA Read] Request device [05:00.0] PASID ffffffff fault addr fffcc000 [fault reason 06] PTE Read access is not set

But whe I do:
dmesg | grep -i vfio
I only get:
[    1.843070] VFIO - User Level meta-driver version: 0.3

Can' someone please tell me what I did wrong!

---

### Post by Tadaen_Sylvermane on 2021-01-20
[https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/](https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/)

The above is what I followed and got gpu passthrough working. It's a bit in depth and explains a bunch. Ultimately it's really a simple process assuming you have the hardware for it. According to the link you did your grub line wrong I think.

```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on kvm.ignore_msrs=1 vfio-pci.ids=10de:1023"
```

Add additional pci ids separated by a comma as needed. 

```
sudo update-grub
```

Everything else is pretty straight forward. Make sure to add the hardware when building the vm with virt-manager.

---

