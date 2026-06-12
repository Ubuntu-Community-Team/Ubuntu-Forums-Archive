---
title: "Persisting Group error in egpu passthrough with in Qemu"
date: 2018-08-19
forum: Virtualisation
---

### Post by nadaeck on 2018-08-19
Hi 

I'm trying to passthrough an egpu (Nvidia GTX 1050 mobile) to my virtual machine on qemu.

I've followed every steps according to this guide :

[https://github.com/kholia/OSX-KVM/blob/master/HighSierra/README.md](https://github.com/kholia/OSX-KVM/blob/master/HighSierra/README.md)

 - I edited line GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.blacklist=1 iommu=pt intel_iommu=on"

```

 - I added 

```
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```

    to /etc/modules

 - nvidia driver is not installed and nouveau driver is blacklisted

 - I've added the ids of the devices to be passed through to the /etc/modprobe.d/vfio.conf

```
options vfio-pci ids=10de:1c8d,10de:0fb9,8086:15d4,8086:9d18,8086:15d3,8086:15d2 disable_vga=1

```

and I still have a vfio error :

```
vfio error: 0000:0b:00.0: group 7 is not viable
Please ensure all devices within the iommu_group are bound to their vfio bus driver.

```

Since it is egpu, in the group 7, including the VGA and the audio device, I have 13 members when I list them is lspci

I have passed them all : all the ids were added to the /etc/modprobe.d/vfio.conf file (some are the same : 8086:15d3 is the same for al least 5 different entries from lspci, and I added a line such as 

```
-device vfio-pci,host=0b:00.1,bus=pcie.0 \
```

to the booting file of qemu for each of the 13 entries of lspci belonging to the same group 

Still I have the same error :

```
vfio error: 0000:0b:00.0: group 7 is not viable
Please ensure all devices within the iommu_group are bound to their vfio bus driver.

```

My lspci with groups:
```

IOMMU Group 0 00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5904] (rev 02)
IOMMU Group 1 00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
IOMMU Group 2 00:08.0 System peripheral [0880]: Intel Corporation Skylake Gaussian Mixture Model [8086:1911]
IOMMU Group 3 00:13.0 Non-VGA unclassified device [0000]: Intel Corporation Sunrise Point-LP Integrated Sensor Hub [8086:9d35] (rev 21)
IOMMU Group 4 00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
IOMMU Group 4 00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
IOMMU Group 5 00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
IOMMU Group 6 00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d10] (rev f1)
IOMMU Group 6 00:1c.2 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port [8086:9d12] (rev f1)
IOMMU Group 6 00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
IOMMU Group 6 02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader [10ec:525a] (rev 01)
IOMMU Group 6 04:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 88)
IOMMU Group 6 05:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961 [144d:a804]
IOMMU Group 7 00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 [8086:9d18] (rev f1)
IOMMU Group 7 06:00.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 07:00.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 07:01.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 07:02.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 07:04.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 08:00.0 System peripheral [0880]: Intel Corporation JHL6540 Thunderbolt 3 NHI (C step) [Alpine Ridge 4C 2016] [8086:15d2] (rev 02)
IOMMU Group 7 09:00.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 0a:01.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 0a:04.0 PCI bridge [0604]: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016] [8086:15d3] (rev 02)
IOMMU Group 7 0b:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] [10de:1c8d] (rev a1)
IOMMU Group 7 0b:00.1 Audio device [0403]: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:0fb9] (rev a1)
IOMMU Group 7 0c:00.0 USB controller [0c03]: Intel Corporation JHL6540 Thunderbolt 3 USB Controller (C step) [Alpine Ridge 4C 2016] [8086:15d4] (rev 02)
IOMMU Group 8 00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d4e] (rev 21)
IOMMU Group 8 00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
IOMMU Group 8 00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev 21)
IOMMU Group 8 00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
IOMMU Group 8 00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-LM [8086:15d7] (rev 21)
```

I also followed this guide, with a patched 4.16 kernel  :

[URL="https://www.reddit.com/r/VFIO/comments/8es86f/successful_thunderbolt3_gpu_passthrough_on_lenovo/"]https://www.reddit.com/r/VFIO/comments/8es86f/successful_thunderbolt3_gpu_passthrough_on_lenovo/
[/URL]
The patch seems working : I have now 7 entries in the lspci group

Same error...

Could you please help me to figure out what is missing here?

Thank you

Victor

---

### Post by KillerKelvUK on 2018-08-23
The error would suggest you still don't have the require IOMMU separation of your GFX card and so the patch/kernel config isn't correct.  A quick read of that link to reddit suggests that patching the kernel is no longer needed for your hardware, have you re-read the thread since those edits were made?

---

