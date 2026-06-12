---
title: "Netgear USB WiFi with Kodibuntu (Lubuntu)"
date: 2016-04-28
forum: Ubuntu/Debian BASED
---

### Post by shanekea on 2016-04-28
Greetings.

I can't seem to get a USB wireless adapter working with a recent installation of Kodibuntu, recently switching over from Win10. I've been scouring a few forums over the past couple days and tried what solutions I can understand and have had no luck. I do have a network connection via ethernet to the device.

Computer: Gateway SX2855
WiFi adapter: Netgear WNDA3100v3
OS: Kodibuntu as downloaded [here]("https://kodi.tv/download/")

I've tried both  ndiswrapper as well as the bcm43. Some outputs below, please let me know if there is anything else I can provide to help troubleshoot. I am not unfamiliar with Ubuntu, but am no expert by any means. Any help or insight is greatly appreciated.

iwconfig:
```
eth0      no wireless extensions.


lo        no wireless extensions.

```
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr c8:9c:dc:d3:d2:2a  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca9c:dcff:fed3:d22a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41152262 (41.1 MB)  TX bytes:2567044 (2.5 MB)
          Interrupt:20 Memory:fe400000-fe420000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120858 (120.8 KB)  TX bytes:120858 (120.8 KB)

```


lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)

```

lsusb:
```
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by wildmanne39 on 2016-04-29
*Thread moved to **(Other Operating Systems, Ubuntu/Debian Based)**.*

---

