---
title: "Help setting up video driver, freezes while streaming"
date: 2017-01-09
forum: Ubuntu/Debian BASED
---

### Post by pemartins on 2017-01-09
I hope this is the right place to post this, if it is not please move this thread to the proper place.

These are my settings:
AMD Graphics Card: Radeon HD 7340
Laptop System: ASUS X55U-SX038H
Operating System: LXLE 16.04.1 64bits (based on Lubuntu), Kernel Linux 4.4.0.57-generic (x86_64)
Driver version installed: 00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7340]
Display Devices: 1366x768
Motherboard CPU/APU: 2x AMD E2-1800 APU with Radeon HD Graphics
RAM: 4G

I'm having trouble running hd streams, like for instance in Youtube at 720. I'm getting a freeze of a second every few seconds I think because there's a slight delay on the video display, so I'd like to find a way to fix this.
This freeze happens in Chrome, Opera and Firefox with hd streams no matter the source, so it's not an issue of browser or provider.

AMD doesn't support my graphic card on 16.04 so I'm using the generic driver, it's called Radeon I think. I tried to add this ppa so I could get new driver updates but I have no idea if it made any change to the driver I'm using or not: [https://www.epicgames.com/unrealtournament/forums/showthread.php?23665-How-to-update-Open-Source-graphic-driver-in-Ubuntu](https://www.epicgames.com/unrealtournament/forums/showthread.php?23665-How-to-update-Open-Source-graphic-driver-in-Ubuntu)

I have no idea how to configure the video settings and even if I did I wouldn't now what to change. In Windows 10 it all works fine so it should me a matter of some small adjustment.

This is the output of :~$ sudo lshw -C display

```
  *-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 7340]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:d0000000-dfffffff ioport:f000(size=256) memory:feb00000-feb3ffff


```

Here's the /var/log/Xorg.0.log: [http://paste.ubuntu.com/23773087/](http://paste.ubuntu.com/23773087/)

Please let me know what more info I can provide in order to try to solve this issue.

Thank you very much in advance.

---

### Post by howefield on 2017-01-09
Moved to the "*Ubuntu/Debian BASED*" forum.

---

