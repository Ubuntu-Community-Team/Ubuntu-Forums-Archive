---
title: "XEN: USB passthrough using pciback is blocked by xhci_hcd"
date: 2014-10-08
forum: Virtualisation
---

### Post by maldo_dawn on 2014-10-08
Hi all,

I am trying to passthrough a USB PCI card to a xen domU.
It works nice when I unbind the xhci_hcd driver from the device.
However, when trying to use pciback I run into trouble as the xhci_hcd driver is compiled in the kernel and loaded before pciback (which is loaded as module).

Is it possible to avoid recompiling the kernel?
 Can I tell the xhci_hcd driver not to sit down on the devices I want to pciback?

/etc/default/grub
GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT="xen-pciback.hide=(01:00.0)(01:00.1)(02:00.0)(02:00.1)(08:00.0)(09:00.0)"

sudo lspci -k
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition]
    Subsystem: Gigabyte Technology Co., Ltd Device 2554
    Kernel driver in use: pciback
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: Gigabyte Technology Co., Ltd Device aab0
    Kernel driver in use: pciback
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition]
    Subsystem: Gigabyte Technology Co., Ltd Device 2554
    Kernel driver in use: pciback
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: Gigabyte Technology Co., Ltd Device aab0
    Kernel driver in use: pciback
08:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
    Kernel driver in use: xhci_hcd
09:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
    Kernel driver in use: xhci_hcd



Thanks

---

