---
title: "External display is not detected through HDMI (Intel WhiskeyLake-U GT2 card)"
date: 2021-06-09
forum: Ubuntu Development Version
---

### Post by kestutis1a on 2021-06-09
External display is not detected through HDMI
Computer: Lenovo E590
Ubuntu Impish Indri 21.10
Kernel: 5.11.0-18-generic

Graphic card:

```
lspci | grep -i --color 'vga\|3d\|2d'
00:02.0 VGA compatible controller: Intel Corporation WhiskeyLake-U GT2 [UHD Graphics 620]
```

```
sudo lshw -class display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: WhiskeyLake-U GT2 [UHD Graphics 620]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a1000000-a1ffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff
  *-display UNCLAIMED
       description: Display controller
       product: Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:90000000-9fffffff memory:a0000000-a01fffff ioport:3000(size=256) memory:a2400000-a243ffff memory:a2440000-a245ffff

```

---

### Post by wildmanne39 on 2021-06-09
Hello and welcome to the forum kestutis1a, since 21.10 has not been released yet I moved your thread to the Development sub-forum.

---

### Post by VMC on 2021-06-09
Is this installed or are you trying to install. Using live iso? Have you check your BIOS? If you have Windows installed, does it work using HDMI?
OK, I see you listed the kernel. Does HDMI work through live iso?

---

### Post by kestutis1a on 2021-06-10
Removing 'nomodset' from GRUB_CMDLINE_LINUX_DEFAULT parameter in /etc/default/grub helped.
The line which was left:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
then 
```
sudo update-grub
```
and the external dispaly is detected. The system boot load is not always even though.

---

