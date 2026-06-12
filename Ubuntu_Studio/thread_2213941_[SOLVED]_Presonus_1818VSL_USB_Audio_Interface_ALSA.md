---
title: "[SOLVED] Presonus 1818VSL USB Audio Interface ALSA playback issues"
date: 2014-03-29
forum: Ubuntu Studio
---

### Post by forest2 on 2014-03-29
Hi, I got a new [Dell desktop computer]("http://www.dell.com/us/p/inspiron-3647-small-desktop/pd?oc=fdcwsn1391&model_id=inspiron-3647-small-desktop") two weeks ago, which I plan to use as my dedicated music-making machine. I installed Ubuntu Studio 14.04 Beta 1 on it. I've run apt-get upgrade several times since then so the software should be updated to the latest Beta 2. I have a [Presonus AudioBox 1818VSL]("https://www.presonus.com/products/AudioBox-1818VSL"), which is a usb audio interface that has worked fine with vanilla ubuntu on my laptop, but is giving me trouble with audio playback in Ubuntu Studio. I'm running everything through JACK, but I think the problem is in ALSA as I'll explain. I'm not a Linux n00b, but I don't know my way around ALSA very well, and I imagine there is an easy fix that I'm somehow overlooking.

So first of all, I can record stuff in Ardour through the AudioBox just fine. Initially, I could playback the recordings but there was a lot of crackling noises. It seemed like there were a lot of xruns, which was troubling because my JACK settings were not very aggressive (frames/period: 1024, sample rate: 44100, periods/buffer: 3) and my laptop, which has less RAM, a slower processor, and no realtime kernel can handle these settings just fine. A couple of forum posts suggested this was coming from Intel Speedstep, which was throttling down the PC and interferring with the realtime kernel. I disabled SpeedStep in the BIOS and rebooted my computer.

Upon reboot, I can still record audio through JACK/Ardour, but I cannot playback the audio, and this problem has persisted for over a week and upon several reboots. There are 18 out channels on the AudioBox. I've tried routing the sound in JACK to all of them and nothing seems to work. Running speaker-test suggested that JACK was trying play back the audio through the internal intel sound card rather than through the AudioBox even though I had selected the AudioBox as the Output Device in QJackCtl.

This is the output of /proc/asound/cards, /proc/asound/devices, and /proc/asound/modules

```

 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7e14000 irq 48
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7e10000 irq 49
 2 [VSL            ]: USB-Audio - AudioBox 1818 VSL
                      PreSonus AudioBox 1818 VSL at usb-0000:00:14.0-3, high speed

```

```

  1:        : sequencer
  2: [ 0- 3]: digital audio playback
  3: [ 0- 0]: hardware dependent
  4: [ 0]   : control
  5: [ 1- 2]: digital audio capture
  6: [ 1- 0]: digital audio playback
  7: [ 1- 0]: digital audio capture
  8: [ 1- 2]: hardware dependent
  9: [ 1]   : control
 10: [ 2- 0]: digital audio playback
 11: [ 2- 0]: digital audio capture
 12: [ 2]   : control
 13: [ 2- 0]: raw midi
 33:        : timer

```

```

 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_usb_audio

```

I tried to force ALSA to use the AudioBox in two different ways.

First, I added blacklist snd-hda-intel to /etc/modprobe.d/blacklist to try and blacklist the internal sound card (and thus leave ALSA with only the AudioBox as an option for its sounds card.) When I did this and rebooted, JACK would no longer start a session because it couldn't start ALSA.

Second, I tried following these steps [here]("https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices") so that my AudioBox would be loaded in the 0 slot rather than the internal sound card. Under that modification, my /etc/modprobe.d/alsa-base.conf file looked this:

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
#COMMENTED OUT - 3/29/2014, want usb audio interface to be primary sound device
#options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
#options snd-usb-audio index=-2

## USB Magic, part 1 - edited 3/29/2014
# from https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices
alias snd-card-0 snd-usb-audio
alias snd-card-1 snd-hda-intel
# Make the Presonus AudioBox 1818VSL appear as hw:0
options snd-usb-audio index=0

```

Again, I could not start a JACK session because it couldn't start ALSA, but there was something even stranger that happened. In the Settings menu of QJackCtl, the AudioBox is no longer an option for Output Device. If anything, it seems like the opposite should be true.

I've tried playing around with all the mixers in Audio Production > Mixers and Card Control > Audio Mixer to make sure no mixer is muted.

I'm also experiencing a strange USB problem that could be related. The computer has a usb mouse and keyboard, and they don't work on reboot about every 1 out of 2 times. So maybe there's a problem with how USB modules are being loaded and that affects the usb audio interface and thus alsa playback??

I'm really at my wits end, and imagine the solution is actually probably something stupidly obvious that I've overlooked. Any help would be really appreciated!


---UPDATED---
I tried adding blacklist snd-hda-intel to /etc/modprobe.d/blacklist.conf rather than to /etc/modprobe.d/blacklist (without the .conf) This time upon reboot, the hda-intel sound card was actually blacklisted, the AudioBox was the only soundcard available in the settings menu in QJackCtl, and I was able to start a jack sessionw it selected, but I still could not hear any audio playback.

I'm attaching a screenshot from patchage and from the QJackCtl settings menu to see my setup. Also, the output of dmesg looks like this:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-12-lowlatency (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu1) ) #32-Ubuntu SMP PREEMPT Fri Feb 21 18:12:35 UTC 2014 (Ubuntu 3.13.0-12.32-lowlatency 3.13.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000ca700fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca701000-0x00000000ca707fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca708000-0x00000000cb0a0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cb0a1000-0x00000000cb421fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cb422000-0x00000000db177fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db178000-0x00000000db201fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000db202000-0x00000000db364fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db365000-0x00000000db88dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000db88e000-0x00000000dbffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dbfff000-0x00000000dbffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dd000000-0x00000000df1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 3647/02YRK5       , BIOS A02 12/03/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x21fe00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7E00000000 write-back
[    0.000000]   1 base 0200000000 mask 7FE0000000 write-back
[    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 00DE000000 mask 7FFE000000 uncachable
[    0.000000]   4 base 00DD000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 021FE00000 mask 7FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3552MB, range: 32MB, type UC
[    0.000000] reg 4, base: 3536MB, range: 16MB, type UC
[    0.000000] reg 5, base: 8702MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8142M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3536MB, range: 16MB, type UC
[    0.000000] reg 4, base: 3552MB, range: 32MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8702MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xdd000000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000fdb40-0x000fdb4f] mapped at [c00fdb40]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b85000, 0x01b85fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35b8c000-0x36dbdfff]
[    0.000000] ACPI: RSDP 000f0490 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT db473088 00008C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP db47f750 00010C (v05 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT db4731a8 00C5A5 (v02 DELL    WN09    00000000 INTL 20120711)
[    0.000000] ACPI: FACS db88c080 000040
[    0.000000] ACPI: APIC db47f860 000072 (v03 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT db47f8d8 000044 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: ASF! db47f920 0000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: LPIT db47f9c8 00005C (v01 DELL    WN09    00000000 AMI. 00000005)
[    0.000000] ACPI: SLIC db47fa28 000176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: SSDT db47fba0 000AD8 (v01  PmRef    CpuPm 00003000 INTL 20120711)
[    0.000000] ACPI: MCFG db480678 00003C (v01 DELL    WN09    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET db4806b8 000038 (v01 DELL    WN09    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT db4806f0 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT db480a60 003406 (v01 SaSsdt  SaSsdt  00003000 INTL 20091112)
[    0.000000] ACPI: MSDM db483e68 000055 (v03 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: DMAR db483ec0 0000B8 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 7810MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b86000, 0x01b86fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x1fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xca700fff]
[    0.000000]   node   0: [mem 0xca708000-0xcb0a0fff]
[    0.000000]   node   0: [mem 0xcb422000-0xdb177fff]
[    0.000000]   node   0: [mem 0xdb202000-0xdb364fff]
[    0.000000]   node   0: [mem 0xdbfff000-0xdbffffff]
[    0.000000]   node   0: [mem 0x00000000-0x1fdfffff]
[    0.000000] On node 0 totalpages: 2075888
[    0.000000] free_area_init_node: node 0, pgdat c1995200, node_mem_map f178c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 15621 pages used for memmap
[    0.000000]   HighMem zone: 1847638 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2074104
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-12-lowlatency root=UUID=2fff13ba-eb8b-4aab-bcb0-6752fa112124 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 17821688 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0021fe00)
[    0.000000] Memory: 8184908K/8303552K available (6523K kernel code, 635K rwdata, 2752K rodata, 864K init, 920K bss, 118644K reserved, 7390552K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19b0000 - 0xc1a88000   ( 864 kB)
[    0.000000]       .data : 0xc165f068 - 0xc19afc80   (3395 kB)
[    0.000000]       .text : 0xc1000000 - 0xc165f068   (6524 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Preemptible hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     Dump stacks of tasks blocking RCU-preempt GP.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.001000] tsc: Detected 2793.266 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5586.53 BogoMIPS (lpj=2793266)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000020] Security Framework initialized
[    0.000031] AppArmor: AppArmor initialized
[    0.000032] Yama: becoming mindful.
[    0.000060] Mount-cache hash table entries: 512
[    0.000197] Initializing cgroup subsys memory
[    0.000200] Initializing cgroup subsys devices
[    0.000201] Initializing cgroup subsys freezer
[    0.000202] Initializing cgroup subsys blkio
[    0.000203] Initializing cgroup subsys perf_event
[    0.000205] Initializing cgroup subsys hugetlb
[    0.000224] CPU: Physical Processor ID: 0
[    0.000224] CPU: Processor Core ID: 0
[    0.000228] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000228] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001873] mce: CPU supports 9 MCE banks
[    0.001885] CPU0: Thermal monitoring enabled (TM1)
[    0.001897] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.001897] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.001897] tlb_flushall_shift: 6
[    0.002153] Freeing SMP alternatives memory: 24K (c1a88000 - c1a8e000)
[    0.002740] ACPI: Core revision 20131115
[    0.008598] ACPI: All ACPI Tables successfully acquired
[    0.009027] ftrace: allocating 27724 entries in 55 pages
[    0.018034] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.018438] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.028451] smpboot: CPU0: Intel(R) Core(TM) i5-4440S CPU @ 2.80GHz (fam: 06, model: 3c, stepping: 03)
[    0.028456] TSC deadline timer enabled
[    0.028537] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.028543] ... version:                3
[    0.028544] ... bit width:              48
[    0.028545] ... generic registers:      8
[    0.028546] ... value mask:             0000ffffffffffff
[    0.028547] ... max period:             0000ffffffffffff
[    0.028548] ... fixed-purpose events:   3
[    0.028548] ... event mask:             00000007000000ff
[    0.037571] CPU 1 irqstacks, hard=f7522000 soft=f7524000
[    0.037573] x86: Booting SMP configuration:
[    0.047943] Initializing CPU#1
[    0.052455] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.037574] .... node  #0, CPUs:      #1
[    0.054475] CPU 2 irqstacks, hard=f75a6000 soft=f75a8000
[    0.064844] Initializing CPU#2
[    0.054476]  #2
[    0.071461] CPU 3 irqstacks, hard=f75f4000 soft=f75f6000
[    0.081830] Initializing CPU#3
[    0.071463]  #3
[    0.086414] x86: Booted up 1 node, 4 CPUs
[    0.086416] smpboot: Total of 4 processors activated (22346.12 BogoMIPS)
[    0.089664] devtmpfs: initialized
[    0.089798] EVM: security.selinux
[    0.089799] EVM: security.SMACK64
[    0.089799] EVM: security.ima
[    0.089800] EVM: security.capability
[    0.089865] PM: Registering ACPI NVS region [mem 0xca701000-0xca707fff] (28672 bytes)
[    0.089867] PM: Registering ACPI NVS region [mem 0xdb365000-0xdb88dfff] (5410816 bytes)
[    0.090486] pinctrl core: initialized pinctrl subsystem
[    0.090537] regulator-dummy: no parameters
[    0.090564] RTC time: 18:07:12, date: 03/29/14
[    0.090590] NET: Registered protocol family 16
[    0.090687] EISA bus registered
[    0.090688] cpuidle: using governor ladder
[    0.090689] cpuidle: using governor menu
[    0.090749] ACPI: bus type PCI registered
[    0.090750] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.090794] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.090796] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.090797] PCI: Using MMCONFIG for extended config space
[    0.090798] PCI: Using configuration type 1 for base access
[    0.091495] bio: create slab <bio-0> at 0
[    0.091597] ACPI: Added _OSI(Module Device)
[    0.091599] ACPI: Added _OSI(Processor Device)
[    0.091600] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.091601] ACPI: Added _OSI(Processor Aggregator Device)
[    0.095429] ACPI: Executed 1 blocks of module-level executable AML code
[    0.097557] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.098139] ACPI: SSDT db1f7c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
[    0.098603] ACPI: Dynamic OEM Table Load:
[    0.098605] ACPI: SSDT   (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
[    0.103725] ACPI: SSDT db1f6d98 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
[    0.104178] ACPI: Dynamic OEM Table Load:
[    0.104180] ACPI: SSDT   (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
[    0.243772] ACPI: Interpreter enabled
[    0.243781] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.243785] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.243797] ACPI: (supports S0 S3 S4 S5)
[    0.243798] ACPI: Using IOAPIC for interrupt routing
[    0.243818] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.243968] ACPI: No dock devices found.
[    0.249969] ACPI: Power Resource [FN00] (off)
[    0.250025] ACPI: Power Resource [FN01] (off)
[    0.250080] ACPI: Power Resource [FN02] (off)
[    0.250134] ACPI: Power Resource [FN03] (off)
[    0.250188] ACPI: Power Resource [FN04] (off)
[    0.250837] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.250842] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.251277] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.251698] PCI host bridge to bus 0000:00
[    0.251701] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.251702] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.251704] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.251705] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.251706] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.251708] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.251709] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.251710] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.251711] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.251713] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.251714] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff]
[    0.251721] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.251792] pci 0000:00:02.0: [8086:0412] type 00 class 0x030000
[    0.251802] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.251808] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.251812] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.251875] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.251882] pci 0000:00:03.0: reg 0x10: [mem 0xf7e14000-0xf7e17fff 64bit]
[    0.251971] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.251990] pci 0000:00:14.0: reg 0x10: [mem 0xf7e00000-0xf7e0ffff 64bit]
[    0.252047] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.252083] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.252110] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.252129] pci 0000:00:16.0: reg 0x10: [mem 0xf7e1e000-0xf7e1e00f 64bit]
[    0.252190] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.252256] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.252276] pci 0000:00:1a.0: reg 0x10: [mem 0xf7e1c000-0xf7e1c3ff]
[    0.252363] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.252412] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.252440] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.252455] pci 0000:00:1b.0: reg 0x10: [mem 0xf7e10000-0xf7e13fff 64bit]
[    0.252517] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.252554] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.252578] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.252640] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.252679] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.252702] pci 0000:00:1c.3: [8086:8c16] type 01 class 0x060400
[    0.252764] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.252802] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.252826] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    0.252891] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.252930] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.252962] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.252983] pci 0000:00:1d.0: reg 0x10: [mem 0xf7e1b000-0xf7e1b3ff]
[    0.253066] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.253113] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.253139] pci 0000:00:1f.0: [8086:8c5c] type 00 class 0x060100
[    0.253290] pci 0000:00:1f.2: [8086:8c02] type 00 class 0x010601
[    0.253306] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.253313] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.253321] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.253328] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.253335] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.253344] pci 0000:00:1f.2: reg 0x24: [mem 0xf7e1a000-0xf7e1a7ff]
[    0.253382] pci 0000:00:1f.2: PME# supported from D3hot
[    0.253436] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.253451] pci 0000:00:1f.3: reg 0x10: [mem 0xf7e19000-0xf7e190ff 64bit]
[    0.253471] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.253575] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.253663] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.253680] pci 0000:02:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.253708] pci 0000:02:00.0: reg 0x18: [mem 0xf7d00000-0xf7d00fff 64bit]
[    0.253727] pci 0000:02:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.253801] pci 0000:02:00.0: supports D1 D2
[    0.253803] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.253835] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.255386] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.255390] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.255394] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.255399] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.255489] pci 0000:03:00.0: [168c:0036] type 00 class 0x028000
[    0.255523] pci 0000:03:00.0: reg 0x10: [mem 0xf7c00000-0xf7c7ffff 64bit]
[    0.255604] pci 0000:03:00.0: reg 0x30: [mem 0xf7c80000-0xf7c8ffff pref]
[    0.255690] pci 0000:03:00.0: supports D1 D2
[    0.255691] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.255730] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.258974] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.258979] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.259005] pci_bus 0000:00: on NUMA node 0
[    0.259597] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.259636] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.259675] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.259712] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.259749] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.259786] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.259824] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.259861] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.260207] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.260212] ACPI: \_SB_.PCI0: notify handler is installed
[    0.260268] Found 1 acpi root devices
[    0.260330] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.260333] vgaarb: loaded
[    0.260334] vgaarb: bridge control possible 0000:00:02.0
[    0.260456] SCSI subsystem initialized
[    0.260481] libata version 3.00 loaded.
[    0.260493] ACPI: bus type USB registered
[    0.260504] usbcore: registered new interface driver usbfs
[    0.260509] usbcore: registered new interface driver hub
[    0.260522] usbcore: registered new device driver usb
[    0.260588] PCI: Using ACPI for IRQ routing
[    0.261908] PCI: pci_cache_line_size set to 64 bytes
[    0.261956] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.261957] e820: reserve RAM buffer [mem 0xca701000-0xcbffffff]
[    0.261959] e820: reserve RAM buffer [mem 0xcb0a1000-0xcbffffff]
[    0.261960] e820: reserve RAM buffer [mem 0xdb178000-0xdbffffff]
[    0.261961] e820: reserve RAM buffer [mem 0xdb365000-0xdbffffff]
[    0.261963] e820: reserve RAM buffer [mem 0x21fe00000-0x21fffffff]
[    0.262017] NetLabel: Initializing
[    0.262018] NetLabel:  domain hash size = 128
[    0.262019] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.262027] NetLabel:  unlabeled traffic allowed by default
[    0.262102] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.262106] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.264136] Switched to clocksource hpet
[    0.268748] AppArmor: AppArmor Filesystem Enabled
[    0.268759] pnp: PnP ACPI init
[    0.268766] ACPI: bus type PNP registered
[    0.268811] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.268814] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.268821] pnp 00:01: [dma 4]
[    0.268832] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.268845] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.268903] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.268934] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.269010] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.269012] system 00:05: [io  0xffff] has been reserved
[    0.269013] system 00:05: [io  0xffff] has been reserved
[    0.269015] system 00:05: [io  0xffff] has been reserved
[    0.269016] system 00:05: [io  0x1c00-0x1cfe] has been reserved
[    0.269018] system 00:05: [io  0x1d00-0x1dfe] has been reserved
[    0.269019] system 00:05: [io  0x1e00-0x1efe] has been reserved
[    0.269021] system 00:05: [io  0x1f00-0x1ffe] has been reserved
[    0.269022] system 00:05: [io  0x1800-0x18fe] could not be reserved
[    0.269024] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.269026] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269042] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.269072] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.269074] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.269161] system 00:08: [io  0x0a00-0x0a1f] has been reserved
[    0.269162] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.269163] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.269165] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269210] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.269211] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269520] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.269522] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.269524] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.269525] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.269527] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.269529] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.269530] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.269532] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.269533] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.269535] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.269536] system 00:0a: [mem 0xf7fdf000-0xf7fdffff] has been reserved
[    0.269538] system 00:0a: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.269540] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269700] pnp: PnP ACPI: found 11 devices
[    0.269701] ACPI: bus type PNP unregistered
[    0.269703] PnPBIOS: Disabled by ACPI PNP
[    0.305647] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.305650] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.305652] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    0.305667] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.305669] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.305670] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.305674] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdf200000-0xdf3fffff]
[    0.305677] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.305680] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.305681] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.305684] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.305689] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf3fffff]
[    0.305693] pci 0000:00:1c.0:   bridge window [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.305698] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.305701] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.305706] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.305710] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.305715] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.305720] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.305728] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.305729] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.305731] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.305732] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.305733] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.305734] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.305736] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.305737] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.305738] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.305740] pci_bus 0000:00: resource 13 [mem 0xdf200000-0xfeafffff]
[    0.305741] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.305742] pci_bus 0000:01: resource 1 [mem 0xdf200000-0xdf3fffff]
[    0.305744] pci_bus 0000:01: resource 2 [mem 0xdf400000-0xdf5fffff 64bit pref]
[    0.305745] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.305747] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.305748] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.305749] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.305768] NET: Registered protocol family 2
[    0.305865] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.305873] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.305882] TCP: Hash tables configured (established 8192 bind 8192)
[    0.305890] TCP: reno registered
[    0.305892] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.305895] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.305926] NET: Registered protocol family 1
[    0.305934] pci 0000:00:02.0: Boot video device
[    0.336313] PCI: CLS 64 bytes, default 64
[    0.336344] Trying to unpack rootfs image as initramfs...
[    0.596153] Freeing initrd memory: 18632K (f5b8c000 - f6dbe000)
[    0.596159] dmar: Host address width 39
[    0.596160] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.596172] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.596173] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.596177] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    0.596178] dmar: RMRR base: 0x000000dbe9b000 end: 0x000000dbea9fff
[    0.596180] dmar: RMRR base: 0x000000dd000000 end: 0x000000df1fffff
[    0.596342] Scanning for low memory corruption every 60 seconds
[    0.596527] Initialise system trusted keyring
[    0.596560] audit: initializing netlink socket (disabled)
[    0.596568] type=2000 audit(1396116432.449:1): initialized
[    0.609941] bounce pool size: 64 pages
[    0.609951] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.611005] zbud: loaded
[    0.611047] VFS: Disk quotas dquot_6.5.2
[    0.611077] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.611346] fuse init (API version 7.22)
[    0.611396] msgmni has been set to 1587
[    0.611436] Key type big_key registered
[    0.611815] Key type asymmetric registered
[    0.611816] Asymmetric key parser 'x509' registered
[    0.611834] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.611861] io scheduler noop registered
[    0.611862] io scheduler deadline registered (default)
[    0.611878] io scheduler cfq registered
[    0.612029] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.612150] pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X
[    0.612255] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.612319] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.612323] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.612338] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.612339] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.612343] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.612356] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.612357] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.612361] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.612370] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.612402] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 8c10 ss_vid 1028 ss_did 611
[    0.612423] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.612426] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.612451] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.612452] vesafb: scrolling: redraw
[    0.612453] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.612864] vesafb: framebuffer at 0xe0000000, mapped to 0xf8480000, using 8128k, total 8128k
[    0.765094] Console: switching to colour frame buffer device 240x67
[    0.916179] fb0: VESA VGA frame buffer device
[    0.916191] intel_idle: MWAIT substates: 0x42120
[    0.916192] intel_idle: v0.4 model 0x3C
[    0.916193] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.916270] ipmi message handler version 39.2
[    0.916275] IPMI System Interface driver.
[    0.916289] ipmi_si: Adding default-specified kcs state machine
[    0.916291] ipmi_si: Trying default-specified kcs state machine at i/o address 0xca2, slave address 0x0, irq 0
[    0.916294] ipmi_si: Interface detection failed
[    0.929941] ipmi_si: Adding default-specified smic state machine
[    0.929942] ipmi_si: Trying default-specified smic state machine at i/o address 0xca9, slave address 0x0, irq 0
[    0.929945] ipmi_si: Interface detection failed
[    0.941977] ipmi_si: Adding default-specified bt state machine
[    0.941980] ipmi_si: Trying default-specified bt state machine at i/o address 0xe4, slave address 0x0, irq 0
[    0.941984] ipmi_si: Interface detection failed
[    0.954000] ipmi_si: Unable to find any System Interface(s)
[    0.954955] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.954959] ACPI: Power Button [PWRB]
[    0.954991] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.954993] ACPI: Power Button [PWRF]
[    0.955034] ACPI: Fan [FAN0] (off)
[    0.955050] ACPI: Fan [FAN1] (off)
[    0.955066] ACPI: Fan [FAN2] (off)
[    0.955081] ACPI: Fan [FAN3] (off)
[    0.955096] ACPI: Fan [FAN4] (off)
[    0.955371] thermal LNXTHERM:00: registered as thermal_zone0
[    0.955373] ACPI: Thermal Zone [TZ00] (28 C)
[    0.955512] thermal LNXTHERM:01: registered as thermal_zone1
[    0.955513] ACPI: Thermal Zone [TZ01] (30 C)
[    0.955532] GHES: HEST is not enabled!
[    0.955553] isapnp: Scanning for PnP cards...
[    0.955607] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.956654] Linux agpgart interface v0.103
[    0.957581] brd: module loaded
[    0.958051] loop: module loaded
[    0.958287] libphy: Fixed MDIO Bus: probed
[    0.958345] tun: Universal TUN/TAP device driver, 1.6
[    0.958346] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.958375] PPP generic driver version 2.4.2
[    0.958404] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.958406] ehci-pci: EHCI PCI platform driver
[    0.958486] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.958490] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.958502] ehci-pci 0000:00:1a.0: debug port 2
[    0.962408] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.962420] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7e1c000
[    0.967990] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.968018] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.968019] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.968021] usb usb1: Product: EHCI Host Controller
[    0.968022] usb usb1: Manufacturer: Linux 3.13.0-12-lowlatency ehci_hcd
[    0.968023] usb usb1: SerialNumber: 0000:00:1a.0
[    0.968127] hub 1-0:1.0: USB hub found
[    0.968131] hub 1-0:1.0: 2 ports detected
[    0.968270] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.968273] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.968284] ehci-pci 0000:00:1d.0: debug port 2
[    0.972185] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.972196] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7e1b000
[    0.978002] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.978028] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.978030] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.978031] usb usb2: Product: EHCI Host Controller
[    0.978032] usb usb2: Manufacturer: Linux 3.13.0-12-lowlatency ehci_hcd
[    0.978033] usb usb2: SerialNumber: 0000:00:1d.0
[    0.978118] hub 2-0:1.0: USB hub found
[    0.978123] hub 2-0:1.0: 2 ports detected
[    0.978192] ehci-platform: EHCI generic platform driver
[    0.978197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.978198] ohci-pci: OHCI PCI platform driver
[    0.978204] ohci-platform: OHCI generic platform driver
[    0.978208] uhci_hcd: USB Universal Host Controller Interface driver
[    0.978285] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.978288] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.978371] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.978386] xhci_hcd 0000:00:14.0: irq 43 for MSI/MSI-X
[    0.978434] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.978435] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.978436] usb usb3: Product: xHCI Host Controller
[    0.978438] usb usb3: Manufacturer: Linux 3.13.0-12-lowlatency xhci_hcd
[    0.978439] usb usb3: SerialNumber: 0000:00:14.0
[    0.978520] hub 3-0:1.0: USB hub found
[    0.978530] hub 3-0:1.0: 10 ports detected
[    0.980332] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.980334] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.980361] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.980362] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.980363] usb usb4: Product: xHCI Host Controller
[    0.980365] usb usb4: Manufacturer: Linux 3.13.0-12-lowlatency xhci_hcd
[    0.980366] usb usb4: SerialNumber: 0000:00:14.0
[    0.980449] hub 4-0:1.0: USB hub found
[    0.980453] hub 4-0:1.0: 2 ports detected
[    0.994092] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.994491] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.994511] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.994599] mousedev: PS/2 mouse device common for all mice
[    0.994739] rtc_cmos 00:06: RTC can wake from S4
[    0.994860] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.994884] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.994925] device-mapper: uevent: version 1.0.3
[    0.994986] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.994997] platform eisa.0: Probing EISA bus 0
[    0.994998] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.995000] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.995001] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.995002] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.995003] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.995005] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.995006] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.995007] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.995013] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.995015] platform eisa.0: EISA: Detected 0 cards
[    0.995018] cpufreq-nforce2: No nForce2 chipset.
[    0.995020] ledtrig-cpu: registered to indicate activity on CPUs
[    0.995100] TCP: cubic registered
[    0.995153] NET: Registered protocol family 10
[    0.995278] NET: Registered protocol family 17
[    0.995285] Key type dns_resolver registered
[    0.995437] Using IPI No-Shortcut mode
[    0.995531] Loading compiled-in X.509 certificates
[    0.997951] Loaded X.509 cert 'Magrathea: Glacier signing key: cb0857ce87b3dd9d908ee65add03a255a28a7264'
[    0.997957] registered taskstats version 1
[    0.999967] Key type trusted registered
[    1.001453] Key type encrypted registered
[    1.002773] AppArmor: AppArmor sha1 policy hashing enabled
[    1.002775] IMA: No TPM chip found, activating TPM-bypass!
[    1.003114]   Magic number: 6:136:141
[    1.003121] block ram6: hash matches
[    1.003142] acpi device:12: hash matches
[    1.003179] rtc_cmos 00:06: setting system clock to 2014-03-29 18:07:13 UTC (1396116433)
[    1.003231] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.003233] EDD information not available.
[    1.003265] PM: Hibernation image not present or could not be loaded.
[    1.268672] isapnp: No Plug & Play device found
[    1.268877] Freeing unused kernel memory: 864K (c19b0000 - c1a88000)
[    1.268928] Write protecting the kernel text: 6528k
[    1.268990] Write protecting the kernel read-only data: 2756k
[    1.268990] NX-protecting the kernel data: 5760k
[    1.270379] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.278329] systemd-udevd[107]: starting version 204
[    1.297479] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.299584] ahci 0000:00:1f.2: version 3.0
[    1.299685] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.299724] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3 impl SATA mode
[    1.299726] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems 
[    1.301372] r8169 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.301533] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xf842a000, c8:1f:66:3e:59:7a, XID 0c000800 IRQ 45
[    1.301536] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.302365] scsi0 : ahci
[    1.302517] scsi1 : ahci
[    1.302645] scsi2 : ahci
[    1.302787] scsi3 : ahci
[    1.302821] ata1: SATA max UDMA/133 abar m2048@0xf7e1a000 port 0xf7e1a100 irq 44
[    1.302823] ata2: SATA max UDMA/133 abar m2048@0xf7e1a000 port 0xf7e1a180 irq 44
[    1.302824] ata3: DUMMY
[    1.302826] ata4: DUMMY
[    1.385015] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.385018] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.385275] hub 1-1:1.0: USB hub found
[    1.385379] hub 1-1:1.0: 4 ports detected
[    1.487697] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.598792] tsc: Refined TSC clocksource calibration: 2793.531 MHz
[    1.602276] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.602279] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.602520] hub 2-1:1.0: USB hub found
[    1.602601] hub 2-1:1.0: 6 ports detected
[    1.607814] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.607834] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.608804] ata1.00: ATA-8: TOSHIBA DT01ACA100, MS2OA7S0, max UDMA/133
[    1.608807] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.609839] ata1.00: configured for UDMA/133
[    1.610010] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA DT01ACA1 MS2O PQ: 0 ANSI: 5
[    1.610118] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.610121] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.610141] sd 0:0:0:0: [sda] Write Protect is off
[    1.610143] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.610145] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.610152] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.611277] ata2.00: ATAPI: PLDS DVD+/-RW DH-16AES, 3D11, max UDMA/100
[    1.612204] ata2.00: configured for UDMA/100
[    1.614382] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DH-16AES 3D11 PQ: 0 ANSI: 5
[    1.618099] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.618102] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.618237] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.618283] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.619772]  sda: sda1 sda2 < sda5 >
[    1.620271] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.757014] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.768655] usb 3-3: New USB device found, idVendor=194f, idProduct=0103
[    1.768658] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.768659] usb 3-3: Product: AudioBox 1818 VSL 
[    1.768661] usb 3-3: Manufacturer: PreSonus
[    1.768662] usb 3-3: SerialNumber: 2209
[    1.821124] random: lvm urandom read with 55 bits of entropy available
[    1.867079] bio: create slab <bio-1> at 1
[    1.923212] usb 3-5: new low-speed USB device number 3 using xhci_hcd
[    1.940896] usb 3-5: New USB device found, idVendor=413c, idProduct=2111
[    1.940899] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.940901] usb 3-5: Product: Dell USB Wired Entry Keyboard
[    1.940902] usb 3-5: Manufacturer: DELL
[    1.941012] usb 3-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.941016] usb 3-5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.946801] hidraw: raw HID events driver (C) Jiri Kosina
[    1.956012] usbcore: registered new interface driver usbhid
[    1.956015] usbhid: USB HID core driver
[    1.959018] input: DELL Dell USB Wired Entry Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.0/input/input4
[    1.959087] hid-generic 0003:413C:2111.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL Dell USB Wired Entry Keyboard] on usb-0000:00:14.0-5/input0
[    1.960092] input: DELL Dell USB Wired Entry Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.1/input/input5
[    1.960176] hid-generic 0003:413C:2111.0002: input,hidraw1: USB HID v1.10 Device [DELL Dell USB Wired Entry Keyboard] on usb-0000:00:14.0-5/input1
[    2.094371] usb 3-6: new low-speed USB device number 4 using xhci_hcd
[    2.109509] usb 3-6: New USB device found, idVendor=0461, idProduct=4e22
[    2.109512] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.109514] usb 3-6: Product: USB Optical Mouse
[    2.109515] usb 3-6: Manufacturer: PixArt
[    2.109630] usb 3-6: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.111475] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input6
[    2.111684] hid-generic 0003:0461:4E22.0003: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:14.0-6/input0
[    2.264619] usb 3-10: new full-speed USB device number 5 using xhci_hcd
[    2.277005] usb 3-10: New USB device found, idVendor=0cf3, idProduct=0036
[    2.277008] usb 3-10: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.278676] random: nonblocking pool is initialized
[    2.302793] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    2.600114] Switched to clocksource tsc
[    9.905661] Adding 8302588k swap on /dev/mapper/ubuntu--studio--vg-swap_1.  Priority:-1 extents:1 across:8302588k FS
[    9.992777] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.019359] systemd-udevd[304]: starting version 204
[   10.222378] lp: driver loaded but no devices found
[   10.255141] mei_me 0000:00:16.0: irq 46 for MSI/MSI-X
[   10.257055] [drm] Initialized drm 1.1.0 20060810
[   10.270171] Bluetooth: Core ver 2.17
[   10.270183] NET: Registered protocol family 31
[   10.270184] Bluetooth: HCI device and connection manager initialized
[   10.270189] Bluetooth: HCI socket layer initialized
[   10.270190] Bluetooth: L2CAP socket layer initialized
[   10.270193] Bluetooth: SCO socket layer initialized
[   10.274898] usbcore: registered new interface driver btusb
[   10.288611] [drm] Memory usable by graphics device = 2048M
[   10.288614] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[   10.288616] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   10.288630] Console: switching to colour dummy device 80x25
[   10.296183] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   10.296191] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   10.296192] [drm] Driver supports precise vblank timestamp query.
[   10.296247] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.304712] cfg80211: Calling CRDA to update world regulatory domain
[   10.311492] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x16
[   10.325364] fbcon: inteldrmfb (fb0) is primary device
[   10.351783] ath: phy0: Set BT/WLAN RX diversity capability
[   10.353525] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.360739] ath: phy0: Enable LNA combining
[   10.361987] ath: phy0: ASPM enabled: 0x43
[   10.361987] ath: EEPROM regdomain: 0x60
[   10.361988] ath: EEPROM indicates we should expect a direct regpair map
[   10.361989] ath: Country alpha2 being used: 00
[   10.361989] ath: Regpair used: 0x60
[   10.366236] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.366453] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xf8780000, irq=16
[   10.454392] Console: switching to colour frame buffer device 240x67
[   10.459713] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.459713] i915 0000:00:02.0: registered panic notifier
[   10.467131] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.467427] acpi device:58: registered as cooling_device9
[   10.467475] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   10.467528] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.467624] HDA driver get symbol successfully from i915 module
[   10.467645] snd_hda_intel 0000:00:03.0: irq 48 for MSI/MSI-X
[   10.467748] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   10.477215] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[   10.481547] SKU: Nid=0x1d sku_cfg=0x40400001
[   10.481548] SKU: port_connectivity=0x1
[   10.481549] SKU: enable_pcbeep=0x0
[   10.481550] SKU: check_sum=0x00000000
[   10.481551] SKU: customization=0x00000000
[   10.481552] SKU: external_amp=0x0
[   10.481553] SKU: platform_type=0x0
[   10.481553] SKU: swap=0x0
[   10.481554] SKU: override=0x1
[   10.481801] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   10.481802]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.481803]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   10.481804]    mono: mono_out=0x0
[   10.481805]    inputs:
[   10.481806]      Rear Mic=0x19
[   10.481807]      Front Mic=0x18
[   10.481808]      Line=0x1a
[   10.481809] realtek: No valid SSID, checking pincfg 0x40400001 for NID 0x1d
[   10.481810] realtek: Enabling init ASM_ID=0x0001 CODEC_ID=10ec0662
[   10.489839] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[   10.490195] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[   10.491910] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[   10.491951] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   10.491984] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   10.492424] ACPI Warning: 0x00001828-0x0000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   10.492428] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.492432] ACPI Warning: 0x00001c30-0x00001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   10.492434] ACPI Warning: 0x00001c30-0x00001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   10.492436] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.492437] ACPI Warning: 0x00001c00-0x00001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   10.492439] ACPI Warning: 0x00001c00-0x00001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   10.492441] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.492442] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.496105] platform microcode: Direct firmware load failed with error -2
[   10.496107] platform microcode: Falling back to user helper
[   10.521472] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x16
[   10.521482] platform microcode: Direct firmware load failed with error -2
[   10.521484] platform microcode: Falling back to user helper
[   10.521896] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x16
[   10.521904] platform microcode: Direct firmware load failed with error -2
[   10.521906] platform microcode: Falling back to user helper
[   10.522180] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x16
[   10.522189] platform microcode: Direct firmware load failed with error -2
[   10.522191] platform microcode: Falling back to user helper
[   10.522799] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.540958] type=1400 audit(1396116443.024:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=405 comm="apparmor_parser"
[   10.540963] type=1400 audit(1396116443.024:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=405 comm="apparmor_parser"
[   10.540966] type=1400 audit(1396116443.024:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
[   10.541287] type=1400 audit(1396116443.024:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=405 comm="apparmor_parser"
[   10.541291] type=1400 audit(1396116443.024:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
[   10.541452] type=1400 audit(1396116443.025:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
[   10.542343] type=1400 audit(1396116443.025:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=404 comm="apparmor_parser"
[   10.542348] type=1400 audit(1396116443.025:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=404 comm="apparmor_parser"
[   10.542351] type=1400 audit(1396116443.025:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=404 comm="apparmor_parser"
[   10.542680] type=1400 audit(1396116443.026:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=404 comm="apparmor_parser"
[   10.566097] cfg80211: World regulatory domain updated:
[   10.566099] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.566101] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.566102] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.566103] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.566104] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.566105] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.915110] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   11.062913] usbcore: registered new interface driver snd-usb-audio
[   11.117484] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   11.158903] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   11.445643] init: failsafe main process (591) killed by TERM signal
[   11.863108] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   12.310782] init: cups main process (685) killed by HUP signal
[   12.310790] init: cups main process ended, respawning
[   13.105219] Bluetooth: RFCOMM TTY layer initialized
[   13.105226] Bluetooth: RFCOMM socket layer initialized
[   13.105230] Bluetooth: RFCOMM ver 1.11
[   13.141657] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.141659] Bluetooth: BNEP filters: protocol multicast
[   13.141664] Bluetooth: BNEP socket layer initialized
[   13.508034] Bluetooth: Error in firmware loading err = -110,len = 448, size = 1906
[   13.508039] Bluetooth: Loading sysconfig file failed
[   13.508045] ath3k: probe of 3-10:1.0 failed with error -110
[   13.508071] usbcore: registered new interface driver ath3k
[   14.592405] r8169 0000:02:00.0 eth0: link down
[   14.592448] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.592699] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.606494] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.609607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.924873] init: samba-ad-dc main process (1289) terminated with status 1
[   15.971177] wlan0: authenticate with c8:d7:19:3d:cb:eb
[   15.987998] wlan0: send auth to c8:d7:19:3d:cb:eb (try 1/3)
[   15.997582] wlan0: authenticated
[   15.997970] wlan0: associate with c8:d7:19:3d:cb:eb (try 1/3)
[   16.001818] wlan0: RX AssocResp from c8:d7:19:3d:cb:eb (capab=0x411 status=0 aid=2)
[   16.001864] wlan0: associated
[   16.001878] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.227511] audit_printk_skb: 141 callbacks suppressed
[   42.227514] type=1400 audit(1396116474.665:59): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2058 comm="apparmor_parser"
[   42.227519] type=1400 audit(1396116474.665:60): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2058 comm="apparmor_parser"
[   42.227843] type=1400 audit(1396116474.665:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2058 comm="apparmor_parser"

```

---

### Post by forest2 on 2014-03-29
Well, I solved my playback issues. In Audio Product > Mixers and Card Control > Audio Mixer, in the AudioBox 1818VSL (Alsa mixer) tab, under "Switches," I needed to enable both AudioBox 1818 VSL Clock Selector Playback S and AudioBox 1818 VSL Clock Selector Playback S 1 (1). As I expected, a stupid fix.

I think my usb woes may be [related to xhci_hcd module]("http://www.pcl-developers.org/xhci-hcd-I-hate-you-USB-3-0-and-Primesense-Asus-Xtion-td5707949.html"), which is loading the AudioBox as a usb 3.0 device, and may explain why the usb keyboard and mouse ocassionally don't work on reboot.

The audio still has crackling noises, but this is definitely progress and the crackling issues / xruns are almost certainly related to cpu frequency throttling. Hope this is helpful to some future internet traveler.

---

### Post by forest2 on 2014-03-30
For others with the PreSonus AudioBox 1818VSL, there is a problem with it being treated as a USB 3.0 device and that is apparently the source of the crackling noise. The kernel comes with two drivers xchi-hda and ehci-hda for usb 3.0 and usb 2.0, respectively. Unfortunately, they are baked in, and to fix the crackling noise, you have to recompile the kernel with the drivers as modules, and then blacklist the xhci-hda driver so it won't be loaded on startup. Here's the details:

[http://www.pcl-developers.org/xhci-hcd-I-hate-you-USB-3-0-and-Primesense-Asus-Xtion-td5707949.html](http://www.pcl-developers.org/xhci-hcd-I-hate-you-USB-3-0-and-Primesense-Asus-Xtion-td5707949.html)

I've been tryign to compile my kernel with make-kpkg, but keep running into errors.

I've created a separate forum thread for these [compile errors]("http://ubuntuforums.org/showthread.php?t=2214154").

---

### Post by jejeman on 2014-03-31
Since the problem is because of the speciffic USB audio device, it is better to change the topic of the thread to include the device name. Better for search, for others haveing similar problem.
Just edit your first post and change the title.

---

### Post by forest2 on 2014-03-31
> **jejeman said:**
> Since the problem is because of the speciffic USB audio device, it is better to change the topic of the thread to include the device name. Better for search, for others haveing similar problem.
Just edit your first post and change the title.

The original problem (no audio playback) was because of a mixer not being turned on correctly and had nothing to do with the specific audio interface. The crackling noise is specific to the Presonus so I've edited the title to indicate this.

---

