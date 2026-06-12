---
title: "VirtualBox hangs around"
date: 2008-03-20
forum: Virtualisation
---

### Post by tonymoloney on 2008-03-20
I installed VirtualBox, then, due to some problems, deleted it.
Now, whenever I shut my system down, I see a message (leftover from booting) that VitualBox is causing some sort of error.
Sorry, it flashes by too quickly to see the full text and I haven't been able to find it Systems Log Viewer.
It's obviuoslly due to some boot time instruction left over from when I installed VB, but where do I go to find the instruction and remove it?
(Kubuntu Gutsy)

---

### Post by p_quarles on 2008-03-20
Can you post the output of this command?
```
ls /etc/rc0.d/
```

---

### Post by tonymoloney on 2008-03-20
tony@tony-laptop:~$ ls /etc/rc0.d/
K01kdm           K20vboxdrv                          S15wpa-ifupdown
K01timidity      K20yate                             S20sendsigs
K01usplash       K25hwclock.sh                       S30urandom
K16avahi-daemon  K50alsa-utils                       S31umountnfs.sh
K16dhcdbd        K81ld10k1                           S40umountfs
K19hpoj          README                              S60umountroot
K20apport        S01linux-restricted-modules-common  S90halt
tony@tony-laptop:~$

---

### Post by p_quarles on 2008-03-20
Okay, this should do the trick:
```
sudo mv /etc/rc0.d/K20vboxdrv .
```
To disable this script from running on reboot, as well, you'll need to move another file:
```
sudo mv /etc/rc6.d/K20vboxdrv .
```

---

### Post by amd-64 on 2008-03-20
Type 

```
sudo kfind /etc  
```
If kfind is not on your system, install it via 

```
sudo apt-get install kfind
```

search for files/directories starting with vbox* in kfind 

Select all files and delete. You will not see the error again. 

Another safer way is reinstall virtual box and then remove it from synaptic.

---

### Post by tonymoloney on 2008-03-20
Hmmm. The tip from p_quarles had no effect.
Following amd-64's tip gave the following output:

tony@tony-laptop:~$ sudo kfind /etc
[sudo] password for tony:
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: "/var/tmp/kdecache-tony" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-tony" is owned by uid 1000 instead of uid 0.
tony@tony-laptop:~$

Sorry guys - I've just had a phone call and I've got to go out.
I'll follow this up when I return.

---

### Post by erginemr on 2008-03-20
> **p_quarles said:**
> Okay, this should do the trick:
```
sudo mv /etc/rc0.d/K20vboxdrv .
```
To disable this script from running on reboot, as well, you'll need to move another file:
```
sudo mv /etc/rc6.d/K20vboxdrv .
```

In the command above, I don't understand where you are moving the files to? To the home folder of the user?

And I remember from past that "S##daemon_name" runs a background service while "K##daemon_name" already disables it. Or am I wrong?

---

### Post by p_quarles on 2008-03-20
Yes, "S" means initiate, and "K" means kill. Those directories, however, control the shutdown and reboot runlevels, respectively, and the problem is that they are attempting to kill a process that doesn't exist, thus giving an error. I suggested moving them to the user's home folder, but you could move them anywhere, or even simply delete them (they are symlinks anyway). 

As for why those commands didn't work, I am puzzled. 

In any case, the error message is ultimately a minor problem. As the OP said, the message flashes by very quickly, so it's not hanging the system or anything, it's just registering the fact that it's attempting to do something impossible.

---

### Post by erginemr on 2008-03-20
Thank you very much for the information.

Maybe the commands moved them silently. Maybe they didn't, because there was already a K20vboxdrv file in the home folder by the time the OP applied the second command (i.e. rc6.d), as sometimes is the case with symlinks.

So, to leave out any question marks in our mind, I suggest the OP to re-post the contents of both folders:
```
ls /etc/rc0.d/
ls /etc/rc6.d/
```
and also:
```
ls /etc/init.d | grep vbox
```

---

### Post by tonymoloney on 2008-03-20
Here's the re-post:

tony@tony-laptop:~$ ls /etc/rc0.d/
K01kdm           K20yate                             S20sendsigs
K01timidity      K25hwclock.sh                       S30urandom
K01usplash       K50alsa-utils                       S31umountnfs.sh
K16avahi-daemon  K81ld10k1                           S40umountfs
K16dhcdbd        README                              S60umountroot
K19hpoj          S01linux-restricted-modules-common  S90halt
K20apport        S15wpa-ifupdown
tony@tony-laptop:~$

tony@tony-laptop:~$ ls /etc/rc6.d/
K01kdm           K20yate                             S20sendsigs
K01timidity      K25hwclock.sh                       S30urandom
K01usplash       K50alsa-utils                       S31umountnfs.sh
K16avahi-daemon  K81ld10k1                           S40umountfs
K16dhcdbd        README                              S60umountroot
K19hpoj          S01linux-restricted-modules-common  S90reboot
K20apport        S15wpa-ifupdown
tony@tony-laptop:~$

tony@tony-laptop:~$ ls /etc/init.d | grep vbox
vboxdrv
tony@tony-laptop:~$

---

### Post by p_quarles on 2008-03-20
Well, this isn't going so well. :)

Can you post the output of this command?:
```
dmesg
```
Also, please wrap the output inside the [noparse]```
 . . .  
```[/noparse] tags, as the results will be lengthy. The code tags will make it easier to read.

---

### Post by tonymoloney on 2008-03-20
Hope this works
```
tony@tony-laptop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-server (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 08:27:05 UTC 2008 (Ubuntu 2.6.22-14.52-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6e0000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6790
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 259808) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259808
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259808
[    0.000000] On node 0 totalpages: 259808
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30195 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6710 checksum 0
[    0.000000] ACPI: RSDP 000F6710, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 3F6E7C07, 0094 (r1 LENOVO TP-63          58  LTP        0)
[    0.000000] ACPI: FACP 3F6EDBD2, 00F4 (r3 INTEL  TP-63          58 ALAN        1)
[    0.000000] ACPI: DSDT 3F6E95CB, 4593 (r1 LENOVO TP-63          58 INTL 20060608)
[    0.000000] ACPI: FACS 3F6EEFC0, 0040
[    0.000000] ACPI: APIC 3F6EDCC6, 0068 (r1 INTEL  TP-63          58 LOHR       5A)
[    0.000000] ACPI: HPET 3F6EDD2E, 0038 (r1 INTEL  TP-63          58 LOHR       5A)
[    0.000000] ACPI: MCFG 3F6EDD66, 003C (r1 INTEL  TP-63          58 LOHR       5A)
[    0.000000] ACPI: TCPA 3F6EDDA2, 0032 (r1 Phoeni TP-63          58  TL         0)
[    0.000000] ACPI: SLIC 3F6EDDD4, 0176 (r1 LENOVO TP-63          58 TBD         1)
[    0.000000] ACPI: DBGP 3F6EDF4A, 0034 (r1 LENOVO TP-63          58 LOHR        0)
[    0.000000] ACPI: APIC 3F6EDF7E, 005A (r1 PTLTD  TP-63          58  LTP        0)
[    0.000000] ACPI: BOOT 3F6EDFD8, 0028 (r1 PTLTD  TP-63          58  LTP        1)
[    0.000000] ACPI: SSDT 3F6E8F7C, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E88EA, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E8402, 04E8 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E81A3, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E7C9B, 0508 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 257779
[    0.000000] Kernel command line: root=UUID=e08ce548-72a8-4674-8334-ddd0d7aa679d ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.209 MHz processor.
[   15.191818] Console: colour VGA+ 80x25
[   15.192097] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.192483] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.224269] Memory: 1018832k/1039232k available (2047k kernel code, 19564k reserved, 920k data, 364k init, 121728k highmem)
[   15.224279] virtual kernel memory layout:
[   15.224280]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.224282]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   15.224283]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   15.224284]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.224285]       .init : 0xc03eb000 - 0xc0446000   ( 364 kB)
[   15.224287]       .data : 0xc02ffd96 - 0xc03e5f04   ( 920 kB)
[   15.224288]       .text : 0xc0100000 - 0xc02ffd96   (2047 kB)
[   15.224292] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.224328] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.224471] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.224476] hpet0: 3 64-bit timers, 14318180 Hz
[   15.375435] Calibrating delay using timer specific routine.. 3461.18 BogoMIPS (lpj=17305901)
[   15.375461] Security Framework v1.0.0 initialized
[   15.375469] SELinux:  Disabled at boot.
[   15.375484] Mount-cache hash table entries: 512
[   15.375611] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   15.375621] monitor/mwait feature present.
[   15.375623] using mwait in idle threads.
[   15.375628] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.375631] CPU: L2 cache: 1024K
[   15.375634] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   15.375644] Compat vDSO mapped to ffffe000.
[   15.375657] Checking 'hlt' instruction... OK.
[   15.415541] SMP alternatives: switching to UP code
[   15.415747] Freeing SMP alternatives: 11k freed
[   15.416021] Early unpacking initramfs... done
[   15.741444] ACPI: Core revision 20070126
[   15.741503] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.771456] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 0c
[   15.771482] Total of 1 processors activated (3461.18 BogoMIPS).
[   15.771677] ENABLING IO-APIC IRQs
[   15.771882] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.985214] Brought up 1 CPUs
[   15.985314] Booting paravirtualized kernel on bare hardware
[   15.985399] Time: 21:45:50  Date: 02/20/108
[   15.985421] NET: Registered protocol family 16
[   15.985498] EISA bus registered
[   15.985503] ACPI: bus type pci registered
[   16.007123] PCI: PCI BIOS revision 2.10 entry at 0xfd883, last bus=5
[   16.007125] PCI: Using configuration type 1
[   16.007127] Setting up standard PCI resources
[   16.011349] ACPI: EC: Look up EC in DSDT
[   16.011960] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   16.048931] ACPI: System BIOS is requesting _OSI(Linux)
[   16.048934] ACPI: Please test with "acpi_osi=!Linux"
[   16.048935] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   16.049462] ACPI: Interpreter enabled
[   16.049465] ACPI: (supports S0 S3 S4 S5)
[   16.049482] ACPI: Using IOAPIC for interrupt routing
[   16.085920] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   16.085967] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.085975] PCI: Probing PCI hardware (bus 00)
[   16.086694] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   16.086699] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   16.087834] PCI: Transparent bridge - 0000:00:1e.0
[   16.087952] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.088268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   16.088393] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   16.088530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   16.094097] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   16.094193] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   16.094287] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   16.094380] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   16.094477] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   16.094571] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   16.094663] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   16.094756] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   16.094850] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.094860] pnp: PnP ACPI init
[   16.094867] ACPI: bus type pnp registered
[   16.115311] pnp: PnP ACPI: found 11 devices
[   16.115314] ACPI: ACPI bus type pnp unregistered
[   16.115317] PnPBIOS: Disabled by ACPI PNP
[   16.115362] PCI: Using ACPI for IRQ routing
[   16.115365] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.136045] NET: Registered protocol family 8
[   16.136047] NET: Registered protocol family 20
[   16.136056] NetLabel: Initializing
[   16.136058] NetLabel:  domain hash size = 128
[   16.136059] NetLabel:  protocols = UNLABELED CIPSOv4
[   16.136072] NetLabel:  unlabeled traffic allowed by default
[   16.136123] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.136126] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.136130] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.136133] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.136142] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   16.136145] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   16.145112] Time: tsc clocksource has been installed.
[   16.145128] Switched to high resolution mode on CPU 0
[   16.166414] PCI: Bridge: 0000:00:1c.0
[   16.166416]   IO window: disabled.
[   16.166422]   MEM window: disabled.
[   16.166427]   PREFETCH window: disabled.
[   16.166433] PCI: Bridge: 0000:00:1c.1
[   16.166434]   IO window: disabled.
[   16.166441]   MEM window: d0000000-d00fffff
[   16.166445]   PREFETCH window: disabled.
[   16.166458] PCI: Bus 6, cardbus bridge: 0000:05:04.0
[   16.166461]   IO window: 00002400-000024ff
[   16.166466]   IO window: 00002800-000028ff
[   16.166472]   PREFETCH window: 50000000-53ffffff
[   16.166478]   MEM window: 54000000-57ffffff
[   16.166483] PCI: Bridge: 0000:00:1e.0
[   16.166486]   IO window: 2000-2fff
[   16.166492]   MEM window: d0100000-d01fffff
[   16.166497]   PREFETCH window: 50000000-53ffffff
[   16.166528] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   16.166535] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.166559] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   16.166565] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.166576] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   16.166582] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.166599] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   16.166616] NET: Registered protocol family 2
[   16.265109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.265188] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.266275] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.266662] TCP: Hash tables configured (established 131072 bind 65536)
[   16.266666] TCP reno registered
[   16.295213] checking if image is initramfs... it is
[   16.935209] Freeing initrd memory: 6725k freed
[   16.935330] Simple Boot Flag at 0x36 set to 0x1
[   16.935664] audit: initializing netlink socket (disabled)
[   16.935676] audit(1206049550.280:1): initialized
[   16.935731] highmem bounce pool size: 64 pages
[   16.937485] VFS: Disk quotas dquot_6.5.1
[   16.937534] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.937623] io scheduler noop registered
[   16.937625] io scheduler anticipatory registered
[   16.937628] io scheduler deadline registered (default)
[   16.937642] io scheduler cfq registered
[   16.937655] Boot video device is 0000:00:02.0
[   16.937824] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.937882] assign_interrupt_mode Found MSI capability
[   16.937885] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.937919] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.938017] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.938074] assign_interrupt_mode Found MSI capability
[   16.938077] Allocate Port Service[0000:00:1c.1:pcie00]
[   16.938104] Allocate Port Service[0000:00:1c.1:pcie02]
[   16.938252] isapnp: Scanning for PnP cards...
[   17.295165] isapnp: No Plug & Play device found
[   17.321286] Real Time Clock Driver v1.12ac
[   17.321488] hpet_resources: 0xfed00000 is busy
[   17.321513] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.322717] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.322894] input: Macintosh mouse button emulation as /class/input/input0
[   17.322968] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.347710] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.369352] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.369358] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.369360] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.369363] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.369365] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.369565] mice: PS/2 mouse device common for all mice
[   17.372052] EISA: Probing bus 0 at eisa.0
[   17.372060] Cannot allocate resource for EISA slot 1
[   17.372064] Cannot allocate resource for EISA slot 2
[   17.372095] EISA: Detected 0 cards.
[   17.372190] TCP cubic registered
[   17.372205] NET: Registered protocol family 1
[   17.372231] Using IPI No-Shortcut mode
[   17.372386]   Magic number: 0:947:803
[   17.372709] Freeing unused kernel memory: 364k freed
[   17.418848] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.623384] fuse init (API version 7.8)
[   18.628281] Capability LSM initialized
[   18.646040] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.646046] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.646060] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.657072] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   18.663119] ACPI: Thermal Zone [TZ00] (35 C)
[   19.165231] usbcore: registered new interface driver usbfs
[   19.165256] usbcore: registered new interface driver hub
[   19.165275] usbcore: registered new device driver usb
[   19.166090] USB Universal Host Controller Interface driver v3.0
[   19.166156] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   19.166168] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.166172] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.166343] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.166377] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[   19.166495] usb usb1: configuration #1 chosen from 1 choice
[   19.166520] hub 1-0:1.0: USB hub found
[   19.166526] hub 1-0:1.0: 2 ports detected
[   19.264648] SCSI subsystem initialized
[   19.269840] libata version 2.21 loaded.
[   19.274259] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   19.274273] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.274277] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.274299] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.274334] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   19.274436] usb usb2: configuration #1 chosen from 1 choice
[   19.274461] hub 2-0:1.0: USB hub found
[   19.274468] hub 2-0:1.0: 2 ports detected
[   19.311081] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   19.385796] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   19.385809] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.385814] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.385836] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.385870] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[   19.385968] usb usb3: configuration #1 chosen from 1 choice
[   19.385993] hub 3-0:1.0: USB hub found
[   19.386000] hub 3-0:1.0: 2 ports detected
[   19.494216] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   19.494230] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   19.494235] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.494262] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   19.494297] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   19.494395] usb usb4: configuration #1 chosen from 1 choice
[   19.494420] hub 4-0:1.0: USB hub found
[   19.494426] hub 4-0:1.0: 2 ports detected
[    4.130000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.140000] Time: hpet clocksource has been installed.
[    4.190000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    4.240000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    4.240000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.240000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.240000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.240000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.240000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.240000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd0544000
[    4.310000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.310000] usb usb5: configuration #1 chosen from 1 choice
[    4.310000] hub 5-0:1.0: USB hub found
[    4.310000] hub 5-0:1.0: 8 ports detected
[    4.420000] ata_piix 0000:00:1f.2: version 2.11
[    4.420000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.580000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    4.580000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.580000] scsi0 : ata_piix
[    4.580000] scsi1 : ata_piix
[    4.580000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.580000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.730000] usb 1-1: device not accepting address 2, error -71
[    4.760000] ata1.00: ATA-7: HTS541080G9SA00, MB4IC60R, max UDMA/100
[    4.760000] ata1.00: 156301488 sectors, multi 16: LBA48
[    4.800000] ata1.00: configured for UDMA/100
[    5.140000] ata2.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HA01, max UDMA/33
[    5.340000] ata2.00: configured for UDMA/33
[    5.340000] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9SA00  MB4I PQ: 0 ANSI: 5
[    5.340000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HA01 PQ: 0 ANSI: 5
[    5.340000] 8139cp 0000:05:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.340000] 8139cp 0000:05:01.0: Try the "8139too" driver instead.
[    5.340000] PCI: Enabling device 0000:05:06.0 (0000 -> 0002)
[    5.340000] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 22 (level, low) -> IRQ 21
[    5.340000] PCI: Setting latency timer of device 0000:05:06.0 to 64
[    5.400000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.400000] 8139too Fast Ethernet driver 0.9.28
[    5.400000] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 22
[    5.400000] PCI: Setting latency timer of device 0000:05:01.0 to 64
[    5.400000] eth0: RealTek RTL8139 at 0xf8848000, 00:0f:b0:d3:1c:ae, IRQ 22
[    5.400000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.420000] sd 0:0:0:0: [sda] Write Protect is off
[    5.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.420000] sd 0:0:0:0: [sda] Write Protect is off
[    5.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.420000]  sda: sda1 sda2 < sda5 >
[    5.470000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.480000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.480000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.500000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.500000] Uniform CD-ROM driver Revision: 3.20
[    5.500000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.760000] Attempting manual resume
[    5.760000] swsusp: Resume From Partition 8:5
[    5.760000] PM: Checking swsusp image.
[    5.760000] PM: Resume from disk failed.
[    5.780000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[    5.800000] kjournald starting.  Commit interval 5 seconds
[    5.800000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.920000] usb 1-1: not running at top speed; connect to a high speed hub
[    5.950000] usb 1-1: configuration #1 chosen from 1 choice
[    5.950000] hub 1-1:1.0: USB hub found
[    5.950000] hub 1-1:1.0: 4 ports detected
[    6.350000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    6.520000] usb 3-1: configuration #1 chosen from 1 choice
[    6.720000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f72a0400640]
[   13.160000] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[   14.280000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.380000] agpgart: Detected an Intel 945GM Chipset.
[   14.380000] agpgart: Detected 7932K stolen memory.
[   14.390000] agpgart: AGP aperture is 256M @ 0xc0000000
[   14.520000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.560000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.580000] Yenta: CardBus bridge found at 0000:05:04.0 [17aa:3828]
[   15.580000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.580000] Yenta: Routing CardBus interrupts to PCI
[   15.580000] Yenta TI: socket 0000:05:04.0, mfunc 0x01111c12, devctl 0x44
[   15.590000] sdhci: Secure Digital Host Controller Interface driver
[   15.590000] sdhci: Copyright(c) Pierre Ossman
[   15.590000] intel_rng: FWH not detected
[   15.630000] iTCO_vendor_support: vendor-support=0
[   15.630000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.650000] NET: Registered protocol family 17
[   15.830000] Yenta: ISA IRQ mask 0x0cd8, PCI irq 17
[   15.830000] Socket status: 30000006
[   15.830000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   15.830000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   15.830000] cs: IO port probe 0x2000-0x2fff: clean.
[   15.830000] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   15.830000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   15.830000] sdhci: SDHCI controller found at 0000:05:06.1 [1180:0822] (rev 19)
[   15.830000] PCI: Enabling device 0000:05:06.1 (0000 -> 0002)
[   15.830000] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 18
[   15.830000] PCI: Setting latency timer of device 0000:05:06.1 to 64
[   15.830000] mmc0: SDHCI at 0xd0100400 irq 18 DMA
[   16.020000] ieee80211_crypt: registered algorithm 'NULL'
[   16.070000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.070000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.130000] usbcore: registered new interface driver hiddev
[   16.150000] input: USB Optical Mouse as /class/input/input2
[   16.150000] input: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-1
[   16.150000] usbcore: registered new interface driver usbhid
[   16.150000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   16.350000] bcm43xx driver
[   16.350000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   16.350000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.450000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   16.520000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.520000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   16.520000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.810000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   16.810000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   16.870000] cs: IO port probe 0x100-0x3af: clean.
[   16.880000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.880000] cs: IO port probe 0x820-0x8ff: clean.
[   16.880000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.880000] cs: IO port probe 0xa00-0xaff: clean.
[   17.320000] lp: driver loaded but no devices found
[   17.400000] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   17.870000] EXT3 FS on sda1, internal journal
[   23.450000] NET: Registered protocol family 10
[   23.450000] lo: Disabled Privacy Extensions
[   23.810000] No dock devices found.
[   23.940000] ACPI: Battery Slot [BAT1] (battery present)
[   24.000000] ACPI: AC Adapter [ACAD] (on-line)
[   24.040000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.050000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.060000] input: Power Button (FF) as /class/input/input4
[   24.060000] ACPI: Power Button (FF) [PWRF]
[   24.060000] input: Lid Switch as /class/input/input5
[   24.060000] ACPI: Lid Switch [LID0]
[   24.060000] input: Power Button (CM) as /class/input/input6
[   24.060000] ACPI: Power Button (CM) [PWRB]
[   26.200000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   26.490000] ppdev: user-space parallel port driver
[   27.570000] [drm] Initialized drm 1.1.0 20060810
[   27.600000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   27.600000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   28.300000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   30.500000] usbcore: registered new interface driver usblp
[   30.500000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   31.160000] apm: BIOS not found.
[   35.880000] Capability LSM initialized
[   37.010000] Bluetooth: Core ver 2.11
[   37.010000] NET: Registered protocol family 31
[   37.010000] Bluetooth: HCI device and connection manager initialized
[   37.010000] Bluetooth: HCI socket layer initialized
[   37.020000] Bluetooth: L2CAP ver 2.8
[   37.020000] Bluetooth: L2CAP socket layer initialized
[   37.240000] Bluetooth: RFCOMM socket layer initialized
[   37.240000] Bluetooth: RFCOMM TTY layer initialized
[   37.240000] Bluetooth: RFCOMM ver 1.8
[   50.530000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   55.150000] eth2: no IPv6 routers present
[   72.570000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   94.600000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  116.680000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  138.710000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  160.740000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  282.780000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
tony@tony-laptop:~$    
```

---

### Post by tonymoloney on 2008-03-20
Sorry about that. I selected the text, then clicked on the icon for "Wrap [QUOTE] tags around the selected text" and this is what I got. Should I have gone to each end of the text and clicked on the icon?

---

### Post by amd-64 on 2008-03-20
> **tonymoloney said:**
> Hmmm. The tip from p_quarles had no effect.
Following amd-64's tip gave the following output:

tony@tony-laptop:~$ sudo kfind /etc
[sudo] password for tony:
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: "/var/tmp/kdecache-tony" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-tony" is owned by uid 1000 instead of uid 0.
tony@tony-laptop:~$

Sorry guys - I've just had a phone call and I've got to go out.
I'll follow this up when I return.

Not sure why it didn't work. Try it this way instead
```

kdesu kfind /etc
```

---

### Post by tonymoloney on 2008-03-21
Sorry about the delay in answering. Being on the other side of the world doesn't help.
Here's the output of kdesu kfind /etc

tony@tony-laptop:~$ kdesu kfind /etc
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
tony@tony-laptop:~$

---

### Post by amd-64 on 2008-03-21
It seems that you have an input device problem. Could you check or post your /etc/X11/xorg.conf file. I am suspecting you have a wacom device configured.

---

### Post by tonymoloney on 2008-03-22
Is this what you're looking for?


Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection


When I check my log files I see plenty of messages pertaining to wacom, but I don't know what to do about them.

---

### Post by tonymoloney on 2008-03-22
I've also found the following comment in xorg.conf:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Should I do that?

---

### Post by amd-64 on 2008-03-22
> **tonymoloney said:**
> Is this what you're looking for?


Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection


When I check my log files I see plenty of messages pertaining to wacom, but I don't know what to do about them.

This is the section defining the device. If you do not use a wacom stylus, you can simply comment out this section. More importantly, you need to comment the line in the server layout section. This would be also in your xorg.conf file. 

It would look like

Inputdevice "stylus"


You need to edit this file as root and please make a backup copy just in case. 

Another method is to remove the wacom deb completely. 

sudo apt-get remove xserver-xorg-input-wacom

---

### Post by tonymoloney on 2008-03-22
Thanks for all the help guys. It looks like the problem has been fixed.

---

