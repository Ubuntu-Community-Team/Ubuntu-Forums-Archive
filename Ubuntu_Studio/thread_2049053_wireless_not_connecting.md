---
title: "wireless not connecting"
date: 2012-08-27
forum: Ubuntu Studio
---

### Post by dsikl on 2012-08-27
hey ppl, i just installed a fresh ubuntu studio lts 12.04 on my fresh assembled desktop with asus dka790gx........other than the stuff that comes with the board, i haven't installed anything yet, wanted to get the machine going first......apart from an old pci wireless card from conceptronic......the system recognized the hw right away, and it's picking up signals from routers in the house, but i simply can't connect.........i have ubuntu on my netbook and that connects to my router without hassles, all settings i can access as a linux noob look the same.......

can anyone help me out? what outputs to i need to post from the terminal?

cheers!

---

### Post by jejeman on 2012-08-28
Give us
```
sudo lshw -C network
```

---

### Post by dsikl on 2012-08-28
thanks for helping mate, here's the output:

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:5b:b2:07
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:e800(size=256) memory:feaff000-feafffff memory:fdff0000-fdffffff memory:feac0000-feadffff
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:80:5a:22:1b:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-23-lowlatency firmware=N/A latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:febf0000-febfffff


cheers!

---

### Post by jejeman on 2012-08-28
I don't see anything wrong
give us this, just to complete the info
```
lspci -nn
```for above just copy the line for the card.
```
dmesg |grep "ath5.*chip"
```

---

### Post by dsikl on 2012-08-28
mate I'm terribly sorry, it was my router! i got it fixed now and everything works just like it should!

when i realized i can't even connect via ethernet, no matter what laptop or cable i take, i thought that can't be right......so i tried changing the security policy, which basically locked me out of the device, i couldn't log on......so i reset it completely and all good!

thanks so much for your help! how should i mark the thread, as solved? didn't really have anything to do with ubuntu.......

cheers!

---

### Post by jejeman on 2012-08-28
I saw that ethernet was not good, but you didn't ask about that. ;)

You can mark it as solved.

---

### Post by mörgæs on 2012-08-28
> **dsikl said:**
> how should i mark the thread, as solved? 

By using 'thread tools' in the top right corner.

---

### Post by dsikl on 2012-08-28
oh the ethernet wasn't good? ok, thanks for mentioning, i'll do another thread for that, but only after i reinstall the system....had trouble with booting, swap was not functional and wanted to check hdd for bad sectors, then reinstall with separate partitions for /boot, /home, /data, /.....

thanks again for your help! and thank you mörgæs too for the hint...

cheers!

---

