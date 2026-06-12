---
title: "Broadcom NetExtreme BCM57711 10gb"
date: 2011-09-27
forum: Server Platforms
---

### Post by rsh2000 on 2011-09-27
Hello :)

I am trying to setup

[LIST]
[*] [B]Broadcom NetExtreme BCM57711 10gb NIC 
[/B]
[/LIST]
**on**
[LIST]
[*]** 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux Ubuntu 10.10**
[/LIST]
The activity LED on the switch side is "on" but on the server side is "off"
The LSPCI command shows the NIC:

[LIST]
[*]           **  +-03.0-[02]--**
[*]**             +-07.0-[03]--+-00.0  Broadcom Corporation NetXtreme II BCM57711 10-Gigabit PCIe**
[*]**             |            \-00.1  Broadcom Corporation NetXtreme II BCM57711 10-Gigabit PCIe**
[/LIST]
[B]The dmesg output is:
[/B]
[LIST]
[*]** dmesg | grep bnx2x**
[*]**[   12.160475] Broadcom NetXtreme II 5771x 10Gigabit Ethernet Driver bnx2x 1.52.53-2 (2010/21/07)**
[*]**[   12.160648] bnx2x 0000:03:00.0: PCI INT A -> GSI 38 (level, low) -> IRQ 38**
[*]**[   12.160656] bnx2x 0000:03:00.0: setting latency timer to 64**
[*]**[   12.162080] bnx2x 0000:03:00.0: part number 394D4342-31373735-31314131-473331**
[*]**[   12.162978] bnx2x 0000:03:00.0: Loading bnx2x-e1h-5.2.13.0.fw**
[*]**[   12.288186] bnx2x 0000:03:00.0: eth4: Broadcom NetXtreme II BCM57711 XGb (A0) PCI-E x8 5GHz (Gen2) found at mem dc000000, IRQ 38, node addr 00:10:18:ae:c4:b8**
[*]**[   12.288217] bnx2x 0000:03:00.1: PCI INT B -> GSI 45 (level, low) -> IRQ 45**
[*]**[   12.288222] bnx2x 0000:03:00.1: setting latency timer to 64**
[*]**[   12.289178] bnx2x 0000:03:00.1: part number 394D4342-31373735-31314131-473331**
[*]**[   12.290049] bnx2x 0000:03:00.1: Loading bnx2x-e1h-5.2.13.0.fw**
[*]**[   12.292060] bnx2x 0000:03:00.1: eth5: Broadcom NetXtreme II BCM57711 XGb (A0) PCI-E x8 5GHz (Gen2) found at mem dd000000, IRQ 45, node addr 00:10:18:ae:c4:ba**
[*]**[   12.624117] bnx2x 0000:03:00.1: irq 113 for MSI/MSI-X**
[*]**[   12.624122] bnx2x 0000:03:00.1: irq 114 for MSI/MSI-X**
[*]**[   12.624127] bnx2x 0000:03:00.1: irq 115 for MSI/MSI-X**
[*]**[   12.624132] bnx2x 0000:03:00.1: irq 116 for MSI/MSI-X**
[*]**[   12.624137] bnx2x 0000:03:00.1: irq 117 for MSI/MSI-X**
[*]**[   12.624142] bnx2x 0000:03:00.1: irq 118 for MSI/MSI-X**
[*]**[   12.624146] bnx2x 0000:03:00.1: irq 119 for MSI/MSI-X**
[*]**[   12.624151] bnx2x 0000:03:00.1: irq 120 for MSI/MSI-X**
[*]**[   12.624156] bnx2x 0000:03:00.1: irq 121 for MSI/MSI-X**
[*]**[   12.624161] bnx2x 0000:03:00.1: irq 122 for MSI/MSI-X**
[*]**[   12.624166] bnx2x 0000:03:00.1: irq 123 for MSI/MSI-X**
[*]**[   12.624171] bnx2x 0000:03:00.1: irq 124 for MSI/MSI-X**
[*]**[   12.624176] bnx2x 0000:03:00.1: irq 125 for MSI/MSI-X**
[*]**[   12.624181] bnx2x 0000:03:00.1: irq 126 for MSI/MSI-X**
[*]**[   12.624185] bnx2x 0000:03:00.1: irq 127 for MSI/MSI-X**
[*]**[   12.624191] bnx2x 0000:03:00.1: irq 128 for MSI/MSI-X**
[*]**[   12.624195] bnx2x 0000:03:00.1: irq 129 for MSI/MSI-X**
[*]**[   12.625739] bnx2x 0000:03:00.1: eth4: using MSI-X  IRQs: sp 113  fp[0] 115 ... fp[14] 129**
[*]**[   13.690226] bnx2x 0000:03:00.0: irq 130 for MSI/MSI-X**
[*]**[   13.690232] bnx2x 0000:03:00.0: irq 131 for MSI/MSI-X**
[*]**[   13.690239] bnx2x 0000:03:00.0: irq 132 for MSI/MSI-X**
[*]**[   13.690245] bnx2x 0000:03:00.0: irq 133 for MSI/MSI-X**
[*]**[   13.690252] bnx2x 0000:03:00.0: irq 134 for MSI/MSI-X**
[*]**[   13.690258] bnx2x 0000:03:00.0: irq 135 for MSI/MSI-X**
[*]**[   13.690265] bnx2x 0000:03:00.0: irq 136 for MSI/MSI-X**
[*]**[   13.690271] bnx2x 0000:03:00.0: irq 137 for MSI/MSI-X**
[*]**[   13.690277] bnx2x 0000:03:00.0: irq 138 for MSI/MSI-X**
[*]**[   13.690284] bnx2x 0000:03:00.0: irq 139 for MSI/MSI-X**
[*]**[   13.690290] bnx2x 0000:03:00.0: irq 140 for MSI/MSI-X**
[*]**[   13.690297] bnx2x 0000:03:00.0: irq 141 for MSI/MSI-X**
[*]**[   13.690303] bnx2x 0000:03:00.0: irq 142 for MSI/MSI-X**
[*]**[   13.690309] bnx2x 0000:03:00.0: irq 143 for MSI/MSI-X**
[*]**[   13.690315] bnx2x 0000:03:00.0: irq 144 for MSI/MSI-X**
[*]**[   13.690322] bnx2x 0000:03:00.0: irq 145 for MSI/MSI-X**
[*]**[   13.690328] bnx2x 0000:03:00.0: irq 146 for MSI/MSI-X**
[*]**[   13.692051] bnx2x 0000:03:00.0: eth5: using MSI-X  IRQs: sp 130  fp[0] 132 ... fp[14] 146**
[/LIST]
and

[LIST]
[*]**dmesg | grep eth4**
[*]**[   12.288186] bnx2x 0000:03:00.0: eth4: Broadcom NetXtreme II BCM57711 XGb (A0) PCI-E x8 5GHz (Gen2) found at mem dc000000, IRQ 38, node addr 00:10:18:ae:c4:b8**
[*]**[   12.381362] udev[503]: renamed network interface eth4 to eth4-eth5**
[*]**[   12.460881] udev[506]: renamed network interface eth5 to eth4**
[*]**[   12.541239] udev[503]: renamed network interface eth4-eth5 to eth5**
[*]**[   12.625739] bnx2x 0000:03:00.1: eth4: using MSI-X  IRQs: sp 113  fp[0] 115 ... fp[14] 129**
[*]**[   13.690011] ADDRCONF(NETDEV_UP): eth4: link is not ready**
[/LIST]
Have anyone ever been able to use this on Ubuntu ?

Thank !

---

### Post by rubylaser on 2011-09-27
Have you tried to setup the Linux driver from [Broadcom's site]("http://www.broadcom.com/support/license.php?file=NXII_10/linux-6.2.23.zip")?

```
sudo -i
apt-get install build-essential
wget http://www.broadcom.com/support/license.php?file=NXII_10/linux-6.2.23.zip
cd Server/Linux/Driver
tar xzvf netxtreme2-6.2.23.tar.gz
cd netxtreme2-6.2.23/bnx2x-1.62.15
rmmod bnx2
rmmod bnx2x
make
make install
insmod bnx2x.ko

```

This isn't tested as I don't have an opportunity to try this out right now, but the Install directions are in the zip file. Good luck :)

---

### Post by rsh2000 on 2011-09-28
Thanks [rubylaser]("http://ubuntuforums.org/member.php?u=1115132")

The bnx2x driver version vas 1.62.01 and i updated that to 1.62.15 as you suggested.

This solved the problem and the NIC is now working fine

---

### Post by rubylaser on 2011-09-28
Glad that solved it for you :)

---

