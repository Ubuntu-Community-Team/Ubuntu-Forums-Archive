---
title: "dmesg error: Unable to read/write to IOMMU perf counter"
date: 2020-11-24
forum: Virtualisation
---

### Post by jcdenton1995 on 2020-11-24
Hello all.

I'm trying to set up PCI passthrough using [this guide]("https://mathiashueber.com/pci-passthrough-ubuntu-2004-virtual-machine/") however I've hit a snag (I think).

I've got as far as enabling the required options in the BIOS - SVM module and IOMMU - as well as setting the "amd_iommu=on" and "iommu=pt" parameters in /etc/default/grub. Also I have isolated my GPU and it's sound 'thingy' (controller?)

However when I run 'dmesg | grep AMD-Vi' I get the following error...```
[    0.642017] pci 0000:00:00.2: AMD-Vi: Unable to read/write to IOMMU perf counter.


```
all the rest of the output suggests everything else is working. I'd love to know what the IOMMU 'perf counter' is, cant find anything online about that. Loads of people have had the same error when trying to install various distros with many threads suggesting setting 'iommu=soft' in /etc/default/grub, however when I tried this I just got a dmesg error saying IOMMU wasn't available, or some similar message.

I've posted the specs of my computer below, I believe all my hardware supports what I'm trying to do (in theory)

Ubuntu 20.04.1 LTS
Kernel 5.4.0-54-generic
Asus ROG Strix X570-I
AMD Ryzen 3400G

Any advice would be much appreciated!

---

### Post by genomey on 2021-03-27
I am also having this exact same issue. I have a ryzen 7 Pro 4750g. I've tried everything every forum suggested. I'm using a B450 based gigabyte motherboard (I'll give my log files once I get access to my PC. I'm also using the linux kernel 5.11.10 on a Ubuntu 20.04 based distro.

I've noticed a common trend with every form post about this issue with IOMMU: they all use a ryzen chip with integrated graphics. Ryzen laptops and desktop cpus with vega graphics both have this issue and the majority of those threds aren't solved. 

This makes me think that the Linux Kernel has a critical issue with AMD-Vi support when the APU being intertwined with the IOMMU grouping.

I could be wrong, and my understanding/terminology is gathered from all the forums I've read. But I definitely know this is an issue bigger then simply setting IOMMU=soft.

---

### Post by CelticWarrior on 2021-03-27
> [COLOR=#000000]I've noticed a common trend with every form post about this issue with IOMMU: they all use a ryzen chip with integrated graphics.[/COLOR]
The IOMMU issue as well as the solution (boot parameter) is older than Ryzen. First time I've noticed it in person was in 2014, don't remember exactly which AMD CPU but I'm sure it wasn't a Ryzen and wasn't any APU either (=no iGPU). The problem is related with the motherboard's firmware and the chipset.

---

