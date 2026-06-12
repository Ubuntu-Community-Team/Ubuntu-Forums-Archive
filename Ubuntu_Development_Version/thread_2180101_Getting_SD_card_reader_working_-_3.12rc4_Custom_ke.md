---
title: "Getting SD card reader working - 3.12rc4 Custom kernel"
date: 2013-10-11
forum: Ubuntu Development Version
---

### Post by rimez on 2013-10-11
Hi Everyone,

So far I've managed to get almost everything on my laptop working better (much better with regards to wifi) by compiling the 3.12rc4 kernel. However, I have one last stumbling block before my laptop is almost perfect (well... my Nvidia GT730m will probably never work) - I cannot get the 2-in-1 card-reader (SD / MMC) to work on my ideapad u430p.

Using the precompiled version in the Ubuntu Mainline PPA It'll work. When I compile though, it seems "make localmodconfig" isn't able to detect the reader. Last night I went and manually compiled support for all MMC modules and this ended in the SD card being readable but the usb mouse (for whatever reason) stopped working. 

Does anyone have any idea how I can properly detect and compile the support into the kernel?  

I've done loads of searching but all I keep getting in the search results are 'booting from SD' or 'installing linux on SD' threads. I did find some highly technical results but it was way over my head :(

Any help sorting this would be most appreciated. Right now I'm back to using the precompiled mainline version.

EDIT: 

Here's the output of lspci -v: 
```
:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
    Subsystem: Lenovo Device 3978
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3800
    Flags: bus master, fast devsel, latency 0, IRQ 63
    Memory at b5000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
    Subsystem: Lenovo Device 3978
    Flags: bus master, fast devsel, latency 0, IRQ 66
    Memory at b5610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 3978
    Flags: bus master, medium devsel, latency 0, IRQ 60
    Memory at b5600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
    Subsystem: Lenovo Device 3978
    Flags: bus master, fast devsel, latency 0, IRQ 64
    Memory at b5618000 (64-bit, non-prefetchable) [size=32]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
    Subsystem: Lenovo Device 3978
    Flags: bus master, fast devsel, latency 0, IRQ 67
    Memory at b5614000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: b5500000-b55fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3978
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: b5400000-b54fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3978
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=08, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: b4000000-b4ffffff
    Prefetchable memory behind bridge: 00000000b2000000-00000000b2ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3978
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b3000000-b3ffffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000b1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Device 3978
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3978
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b561c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
    Subsystem: Lenovo Device 3978
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3978
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 61
    I/O ports at 6088 [size=8]
    I/O ports at 6094 [size=4]
    I/O ports at 6080 [size=8]
    I/O ports at 6090 [size=4]
    I/O ports at 6060 [size=32]
    Memory at b561b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
    Subsystem: Lenovo Device 3978
    Flags: medium devsel, IRQ 11
    Memory at b5619000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 6040 [size=32]

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
    Subsystem: Lenovo Device 3801
    Flags: bus master, fast devsel, latency 0, IRQ 62
    I/O ports at 5000 [size=256]
    Memory at b5504000 (64-bit, non-prefetchable) [size=4K]
    Memory at b5500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] #1e
    Kernel driver in use: r8169

02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
    Subsystem: Intel Corporation Wireless-N 7260
    Flags: bus master, fast devsel, latency 0, IRQ 65
    Memory at b5400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 0c-8b-fd-ff-ff-31-5f-4c
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [154] Vendor Specific Information: ID=cafe Rev=1 Len=014 <?>
    Kernel driver in use: iwlwifi

09:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 730M] (rev a1)
    Subsystem: Lenovo Device 3800
    Flags: fast devsel, IRQ 16
    Memory at b3000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
```

---

### Post by rimez on 2013-10-13
Hi All,

I finally thought to compare the LSPCI from the 2 kernels and what I found on the standard kernel for Ubuntu 13.10 (k3.11) was that this module is loaded (unlike the 3.12 customer kernel I compiled): 
```

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5227 (rev 01)
    Subsystem: Lenovo Device 3801
    Physical Slot: 3
    Flags: bus master, fast devsel, latency 0, IRQ 68
    Memory at b4000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00
    Capabilities: [150] Latency Tolerance Reporting
    Capabilities: [158] #1e
    Kernel driver in use: rtsx_pci
```

So I now think I have the driver to be used, but where can I find it in the kernel config? Could someone point me in the right direction?

Edit: 

I think I found it :) 
[IMG]http://i.imm.io/1igwc.png[/IMG]

Compiling now, let's hope it works :)

UPDATE: It didn't work :(



**Solution & Final Update: **OK.. there was another step involved. Since I knew the driver, I was able to find[ somone who had the same issue]("http://www.skuldougery.com/?cat=7"). 
So the steps are (for this sd card reader): 
In the kernel config enable (in devices)- 
 - Multifunction Device Drivers> Realtek PCI-E Card reader
 - MMC/SD/SDIO Card Support> MMC Block Driver
 - MMC/SD/SDIO Card Support> REALTEK PCI-E SD/MMC Card interface driver

the lesson learned for me, is that when you have 2 kernels where one works and the other doesn't, simply compare the output of lspci - this gave me the driver name.

---

### Post by fooman on 2013-10-14
i just compiled my first kernel last night using paul_from_london's method and all seemed to work fine.  i then came across this thread and figured i should try a flash card in my reader....it would not mount.  same went for my front usb ports...none of them worked either.

not being the brightest user when it comes to configuring things,  i took a different approach:

first i booted up to an older, mainline kernel,  uninstalled the custom kernel i had compiled...then re-compiled it, *but this time* i first mounted a flash card in my reader and a flash drive in one of my front usb2 ports,  as well as mounting a drive in one of my front usb3 ports (just for good measure,  i also loaded up a dvd, made sure that was mounted and turned on my wireless printer upstairs to make sure that was recognized *before* compiling).  proceeded to compile the custom kernel, rebooted and everything (as far as i can tell) is now working!!!  

probably not the proper way to go about it...but hey IT WORKED!!

thanks rimez for pointing this out (i would have never known they were not working until i went to use them), and of course props to paul for his guide!!

---

### Post by rimez on 2013-10-14
@fooman - no problem. Glad I could be of some (indirect) help. 

The funny thing is I tried the technique you described but it still didn't work.

P.S. This kernel rocks!:guitar:

---

