---
title: "Broadcom NetExtreme BCM57711 10gb"
date: 2011-08-02
forum: Server Platforms
---

### Post by synrat on 2011-08-02
Does anyone have this working ? bnx2 module doesn't seem to be attaching to it.

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM57711 10-Gigabit PCIe
02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM57711 10-Gigabit PCIe

bnx2x                 359394  0 
libcrc32c              12644  2 btrfs,bnx2x
bnx2                   85989  0 
mdio                   13770  1 bnx2x

---

### Post by synrat on 2011-08-02
dmesg

[    3.058133] bnx2: Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.0.21 (Dec 23, 2010)
[    3.058365] bnx2 0000:04:00.0: PCI INT A -> Link[LN48] -> GSI 48 (level, high) -> IRQ 48
[    3.058370] bnx2 0000:04:00.0: setting latency timer to 64
[    3.066832] bnx2 0000:04:00.0: eth0: Broadcom NetXtreme II BCM5716 1000Base-T (C0) PCI Express found at mem e8000000, IRQ 48, node addr 60:eb:69:82:54:99
[    3.066834] Broadcom NetXtreme II 5771x 10Gigabit Ethernet Driver bnx2x 1.62.00-6 (2011/01/30)
[    3.066991] bnx2 0000:04:00.1: PCI INT B -> Link[LN49] -> GSI 49 (level, high) -> IRQ 49
[    3.066996] bnx2 0000:04:00.1: setting latency timer to 64
[    3.067404] bnx2x 0000:02:00.0: PCI INT A -> Link[LN28] -> GSI 28 (level, high) -> IRQ 28
[    3.067408] bnx2x 0000:02:00.0: setting latency timer to 64
[    3.068044] bnx2x 0000:02:00.0: part number 394D4342-31373735-31314131-473331
[    3.068706] bnx2x 0000:02:00.0: irq 78 for MSI/MSI-X
[    3.068712] bnx2x 0000:02:00.0: irq 79 for MSI/MSI-X
[    3.068718] bnx2x 0000:02:00.0: irq 80 for MSI/MSI-X
[    3.068724] bnx2x 0000:02:00.0: irq 81 for MSI/MSI-X
[    3.068730] bnx2x 0000:02:00.0: irq 82 for MSI/MSI-X
[    3.068736] bnx2x 0000:02:00.0: irq 83 for MSI/MSI-X
[    3.068743] bnx2x 0000:02:00.0: irq 84 for MSI/MSI-X
[    3.068749] bnx2x 0000:02:00.0: irq 85 for MSI/MSI-X
[    3.068755] bnx2x 0000:02:00.0: irq 86 for MSI/MSI-X
[    3.068761] bnx2x 0000:02:00.0: irq 87 for MSI/MSI-X
[    3.068767] bnx2x 0000:02:00.0: irq 88 for MSI/MSI-X
[    3.068773] bnx2x 0000:02:00.0: irq 89 for MSI/MSI-X
[    3.068779] bnx2x 0000:02:00.0: irq 90 for MSI/MSI-X
[    3.068785] bnx2x 0000:02:00.0: irq 91 for MSI/MSI-X
[    3.069478] bnx2x 0000:02:00.0: eth1: Broadcom NetXtreme II BCM57711 XGb (A0) PCI-E x4 5GHz (Gen2) found at mem ec000000, IRQ 28, node addr 00:10:18:a6:ed:3c
[    3.069641] bnx2x 0000:02:00.1: PCI INT B -> Link[LN29] -> GSI 29 (level, high) -> IRQ 29
[    3.069646] bnx2x 0000:02:00.1: setting latency timer to 64
[    3.070327] bnx2x 0000:02:00.1: part number 394D4342-31373735-31314131-473331
[    3.070971] bnx2x 0000:02:00.1: irq 92 for MSI/MSI-X
[    3.070978] bnx2x 0000:02:00.1: irq 93 for MSI/MSI-X
[    3.070985] bnx2x 0000:02:00.1: irq 94 for MSI/MSI-X
[    3.070991] bnx2x 0000:02:00.1: irq 95 for MSI/MSI-X
[    3.070997] bnx2x 0000:02:00.1: irq 96 for MSI/MSI-X
[    3.071003] bnx2x 0000:02:00.1: irq 97 for MSI/MSI-X
[    3.071009] bnx2x 0000:02:00.1: irq 98 for MSI/MSI-X
[    3.071015] bnx2x 0000:02:00.1: irq 99 for MSI/MSI-X
[    3.071021] bnx2x 0000:02:00.1: irq 100 for MSI/MSI-X
[    3.071027] bnx2x 0000:02:00.1: irq 101 for MSI/MSI-X
[    3.071033] bnx2x 0000:02:00.1: irq 102 for MSI/MSI-X
[    3.071039] bnx2x 0000:02:00.1: irq 103 for MSI/MSI-X
[    3.071045] bnx2x 0000:02:00.1: irq 104 for MSI/MSI-X
[    3.071051] bnx2x 0000:02:00.1: irq 105 for MSI/MSI-X
[    3.071771] bnx2x 0000:02:00.1: eth2: Broadcom NetXtreme II BCM57711 XGb (A0) PCI-E x4 5GHz (Gen2) found at mem ed000000, IRQ 29, node addr 00:10:18:a6:ed:3e
[    3.072477] bnx2 0000:04:00.1: eth3: Broadcom NetXtreme II BCM5716 1000Base-T (C0) PCI Express found at mem ea000000, IRQ 49, node addr 60:eb:69:82:54:9a
[    6.682610] bnx2x 0000:02:00.0: eth0: using MSI-X  IRQs: sp 78  fp[0] 80 ... fp[11] 91
[    7.152217] bnx2 0000:04:00.0: irq 109 for MSI/MSI-X
[    7.152225] bnx2 0000:04:00.0: irq 110 for MSI/MSI-X
[    7.152236] bnx2 0000:04:00.0: irq 111 for MSI/MSI-X
[    7.152243] bnx2 0000:04:00.0: irq 112 for MSI/MSI-X
[    7.152249] bnx2 0000:04:00.0: irq 113 for MSI/MSI-X
[    7.152255] bnx2 0000:04:00.0: irq 114 for MSI/MSI-X
[    7.152266] bnx2 0000:04:00.0: irq 115 for MSI/MSI-X
[    7.152272] bnx2 0000:04:00.0: irq 116 for MSI/MSI-X
[    7.152279] bnx2 0000:04:00.0: irq 117 for MSI/MSI-X
[    7.233802] bnx2 0000:04:00.0: eth2: using MSIX
[   10.006630] bnx2 0000:04:00.0: eth2: NIC Copper Link is Up, 1000 Mbps full duplex

---

### Post by rsh2000 on 2011-09-27
Hello,

I have exactly the same problem with NetXtreme II BCM57711 !
I was wondering if you could solve the problem and use it with ubuntu?

Thanks!

---

