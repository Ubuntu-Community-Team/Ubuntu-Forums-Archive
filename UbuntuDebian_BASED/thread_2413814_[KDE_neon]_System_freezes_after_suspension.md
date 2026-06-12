---
title: "[KDE neon] System freezes after suspension"
date: 2019-03-02
forum: Ubuntu/Debian BASED
---

### Post by tomekj on 2019-03-02
I have a problem with KDE neon 5.12 (based on Ubuntu, KDE version: 5.15.2). After I suspended system, I am not able to wake it up. I need to switch to tty2 and go back to tty1 (Ctrl + Alt + F2 and Ctrl + Alt + F1) after each wake up in order to unfreeze it. Before unfreezing, I am able to use my mouse, but I am not able to click on anything. I found similar issue on Manjaro forum, but it didn't fix it.
Problem occurs only on X.org - when I switch to Wayland it doesn`t happen. Unfortunately, I need to use X.org.
[https://forum.manjaro.org/t/gui-freeze-after-each-suspend/69452](https://forum.manjaro.org/t/gui-freeze-after-each-suspend/69452)
lshw -short:
```

H/W path           Device     Class          Description
========================================================
                              system         LIFEBOOK P701
/0                            bus            FJNB229
/0/0                          processor      Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
/0/0/1                        memory         64KiB L1 cache
/0/0/2                        memory         256KiB L2 cache
/0/0/3                        memory         3MiB L3 cache
/0/4                          memory         8GiB System Memory
/0/4/0                        memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/4/1                        memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/b                          memory         128KiB BIOS
/0/100                        bridge         2nd Generation Core Processor Family DRAM Controller
/0/100/2                      display        2nd Generation Core Processor Family Integrated Graphics Controller
/0/100/16                     communication  6 Series/C200 Series Chipset Family MEI Controller #1
/0/100/19          enp0s25    network        82579V Gigabit Network Connection
/0/100/1a                     bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1a/1        usb1       bus            EHCI Host Controller
/0/100/1a/1/1                 bus            Integrated Rate Matching Hub
/0/100/1a/1/1/4               input          USB gaming mouse
/0/100/1b                     multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller
/0/100/1c                     bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1
/0/100/1c.2                   bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 3
/0/100/1c.2/0      wlp10s0    network        AR9287 Wireless Network Adapter (PCI-Express)
/0/100/1c.7                   bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 8
/0/100/1c.7/0                 generic        RTS5209 PCI Express Card Reader
/0/100/1c.7/0.1               generic        RTS5209 PCI Express Card Reader
/0/100/1d                     bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1d/1        usb2       bus            EHCI Host Controller
/0/100/1d/1/1                 bus            Integrated Rate Matching Hub
/0/100/1d/1/1/1               multimedia     FJ Camera
/0/100/1d/1/1/2               bus            Oz776 1.1 Hub
/0/100/1d/1/1/2/2             generic        O2Micro CCID SC Reader
/0/100/1d/1/1/4               generic        BCM20702A0
/0/100/1f                     bridge         HM65 Express Chipset LPC Controller
/0/100/1f.2                   storage        6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller
/0/100/1f.3                   bus            6 Series/C200 Series Chipset Family SMBus Controller
/0/1               scsi0      storage        
/0/1/0.0.0         /dev/sda   disk           120GB GOODRAM
/0/1/0.0.0/1       /dev/sda1  volume         111GiB EXT4 volume
/0/1/0.0.0/2       /dev/sda2  volume         571MiB Extended partition
/0/1/0.0.0/2/5     /dev/sda5  volume         571MiB Windows FAT volume
/1                            power          CP483691-01

```
Kernel information:
```
Linux LIFEBOOK-P701 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Frogs Hair on 2019-03-02
Moved to *Ubuntu/Debian Based*.

---

