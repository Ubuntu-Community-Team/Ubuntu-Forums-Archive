---
title: "[HELP] VFIO Virtualization IOMMU ERROR RMRR GPU passthrough"
date: 2015-10-14
forum: Virtualisation
---

### Post by sspeedy43 on 2015-10-14
Using these guides I was able to get most everything setup:

[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)
[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)


Everything is ready to go and start the virtual machine, however I am getting a unique error that Im having trouble searching for and finding a resolution. 

IOMMU GROUPS ARE SETUP
DEVICES ARE BLACKLISTED (I THINK)

ERROR: 

```
qemu-system-x86_64: -device vfio-pci,host=0b:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: failed to set iommu for container: Operation not permitted
qemu-system-x86_64: -device vfio-pci,host=0b:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: failed to setup container for group 19
qemu-system-x86_64: -device vfio-pci,host=0b:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: failed to get group 19
qemu-system-x86_64: -device vfio-pci,host=0b:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device initialization failed.
qemu-system-x86_64: -device vfio-pci,host=0b:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device 'vfio-pci' could not be initialized
```

Alright, so I checked some dmsg logs

```
[  116.814073] vfio-pci 0000:0b:00.0: Device is ineligible for IOMMU domain attach due to platform RMRR requirement.  Contact your platform vendor.
[ 1136.576661] vfio-pci 0000:0b:00.0: Device is ineligible for IOMMU domain attach due to platform RMRR requirement.  Contact your platform vendor.

```

Anything I am doing wrong? I found that a user had a similar issue with trying to virtualize a whole RAID CONTROLLER but he said the GPU was working fine. That thread is closed and that topic destroyed, so I cant ask him. (Even though his issue was RAID CONTROLLER pass and mine is GPU.)

Is it kernel related? I haven't touched the kernel in terms of patches I'm just using standard Ubuntu 14.04.3

---

### Post by sspeedy43 on 2015-10-16
Anyone?

---

### Post by KillerKelvUK on 2015-10-17
When you stay blacklisted (i think)....

if you're using vfio then why arent you stubbing the devices or is this what you mean?  You can tell in a number of ways whether the module has been loaded or not for the hardware 'lspci -vvv' or a 'dmesg | grep stub' for instance.

Please can you also paste back your IOMMU group list, use this if you like or your own code (i pinched this off someone else) [ATTACH]264997[/ATTACH]

Have you confirmed vt-d is enabled in your bios also?

---

