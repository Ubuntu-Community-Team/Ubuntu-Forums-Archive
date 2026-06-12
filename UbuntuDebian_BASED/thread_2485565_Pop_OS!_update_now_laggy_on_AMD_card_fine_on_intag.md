---
title: "Pop_OS! update now laggy on AMD card fine on intagrated video"
date: 2023-04-02
forum: Ubuntu/Debian BASED
---

### Post by obese-chinchilla on 2023-04-02
HDMI out from motherboard on AMD 5800G works fine, but using video from AMD 6750 interface is laggy / sluggish, after an OS update.
I used refresh OS to go back ,and it worked again.
After trying the update again, I can't refresh.


I found this thread, but there is no resolution.
[https://ubuntuforums.org/showthread.php?t=2472039](https://ubuntuforums.org/showthread.php?t=2472039)

A poster in the above thread asked for a terminal result, I ran it and pasted it below.

While on integrated graphics:
chinchew@pop-os:~$ sudo lshw -c video
[sudo] password for chinchew:
  *-display                 
       description: VGA compatible controller
       product: Navi 22 [Radeon RX 6700/6700 XT / 6800M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: /dev/fb1
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=1920,1080
       resources: irq:92 memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:e000(size=256) memory:fcb00000-fcbfffff memory:fcc00000-fcc1ffff
  *-display
       description: VGA compatible controller
       product: Cezanne
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: /dev/fb0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=1920,1080
       resources: irq:49 memory:b0000000-bfffffff memory:c0000000-c01fffff ioport:d000(size=256) memory:fca00000-fca7ffff memory:c0000-dffff

---

