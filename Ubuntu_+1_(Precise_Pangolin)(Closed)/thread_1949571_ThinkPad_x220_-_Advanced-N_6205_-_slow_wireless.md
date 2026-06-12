---
title: "ThinkPad x220 - Advanced-N 6205 - slow wireless"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by meborc on 2012-03-30
Hi, I have gone this thread - [http://ubuntuforums.org/showthread.php?t=1859151](http://ubuntuforums.org/showthread.php?t=1859151) , but it seems that the fixes proposed do not solve the problem for me.

the problem is that when I am connecting to "N" wireless network (university campus), my wireless is very slow. Speedtest.net is giving me a 0.7 Mbps :(

When I connect to a wireless at home, I get 10.0 Mbps. Also Windows 7 in the university is giving high speeds. So I have narrowed down the problem to be with software and only under some situations.

I tried the known trick by disabling 11n:```
$ sudo rmmod iwlagn
$ sudo modprobe iwlagn 11n_disable=1
```

but it has no effect and i think i am using the iwlwifi module anyway

any ideas?

lspci:```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 07)
0e:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

```
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:d0:ce:e0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:f2600000-f261ffff memory:f262b000-f262bfff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 10:0b:a9:8d:6d:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-20-generic firmware=17.168.5.3 build 42301 ip=193.11.93.94 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f2500000-f2501fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ncm driverversion=04-Aug-2011 firmware=CDC NCM link=no multicast=yes

```

---

### Post by Starks on 2012-03-30
See this bug:

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2328](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2328)

Only way around it is to load the iwlwifi module with the 11n_disable=1 option.

---

### Post by meborc on 2012-04-04
> **Starks said:**
> See this bug:

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2328](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2328)

Only way around it is to load the iwlwifi module with the 11n_disable=1 option.

tried that, but no change... however after latest updates my speed is back up

and this is defenetly not because of 11n_disable=1 as I did not make the change permanent

so all is well again

---

