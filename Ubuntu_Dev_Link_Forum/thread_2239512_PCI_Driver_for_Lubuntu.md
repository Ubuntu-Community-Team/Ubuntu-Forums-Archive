---
title: "PCI Driver for Lubuntu"
date: 2014-08-14
forum: Ubuntu Dev Link Forum
---

### Post by cart2 on 2014-08-14
Hey guys

I am tasked with writing a PCI driver for lubuntu or any linux really but I thought where better to start with a lightweight Ubuntu.

No what I am suppose to do with the PCI driver for is literally just latch onto a piece of RAM and dump all of the content to a file.
Im using the PLX PCI9054.

I am having trouble finding the libraries to do this though. I thought that using the libraries in /usr/include/linux/pci.h would give me some functions to work with like attaching the devices and attach the device handler too like "pci_attach_device() but I cant find any of these functions. Also mmap_device_memory(); 

Keep in mind that I dont need to do any PCI configuration. Everything is done on startup with an FPGA!
So I will be accessing the already set block or RAM.

The functions above are QNX functions and they work fine but I need Linux equivalents.

Anybody have any idea on where I can start looking to get this going ?

Thanks and regards
Cart

---

