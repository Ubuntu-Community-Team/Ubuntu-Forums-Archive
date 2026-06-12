---
title: "sifive unmatched hugespages"
date: 2024-10-13
forum: Server Platforms
---

### Post by ctclmsn on 2024-10-13
I've installed the ubuntu riscv distribution for a sifive unmatched dev board ([https://ubuntu.com/download/risc-v](https://ubuntu.com/download/risc-v)) onto an internal SSD M2 storage media. Because of the dev board's design, the boot process has to start from microSD. UEFI/U-Boot has directives turned on that allow it to redirect the boot process to the internal SSD M2 storage media. I've verified my ubuntu distribution is booting from the internal SSD M2 storage media.

The ubuntu riscv distribution has hugepages turned on (/proc/meminfo has variables and values set for hugepages). By default, the ubuntu riscv distribution sets hugepages to 2MB. I'd like to set the value to something larger. I've modified the grub.conf file and run the grub update tool but the value continues to be 2MB.

modified `/boot/grub/grub.cfg`with the following content:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hugepagesz=1024MB hugepages=1 default_hugepagesz=1024MB iommu=pt"
> GRUB_CMDLINE_LINUX="quiet splash hugepagesz=1024MB hugepages=1 default_hugepagesz=1024MB iommu=pt"

`$> update-grub`

modified `/etc/sysctl.conf` with the following content:

> vm.nr_hugepages = 1

Any help would be greatly appreciated!

---

