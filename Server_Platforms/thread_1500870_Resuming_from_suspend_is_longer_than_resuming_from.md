---
title: "Resuming from suspend is longer than resuming from hibernation"
date: 2010-06-03
forum: Server Platforms
---

### Post by Osmoroid on 2010-06-03
Hi,
I have been trying to find ways to save power on my server. On discovering how to set-up hibernation and suspend on ubuntu server, I have found that suspend is almost useless.

It takes around 35 seconds to resume from suspend.
23 seconds to boot from hibernation.
Testing suspend in windows works fine. Less than 5 seconds.

Have been using pm-suspend, but have tried various other methods. Such as echo status in power status proc file, using tuxonice suspend script, s2ram.

On diagnosing network, I have found that pinging the server before the 35 seconds has past is successful. But attempting to use any of the installed services such as samba, mysql, web etc fails. No connection/reply.

**lspci -vnnn output**
```
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 02)
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 32
        Memory at <ignored> (32-bit, non-prefetchable)
        Capabilities: [a0] AGP version 3.1
        Capabilities: [d0] HyperTransport: Slave or Primary Interface
        Capabilities: [f0] HyperTransport: Interrupt Discovery and Configuration
        Kernel driver in use: agpgart-amd64
        Kernel modules: sis-agp

00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e8000000-e80fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff
        Kernel modules: shpchp

00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] [1039:0964] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01) (prog-if 80 [Master])
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 128
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 4000 [size=16]
        Kernel driver in use: pata_sis
        Kernel modules: ata_generic, pata_acpi, pata_sis, ide-pci-generic, sis5513

00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at e000 [size=256]
        I/O ports at e800 [size=128]
        Capabilities: [48] Power Management version 2
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at e8124000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at e8120000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at e8121000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd
        Kernel modules: ohci-hcd

00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
        Flags: bus master, medium devsel, latency 32, IRQ 23
        Memory at e8122000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at e400 [size=256]
        Memory at e8123000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: sis900
        Kernel modules: sis900

00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] [1039:0180] (rev 01) (prog-if 85 [Master SecO PriO])
        Subsystem: Foxconn International, Inc. Device [105b:0c54]
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        I/O ports at e900 [size=8]
        I/O ports at ea00 [size=4]
        I/O ports at eb00 [size=8]
        I/O ports at ec00 [size=4]
        I/O ports at ed00 [size=16]
        I/O ports at <unassigned>
        Capabilities: [58] Power Management version 2
        Kernel driver in use: sata_sis
        Kernel modules: ata_generic, pata_acpi, sata_sis, ide-pci-generic

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
        Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
        Flags: fast devsel
        Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
        Flags: fast devsel
        Kernel driver in use: k8temp
        Kernel modules: k8temp

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330] (prog-if 00 [VGA controller])
        Subsystem: Silicon Integrated Systems [SiS] [M]661xX/[M]741[GX]/[M]760 PCI/AGP VGA Adapter [1039:6330]
        Flags: 66MHz, medium devsel, IRQ 5
        BIST result: 00
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=128]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] AGP version 3.0
        Kernel modules: sisfb

```[B]
pm-suspend.log[/B]
```
Initial commandline parameters:
Thu Jun  3 20:41:40 BST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux server 2.6.33 #1 S                                             MP PREEMPT Thu May 20 22:59:50 BST 2010 x86_64 AMD Sempron(tm) Processor 2600+ A                                             uthenticAMD GNU/Linux
Module                  Size  Used by
ipv6                  280670  23
snd_seq_dummy           1439  0
snd_seq_oss            28928  0
snd_seq_midi_event      5412  1 snd_seq_oss
snd_seq                50530  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          5233  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            39096  0
snd_mixer_oss          16956  1 snd_pcm_oss
ppdev                   6006  0
snd_intel8x0           26831  0
fan                     3314  0
snd_ac97_codec        110707  1 snd_intel8x0
ac97_bus                1150  1 snd_ac97_codec
snd_pcm                70924  3 snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_timer              19684  2 snd_seq,snd_pcm
parport_pc             31351  1
ohci_hcd               21613  0
snd                    57209  9 snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,s                                             nd_mixer_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               6153  1 snd
sr_mod                 14810  0
snd_page_alloc          7129  2 snd_intel8x0,snd_pcm
processor              29630  0
button                  4778  0
thermal                12154  0
lp                      9024  0
ehci_hcd               35087  0
cdrom                  35745  1 sr_mod
shpchp                 31108  0
usbcore               144288  3 ohci_hcd,ehci_hcd
sis900                 19322  0
mii                     3802  1 sis900
parport                29639  3 ppdev,parport_pc,lp
edac_core              33927  0
pci_hotplug            26775  1 shpchp
edac_mce_amd            6809  0
pcspkr                  1795  0
k8temp                  3379  0
evdev                   8711  4
sg                     25200  0
rtc_cmos                8886  0
rtc_core               14471  1 rtc_cmos
rtc_lib                 1874  1 rtc_core
ext3                  126087  3
jbd                    47131  1 ext3
mbcache                 5754  1 ext3
sd_mod                 27507  5
sata_sis                4130  4
pata_sis               10496  1 sata_sis
libata                154235  2 sata_sis,pata_sis
scsi_mod               94276  4 sr_mod,sg,sd_mod,libata
lzo                     1363  0
lzo_compress            1990  1 lzo
             total       used       free     shared    buffers     cached
Mem:        473988     153352     320636          0       5872      66008
-/+ buffers/cache:      81472     392516
Swap:       497972          0     497972
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01grub suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/11netcfg suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/etc/pm/sleep.d/80tuxonice-userui suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
success.
Thu Jun  3 20:41:40 BST 2010: performing suspend
Thu Jun  3 20:42:22 BST 2010: Awake.
Thu Jun  3 20:42:22 BST 2010: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume suspend:Function not supported
Function not supported
success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/etc/pm/sleep.d/80tuxonice-userui resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/11netcfg resume suspend:success.
/usr/lib/pm-utils/sleep.d/01grub resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
Thu Jun  3 20:42:23 BST 2010: Finished.

```**Computer Specifications**

AMD Sempron 2400+ (Running 64 bit)
512MB Ram
500GB Sata drive - sis sata controller
Sis900 100MB LAN Network Card
Onboard SiS 760 Graphics

---------------------------------------------
Any ideas on why such a large delay on resuming from suspend??

---

