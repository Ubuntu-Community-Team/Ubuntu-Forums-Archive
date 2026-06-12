---
title: "Microsoft Zune on VirtualBox with USB 2.0"
date: 2008-02-14
forum: Virtualisation
---

### Post by brokencrystal on 2008-02-14
I have a Microsoft Zune 30GB and I am trying to run Microsoft's Zune software in Ubuntu Gutsy.  I know this is near impossible.  So I installed the closed source version of VirtualBox that supports USB 2.0.  I decided on Windows XP since I have a licensed retail version laying around not doing anything.  The installation went well.  I followed the extra steps to enable USB support for VirtualBox as instructed in their tutorial.  I installed the Zune software and that went well.  It runs fine.  I plugged in my Zune, selected it in my USB list in VirtualBox's list, but nothing happened.  My Zune software and XP both don't acknowledge that the Zune is connected.  My Ubuntu sees it and pops up my default media player.  I close that and go back to VirtualBox, but see nothing.  Any ideas?

Thanks in advance,
BrokenCrystal

---

### Post by tgalati4 on 2008-02-14
When you polish the Zune, can you see the lines of your teeth?  That's when you know you have it really shiny.  The brown Zune matches the Ubuntu theme.

Immediately after you plug it in, post the output of:

dmesg | tail -25

---

### Post by brokencrystal on 2008-02-14
> **tgalati4 said:**
> When you polish the Zune, can you see the lines of your teeth?  That's when you know you have it really shiny.  The brown Zune matches the Ubuntu theme.

Immediately after you plug it in, post the output of:

dmesg | tail -25

I keep it in the case so it stays nice and shiny.  I will try dmesg | tail -25 when I get home.  In the mean time, have you ever heard of anyone trying to do this and succeeding?

---

### Post by tgalati4 on 2008-02-15
Add to that output:

lsusb

---

### Post by brokencrystal on 2008-02-15
```
fowlers@eMachines:~$ dmesg | tail -25
[  261.264805] usb 3-4: configuration #1 chosen from 1 choice
[  310.889340] usb 3-4: USB disconnect, address 4
[  316.998433] hub 2-1:1.0: port 3 disabled by hub (EMI?), re-enabling...
[  316.998445] usb 2-1.3: USB disconnect, address 3
[  317.070369] usb 2-1.3: new low speed USB device using ohci_hcd and address 4
[  317.177406] usb 2-1.3: configuration #1 chosen from 1 choice
[  317.184627] input: Logitech Optical USB Mouse as /class/input/input6
[  317.184713] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-1.3
[  321.738970] usb 2-1.2: new full speed USB device using ohci_hcd and address 5
[  321.838873] usb 2-1.2: not running at top speed; connect to a high speed hub
[  321.856005] usb 2-1.2: rejected 1 configuration due to insufficient available bus power
[  321.856015] usb 2-1.2: no configuration chosen from 1 choice
[  328.955848] usb 2-1.2: new config #1 exceeds power limit by 400mA
[  362.939159] usb 2-1.2: USB disconnect, address 5
[  374.802825] usb 3-1: new high speed USB device using ehci_hcd and address 5
[  374.942891] usb 3-1: configuration #1 chosen from 1 choice
[  399.208052] usb 3-1: USB disconnect, address 5
[  415.849404] hub 2-1:1.0: port 3 disabled by hub (EMI?), re-enabling...
[  415.849418] usb 2-1.3: USB disconnect, address 4
[  415.926250] usb 2-1.3: new low speed USB device using ohci_hcd and address 6
[  416.033291] usb 2-1.3: configuration #1 chosen from 1 choice
[  416.043625] input: Logitech Optical USB Mouse as /class/input/input7
[  416.043709] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-1.3
[  522.090542] usb 3-5: new high speed USB device using ehci_hcd and address 6
[  522.231808] usb 3-5: configuration #1 chosen from 1 choice
fowlers@eMachines:~$ 
```

---

### Post by brokencrystal on 2008-02-15
```
fowlers@eMachines:~$ lsusb
Bus 003 Device 006: ID 045e:0710 Microsoft Corp. 
Bus 003 Device 003: ID 058f:6377 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
fowlers@eMachines:~$ 
```

---

### Post by tgalati4 on 2008-02-15
Try removing all of your other USB devices (even the mouse if you have an old PS/2 mouse) then post again.  It looks like your hub may be drawing too much current causing it to shut down.

Also note that I assume the Zune is on Bus 3-Device-6 but dmesg doesn't show enumeration by the kernel.  So you would either need to load a module (sudo modprobe mszune, for example) or check for a newer kernel with support for it.  You will have to do some research to see if a newer kernel (such as 2.6.24) has built-in support for it.

Also post differences between (dmesg, lsusb, lsmod) using Virtual Box and Ubuntu-only.

You might need to file a bug/feature request for Virtual Box on this matter, but search to see if it has already been posted.

---

### Post by brokencrystal on 2008-02-15
> **tgalati4 said:**
> Try removing all of your other USB devices (even the mouse if you have an old PS/2 mouse) then post again.  It looks like your hub may be drawing too much current causing it to shut down.

Also note that I assume the Zune is on Bus 3-Device-6 but dmesg doesn't show enumeration by the kernel.  So you would either need to load a module (sudo modprobe mszune, for example) or check for a newer kernel with support for it.  You will have to do some research to see if a newer kernel (such as 2.6.24) has built-in support for it.

Also post differences between (dmesg, lsusb, lsmod) using Virtual Box and Ubuntu-only.

You might need to file a bug/feature request for Virtual Box on this matter, but search to see if it has already been posted.

I think the reason for the surge was when I tried to plug the Zune into my keyboard's built-in USB 1.1 hub.  Here is with the mouse and the hub that is built into the keyboard both unplugged:

```

fowlers@eMachines:~$ lsmod
Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                60208  0 
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
container               5504  0 
ac                      6148  0 
button                  8976  0 
video                  18060  0 
sbs                    19592  0 
dock                   10656  0 
battery                11012  0 
lp                     12580  0 
snd_hda_intel         263840  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sg                     36764  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sd_mod                 30336  0 
psmouse                39952  0 
serio_raw               8068  0 
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
fglrx                1476940  20 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
shpchp                 34580  0 
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  0 
ata_generic             8452  0 
libusual               18448  1 usb_storage
8139too                27776  0 
atiixp                  7056  0 [permanent]
ide_core              116804  4 ide_disk,ide_cd,usb_storage,atiixp
sata_sil               12168  0 
libata                125168  2 ata_generic,sata_sil
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
fowlers@eMachines:~$ 
```

```
fowlers@eMachines:~$ lsusb
Bus 003 Device 011: ID 045e:0710 Microsoft Corp. 
Bus 003 Device 003: ID 058f:6377 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

```
fowlers@eMachines:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ef60000 (usable)
[    0.000000]  BIOS-e820: 000000007ef60000 - 000000007f004000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f004000 - 000000007fd90000 (usable)
[    0.000000]  BIOS-e820: 000000007fd90000 - 000000007fd98000 (reserved)
[    0.000000]  BIOS-e820: 000000007fd98000 - 000000007fe2e000 (usable)
[    0.000000]  BIOS-e820: 000000007fe2e000 - 000000007fe32000 (reserved)
[    0.000000]  BIOS-e820: 000000007fe32000 - 000000007feab000 (usable)
[    0.000000]  BIOS-e820: 000000007feab000 - 000000007feef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007feef000 - 000000007fef1000 (usable)
[    0.000000]  BIOS-e820: 000000007fef1000 - 000000007feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007feff000 - 000000007ff00000 (usable)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe860
[    0.000000] Entering add_active_range(0, 0, 524032) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524032
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524032
[    0.000000] On node 0 totalpages: 524032
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292354 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 GATEWA)
[    0.000000] ACPI: RSDT 7FEFE038, 0048 (r1 GATEWA SYSTEM        7E8       1000013)
[    0.000000] ACPI: FACP 7FEFD000, 0074 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: DSDT 7FEF9000, 3918 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: FACS 7FEAB000, 0040
[    0.000000] ACPI: APIC 7FEF8000, 0084 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: MCFG 7FEF7000, 003C (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: SSDT 7FEF6000, 01B4 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: SSDT 7FEF5000, 0175 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: SSDT 7FEF4000, 0175 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: SSDT 7FEF3000, 0175 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: SSDT 7FEF2000, 0175 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ACPI: SLIC 7FEF1000, 0176 (r1 GATEWA SYSTEM        7E8 MSFT  1000013)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:80080000)
[    0.000000] Built 1 zonelists.  Total pages: 519938
[    0.000000] Kernel command line: root=UUID=b064cdc5-3d6e-4493-8797-79fe9d63b3b9 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.654 MHz processor.
[   36.588341] Console: colour VGA+ 80x25
[   36.588987] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.589506] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.686849] Memory: 2065600k/2096128k available (2015k kernel code, 28176k reserved, 915k data, 364k init, 1177592k highmem)
[   36.686859] virtual kernel memory layout:
[   36.686860]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   36.686861]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.686863]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   36.686864]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   36.686865]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   36.686866]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   36.686867]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   36.686870] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.686923] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   36.766885] Calibrating delay using timer specific routine.. 6007.46 BogoMIPS (lpj=12014938)
[   36.766922] Security Framework v1.0.0 initialized
[   36.766929] SELinux:  Disabled at boot.
[   36.766943] Mount-cache hash table entries: 512
[   36.767109] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   36.767118] monitor/mwait feature present.
[   36.767120] using mwait in idle threads.
[   36.767128] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   36.767131] CPU: L2 cache: 2048K
[   36.767134] CPU: Physical Processor ID: 0
[   36.767136] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e59d 00000000 00000001
[   36.767150] Compat vDSO mapped to ffffe000.
[   36.767168] Checking 'hlt' instruction... OK.
[   36.783026] SMP alternatives: switching to UP code
[   36.783642] Early unpacking initramfs... done
[   37.067474] ACPI: Core revision 20070126
[   37.067523] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   37.079830] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   37.079849] SMP alternatives: switching to SMP code
[   37.079968] Booting processor 1/1 eip 3000
[   37.090267] Initializing CPU#1
[   37.170526] Calibrating delay using timer specific routine.. 6000.71 BogoMIPS (lpj=12001439)
[   37.170537] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   37.170544] monitor/mwait feature present.
[   37.170551] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   37.170555] CPU: L2 cache: 2048K
[   37.170557] CPU: Physical Processor ID: 0
[   37.170560] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e59d 00000000 00000001
[   37.171123] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   37.171168] Total of 2 processors activated (12008.18 BogoMIPS).
[   37.171340] ENABLING IO-APIC IRQs
[   37.171544] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   37.211246] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   37.211301] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   37.211304] ...trying to set up timer as Virtual Wire IRQ... works.
[   37.358480] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   37.378481] Brought up 2 CPUs
[   37.424581] migration_cost=7
[   37.424769] Booting paravirtualized kernel on bare hardware
[   37.424858] Time: 11:55:41  Date: 01/15/108
[   37.424884] NET: Registered protocol family 16
[   37.424981] EISA bus registered
[   37.424987] ACPI: bus type pci registered
[   37.427924] PCI: Using configuration type 1
[   37.427926] Setting up standard PCI resources
[   37.446782] ACPI: EC: Look up EC in DSDT
[   37.449679] ACPI: Interpreter enabled
[   37.449683] ACPI: (supports S0 S1 S3 S4 S5)
[   37.449706] ACPI: Using IOAPIC for interrupt routing
[   37.454379] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   37.454389] PCI: Probing PCI hardware (bus 00)
[   37.455872] PCI: Transparent bridge - 0000:00:14.4
[   37.455920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   37.456102] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
[   37.456243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   37.459229] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459335] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459437] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459538] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459639] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459739] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459840] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.459941] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   37.460040] Linux Plug and Play Support v0.97 (c) Adam Belay
[   37.460051] pnp: PnP ACPI init
[   37.460060] ACPI: bus type pnp registered
[   37.462298] pnp: PnP ACPI: found 10 devices
[   37.462301] ACPI: ACPI bus type pnp unregistered
[   37.462306] PnPBIOS: Disabled by ACPI PNP
[   37.462367] PCI: Using ACPI for IRQ routing
[   37.462371] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   37.462475] NET: Registered protocol family 8
[   37.462478] NET: Registered protocol family 20
[   37.462545] pnp: 00:06: ioport range 0x400-0x4cf has been reserved
[   37.462548] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   37.462555] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   37.462558] pnp: 00:07: iomem range 0xec000-0xfffff could not be reserved
[   37.462561] pnp: 00:07: iomem range 0x100000-0x7fffffff could not be reserved
[   37.462565] pnp: 00:07: iomem range 0xe0000000-0xefffffff has been reserved
[   37.466308] Time: tsc clocksource has been installed.
[   37.492948] PCI: Bridge: 0000:00:02.0
[   37.492952]   IO window: 2000-2fff
[   37.492957]   MEM window: a0100000-a01fffff
[   37.492961]   PREFETCH window: 80000000-9fffffff
[   37.492965] PCI: Bridge: 0000:00:14.4
[   37.492969]   IO window: 1000-1fff
[   37.492977]   MEM window: a0000000-a00fffff
[   37.492982]   PREFETCH window: disabled.
[   37.493002] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   37.493014] PCI: Setting latency timer of device 0000:00:14.4 to 64
[   37.493025] NET: Registered protocol family 2
[   37.538383] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   37.538477] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   37.539399] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   37.539714] TCP: Hash tables configured (established 131072 bind 65536)
[   37.539717] TCP reno registered
[   37.550548] checking if image is initramfs... it is
[   37.993868] Switched to high resolution mode on CPU 0
[   37.993951] Switched to high resolution mode on CPU 1
[   38.112563] Freeing initrd memory: 7052k freed
[   38.113196] audit: initializing netlink socket (disabled)
[   38.113213] audit(1203076541.116:1): initialized
[   38.113323] highmem bounce pool size: 64 pages
[   38.115727] VFS: Disk quotas dquot_6.5.1
[   38.115792] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.115902] io scheduler noop registered
[   38.115905] io scheduler anticipatory registered
[   38.115908] io scheduler deadline registered
[   38.115924] io scheduler cfq registered (default)
[   38.115940] PCI: MSI quirk detected. MSI deactivated.
[   38.115965] Boot video device is 0000:01:00.0
[   38.116056] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   38.116097] assign_interrupt_mode Found MSI capability
[   38.116100] Allocate Port Service[0000:00:02.0:pcie00]
[   38.116272] isapnp: Scanning for PnP cards...
[   38.467639] isapnp: No Plug & Play device found
[   38.495327] Real Time Clock Driver v1.12ac
[   38.495439] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.495579] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.496341] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.497111] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.497333] input: Macintosh mouse button emulation as /class/input/input0
[   38.497418] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
[   38.497421] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   38.500246] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.500254] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.500437] mice: PS/2 mouse device common for all mice
[   38.500572] EISA: Probing bus 0 at eisa.0
[   38.500582] Cannot allocate resource for EISA slot 1
[   38.500585] Cannot allocate resource for EISA slot 2
[   38.500587] Cannot allocate resource for EISA slot 3
[   38.500615] EISA: Detected 0 cards.
[   38.500710] TCP cubic registered
[   38.500722] NET: Registered protocol family 1
[   38.500746] Using IPI No-Shortcut mode
[   38.500921]   Magic number: 12:158:934
[   38.501375] Freeing unused kernel memory: 364k freed
[   38.518932] input: AT Translated Set 2 keyboard as /class/input/input1
[   39.856019] AppArmor: AppArmor initialized<5>audit(1203076542.616:2):  type=1505 info="AppArmor initialized" pid=1194
[   39.864430] fuse init (API version 7.8)
[   39.869377] Failure registering capabilities with primary security module.
[   39.910457] ACPI: Processor [CPU0] (supports 8 throttling states)
[   39.910543] ACPI: Processor [CPU1] (supports 8 throttling states)
[   39.910558] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.910572] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   40.514311] usbcore: registered new interface driver usbfs
[   40.514349] usbcore: registered new interface driver hub
[   40.514388] usbcore: registered new device driver usb
[   40.515451] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.515491] PCI: Enabling device 0000:00:13.0 (0000 -> 0002)
[   40.515507] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[   40.515526] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   40.515726] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   40.515750] ohci_hcd 0000:00:13.0: irq 16, io mem 0xa0204000
[   40.584755] usb usb1: configuration #1 chosen from 1 choice
[   40.584807] hub 1-0:1.0: USB hub found
[   40.584826] hub 1-0:1.0: 4 ports detected
[   40.600920] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   40.616166] SCSI subsystem initialized
[   40.623965] libata version 2.21 loaded.
[   40.658542] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   40.658551] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   40.687863] PCI: Enabling device 0000:00:13.1 (0000 -> 0002)
[   40.687875] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[   40.687898] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   40.687936] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   40.687958] ohci_hcd 0000:00:13.1: irq 16, io mem 0xa0205000
[   40.747726] usb usb2: configuration #1 chosen from 1 choice
[   40.747771] hub 2-0:1.0: USB hub found
[   40.747785] hub 2-0:1.0: 4 ports detected
[   40.851831] PCI: Enabling device 0000:00:13.2 (0000 -> 0002)
[   40.851840] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[   40.851859] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   40.851897] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   40.851958] ehci_hcd 0000:00:13.2: irq 16, io mem 0xa0206000
[   40.851974] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.852079] usb usb3: configuration #1 chosen from 1 choice
[   40.852121] hub 3-0:1.0: USB hub found
[   40.852132] hub 3-0:1.0: 8 ports detected
[   40.955726] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   40.955735] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   40.958426] 8139too Fast Ethernet driver 0.9.28
[   40.958491] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   40.958508] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   40.959270] eth0: RealTek RTL8139 at 0xf8846000, 00:19:d1:52:85:ca, IRQ 21
[   40.959274] eth0:  Identified 8139 chip type 'RTL-8101'
[   40.959400] sata_sil 0000:00:11.0: version 2.2
[   40.959472] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 17
[   40.959494] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   40.959580] scsi0 : sata_sil
[   40.959850] scsi1 : sata_sil
[   40.959904] ata1: SATA max UDMA/100 cmd 0xf8844680 ctl 0xf884468a bmdma 0xf8844600 irq 17
[   40.959911] ata2: SATA max UDMA/100 cmd 0xf88446c0 ctl 0xf88446ca bmdma 0xf8844608 irq 17
[   41.271198] ata1: SATA link down (SStatus 0 SControl 310)
[   41.582941] ata2: SATA link down (SStatus 0 SControl 310)
[   41.583037] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   41.583059] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   41.583107] scsi2 : sata_sil
[   41.583173] scsi3 : sata_sil
[   41.583221] ata3: SATA max UDMA/100 cmd 0xf8868480 ctl 0xf886848a bmdma 0xf8868400 irq 18
[   41.583228] ata4: SATA max UDMA/100 cmd 0xf88684c0 ctl 0xf88684ca bmdma 0xf8868408 irq 18
[   41.586955] usb 3-7: new high speed USB device using ehci_hcd and address 3
[   41.721031] usb 3-7: configuration #1 chosen from 1 choice
[   41.894696] ata3: SATA link down (SStatus 0 SControl 310)
[   42.022595] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   42.206432] ata4: SATA link down (SStatus 0 SControl 310)
[   42.206510] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   42.206545] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   42.206561] ATIIXP: chipset revision 128
[   42.206565] ATIIXP: not 100% native mode: will probe irqs later
[   42.206578]     ide0: BM-DMA at 0x3000-0x3007, BIOS settings: hda:DMA, hdb:pio
[   42.206599]     ide1: BM-DMA at 0x3008-0x300f, BIOS settings: hdc:DMA, hdd:pio
[   42.206614] Probing IDE interface ide0...
[   42.223381] usb 2-1: configuration #1 chosen from 1 choice
[   42.225309] hub 2-1:1.0: USB hub found
[   42.227251] hub 2-1:1.0: 4 ports detected
[   42.494640] hda: Hitachi HDS721616PLAT80, ATA DISK drive
[   42.550956] usb 2-1.3: new low speed USB device using ohci_hcd and address 3
[   42.656970] usb 2-1.3: configuration #1 chosen from 1 choice
[   42.662868] usbcore: registered new interface driver libusual
[   42.669385] Initializing USB Mass Storage driver...
[   42.669469] scsi4 : SCSI emulation for USB Mass Storage devices
[   42.669532] usb-storage: device found at 3
[   42.669535] usb-storage: waiting for device to settle before scanning
[   42.669557] usbcore: registered new interface driver usb-storage
[   42.669562] USB Mass Storage support registered.
[   42.675562] usbcore: registered new interface driver hiddev
[   42.680031] input: Logitech Optical USB Mouse as /class/input/input2
[   42.680065] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-1.3
[   42.680082] usbcore: registered new interface driver usbhid
[   42.680088] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.165667] hda: selected mode 0x45
[   43.165893] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   43.182192] Probing IDE interface ide1...
[   43.917471] hdc: TSSTcorpCD/DVDW TS-H652D, ATAPI CD/DVD-ROM drive
[   44.588505] hdc: selected mode 0x42
[   44.588931] ide1 at 0x170-0x177,0x376 on irq 15
[   44.607119] hda: max request size: 512KiB
[   44.607316] hda: 321672960 sectors (164696 MB) w/7384KiB Cache, CHS=20023/255/63, UDMA(100)
[   44.607516] hda: cache flushes supported
[   44.607570]  hda:<6>hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   44.609923] Uniform CD-ROM driver Revision: 3.20
[   44.617622]  hda1 hda2 < hda5 >
[   44.796581] Attempting manual resume
[   44.796586] swsusp: Resume From Partition 3:5
[   44.796588] PM: Checking swsusp image.
[   44.796723] PM: Resume from disk failed.
[   44.835918] kjournald starting.  Commit interval 5 seconds
[   44.835932] EXT3-fs: mounted filesystem with ordered data mode.
[   47.662161] usb-storage: device scan complete
[   47.662765] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   47.663392] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   47.664017] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   47.664515] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   50.459314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.549126] Linux agpgart interface v0.102 (c) Dave Jones
[   50.570711] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.779387] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   51.141604] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   51.179120] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   51.179178] [fglrx] ASYNCIO init succeed!
[   51.180598] [fglrx] PAT is enabled successfully!
[   51.180656] [fglrx] module loaded - fglrx 8.45.4 [Jan 16 2008] on minor 0
[   51.425101] parport_pc 00:08: reported by Plug and Play ACPI
[   51.425142] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   51.465095] input: PC Speaker as /class/input/input3
[   51.560232] sd 4:0:0:0: [sda] Attached SCSI removable disk
[   51.561324] sd 4:0:0:1: [sdb] Attached SCSI removable disk
[   51.562274] sd 4:0:0:2: [sdc] Attached SCSI removable disk
[   51.563148] sd 4:0:0:3: [sdd] Attached SCSI removable disk
[   51.586820] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   51.587057] sd 4:0:0:1: Attached scsi generic sg1 type 0
[   51.587290] sd 4:0:0:2: Attached scsi generic sg2 type 0
[   51.587525] sd 4:0:0:3: Attached scsi generic sg3 type 0
[   51.966384] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   53.122837] lp0: using parport0 (interrupt-driven).
[   53.169092] Adding 1309256k swap on /dev/hda5.  Priority:-1 extents:1 across:1309256k
[   53.527303] EXT3 FS on hda1, internal journal
[   54.507844] No dock devices found.
[   54.605804] input: Power Button (FF) as /class/input/input4
[   54.605834] ACPI: Power Button (FF) [PWRF]
[   54.605895] input: Power Button (CM) as /class/input/input5
[   54.605931] ACPI: Power Button (CM) [PWRB]
[   55.768941] ppdev: user-space parallel port driver
[   55.944691] audit(1203076559.427:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4885 profile="/usr/sbin/cupsd"
[   56.024695] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.024702] apm: disabled - APM is not SMP safe.
[   56.086530] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   56.743656] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   56.743665] vboxdrv: Successfully done.
[   56.746391] vboxdrv: Successfully loaded version 1.5.4 (interface 0x00050002).
[   57.096249] Failure registering capabilities with primary security module.
[   57.296882] Bluetooth: Core ver 2.11
[   57.297086] NET: Registered protocol family 31
[   57.297092] Bluetooth: HCI device and connection manager initialized
[   57.297098] Bluetooth: HCI socket layer initialized
[   57.316207] Bluetooth: L2CAP ver 2.8
[   57.316215] Bluetooth: L2CAP socket layer initialized
[   57.353506] Bluetooth: RFCOMM socket layer initialized
[   57.353691] Bluetooth: RFCOMM TTY layer initialized
[   57.353698] Bluetooth: RFCOMM ver 1.8
[   60.049153] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   61.543775] NET: Registered protocol family 17
[   64.052376] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   64.052382] [fglrx] Reserve Block - 1 offset =  0X7fc0000 length = 0X40000
[   64.236156] [fglrx] interrupt source 20008000 successfully enabled
[   64.236163] [fglrx] enable ID = 0x00000004
[   64.236176] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   64.236771] [fglrx] interrupt source 10000000 successfully enabled
[   64.236775] [fglrx] enable ID = 0x00000005
[   64.236781] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   64.499259] NET: Registered protocol family 10
[   64.499609] lo: Disabled Privacy Extensions
[   69.029215] hda-intel: Invalid position buffer, using LPIB read method instead.
[   70.578044] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list
[   70.639310] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   70.690652] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   70.745869] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   70.841933] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   75.079578] eth0: no IPv6 routers present
[  261.123678] usb 3-4: new high speed USB device using ehci_hcd and address 4
[  261.264805] usb 3-4: configuration #1 chosen from 1 choice
[  310.889340] usb 3-4: USB disconnect, address 4
[  316.998433] hub 2-1:1.0: port 3 disabled by hub (EMI?), re-enabling...
[  316.998445] usb 2-1.3: USB disconnect, address 3
[  317.070369] usb 2-1.3: new low speed USB device using ohci_hcd and address 4
[  317.177406] usb 2-1.3: configuration #1 chosen from 1 choice
[  317.184627] input: Logitech Optical USB Mouse as /class/input/input6
[  317.184713] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-1.3
[  321.738970] usb 2-1.2: new full speed USB device using ohci_hcd and address 5
[  321.838873] usb 2-1.2: not running at top speed; connect to a high speed hub
[  321.856005] usb 2-1.2: rejected 1 configuration due to insufficient available bus power
[  321.856015] usb 2-1.2: no configuration chosen from 1 choice
[  328.955848] usb 2-1.2: new config #1 exceeds power limit by 400mA
[  362.939159] usb 2-1.2: USB disconnect, address 5
[  374.802825] usb 3-1: new high speed USB device using ehci_hcd and address 5
[  374.942891] usb 3-1: configuration #1 chosen from 1 choice
[  399.208052] usb 3-1: USB disconnect, address 5
[  415.849404] hub 2-1:1.0: port 3 disabled by hub (EMI?), re-enabling...
[  415.849418] usb 2-1.3: USB disconnect, address 4
[  415.926250] usb 2-1.3: new low speed USB device using ohci_hcd and address 6
[  416.033291] usb 2-1.3: configuration #1 chosen from 1 choice
[  416.043625] input: Logitech Optical USB Mouse as /class/input/input7
[  416.043709] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-1.3
[  522.090542] usb 3-5: new high speed USB device using ehci_hcd and address 6
[  522.231808] usb 3-5: configuration #1 chosen from 1 choice
[ 1161.292530] usb 3-7: reset high speed USB device using ehci_hcd and address 3
[ 1161.425968] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1161.426054] usb-storage: device found at 3
[ 1161.426059] usb-storage: waiting for device to settle before scanning
[ 1166.420475] usb-storage: device scan complete
[ 1166.421091] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[ 1166.421714] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[ 1166.422337] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[ 1166.422961] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[ 1166.424692] sd 5:0:0:0: [sda] Attached SCSI removable disk
[ 1166.424767] sd 5:0:0:0: Attached scsi generic sg0 type 0
[ 1166.426389] sd 5:0:0:1: [sdb] Attached SCSI removable disk
[ 1166.426461] sd 5:0:0:1: Attached scsi generic sg1 type 0
[ 1166.428253] sd 5:0:0:2: [sdc] Attached SCSI removable disk
[ 1166.428341] sd 5:0:0:2: Attached scsi generic sg2 type 0
[ 1166.430098] sd 5:0:0:3: [sdd] Attached SCSI removable disk
[ 1166.430169] sd 5:0:0:3: Attached scsi generic sg3 type 0
[ 1821.103793] usb 3-5: USB disconnect, address 6
[ 1842.424285] usb 3-5: new high speed USB device using ehci_hcd and address 7
[ 1842.566403] usb 3-5: configuration #1 chosen from 1 choice
[ 1880.658631] usb 3-5: USB disconnect, address 7
[ 1886.104598] usb 3-6: new high speed USB device using ehci_hcd and address 8
[ 1886.244834] usb 3-6: configuration #1 chosen from 1 choice
[ 1965.188020] usb 3-6: reset high speed USB device using ehci_hcd and address 8
[33281.959701] usb 3-6: USB disconnect, address 8
[33284.474759] usb 3-6: new high speed USB device using ehci_hcd and address 9
[33284.616020] usb 3-6: configuration #1 chosen from 1 choice
[33312.958910] usb 2-1: USB disconnect, address 2
[33312.958918] usb 2-1.3: USB disconnect, address 6
[33321.659608] usb 3-6: USB disconnect, address 9
[33377.167049] usb 2-2: new full speed USB device using ohci_hcd and address 7
[33377.367433] usb 2-2: configuration #1 chosen from 1 choice
[33377.369357] hub 2-2:1.0: USB hub found
[33377.371299] hub 2-2:1.0: 4 ports detected
[33377.698986] usb 2-2.3: new low speed USB device using ohci_hcd and address 8
[33377.809024] usb 2-2.3: configuration #1 chosen from 1 choice
[33377.816281] input: Logitech Optical USB Mouse as /class/input/input8
[33377.816366] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-2.3
[33424.190269] usb 2-2: USB disconnect, address 7
[33424.190277] usb 2-2.3: USB disconnect, address 8
[33488.915788] usb 3-5: new high speed USB device using ehci_hcd and address 11
[33489.056971] usb 3-5: configuration #1 chosen from 1 choice
[33591.667872] usb 1-2: new full speed USB device using ohci_hcd and address 2
[33591.868809] usb 1-2: configuration #1 chosen from 1 choice
[33591.870729] hub 1-2:1.0: USB hub found
[33591.872669] hub 1-2:1.0: 4 ports detected
[33592.196357] usb 1-2.3: new low speed USB device using ohci_hcd and address 3
[33592.303409] usb 1-2.3: configuration #1 chosen from 1 choice
[33592.310662] input: Logitech Optical USB Mouse as /class/input/input9
[33592.310744] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.0-2.3
[34008.585220] usb 1-2: USB disconnect, address 2
[34008.585229] usb 1-2.3: USB disconnect, address 3
[34014.410361] usb 3-5: USB disconnect, address 11
[34017.092449] usb 3-5: new high speed USB device using ehci_hcd and address 13
[34017.233548] usb 3-5: configuration #1 chosen from 1 choice
[34028.283312] usb 2-2: new full speed USB device using ohci_hcd and address 9
[34028.484247] usb 2-2: configuration #1 chosen from 1 choice
[34028.486163] hub 2-2:1.0: USB hub found
[34028.488106] hub 2-2:1.0: 4 ports detected
[34028.812796] usb 2-2.3: new low speed USB device using ohci_hcd and address 10
[34028.917837] usb 2-2.3: configuration #1 chosen from 1 choice
[34028.925106] input: Logitech Optical USB Mouse as /class/input/input10
[34028.925189] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-2.3
[34086.975264] usb 2-2: USB disconnect, address 9
[34086.975273] usb 2-2.3: USB disconnect, address 10
[34103.457912] usb 1-2: new full speed USB device using ohci_hcd and address 4
[34103.658850] usb 1-2: configuration #1 chosen from 1 choice
[34103.660769] hub 1-2:1.0: USB hub found
[34103.662712] hub 1-2:1.0: 4 ports detected
[34103.986404] usb 1-2.3: new low speed USB device using ohci_hcd and address 5
[34104.093478] usb 1-2.3: configuration #1 chosen from 1 choice
[34104.100659] input: Logitech Optical USB Mouse as /class/input/input11
[34104.100748] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.0-2.3
[34124.333977] usb 1-2: USB disconnect, address 4
[34124.333985] usb 1-2.3: USB disconnect, address 5
[34126.280907] usb 3-5: USB disconnect, address 13
[34130.044238] usb 3-5: new high speed USB device using ehci_hcd and address 16
[34130.184474] usb 3-5: configuration #1 chosen from 1 choice
[34139.040859] usb 1-2: new full speed USB device using ohci_hcd and address 6
[34139.241798] usb 1-2: configuration #1 chosen from 1 choice
[34139.243714] hub 1-2:1.0: USB hub found
[34139.245658] hub 1-2:1.0: 4 ports detected
[34139.570343] usb 1-2.3: new low speed USB device using ohci_hcd and address 7
[34139.676396] usb 1-2.3: configuration #1 chosen from 1 choice
[34139.683665] input: Logitech Optical USB Mouse as /class/input/input12
[34139.683746] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.0-2.3
[34240.600946] usb 1-2: USB disconnect, address 6
[34240.600954] usb 1-2.3: USB disconnect, address 7
[34242.614227] usb 3-5: USB disconnect, address 16
[34246.145388] usb 3-5: new high speed USB device using ehci_hcd and address 18
[34246.285600] usb 3-5: configuration #1 chosen from 1 choice
fowlers@eMachines:~$ 

```

---

### Post by brokencrystal on 2008-02-15
When I plug the Zune into the front side USB port, then unplug it, then plug it into the other front side USB port, this is what I get:

```

[34658.656509] usb 3-6: new high speed USB device using ehci_hcd and address 20
[34658.797706] usb 3-6: configuration #1 chosen from 1 choice
[34689.213270] usb 3-6: USB disconnect, address 20
[34692.073220] usb 3-5: new high speed USB device using ehci_hcd and address 21
[34692.214309] usb 3-5: configuration #1 chosen from 1 choice
[34713.149789] usb 3-5: USB disconnect, address 21

```

---

### Post by brokencrystal on 2008-02-16
I found this:

[http://ubuntuforums.org/showthread.php?t=657191]("http://ubuntuforums.org/showthread.php?t=657191")

I will try it when I get home and give you an update.  It says that I may need to disable the EHCI-Controller by unchecking the Enable EHCI-Controller checkbox.

---

