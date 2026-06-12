---
title: "Lenovo E531 (UK) with 14.04 Report"
date: 2014-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by carl4926 on 2014-12-12
Recently had a E531 from Ebuyer UK

14.04 went on it and it's flawless.

Here is the inxi info

```
ThinkPad-Edge-E531 Kernel: 3.13.0-40-generic x86_64 (64 bit)            Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO (portable) product: 6885DLG version: ThinkPad Edge E531
           Mobo: LENOVO model: 6885DLG version: 0B98401 WIN Bios: LENOVO version: HEET42WW (1.23 ) date: 01/27/2014
CPU:       Dual core Intel Core i3-3120M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 2500.00 MHz 2: 1200.00 MHz 3: 1200.00 MHz 4: 2500.00 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 10.1.3
Audio:     Card: Intel 7 Series/C210 Series Family High Definition Audio Controller driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-40-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: down mac: 68:f7:28:0f:20:bd
           Card-2: Intel Centrino Wireless-N 2230 driver: iwlwifi 
           IF: wlan0 state: down mac: 00:c2:c6:5b:92:6c
Drives:    HDD Total Size: 516.8GB (2.5% used) 1: id: /dev/sda model: WDC_WD5000LPVX size: 500.1GB 
           2: USB id: /dev/sdb model: Flash_Disk size: 16.7GB 
Partition: ID: / size: 43G used: 4.8G (12%) fs: ext4 ID: /home size: 408G used: 93M (1%) fs: ext4 
           ID: swap-1 size: 9.08GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 29.8C mobo: N/A 
           Fan Speeds (in rpm): cpu: 0 
Info:      Processes: 203 Uptime: 1 min Memory: 416.6/3524.8MB Client: Shell (bash) inxi: 1.9.17 
```

and also lspci -nnk

```
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)	Subsystem: Lenovo Device [17aa:5018]
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Lenovo Device [17aa:5018]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: rtsx_pci
04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
	Kernel driver in use: iwlwifi
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5018]
	Kernel driver in use: r8169
```

---

