---
title: "No USB function (except storage devices)"
date: 2013-03-11
forum: Ubuntu Studio
---

### Post by conjunctivitis on 2013-03-11
Hi all,

just installed ubuntu studio 12.04.2.  Everything seems to work fine so far except USB, which works only for external drives and pen drives.

I have tried two external USB mice (logitech notebook external mouse plus and trus predator gamer mouse) and two USB audio interfaces (tascam us-800 and lexicon omega).  In all cases, the external storage mounts and opens a Nautilus window when inserted, but plugging a mouse or an audio interface causes no visible activitiy whatsoever, and the audio interfaces indicate no usb connectivity as well.

dmesg and lsusb reveal this as well--when plugging the hard drives you can see activity, but the mouses (mice?) or interfaces don't appear in either dmesg or lsusb.  these are optical mice and the laser doesn't light either upon plugging as it normally does.  it simply flashes once on plugging or unplugging.

i have tried all three usb ports.

I have used all this hardware on this computer with AVLinux and Ubuntu 12.04 and it works fine, but with Ubuntu Studio (which seems great in all other respects), it's totally failed.  Please help!

Thanks

Dan

P.S. The computer is a Dell Inspiron M5030.  Here's lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Dell Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)

---

### Post by jejeman on 2013-03-11
Plugin all problematic devices and give us
```
lsusb
```

---

### Post by conjunctivitis on 2013-03-11
here's lsusb with nothing plugged in:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c45:6321 Microdia 

I get the exact same output after plugging in both mice and sound cards.  Thanks!

---

### Post by conjunctivitis on 2013-03-11
forgot to mention, my usb printer works as well (with the samsung proprietary driver).

---

### Post by jejeman on 2013-03-11
If no devices are shown, then that is real problem. Regardles if device will work (driver wise) it should be listed.
After plugin the problematic devices give us
```
dmesg | grep usb
```

I've read yor first post again, and see that you have already look in this ouputs. 
You said that on Ubuntu 12.04 it works, Studio is not different thatn plain Ubuntu. Only the kernel differs. Maybe you can try with generic kernel. Does it work on live system? Maybe the install went bad.

---

### Post by conjunctivitis on 2013-03-11
here it is:
[    0.210766] usbcore: registered new interface driver usbfs
[    0.210766] usbcore: registered new interface driver hub
[    0.210849] usbcore: registered new device driver usb
[    0.800409] usbcore: registered new interface driver libusual
[    0.937140] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.072981] usbcore: registered new interface driver usb-storage
[    1.173085] usb 2-2: new high-speed USB device number 3 using ehci_hcd
[    1.315616] scsi4 : usb-storage 2-1:1.0
[    1.315712] usbcore: registered new interface driver ums-realtek
[    1.362652] usb 2-1: USB disconnect, device number 2
[   14.462345] input: Laptop_Integrated_Webcam_0.3M as /devices/pci0000:00/0000:00:16.2/usb2/2-2/2-2:1.0/input/input6
[   14.462677] usbcore: registered new interface driver uvcvideo
[   15.138738] [<c10c2020>] irq_default_primary_handler threaded [<c141b540>] usb_hcd_irq
[   15.138744] [<c10c2020>] irq_default_primary_handler threaded [<c141b540>] usb_hcd_irq
[   15.138749] [<c10c2020>] irq_default_primary_handler threaded [<c141b540>] usb_hcd_irq

---

### Post by conjunctivitis on 2013-03-11
this might be interesting:

i found this looking through dmesg:
[   15.549983] irq 18: nobody cared (try booting with the "irqpoll" option)
[   15.549994] Pid: 56, comm: irq/18-ohci_hcd Not tainted 3.2.0-38-lowlatency-pae #40-Ubuntu
[   15.549997] Call Trace:
[   15.550016]  [<c159ef5c>] ? printk+0x2d/0x2f
[   15.550021]  [<c10c3da9>] __report_bad_irq+0x29/0xd0
[   15.550025]  [<c10c4004>] note_interrupt+0x104/0x150
[   15.550028]  [<c10c2a28>] ? irq_forced_thread_fn+0x38/0x50
[   15.550031]  [<c10c2987>] irq_thread+0x1b7/0x1e0
[   15.550034]  [<c10c29f0>] ? irq_thread_fn+0x40/0x40
[   15.550037]  [<c10c27d0>] ? irq_finalize_oneshot+0x20/0x20
[   15.550041]  [<c107bebd>] kthread+0x6d/0x80
[   15.550044]  [<c107be50>] ? kthread_worker_fn+0x160/0x160
[   15.550047]  [<c15bc1fe>] kernel_thread_helper+0x6/0x10
[   15.550049] handlers:
[   15.550052] [<c10c2020>] irq_default_primary_handler threaded [<c141b540>] usb_hcd_irq
[   15.550058] [<c10c2020>] irq_default_primary_handler threaded [<c141b540>] usb_hcd_irq
[   15.550062] [<c10c2020>] irq_default_primary_handler threaded [<c141b540>] usb_hcd_irq
[   15.550066] Disabling IRQ #18

lspci -v shows me the usb controller is on irq 18 and/or 17 with numerous entries.  i don't know if this is normal.  here:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32
	Capabilities: <access denied>

00:01.0 PCI bridge: Dell Device 9602 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ff300000-ff4fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: ff600000-ff6fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff500000-ff5fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 42
	I/O ports at f090 [size=8]
	I/O ports at f080 [size=4]
	I/O ports at f070 [size=8]
	I/O ports at f060 [size=4]
	I/O ports at f050 [size=16]
	Memory at ff709000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

[B]00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at ff708000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at ff707000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at ff706000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd[/B]

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Dell Device 0487
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at ff700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0c, subordinate=13, sec-latency=64

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at ff705000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

[B]00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Dell Device 0487
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at ff704000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
[/B]
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0487
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at e000 [size=256]
	Memory at ff400000 (32-bit, non-prefetchable) [size=64K]
	Memory at ff300000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Wistron NeWeb Corp. DNXA-95 802.11bgn Wireless Half-size Mini PCIe Card
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ff600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

05:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
	Subsystem: Dell Device 0487
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at ff500000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

---

### Post by conjunctivitis on 2013-03-11
checked with a generic kernel: 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 athlon i386 GNU/Linux

usb mouse works with it, but with horrible lag and low sample rate.

i tried regular ubuntu 12.04 on a live usb stick.  the mouse works perfectly as it should.  the kernel here is newer: Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP

---

### Post by conjunctivitis on 2013-03-11
Linux dan-Inspiron-M5030 3.5.0-25-generic #39~precise1-Ubuntu SMP Tue Feb 26 00:11:13 UTC 2013 i686 athlon i386 GNU/Linux

With this kernel my mouse works fine under Ubuntu Studio.  I obviously lose the advantage of the low-latency kernel though...

Should I file a bug report?  Any ideas about how to get the other kernel working?

Thanks
Dan

---

