---
title: "Wireless connection dropping"
date: 2012-09-11
forum: System76 Support
---

### Post by cephalopoda on 2012-09-11
Hello,

I'm running Ubuntu 12.04 64-bit, on my System76 Lemur. 

At home my wireless works perfectly, but while at work it drops my connection intermittently. In order to regain connectivity I must disable then re-enable Networking or Wireless (it will not reconnect on its own). This is extremely frustrating, and my IT support was of no help.

Can anyone help? Here is some output that may be useful:

iwconfig:
> 
lo        no wireless extensions.


          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:24:97:8A:69:BC   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:77  Invalid misc:342   Missed beacon:0

eth0      no wireless extensions.
lshw -C Network:
> 
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:9f:58:17
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-30-generic firmware=18.168.6.1 ip=128.54.9.248 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:f7d00000-f7d01fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:c5:3d:65
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 memory:f7c20000-f7c23fff ioport:e100(size=128) ioport:e000(size=256) memory:f7c10000-f7c1ffff memory:f7c00000-f7c0ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

lspci:
> 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)

lsusb:
> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 002 Device 004: ID 5986:0315 Acer, Inc 
Thanks.

---

### Post by isantop on 2012-09-11
> **cephalopoda said:**
> Hello,

I'm running Ubuntu 12.04 64-bit, on my System76 Lemur. 

At home my wireless works perfectly, but while at work it drops my connection intermittently. In order to regain connectivity I must disable then re-enable Networking or Wireless (it will not reconnect on its own). This is extremely frustrating, and my IT support was of no help.

Can anyone help? Here is some output that may be useful:

iwconfig:
lshw -C Network:
lspci:
lsusb:
Thanks.


See if you can get the IT at your work to reset the WAPs/Routers there. That will usually clear up most WiFi issues.

---

### Post by steeldriver on 2012-09-11
The Intel drivers often barf on wireless n mode - you could try this

[http://ubuntuforums.org/showthread.php?t=2055086&highlight=iwlwifi](http://ubuntuforums.org/showthread.php?t=2055086&highlight=iwlwifi)

If your home router runs in g mode and work is n that might explain the difference

---

