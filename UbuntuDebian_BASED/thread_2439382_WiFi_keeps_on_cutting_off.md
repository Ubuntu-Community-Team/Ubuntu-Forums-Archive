---
title: "WiFi keeps on cutting off"
date: 2020-03-27
forum: Ubuntu/Debian BASED
---

### Post by andre1230 on 2020-03-27
I am using Zorin OS, which is based off Ubuntu 18.04. But the problem I face is that my WiFI keep on getting cut off whenever i'm connected to my mobile hotspot. When I connect to my router, I have no problems, it works seamlessly. But whenever I connect to my phone hotspot, the connection cuts off after seconds. I have to use the command "sudo systemctl restart NetworkManager.service" everytime i boot the laptop and connect to the hotspot, only then does the connection work without any issues. I was using Ubuntu 18.04 before switching to Zorin OS, but this was there when I was using Ubuntu as well. Is there any way I can fix this issue properly?
Here is my wireless adapter info.:
  
Description: Wireless interface
         product: RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]
         vendor: Ralink corp.
         physical id: 0
         bus info: pci@0000:01:00.0
         logical name: wlo1
         version: 00
         serial: 7c:e9:d3:9a:c8:11
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=rt2800pci driverversion=5.3.0-42-generic firmware=0.40 ip=192.168.43.65 latency=0 link=yes multicast=yes wireless=IEEE 802.11
         resources: irq:16 memory:c2500000-c250ffff

---

### Post by wildmanne39 on 2020-03-27
Thread moved to Ubuntu/Debian BASED sub-forum.

---

