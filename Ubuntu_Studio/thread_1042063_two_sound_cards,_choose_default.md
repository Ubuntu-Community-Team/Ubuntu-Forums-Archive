---
title: "two sound cards, choose default"
date: 2009-01-17
forum: Ubuntu Studio
---

### Post by dontiego on 2009-01-17
Hello all.

I've read quite a lot of posts about setting the default soundcard in .asoundconf. I can't seem to get it right, though.

```
$ asoundconf list
Names of available sound cards:
Intel
EMU1010

```
Right.
I want to use the EMU1010 card as default.

```
asoundconf set-default-card EMU1010

```
Returns no error.
Still, there is only my Intel sound card (embedded in the mobo) making sound.

Content of ~/.asoundrc:
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/gauthier/.asoundrc.asoundconf>
```

Content of ~/.asoundrc.asoundconf:
```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card EMU1010
defaults.ctl.card EMU1010
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
```

alsamixer seems to see only the EMU card (the one that does NOT sound!)

Content of /etc/modprobe.d/alsa-base:
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# user entry, GF 090113
options snd-emu10k1 index=0
options snd_hda_intel=-2
```

This last row I though would disable the Intel soundcard. But the card works.

If you see anything I've done wrong, please tell me, I just can't figure it out!

Thanks!

---

### Post by thorgal on 2009-01-17
hello,

remove what you have done in /etc/modprobe.d/alsa-base
then create a new text file called /etc/modprobe.d/sound

add this:

```

alias snd-card-0 snd-emu10k1
alias snd-card-1 snd-hda-intel
options snd-emu10k1 index=0
options snd-hda-intel index=1

```

then reboot.

The .asoundrc can also be reset to default (I don't even have one and I have two soundcards which were correctly indexed after my recipe above). Just move this file to something else (or delete it if you don't care).

---

### Post by ushimitsudoki on 2009-01-17
What I did was **disable** my internal sound card, because I just figured I use my "real" sound card (external USB audio interface) for everything. 

If you want to go that route, it's easy: just blacklist the audio driver and put something like: 
install sound-slot-0 /sbin/modprobe snd_usb_audio

in /etc/modprobe.d/alsa-base

I did fiddle with having them both active, and setting one as a default, but as I recall it caused some problems with some applications, and I just gave up on it ... I didn't put a whole lot of effort into that, because that was back in the day.

---

### Post by dontiego on 2009-01-21
Hi!

Sorry for the delay, thanks for the reply.
I tried your solution, I'm sorry to say it didn't help.

What I'm trying to do now is to reinstall the alsa from the beginning:
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga]("http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga")

Exactly as the first time, I get into troubles because I can't seem to have the sources of linux at the right place.
The ./configure script of alsa is looking there: /usr/src/linux.
I have 
/usr/src/linux-headers-2.6.24-23
and
/usr/src/linux-headers-2.6.24-19
(plus associated -generic).

I tried also to give these paths in the command line of ./configure, but the underlying structure does not seem to be as expected by the script:
```
gauthier@ubuntu:/usr/src/alsa/alsa-driver-1.0.18a$ sudo ./configure --with-cards=emu10k1 --with-sequencer=yes --with-kernel=/usr/src/linux-headers-2.6.24-19
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.18a
checking cross compile... 
checking for directory with kernel source... /usr/src/linux-headers-2.6.24-19
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux-headers-2.6.24-19/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
gauthier@ubuntu:/usr/src/alsa/alsa-driver-1.0.18a$ 

```
How could I get the linux src containing so that I get
/usr/src/linux/include/linux/version.h?

'cause I guess that's what I need?

---

### Post by thorgal on 2009-01-22
could you be a bit more explicit about what did not work ?
any 'dmesg' output would help as well.

I don't think recompiling ALSA will help. In any case, if you want to do that, you need to install the linux-headers package corresponding to your actual kernel version (check your installed linux-image package).

Now, concerning my suggestion above, I don't see why it would not work. I tried it many times and it's always been spot-on. But I'm using debian, not ubuntu. Would that be different ? I doubt it but who knows ...

---

### Post by dontiego on 2009-01-22
I'll give it some more tries before reinstalling alsa, I havenät check if the other soundcard was working.

I think the problem might be related to which card is 0 and which one is 1. i will paste in the output of dmesg when I get home!

Thank you so far!

---

### Post by dontiego on 2009-01-23
Here is the output of dmseg. ALSA related stuff round line 580.
The strange thing: ALSA seems to do stuff with emu10k1 (the card I want to use), and nothing to any Intel sound card.
The Intel sound card is the one actually sounding.

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-rt (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP PREEMPT RT Thu Nov 27 20:37:26 UTC 2008 (Ubuntu 2.6.24-4.6-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c800 (usable)
[    0.000000]  BIOS-e820: 000000000009c800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3ce0
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4040 pages, LIFO batch:0
[    0.000000]   Normal zone: 3080 pages used for memmap
[    0.000000]   Normal zone: 222200 pages, LIFO batch:31
[    0.000000]   HighMem zone: 447 pages used for memmap
[    0.000000]   HighMem zone: 32305 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7D40 checksum 0
[    0.000000] ACPI: RSDP 000F7D40, 0014 (r0 FOXCON)
[    0.000000] ACPI: RSDT 3FFF3040, 0030 (r1 FOXCON AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF30C0, 0074 (r1 FOXCON AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF3180, 4341 (r1 FOXCON AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: MCFG 3FFF7640, 003C (r1 FOXCON AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FFF7540, 0084 (r1 FOXCON AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 000000000009d000
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 258545
[    0.000000] Kernel command line: root=UUID=9e52c1e4-44e2-45de-b7bc-f718af236745 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3400.157 MHz processor.
[   32.751125] Console: colour VGA+ 80x25
[   32.751128] console [tty0] enabled
[   32.751413] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   32.751719] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.779473] Memory: 1020784k/1048512k available (2243k kernel code, 26892k reserved, 1065k data, 368k init, 131008k highmem)
[   32.779482] virtual kernel memory layout:
[   32.779483]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   32.779484]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.779485]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   32.779486]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   32.779487]       .init : 0xc0441000 - 0xc049d000   ( 368 kB)
[   32.779487]       .data : 0xc0330c64 - 0xc043b324   (1065 kB)
[   32.779488]       .text : 0xc0100000 - 0xc0330c64   (2243 kB)
[   32.779491] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.839609] Calibrating delay using timer specific routine.. 6803.51 BogoMIPS (lpj=3401755)
[   32.839654] Security Framework initialized
[   32.839659] SELinux:  Disabled at boot.
[   32.839668] AppArmor: AppArmor initialized
[   32.839671] Failure registering capabilities with primary security module.
[   32.839688] Mount-cache hash table entries: 512
[   32.839833] Initializing cgroup subsys ns
[   32.839838] Initializing cgroup subsys cpuacct
[   32.839851] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000 00000000
[   32.839860] monitor/mwait feature present.
[   32.839861] using mwait in idle threads.
[   32.839867] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   32.839869] CPU: L2 cache: 1024K
[   32.839872] CPU: Physical Processor ID: 0
[   32.839874] CPU: After all inits, caps: bfebfbff 00100000 00000000 00043180 0000441d 00000000 00000000 00000000
[   32.839883] Compat vDSO mapped to ffffe000.
[   32.839897] Checking 'hlt' instruction... OK.
[   32.844038] SMP alternatives: switching to UP code
[   32.845403] Early unpacking initramfs... done
[   33.113387] ACPI: Core revision 20070126
[   33.113450] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   33.119033] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 01
[   33.119052] SMP alternatives: switching to SMP code
[   33.119635] Booting processor 1/1 eip 3000
[   33.129896] Initializing CPU#1
[   33.190348] Calibrating delay using timer specific routine.. 6799.06 BogoMIPS (lpj=3399533)
[   33.190357] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000 00000000
[   33.190365] monitor/mwait feature present.
[   33.190371] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   33.190374] CPU: L2 cache: 1024K
[   33.190376] CPU: Physical Processor ID: 0
[   33.190378] CPU: After all inits, caps: bfebfbff 00100000 00000000 00043180 0000441d 00000000 00000000 00000000
[   33.190743] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 01
[   33.190780] Total of 2 processors activated (13602.57 BogoMIPS).
[   33.190926] ENABLING IO-APIC IRQs
[   33.191097] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   33.303050] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   33.323076] Brought up 2 CPUs
[   33.323108] CPU0 attaching sched-domain:
[   33.323111]  domain 0: span 03
[   33.323114]   groups: 01 02
[   33.323117]   domain 1: span 03
[   33.323119]    groups: 03
[   33.323123] CPU1 attaching sched-domain:
[   33.323124]  domain 0: span 03
[   33.323126]   groups: 02 01
[   33.323129]   domain 1: span 03
[   33.323131]    groups: 03
[   33.323433] net_namespace: 76 bytes
[   33.323439] Booting paravirtualized kernel on bare hardware
[   33.324002] Time: 20:10:21  Date: 01/23/09
[   33.324046] NET: Registered protocol family 16
[   33.324368] EISA bus registered
[   33.324374] ACPI: bus type pci registered
[   33.351975] PCI: PCI BIOS revision 3.00 entry at 0xfa070, last bus=2
[   33.351978] PCI: Using configuration type 1
[   33.351982] Setting up standard PCI resources
[   33.371210] ACPI: EC: Look up EC in DSDT
[   33.375966] ACPI: Interpreter enabled
[   33.375969] ACPI: (supports S0 S1 S4 S5)
[   33.375987] ACPI: Using IOAPIC for interrupt routing
[   33.381934] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.382480] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   33.382484] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   33.383114] PCI: Transparent bridge - 0000:00:1e.0
[   33.383139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.383355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   33.391929] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   33.392049] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   33.392154] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   33.392265] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   33.392371] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   33.392476] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   33.392579] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   33.392681] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   33.392846] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.392891] pnp: PnP ACPI init
[   33.392902] ACPI: bus type pnp registered
[   33.396379] pnpacpi: exceeded the max number of mem resources: 12
[   33.396460] pnp: PnP ACPI: found 14 devices
[   33.396463] ACPI: ACPI bus type pnp unregistered
[   33.396466] PnPBIOS: Disabled by ACPI PNP
[   33.396798] PCI: Using ACPI for IRQ routing
[   33.396802] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.420997] NET: Registered protocol family 8
[   33.421001] NET: Registered protocol family 20
[   33.421134] AppArmor: AppArmor Filesystem Enabled
[   33.429274] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   33.429279] system 00:01: ioport range 0x290-0x29f has been reserved
[   33.429282] system 00:01: ioport range 0x290-0x297 has been reserved
[   33.429298] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[   33.429308] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   33.429322] system 00:0d: iomem range 0xd0000-0xd3fff has been reserved
[   33.429325] system 00:0d: iomem range 0xdc600-0xdffff has been reserved
[   33.429328] system 00:0d: iomem range 0xf0000-0xfbfff could not be reserved
[   33.429331] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   33.429333] system 00:0d: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   33.429336] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   33.429339] system 00:0d: iomem range 0x100000-0x3ffeffff could not be reserved
[   33.429341] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[   33.429344] system 00:0d: iomem range 0xfed13000-0xfed1dfff could not be reserved
[   33.429347] system 00:0d: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   33.429349] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   33.429352] system 00:0d: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   33.459936] PCI: Bridge: 0000:00:01.0
[   33.459938]   IO window: disabled.
[   33.459942]   MEM window: c8000000-d7ffffff
[   33.459945]   PREFETCH window: 50000000-500fffff
[   33.459951] PCI: Bridge: 0000:00:1e.0
[   33.459953]   IO window: d000-dfff
[   33.459958]   MEM window: d8000000-d80fffff
[   33.459967]   PREFETCH window: disabled.
[   33.459984] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.459990] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   33.460001] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   33.460031] NET: Registered protocol family 2
[   33.495044] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   33.495370] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   33.496063] TCP bind hash table entries: 65536 (order: 9, 2359296 bytes)
[   33.497312] TCP: Hash tables configured (established 131072 bind 65536)
[   33.497317] TCP reno registered
[   33.509366] checking if image is initramfs... it is
[   34.046917] Freeing initrd memory: 7386k freed
[   34.047912] audit: initializing netlink socket (disabled)
[   34.047929] audit(1232741421.145:1): initialized
[   34.047999] krcupreemptd setsched 0
[   34.048002]   prio = 98
[   34.048146] highmem bounce pool size: 64 pages
[   34.048233] VFS: Disk quotas dquot_6.5.1
[   34.048263] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.048373] io scheduler noop registered
[   34.048375] io scheduler anticipatory registered
[   34.048377] io scheduler deadline registered
[   34.048387] io scheduler cfq registered (default)
[   34.048488] Boot video device is 0000:01:00.0
[   34.048635] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   34.048673] assign_interrupt_mode Found MSI capability
[   34.048692] Allocate Port Service[0000:00:01.0:pcie00]
[   34.049013] isapnp: Scanning for PnP cards...
[   34.403250] isapnp: No Plug & Play device found
[   34.441525] Real Time Clock Driver v1.12ac
[   34.441659] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.441793] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.441945] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.442668] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.443859] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.443949] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   34.444162] PNP: No PS/2 controller found. Probing ports directly.
[   34.446907] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.446914] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.455294] mice: PS/2 mouse device common for all mice
[   34.455458] EISA: Probing bus 0 at eisa.0
[   34.455489] EISA: Detected 0 cards.
[   34.455492] cpuidle: using governor ladder
[   34.455565] NET: Registered protocol family 1
[   34.455593] Using IPI No-Shortcut mode
[   34.455646] registered taskstats version 1
[   34.455753]   Magic number: 9:435:195
[   34.455786]   hash matches device ttys7
[   34.455794]   hash matches device ttypa
[   34.455860] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   34.455862] EDD information not available.
[   34.456041] Freeing unused kernel memory: 368k freed
[   34.456074] Write protecting the kernel read-only data: 836k
[   35.701769] fuse init (API version 7.9)
[   35.708460] ACPI: Fan [FAN] (on)
[   35.716327] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.716344] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.717895] ACPI: Thermal Zone [THRM] (39 C)
[   35.910758] usbcore: registered new interface driver usbfs
[   35.910794] usbcore: registered new interface driver hub
[   35.913754] usbcore: registered new device driver usb
[   35.921355] USB Universal Host Controller Interface driver v3.0
[   35.921427] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   35.921442] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   35.921447] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   35.921784] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   35.933602] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e300
[   35.933812] usb usb1: configuration #1 chosen from 1 choice
[   35.933852] hub 1-0:1.0: USB hub found
[   35.933862] hub 1-0:1.0: 2 ports detected
[   36.034700] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   36.034715] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   36.034720] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   36.034761] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   36.044694] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e000
[   36.044881] usb usb2: configuration #1 chosen from 1 choice
[   36.044920] hub 2-0:1.0: USB hub found
[   36.044929] hub 2-0:1.0: 2 ports detected
[   36.145624] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   36.145639] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   36.145644] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   36.145681] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   36.155753] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e100
[   36.155943] usb usb3: configuration #1 chosen from 1 choice
[   36.155984] hub 3-0:1.0: USB hub found
[   36.155994] hub 3-0:1.0: 2 ports detected
[   36.240476] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   36.256578] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   36.256593] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   36.256598] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   36.256634] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   36.285468] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e200
[   36.285666] usb usb4: configuration #1 chosen from 1 choice
[   36.285705] hub 4-0:1.0: USB hub found
[   36.285715] hub 4-0:1.0: 2 ports detected
[   36.294364] SCSI subsystem initialized
[   36.327880] libata version 3.00 loaded.
[   36.386700] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   36.386716] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   36.386721] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   36.386757] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   36.390661] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   36.390673] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd8104000
[   36.402404] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.402576] usb usb5: configuration #1 chosen from 1 choice
[   36.402619] hub 5-0:1.0: USB hub found
[   36.402629] hub 5-0:1.0: 8 ports detected
[   36.408602] Floppy drive(s): fd0 is 1.44M
[   36.412519] usb 1-1: configuration #1 chosen from 1 choice
[   36.416374] usb 1-1: can't set config #1, error -71
[   36.423151] FDC 0 is a post-1991 82077
[   36.503579] ata_piix 0000:00:1f.1: version 2.12
[   36.503603] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   36.503653] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   36.507043] scsi0 : ata_piix
[   36.508031] scsi1 : ata_piix
[   36.509037] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   36.509042] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   36.814410] ata1.00: ATAPI: _NEC DVD_RW ND-3520AW, 3.07, max UDMA/33
[   36.830046] usb 1-1: USB disconnect, address 2
[   36.971235] ata1.00: configured for UDMA/33
[   37.035946] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   37.134017] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520AW 3.07 PQ: 0 ANSI: 5
[   37.134169] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   37.134209] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   37.134254] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   37.135901] scsi2 : ata_piix
[   37.136180] scsi3 : ata_piix
[   37.137185] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 18
[   37.137190] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 18
[   37.197058] usb 1-1: configuration #1 chosen from 1 choice
[   37.310348] ata3.00: ATA-7: SAMSUNG HD080HJ, WT100-33, max UDMA7
[   37.310353] ata3.00: 156301488 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   37.310501] ata3.01: ATA-7: SAMSUNG HD080HJ, WT100-33, max UDMA7
[   37.310505] ata3.01: 156301488 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   37.329363] ata3.00: configured for UDMA/133
[   37.348338] ata3.01: configured for UDMA/133
[   37.415751] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   37.538278] ata4.01: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[   37.538283] ata4.01: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   37.557026] ata4.01: configured for UDMA/133
[   37.557161] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD080HJ  WT10 PQ: 0 ANSI: 5
[   37.557327] scsi 2:0:1:0: Direct-Access     ATA      SAMSUNG HD080HJ  WT10 PQ: 0 ANSI: 5
[   37.557493] scsi 3:0:1:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[   37.560048] r8169 Gigabit Ethernet driver 2.2LK loaded
[   37.560077] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[   37.560470] eth0: RTL8110s at 0xf8842000, 00:01:6c:30:ce:18, XID 04000000 IRQ 20
[   37.564646] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   37.581842] usb 1-2: configuration #1 chosen from 1 choice
[   37.584929] usbcore: registered new interface driver hiddev
[   37.597972] input: A4Tech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   37.608733] input,hidraw0: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:1d.0-1
[   37.620973] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d8025000-d80257ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   37.623368] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[   37.626291] ACPI: PCI Interrupt 0000:02:02.2[B] -> GSI 18 (level, low) -> IRQ 19
[   37.630971] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   37.663290] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input3
[   37.666153] Driver 'sd' needs updating - please use bus_type methods
[   37.666286] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   37.666310] sd 2:0:0:0: [sda] Write Protect is off
[   37.666315] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.666351] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.666435] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   37.666456] sd 2:0:0:0: [sda] Write Protect is off
[   37.666459] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.666494] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.666501]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   37.674964]  sda1
[   37.674969]  sda: p1 exceeds device capacity
[   37.675062] sd 2:0:0:0: [sda] Attached SCSI disk
[   37.675147] sd 2:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   37.675166] sd 2:0:1:0: [sdb] Write Protect is off
[   37.675170] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   37.675198] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.675273] sd 2:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   37.675294] sd 2:0:1:0: [sdb] Write Protect is off
[   37.675298] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   37.675333] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.675338]  sdb:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   37.676325] Uniform CD-ROM driver Revision: 3.20
[   37.676376] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   37.679955] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   37.679977] usbcore: registered new interface driver usbhid
[   37.679983] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   37.684271]  unknown partition table
[   37.684341] sd 2:0:1:0: [sdb] Attached SCSI disk
[   37.684417] sd 3:0:1:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   37.684435] sd 3:0:1:0: [sdc] Write Protect is off
[   37.684439] sd 3:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   37.684468] sd 3:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.684527] sd 3:0:1:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   37.684544] sd 3:0:1:0: [sdc] Write Protect is off
[   37.684547] sd 3:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   37.684574] sd 3:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.684578]  sdc: sdc1 sdc2 <<6>ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d8024000-d80247ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   37.704727]  sdc5 sdc6 >
[   37.719175] sd 3:0:1:0: [sdc] Attached SCSI disk
[   37.732801] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   37.732835] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   37.732898] sd 2:0:1:0: Attached scsi generic sg2 type 0
[   37.732932] sd 3:0:1:0: Attached scsi generic sg3 type 0
[   37.896698] attempt to access beyond end of device
[   37.896706] sda: rw=0, want=312576577, limit=156301488
[   37.896710] Buffer I/O error on device sda1, logical block 156288256
[   37.896715] attempt to access beyond end of device
[   37.896718] sda: rw=0, want=312576579, limit=156301488
[   37.896720] Buffer I/O error on device sda1, logical block 156288257
[   37.896724] attempt to access beyond end of device
[   37.896726] sda: rw=0, want=312576581, limit=156301488
[   37.896729] Buffer I/O error on device sda1, logical block 156288258
[   37.896737] attempt to access beyond end of device
[   37.896739] sda: rw=0, want=312576583, limit=156301488
[   37.896741] Buffer I/O error on device sda1, logical block 156288259
[   37.896745] attempt to access beyond end of device
[   37.896747] sda: rw=0, want=312576577, limit=156301488
[   37.896749] Buffer I/O error on device sda1, logical block 156288256
[   37.896752] attempt to access beyond end of device
[   37.896754] sda: rw=0, want=312576579, limit=156301488
[   37.896756] Buffer I/O error on device sda1, logical block 156288257
[   37.896759] attempt to access beyond end of device
[   37.896761] sda: rw=0, want=312576581, limit=156301488
[   37.896763] Buffer I/O error on device sda1, logical block 156288258
[   37.896766] attempt to access beyond end of device
[   37.896768] sda: rw=0, want=312576583, limit=156301488
[   37.896771] Buffer I/O error on device sda1, logical block 156288259
[   37.896784] attempt to access beyond end of device
[   37.896787] sda: rw=0, want=312576689, limit=156301488
[   37.896789] Buffer I/O error on device sda1, logical block 156288312
[   37.896792] attempt to access beyond end of device
[   37.896795] sda: rw=0, want=312576691, limit=156301488
[   37.896797] Buffer I/O error on device sda1, logical block 156288313
[   37.896800] attempt to access beyond end of device
[   37.896802] sda: rw=0, want=312576693, limit=156301488
[   37.896805] attempt to access beyond end of device
[   37.896822] sda: rw=0, want=312576695, limit=156301488
[   37.896827] attempt to access beyond end of device
[   37.896829] sda: rw=0, want=312576689, limit=156301488
[   37.896832] attempt to access beyond end of device
[   37.896834] sda: rw=0, want=312576691, limit=156301488
[   37.896836] attempt to access beyond end of device
[   37.896838] sda: rw=0, want=312576693, limit=156301488
[   37.896841] attempt to access beyond end of device
[   37.896843] sda: rw=0, want=312576695, limit=156301488
[   37.896946] attempt to access beyond end of device
[   37.896949] sda: rw=0, want=312576705, limit=156301488
[   37.896953] attempt to access beyond end of device
[   37.896955] sda: rw=0, want=312576705, limit=156301488
[   37.896964] attempt to access beyond end of device
[   37.896967] sda: rw=0, want=312576705, limit=156301488
[   37.896975] attempt to access beyond end of device
[   37.896977] sda: rw=0, want=312576705, limit=156301488
[   37.896984] attempt to access beyond end of device
[   37.896987] sda: rw=0, want=312576705, limit=156301488
[   37.896995] attempt to access beyond end of device
[   37.896998] sda: rw=0, want=312576705, limit=156301488
[   37.897010] attempt to access beyond end of device
[   37.897013] sda: rw=0, want=312576705, limit=156301488
[   37.897034] attempt to access beyond end of device
[   37.897037] sda: rw=0, want=312576641, limit=156301488
[   37.897041] attempt to access beyond end of device
[   37.897044] sda: rw=0, want=312576643, limit=156301488
[   37.897048] attempt to access beyond end of device
[   37.897050] sda: rw=0, want=312576645, limit=156301488
[   37.897054] attempt to access beyond end of device
[   37.897057] sda: rw=0, want=312576647, limit=156301488
[   37.897067] attempt to access beyond end of device
[   37.897071] sda: rw=0, want=312576689, limit=156301488
[   37.897075] attempt to access beyond end of device
[   37.897078] sda: rw=0, want=312576691, limit=156301488
[   37.897082] attempt to access beyond end of device
[   37.897084] sda: rw=0, want=312576693, limit=156301488
[   37.897087] attempt to access beyond end of device
[   37.897089] sda: rw=0, want=312576695, limit=156301488
[   37.897097] attempt to access beyond end of device
[   37.897099] sda: rw=0, want=312576705, limit=156301488
[   37.897107] attempt to access beyond end of device
[   37.897109] sda: rw=0, want=312576705, limit=156301488
[   38.044876] Attempting manual resume
[   38.044880] swsusp: Resume From Partition 8:38
[   38.044882] PM: Checking swsusp image.
[   38.045091] PM: Resume from disk failed.
[   38.083091] kjournald starting.  Commit interval 5 seconds
[   38.083106] EXT3-fs: mounted filesystem with ordered data mode.
[   38.882346] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200006948d]
[   38.960297] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c0121004e45]
[   43.129451] attempt to access beyond end of device
[   43.129459] sda: rw=0, want=312576577, limit=156301488
[   43.129463] printk: 23 messages suppressed.
[   43.129467] Buffer I/O error on device sda1, logical block 156288256
[   43.129472] attempt to access beyond end of device
[   43.129476] sda: rw=0, want=312576579, limit=156301488
[   43.129480] attempt to access beyond end of device
[   43.129483] sda: rw=0, want=312576581, limit=156301488
[   43.129487] attempt to access beyond end of device
[   43.129491] sda: rw=0, want=312576583, limit=156301488
[   43.129497] attempt to access beyond end of device
[   43.129501] sda: rw=0, want=312576577, limit=156301488
[   43.129505] attempt to access beyond end of device
[   43.129508] sda: rw=0, want=312576579, limit=156301488
[   43.129512] attempt to access beyond end of device
[   43.129516] sda: rw=0, want=312576581, limit=156301488
[   43.129519] attempt to access beyond end of device
[   43.129523] sda: rw=0, want=312576583, limit=156301488
[   43.129541] attempt to access beyond end of device
[   43.129545] sda: rw=0, want=312576689, limit=156301488
[   43.129550] attempt to access beyond end of device
[   43.129553] sda: rw=0, want=312576691, limit=156301488
[   43.129557] attempt to access beyond end of device
[   43.129560] sda: rw=0, want=312576693, limit=156301488
[   43.129564] attempt to access beyond end of device
[   43.129567] sda: rw=0, want=312576695, limit=156301488
[   43.129573] attempt to access beyond end of device
[   43.129578] sda: rw=0, want=312576689, limit=156301488
[   43.129582] attempt to access beyond end of device
[   43.129585] sda: rw=0, want=312576691, limit=156301488
[   43.129589] attempt to access beyond end of device
[   43.129593] sda: rw=0, want=312576693, limit=156301488
[   43.129598] attempt to access beyond end of device
[   43.129601] sda: rw=0, want=312576695, limit=156301488
[   43.129759] attempt to access beyond end of device
[   43.129764] sda: rw=0, want=312576705, limit=156301488
[   43.129834] attempt to access beyond end of device
[   43.129838] sda: rw=0, want=312576705, limit=156301488
[   43.129852] attempt to access beyond end of device
[   43.129855] sda: rw=0, want=312576705, limit=156301488
[   43.129865] attempt to access beyond end of device
[   43.129869] sda: rw=0, want=312576705, limit=156301488
[   43.129878] attempt to access beyond end of device
[   43.129881] sda: rw=0, want=312576705, limit=156301488
[   43.129890] attempt to access beyond end of device
[   43.129895] sda: rw=0, want=312576705, limit=156301488
[   43.129905] attempt to access beyond end of device
[   43.129910] sda: rw=0, want=312576705, limit=156301488
[   43.129926] attempt to access beyond end of device
[   43.129930] sda: rw=0, want=312576641, limit=156301488
[   43.129935] attempt to access beyond end of device
[   43.129939] sda: rw=0, want=312576643, limit=156301488
[   43.129943] attempt to access beyond end of device
[   43.129946] sda: rw=0, want=312576645, limit=156301488
[   43.129951] attempt to access beyond end of device
[   43.129954] sda: rw=0, want=312576647, limit=156301488
[   43.129968] attempt to access beyond end of device
[   43.129972] sda: rw=0, want=312576689, limit=156301488
[   43.129977] attempt to access beyond end of device
[   43.129980] sda: rw=0, want=312576691, limit=156301488
[   43.129985] attempt to access beyond end of device
[   43.129988] sda: rw=0, want=312576693, limit=156301488
[   43.129993] attempt to access beyond end of device
[   43.129996] sda: rw=0, want=312576695, limit=156301488
[   43.130008] attempt to access beyond end of device
[   43.130014] sda: rw=0, want=312576705, limit=156301488
[   43.130025] attempt to access beyond end of device
[   43.130029] sda: rw=0, want=312576705, limit=156301488
[   43.527782] Linux agpgart interface v0.102
[   43.599883] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.795720] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.840641] iTCO_vendor_support: vendor-support=0
[   43.892612] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   43.892800] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   43.892867] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   43.939533] intel_rng: FWH not detected
[   43.988759] input: Power Button (FF) as /devices/virtual/input/input4
[   43.997209] ACPI: Power Button (FF) [PWRF]
[   43.997352] input: Power Button (CM) as /devices/virtual/input/input5
[   44.005225] ACPI: Power Button (CM) [PWRB]
[   44.617842] nvidia: module license 'NVIDIA' taints kernel.
[   45.305896] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 22
[   45.344794] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Special config.
[   45.344890] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_HANA_ID=0x7f
[   45.344896] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/hana.fw testing
[   45.594832] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   45.665610] r8169: eth0: link up
[   45.983504] irda_init()
[   45.983529] NET: Registered protocol family 23
[   46.213759] parport_pc 00:09: reported by Plug and Play ACPI
[   46.213808] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   46.976653] NET: Registered protocol family 17
[   47.338316] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:684: firmware size=0x133a4
[   56.736354] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:897: emu1010: Hana Firmware loaded
[   56.736403] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:900: Hana ver:3.4
[   56.736460] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:905: emu1010: Card options=0x1
[   56.736486] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:907: emu1010: Card options=0x1
[   56.736954] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:945: emu1010: Card options3=0x1
[   56.753732] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1520: EMU outputs on
[   56.753739] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1576: EMU inputs on
[   56.765790] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.765803] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   56.766015] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   56.862128] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.862161] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   56.871161] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   56.871635] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
[   57.864438] loop: module loaded
[   57.881939] lp0: using parport0 (interrupt-driven).
[   57.994652] Adding 1951856k swap on /dev/sdc6.  Priority:-1 extents:1 across:1951856k
[   58.555538] EXT3 FS on sdc1, internal journal
[   58.848847] NET: Registered protocol family 10
[   58.849212] lo: Disabled Privacy Extensions
[   59.328703] kjournald starting.  Commit interval 5 seconds
[   59.329007] EXT3 FS on sdc5, internal journal
[   59.329015] EXT3-fs: mounted filesystem with ordered data mode.
[   59.748597] ip_tables: (C) 2000-2006 Netfilter Core Team
[   60.186247] No dock devices found.
[   61.059852] apm: BIOS not found.
[   61.157948] ppdev: user-space parallel port driver
[   61.243390] audit(1232737845.545:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5324 profile="/usr/sbin/cupsd" namespace="default"
[   62.135310] attempt to access beyond end of device
[   62.135321] sda: rw=0, want=312576577, limit=156301488
[   62.135326] printk: 32 messages suppressed.
[   62.135331] Buffer I/O error on device sda1, logical block 156288256
[   62.135337] attempt to access beyond end of device
[   62.135345] sda: rw=0, want=312576579, limit=156301488
[   62.135349] Buffer I/O error on device sda1, logical block 156288257
[   62.135354] attempt to access beyond end of device
[   62.135357] sda: rw=0, want=312576581, limit=156301488
[   62.135361] Buffer I/O error on device sda1, logical block 156288258
[   62.135365] attempt to access beyond end of device
[   62.135369] sda: rw=0, want=312576583, limit=156301488
[   62.135374] attempt to access beyond end of device
[   62.135378] sda: rw=0, want=312576577, limit=156301488
[   62.135382] attempt to access beyond end of device
[   62.135386] sda: rw=0, want=312576579, limit=156301488
[   62.135390] attempt to access beyond end of device
[   62.135393] sda: rw=0, want=312576581, limit=156301488
[   62.135397] attempt to access beyond end of device
[   62.135400] sda: rw=0, want=312576583, limit=156301488
[   62.135417] attempt to access beyond end of device
[   62.135421] sda: rw=0, want=312576689, limit=156301488
[   62.135425] attempt to access beyond end of device
[   62.135429] sda: rw=0, want=312576691, limit=156301488
[   62.135434] attempt to access beyond end of device
[   62.135437] sda: rw=0, want=312576693, limit=156301488
[   62.135441] attempt to access beyond end of device
[   62.135444] sda: rw=0, want=312576695, limit=156301488
[   62.135450] attempt to access beyond end of device
[   62.135454] sda: rw=0, want=312576689, limit=156301488
[   62.135458] attempt to access beyond end of device
[   62.135461] sda: rw=0, want=312576691, limit=156301488
[   62.135465] attempt to access beyond end of device
[   62.135468] sda: rw=0, want=312576693, limit=156301488
[   62.135472] attempt to access beyond end of device
[   62.135475] sda: rw=0, want=312576695, limit=156301488
[   62.135586] attempt to access beyond end of device
[   62.135590] sda: rw=0, want=312576705, limit=156301488
[   62.135596] attempt to access beyond end of device
[   62.135599] sda: rw=0, want=312576705, limit=156301488
[   62.135612] attempt to access beyond end of device
[   62.135615] sda: rw=0, want=312576705, limit=156301488
[   62.135626] attempt to access beyond end of device
[   62.135630] sda: rw=0, want=312576705, limit=156301488
[   62.135646] attempt to access beyond end of device
[   62.135650] sda: rw=0, want=312576705, limit=156301488
[   62.135662] attempt to access beyond end of device
[   62.135666] sda: rw=0, want=312576705, limit=156301488
[   62.135676] attempt to access beyond end of device
[   62.135679] sda: rw=0, want=312576705, limit=156301488
[   62.135692] attempt to access beyond end of device
[   62.135697] sda: rw=0, want=312576641, limit=156301488
[   62.135700] attempt to access beyond end of device
[   62.135703] sda: rw=0, want=312576643, limit=156301488
[   62.135707] attempt to access beyond end of device
[   62.135710] sda: rw=0, want=312576645, limit=156301488
[   62.135714] attempt to access beyond end of device
[   62.135717] sda: rw=0, want=312576647, limit=156301488
[   62.135728] attempt to access beyond end of device
[   62.135732] sda: rw=0, want=312576689, limit=156301488
[   62.135736] attempt to access beyond end of device
[   62.135739] sda: rw=0, want=312576691, limit=156301488
[   62.135742] attempt to access beyond end of device
[   62.135745] sda: rw=0, want=312576693, limit=156301488
[   62.135749] attempt to access beyond end of device
[   62.135752] sda: rw=0, want=312576695, limit=156301488
[   62.135764] attempt to access beyond end of device
[   62.135768] sda: rw=0, want=312576705, limit=156301488
[   62.135779] attempt to access beyond end of device
[   62.135783] sda: rw=0, want=312576705, limit=156301488
[   62.333536] Bluetooth: Core ver 2.11
[   62.333956] NET: Registered protocol family 31
[   62.333963] Bluetooth: HCI device and connection manager initialized
[   62.333969] Bluetooth: HCI socket layer initialized
[   62.352412] Bluetooth: L2CAP ver 2.9
[   62.352419] Bluetooth: L2CAP socket layer initialized
[   62.393509] Bluetooth: RFCOMM socket layer initialized
[   62.393525] Bluetooth: RFCOMM TTY layer initialized
[   62.393529] Bluetooth: RFCOMM ver 1.8
[   69.068727] eth0: no IPv6 routers present
```

The problem seems to be in the default selection of the sound card. I thought the alias line you made me copy would help but it did not.
Now I remember that I have written these alias lines in another file earlier, I just can't remember which. There might be a conflict?

---

### Post by dontiego on 2009-01-23
Alright, I got sound again!!

I needed to get through the alsamixer settings again, it turned out the mixer is setup for another EMU card by default.

In Playback, I needed to setup the output "0202 DAC Left" and "0202 DAC Right".

Hurray! Thanks for the support!

Now I have sound when I for example play a video on youtube.
BUT playing a wmv or mp3 in Totem still gives sound to my other sound card. :o

I went to System -> preferences -> sound, and there it seemed that I had to run PulseAudio. Trying with Alsa and "Test" returned an error. Should I try to fix it so that I can select Alsa, or is PulseAudio ok?

I'm actually not quite sure of what PulseAudio is meant to do. Isn't it the same job as Jack's?

---

### Post by quitus on 2009-01-24
select one sound card in the bios system, and desactivate the other one.


sorry for my bad english.

---

