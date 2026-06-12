---
title: "Difficulties with VGA passthrough on gtx 760"
date: 2015-04-19
forum: Virtualisation
---

### Post by carter3 on 2015-04-19
Hello! I'm trying to VGA passthrough to work on my GTX 760 using this tutorial: [https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

However, whenever I try to run the virutal machine, I get this error...

qemu-system-x86_64: -device  vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on:  vfio: error, group 6 is not viable, please ensure all devices within the  iommu_group are bound to their vfio bus driver.
qemu-system-x86_64: -device vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: failed to get group 6
qemu-system-x86_64: -device vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device initialization failed.
qemu-system-x86_64:  -device  vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on:  Device 'vfio-pci' could not be initialized

Any idea what would cause this?

Edit: After some digging around I've found that this issue may be fixed by a patch found here: [https://lkml.org/lkml/2013/5/30/513](https://lkml.org/lkml/2013/5/30/513)

Unfortunately, I have no idea how to apply it. Can someone help me with that, and/or let me know if this patch will fix my problem?

---

### Post by Vegan on 2015-04-19
graphics cards are not designed for a virtual environment so use a basic display adapter driver for each virtualized instance

---

### Post by redger on 2015-04-19
errrr ... you have provided bery little information for debugging ..... but .....

IOMMU / VT-D functionality is designed to ensure isolation between devices allocated to VMs. Nett is that 2 devices in the same IOMMU group cannot be assigned to different VMs, ensuring that there is no data leakage between VMs

You either need to (a) assign all devices in the IOMMU group to the same VM (assign them to PCI-Stub first) (b) apply the ACS Override patch and set the kernel parameter

The definitive source for all this is the Arch discussion ..... you can find most of the info [http://ubuntuforums.org/showthread.php?t=2266916]("http://ubuntuforums.org/showthread.php?t=2266916") ... including all the references

tbh the easiest and most robust way to achieve this is to use UEFI and manage via virt-manager (libvirt) ..... then you'll also have a nice graphical front end to manage it with. The main proviso being that the UEFI approach is much easier with Win 8.1 than Win 7

---

### Post by carter3 on 2015-04-19
> **redger said:**
> errrr ... you have provided bery little information for debugging ..... but .....

IOMMU / VT-D functionality is designed to ensure isolation between devices allocated to VMs. Nett is that 2 devices in the same IOMMU group cannot be assigned to different VMs, ensuring that there is no data leakage between VMs

You either need to (a) assign all devices in the IOMMU group to the same VM (assign them to PCI-Stub first) (b) apply the ACS Override patch and set the kernel parameter

The definitive source for all this is the Arch discussion ..... you can find most of the info [http://ubuntuforums.org/showthread.php?t=2266916](http://ubuntuforums.org/showthread.php?t=2266916) ... including all the references

tbh the easiest and most robust way to achieve this is to use UEFI and manage via virt-manager (libvirt) ..... then you'll also have a nice graphical front end to manage it with. The main proviso being that the UEFI approach is much easier with Win 8.1 than Win 7
Alright, what more would you like to know? GTX 560 and 760. I have my 760 and it's audio device both claimed by the stub, but would the 560 also be part of the same IOMMU group? What defines the which group it's in? my 560 and it's audio device are in 01:00.0 and 01:00.1 respectovely while my 760 is in 07:00.0 and 07:00.1

How exactly would I go about doing it with UEFI and Virt-Manager? Is there perhaps I guide to follow or is it pretty simple?

---

### Post by redger on 2015-04-21
The link in my last post contains all the necessary inofrmation - read it first

from that link ........  Use this script to display the IOMMU groupings (thanks to Alex WIlliamson)
```
#!/bin/sh

# List the devices in each IOMMU group, from AW at
# https://bbs.archlinux.org/viewtopic.php?id=162768&p=29

BASE="/sys/kernel/iommu_groups"

for i in $(find $BASE -maxdepth 1 -mindepth 1 -type d); do
	GROUP=$(basename $i)
	echo "### Group $GROUP ###"
	for j in $(find $i/devices -type l); do
		DEV=$(basename $j)
		echo -n "    "
		lspci -s $DEV
	done
done
```

---

