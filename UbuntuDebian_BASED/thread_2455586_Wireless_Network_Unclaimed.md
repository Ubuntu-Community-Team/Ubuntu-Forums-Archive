---
title: "Wireless Network Unclaimed?"
date: 2020-12-23
forum: Ubuntu/Debian BASED
---

### Post by mr-snrub on 2020-12-23
Hi All, Linux noob here. I recently installed PopOS on my Teclast F6 plus and cannot get the system to recognize my wireless card (Intel 3165). I have tried literally dozens of fixes for similar issues I found on the Net but nothing works. Network Settings does not give me the option to add a wireless network, only wired and VPN. Based on my research I suspect the problem is a missing driver, but the 3165 is a common card and the driver should be included in the installation. In fact:[INDENT]
[B]ls /lib/firmware | grep 3165
[/B]
iwlwifi-3165-13.ucode
iwlwifi-3165-9.ucode
[/INDENT]

Here is some more output:

[INDENT][B]lshw -c net
[/B]
*-network UNCLAIMED       
       description: Network controller
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 79
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:80100000-80101fff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:5
       logical name: usb0
       serial: ca:88:d5:4e:13:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.156 link=yes multicast=yes

[B]lspci -knn | grep Net -A3; rfkill list
[/B]
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 79)
    Subsystem: Intel Corporation Wireless 3165 [8086:8110]
    Kernel modules: iwlwifi
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[/INDENT]

Can anyone help me? As I said I am a total noob and would appreciate explicit instructions. I am tethering though my phone and can download whatever packages I might need. Many thanks!

---

### Post by howefield on 2020-12-23
Moved to the "*Ubuntu/Debian BASED*" forum.

---

