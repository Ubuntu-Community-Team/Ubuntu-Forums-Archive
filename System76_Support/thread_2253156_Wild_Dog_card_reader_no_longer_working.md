---
title: "Wild Dog card reader no longer working"
date: 2014-11-17
forum: System76 Support
---

### Post by ayami2 on 2014-11-17
I have a Wild Dof Performance desktop with the built-in SD/Flash/Memory stick reader, but that component has mostly stopped working. All of a sudden (not after an OS version upgrade) it will not longer mount or read SD cards. However, the USB port on the reader does still work. I don't have cards to test the other slots.

lspci -v lists it as:  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI

Both lights still work (red power light always on, green activity light comes on even when an SD card is inserted, though the card isn't read). The disks utility shows the drive as empty even when a card is inserted.

I followed the instructions at [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876) but there was no change.

Full output of lspci for the device is:

```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
        Subsystem: ASUSTeK Computer Inc. Device 8554
        Flags: bus master, fast devsel, latency 0, IRQ 43
        I/O ports at d000 [size=256]
        Memory at f7100000 (64-bit, non-prefetchable) [size=4K]
        Memory at f2100000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
        Capabilities: [170] Latency Tolerance Reporting
        Kernel driver in use: r8169


```

---

