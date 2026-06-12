---
title: "Broken something...not sure"
date: 2016-12-02
forum: Ubuntu/Debian BASED
---

### Post by -Oz- on 2016-12-02
Hi guys,

I recently installed Backbox 4.6 and after updating it through "Software Updater" my system seems to be broken. Title bar for any software that i run is missing, as you can see in the following screenshot for Opera browser. I tried other software too and its missing in them too.

[IMG]http://i66.tinypic.com/szhhqu.png[/img]

Desktop icons are missing, right click on desktop doesnt do anything. Also i cannot type in the start menu, i can click icons and menu buttons but doesnt let me type in the run dialog box.

I tried booting up with the previos 4.2 kernel, but no luck. Please help. 


Info about my system

```
H/W path * * * *Device * * *Class * * * * *Description
======================================================
 * * * * * * * * * * * * * *system * * * * 406333M ()
/0 * * * * * * * * * * * * *bus * * * * * *406333M
/0/0 * * * * * * * * * * * *memory * * * * 128KiB BIOS
/0/6 * * * * * * * * * * * *processor * * *Intel(R) Core(TM)2 Duo CPU * * T9400 *@ 2.53GHz
/0/6/a * * * * * * * * * * *memory * * * * 64KiB L1 cache
/0/6/c * * * * * * * * * * *memory * * * * 6MiB L2 cache
/0/b * * * * * * * * * * * *memory * * * * 64KiB L1 cache
/0/2b * * * * * * * * * * * memory * * * * 4GiB System Memory
/0/2b/0 * * * * * * * * * * memory * * * * 2GiB SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
/0/2b/1 * * * * * * * * * * memory * * * * 2GiB SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
/0/100 * * * * * * * * * * *bridge * * * * Mobile 4 Series Chipset Memory Controller Hub
/0/100/2 * * * * * * * * * *display * * * *Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1 * * * * * * * * *display * * * *Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/3 * * * * * * * * * *communication *Mobile 4 Series Chipset MEI Controller
/0/100/3.3 * * * * * * * * *communication *Mobile 4 Series Chipset AMT SOL Redirection
/0/100/19 * * * eth0 * * * *network * * * *82567LM Gigabit Network Connection
/0/100/1a * * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1 * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2 * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7 * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b * * * * * * * * * multimedia * * 82801I (ICH9 Family) HD Audio Controller
/0/100/1c * * * * * * * * * bridge * * * * 82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1 * * * * * * * * bridge * * * * 82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0 * wlan0 * * * network * * * *PRO/Wireless 5100 AGN [Shiloh] Network Connection
/0/100/1c.3 * * * * * * * * bridge * * * * 82801I (ICH9 Family) PCI Express Port 4
/0/100/1c.4 * * * * * * * * bridge * * * * 82801I (ICH9 Family) PCI Express Port 5
/0/100/1d * * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1 * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2 * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7 * * * * * * * * bus * * * * * *82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e * * * * * * * * * bridge * * * * 82801 Mobile PCI Bridge
/0/100/1e/0 * * * * * * * * bridge * * * * RL5c476 II
/0/100/1e/0.1 * * * * * * * bus * * * * * *R5C832 IEEE 1394 Controller
/0/100/1e/0.2 * * * * * * * generic * * * *R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
/0/100/1e/0.4 * * * * * * * generic * * * *R5C592 Memory Stick Bus Host Adapter
/0/100/1e/0.5 * * * * * * * generic * * * *xD-Picture Card Controller
/0/100/1f * * * * * * * * * bridge * * * * ICH9M-E LPC Interface Controller
/0/100/1f.2 * * * * * * * * storage * * * *82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
/0/100/1f.3 * * * * * * * * bus * * * * * *82801I (ICH9 Family) SMBus Controller
/0/1 * * * * * *scsi0 * * * storage * * * *
/0/1/0.0.0 * * */dev/sda * *disk * * * * * 160GB FUJITSU MHZ2160B
/0/1/0.0.0/1 * */dev/sda1 * volume * * * * 976MiB Extended partition
/0/1/0.0.0/1/5 */dev/sda5 * volume * * * * 976MiB Linux filesystem partition
/0/1/0.0.0/2 * */dev/sda2 * volume * * * * 3906MiB Linux swap volume
/0/1/0.0.0/3 * */dev/sda3 * volume * * * * 41GiB HPFS/NTFS partition
/0/1/0.0.0/4 * */dev/sda4 * volume * * * * 102GiB Linux filesystem partition
/0/2 * * * * * *scsi1 * * * storage * * * *
/0/2/0.0.0 * * */dev/cdrom *disk * * * * * DVD-RAM UJ862AC
/1 * * * * * * * * * * * * *power * * * * *42T4619

```

---

### Post by TheFu on 2016-12-02
Don't know **anything** about that distro, but the common thing to do it look at the log files. See what they show.  Warnings and errors should be in there.

---

### Post by vasa1 on 2016-12-02
> **TheFu said:**
> Don't know **anything** about that distro, ...
According to DistroWatch, it's a pen-testing Ubuntu-based distro. Xfce seems to be the default DE.

OP, you should be able to find support at [http://groups.google.com/group/backbox-linux](http://groups.google.com/group/backbox-linux) or [http://forum.backbox.org/](http://forum.backbox.org/)

---

### Post by -Oz- on 2016-12-02
Well its based on Ubuntu 14.04 so what would you have suggested if this problem arised in ubuntu 14.04

---

### Post by TheFu on 2016-12-02
Check to see if one of the keys on your keyboard is stuck.  alt/ctl/shift ... super.  AND check the logs.

This won't help you, but ... on a chromebook here, I can't have any USB HID or storage devices connected when booting or the touchpad doesn't work. A USB-2-GigE network adapter is fine. Think the storage gets found before the touchpad in USB order and that confuses ubuntu server.  But I haven't done any research. It isn't THAT much of an issue. It isn't an issue when booting off a live-boot media (flash/usb), just when booting the installed-to-SSD version.  I probably just need to find the script that locates the touchpad and tweak it a bit to be more generic on device order.

---

