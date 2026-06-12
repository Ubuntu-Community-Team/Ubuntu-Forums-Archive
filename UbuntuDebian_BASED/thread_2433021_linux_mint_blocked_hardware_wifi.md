---
title: "linux mint blocked hardware wifi"
date: 2019-12-12
forum: Ubuntu/Debian BASED
---

### Post by zivaralam on 2019-12-12
hello everyone
i have installed Linux mint 19.2 on my laptop (ASUS x45v)
after running rfkill list all i receive this message:
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
and when i press fn + f2 and run again this command i receive this 
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
as a fact  i can only on and of the soft blocked not hard blocked .
please if anybody knows about that , tell me  [IMG]https://forums.linuxmint.com/images/smilies/icon_idea.gif[/IMG]  [IMG]https://forums.linuxmint.com/images/smilies/icon_razz.gif[/IMG] thanks a lot
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
with fn+f2 i can just unblocked the soft blocked. not hardware.

1- after this code sudo lshw -C network
  *-network DISABLED        
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0f0
       version: 00
       serial: 68:94:23:5e:58:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.18.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f7910000-f791ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: enp4s0f2
       version: 0a
       serial: 08:60:6e:4c:bb:cc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.178.32 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 ioport:d000(size=256) memory:ea104000-ea104fff memory:ea100000-ea103fff


2- after this code nmcli dev wifi rescan
Error: Scanning not allowed while unavailable or activating.



3 after this code  : iw dev
phy#0
    Interface wlp3s0f0
        ifindex 3
        wdev 0x1
        addr 68:94:23:5e:58:b3
        type managed
        txpower 0.00 dBm


4- after this code : sudo ip link set wlp3s0f0 up   RTNETLINK answers: Operation not possible due to RF-kill

inxi -Fxz
System:
  Host: razieh-X45VD Kernel: 4.18.0-25-generic x86_64 bits: 64 compiler: gcc 
  v: 7.4.0 Desktop: Cinnamon 4.2.4 Distro: Linux Mint 19.2 Tina 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Laptop System: ASUSTeK product: X45VD v: 1.0 serial: <filter> 
  Mobo: ASUSTeK model: X45VD v: 1.0 serial: <filter> 
  UEFI: American Megatrends v: X45VD.207 date: 09/14/2012 
Battery:
  ID-1: BAT0 charge: 21.1 Wh condition: 21.0/49.5 Wh (42%) 
  model: ASUSTeK K55--44 status: Unknown 
CPU:
  Topology: Dual Core model: Intel Core i3-3110M bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 19157 
  Speed: 1197 MHz min/max: 1200/2400 MHz Core speeds (MHz): 1: 1197 2: 1197 
  3: 1197 4: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics vendor: ASUSTeK 
  driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA GF119M [GeForce 610M] vendor: ASUSTeK driver: nvidia 
  v: 390.116 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.19.6 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: GeForce 610M/PCIe/SSE2 v: 4.6.0 NVIDIA 390.116 
  direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k4.18.0-25-generic 
Network:
  Device-1: Ralink RT3290 Wireless 802.11n 1T/1R PCIe vendor: Foxconn 
  driver: rt2800pci v: 2.3.0 port: e000 bus ID: 03:00.0 
  IF: wlp3s0f0 state: down mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASUSTeK driver: r8169 v: 2.3LK-NAPI port: d000 bus ID: 04:00.2 
  IF: enp4s0f2 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 698.64 GiB used: 10.00 GiB (1.4%) 
  ID-1: /dev/sda vendor: Seagate model: ST750LM022 HN-M750MBB 
  size: 698.64 GiB temp: 33 C 
Partition:
  ID-1: / size: 684.49 GiB used: 9.77 GiB (1.4%) fs: ext4 dev: /dev/dm-1 
  ID-2: /boot size: 704.5 MiB used: 224.3 MiB (31.8%) fs: ext4 
  dev: /dev/sda2 
  ID-3: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-2 
Sensors:
  System Temperatures: cpu: 55.0 C mobo: N/A gpu: nvidia temp: 46 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 208 Uptime: 1h 37m Memory: 3.31 GiB used: 1.72 GiB (51.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.20 
  inxi: 3.0.32 



5 - after this code :

---

### Post by howefield on 2019-12-12
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by zivaralam on 2019-12-12
> **howefield said:**
> Thread moved to the "*Ubuntu/Debian BASED*" forum.

can you send me the link

---

### Post by howefield on 2019-12-12
> **zivaralam said:**
> can you send me the link

Link to what ?

You originally posted to an Ubuntu support forum for Ubuntu or Ubuntu flavours.

It has been moved to this sub forum which has a strapline of..

> Forum: Ubuntu/Debian BASED

Support for Ubuntu or Debian based distributions - not for Official Ubuntu flavours

Your thread has been moved to the appropriate sub forum.

---

### Post by mörgæs on 2019-12-14
> **zivaralam said:**
> 
Hard blocked: yes


Is there a mechanical or touch activated switch on the computer for disabling wifi access?

---

