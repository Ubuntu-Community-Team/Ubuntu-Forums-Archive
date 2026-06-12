---
title: "HD-Audio Stopping sound from M-Audio Card"
date: 2011-10-22
forum: Ubuntu Studio
---

### Post by beefheartvliet on 2011-10-22
Hi,

I'm having a bit of a problem.I have just added an ATI Radeon 5450 GFX Card to my PC, It has HD Audio on it ( Which I don't want to use). I read a guide that allows me to force a certain sound card to be the first, and have done that.* I knew of this from when I once had 2 sound cards in my pc that I wanted to use.* So I thought it would as simple now as it was then. Despite my M-Audio Sound card now being the first device or "0" if you like, I'm still getting no sound. I have ran **alsamixer** in the terminal and checked that it is indeed "0" I have checked that the DAC Levels are not muted. Now here's the kicker, and I hope it's something really simple that one of you folks might be able to help me with. 
I ran **ubuntu-bug audio** as suggested here [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems). I hear the first set of test tones, but not the second set. As if to say, sound is coming through my M-audio when I run that test. What am I missing?

I should add, that this refers to a stock install of 10.10 (not studio) But' it's the same in 11.10 also 

Thanks for looking

---

### Post by jejeman on 2011-10-22
Give us the output from 
```
aplay -l
```
I supose that you are using pulseaudio, what is the default card setup in sound preferences? Which hardware profile?

---

### Post by beefheartvliet on 2011-10-22
Hi,

Here is the output 

**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm currently using Pulse Audio, When I bring up sound preferences, it's currently set to my M-audio card (The one I want to work). 
I have disabled On Board Audio and On Board HDMI Audio in the BIOS

I have noticed that my BIOS has never been updated. It's a 2008 board and there are 2011 updates. So I'm going give that a whirl, for what it's worth. 

I'm also yet to try with something like Dream Studio (based on on Ubuntu Studio), Just in case I get lucky ;-) 

I'd appreciate if you have any suggestions for me to try. I'm by no means a Linux genius, but I can manage to find my way round by reading older posts on forums. I'm just at a bit of a loss right now! 

Then there's getting my TV card working, but  that's another post...Well assuming that I don't work it out in the meanwhile :-)

Thanks

---

### Post by beefheartvliet on 2011-10-22
Here's the Hardware Profile

id:     
ubuntu 
description:     Desktop Computer 
product:     System Product Name 
vendor:     System manufacturer 
version:     System Version 
serial:     System Serial Number 
width:     32 bits 
capabilities:     smbios-2.5 dmi-2.5 smp-1.4 smp 
configuration:     
boot    =    normal 
chassis    =    desktop 
cpus    =    4 
uuid    =   
id:     
core 
description:     Motherboard 
product:     M3N-HT DELUXE 
vendor:     ASUSTeK Computer INC. 
physical id:      
0 
version:     1.XX 
serial:     
id:     
firmware 
description:     BIOS 
vendor:     Phoenix Technologies, LTD 
physical id:      
0 
version:     ASUS M3N-HT Deluxe ACPI BIOS Revision 0702 (04/09/2008) 
size:     128KiB 
capacity:     960KiB 
capabilities:     pci pnp apm upgrade shadowing cdboot bootselect  socketedrom edd int13floppy360 int13floppy1200 int13floppy720  int13floppy2880 int5printscreen int9keyboard int14serial int17printer  int10video acpi usb ls120boot zipboot biosbootspecification 
id:     
cpu:0 
description:     CPU 
product:     AMD Phenom(tm) 9850 Quad-Core Processor 
vendor:     Advanced Micro Devices [AMD] 
physical id:      
3 
bus info:      
cpu@0 
version:     15.2.3 
slot:     Socket AM2 
size:     2500MHz 
capacity:     3700MHz 
width:     64 bits 
clock:     200MHz 
capabilities:     boot fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht  syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow  constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm  cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch  osvw ibs npt lbrv svm_lock 
id:     
cache:0 
description:     L1 cache 
physical id:      
5 
slot:     L1 Cache 
size:     128KiB 
capacity:     256KiB 
capabilities:     synchronous internal write-back data 
id:     
cache:1 
description:     L2 cache 
physical id:      
6 
slot:     L2 Cache 
size:     512KiB 
capacity:     1MiB 
capabilities:     synchronous internal write-back unified 
id:     
memory:0 
description:     System Memory 
physical id:      
2a 
slot:     System board or motherboard 
size:     4GiB 
id:     
bank:0 
description:     DIMM [empty] 
product:     None 
vendor:     None 
physical id:      
0 
serial:     None 
slot:     DIMM_A1 
width:     64 bits 
id:     
bank:1 
description:     DIMM [empty] 
product:     None 
vendor:     None 
physical id:      
1 
serial:     None 
slot:     DIMM_B1 
width:     64 bits 
id:     
bank:2 
description:     DIMM DDR2 800 MHz (1.2 ns) 
product:     None 
vendor:     None 
physical id:      
2 
serial:     None 
slot:     DIMM_A2 
size:     2GiB 
width:     64 bits 
clock:     800MHz (1.2ns) 
id:     
bank:3 
description:     DIMM DDR2 800 MHz (1.2 ns) 
product:     None 
vendor:     None 
physical id:      
3 
serial:     None 
slot:     DIMM_B2 
size:     2GiB 
width:     64 bits 
clock:     800MHz (1.2ns) 
id:     
cpu:1 
physical id:      
4 
bus info:      
cpu@1 
version:     15.2.3 
size:     2500MHz 
id:     
cache:0 
description:     L1 cache 
physical id:      
0 
size:     128KiB 
id:     
cache:1 
description:     L2 cache 
physical id:      
1 
size:     512KiB 
id:     
cpu:2 
physical id:      
5 
bus info:      
cpu@2 
version:     15.2.3 
size:     2500MHz 
id:     
cache:0 
description:     L1 cache 
physical id:      
0 
size:     128KiB 
id:     
cache:1 
description:     L2 cache 
physical id:      
1 
size:     512KiB 
id:     
cpu:3 
physical id:      
7 
bus info:      
cpu@3 
version:     15.2.3 
size:     2500MHz 
id:     
cache:0 
description:     L1 cache 
physical id:      
0 
size:     128KiB 
id:     
cache:1 
description:     L2 cache 
physical id:      
1 
size:     512KiB 
id:     
memory:1 
description:     RAM memory 
product:     MCP78S [GeForce 8200] Memory Controller 
vendor:     nVidia Corporation 
physical id:      
a 
bus info:      
pci@0000:00:00.0 
version:     a2 
width:     32 bits 
clock:     66MHz (15.2ns) 
capabilities:     ht bus_master cap_list 
configuration:     
latency    =    0 
id:     
isa 
description:     ISA bridge 
product:     MCP78S [GeForce 8200] LPC Bridge 
vendor:     nVidia Corporation 
physical id:      
1 
bus info:      
pci@0000:00:01.0 
version:     a2 
width:     32 bits 
clock:     66MHz 
capabilities:     isa bus_master 
configuration:     
latency    =    0 
id:     
serial 
description:     SMBus 
product:     MCP78S [GeForce 8200] SMBus 
vendor:     nVidia Corporation 
physical id:      
1.1 
bus info:      
pci@0000:00:01.1 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     pm cap_list 
configuration:     
driver    =    nForce2_smbus 
latency    =    0 
resources:     
irq    :    5 
ioport    :    fc00(size=64) 
ioport    :    1c00(size=64) 
ioport    :    1c40(size=64) 
id:     
memory:2 
description:     RAM memory 
product:     MCP78S [GeForce 8200] Memory Controller 
vendor:     nVidia Corporation 
physical id:      
1.2 
bus info:      
pci@0000:00:01.2 
version:     a1 
width:     32 bits 
clock:     66MHz (15.2ns) 
configuration:     
latency    =    0 
id:     
processor 
description:     Co-processor 
product:     MCP78S [GeForce 8200] Co-Processor 
vendor:     nVidia Corporation 
physical id:      
1.3 
bus info:      
pci@0000:00:01.3 
version:     a2 
width:     32 bits 
clock:     66MHz 
capabilities:     bus_master 
configuration:     
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
memory    :    fdf80000-fdffffff 
id:     
memory:3 
description:     RAM memory 
product:     MCP78S [GeForce 8200] Memory Controller 
vendor:     nVidia Corporation 
physical id:      
1.4 
bus info:      
pci@0000:00:01.4 
version:     a1 
width:     32 bits 
clock:     66MHz (15.2ns) 
configuration:     
latency    =    0 
id:     
usb:0 
description:     USB Controller 
product:     MCP78S [GeForce 8200] OHCI USB 1.1 Controller 
vendor:     nVidia Corporation 
physical id:      
2 
bus info:      
pci@0000:00:02.0 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     pm ohci bus_master cap_list 
configuration:     
driver    =    ohci_hcd 
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
irq    :    20 
memory    :    fe02f000-fe02ffff 
id:     
usb:1 
description:     USB Controller 
product:     MCP78S [GeForce 8200] EHCI USB 2.0 Controller 
vendor:     nVidia Corporation 
physical id:      
2.1 
bus info:      
pci@0000:00:02.1 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     debug pm ehci bus_master cap_list 
configuration:     
driver    =    ehci_hcd 
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
irq    :    22 
memory    :    fe02e000-fe02e0ff 
id:     
usb:2 
description:     USB Controller 
product:     MCP78S [GeForce 8200] OHCI USB 1.1 Controller 
vendor:     nVidia Corporation 
physical id:      
b 
bus info:      
pci@0000:00:04.0 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     pm ohci bus_master cap_list 
configuration:     
driver    =    ohci_hcd 
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
irq    :    23 
memory    :    fe02d000-fe02dfff 
id:     
usb:3 
description:     USB Controller 
product:     MCP78S [GeForce 8200] EHCI USB 2.0 Controller 
vendor:     nVidia Corporation 
physical id:      
4.1 
bus info:      
pci@0000:00:04.1 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     debug pm ehci bus_master cap_list 
configuration:     
driver    =    ehci_hcd 
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
irq    :    21 
memory    :    fe02c000-fe02c0ff 
id:     
ide:0 
description:     IDE interface 
product:     MCP78S [GeForce 8200] IDE 
vendor:     nVidia Corporation 
physical id:      
6 
bus info:      
pci@0000:00:06.0 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     ide pm bus_master cap_list 
configuration:     
driver    =    pata_amd 
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
irq    :    0 
ioport    :    1f0(size=8) 
ioport    :    3f6 
ioport    :    170(size=8) 
ioport    :    376 
ioport    :    f000(size=16) 
id:     
pci:0 
description:     PCI bridge 
product:     MCP78S [GeForce 8200] PCI Bridge 
vendor:     nVidia Corporation 
physical id:      
8 
bus info:      
pci@0000:00:08.0 
version:     a1 
width:     32 bits 
clock:     66MHz 
capabilities:     pci ht subtractive_decode bus_master cap_list 
resources:     
ioport    :    b000(size=8192) 
memory    :    fdd00000-fddfffff 
memory    :    fde00000-fdefffff 
id:     
usb:0 
description:     USB Controller 
product:     VT82xxxxx UHCI USB 1.1 Controller 
vendor:     VIA Technologies, Inc. 
physical id:      
8 
bus info:      
pci@0000:01:08.0 
version:     62 
width:     32 bits 
clock:     33MHz 
capabilities:     pm uhci bus_master cap_list 
configuration:     
driver    =    uhci_hcd 
latency    =    32 
resources:     
irq    :    16 
ioport    :    cc00(size=32) 
id:     
usb:1 
description:     USB Controller 
product:     USB 2.0 
vendor:     VIA Technologies, Inc. 
physical id:      
8.2 
bus info:      
pci@0000:01:08.2 
version:     65 
width:     32 bits 
clock:     33MHz 
capabilities:     pm ehci bus_master cap_list 
configuration:     
driver    =    ehci_hcd 
latency    =    32 
resources:     
irq    :    18 
memory    :    fddff000-fddff0ff 
id:     
multimedia 
description:     Multimedia audio controller 
product:     ICE1712 [Envy24] PCI Multi-Channel I/O Controller 
vendor:     VIA Technologies Inc. 
physical id:      
9 
bus info:      
pci@0000:01:09.0 
version:     02 
width:     32 bits 
clock:     33MHz 
capabilities:     pm bus_master cap_list 
configuration:     
driver    =    ICE1712 
latency    =    32 
resources:     
irq    :    17 
ioport    :    c800(size=32) 
ioport    :    c400(size=16) 
ioport    :    c000(size=16) 
ioport    :    bc00(size=64) 
id:     
ide:1 
description:     IDE interface 
product:     MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) 
vendor:     nVidia Corporation 
physical id:      
9 
bus info:      
pci@0000:00:09.0 
logical name:      
scsi2 
logical name:      
scsi4 
logical name:      
scsi5 
version:     a2 
width:     32 bits 
clock:     66MHz 
capabilities:     ide pm msi ht bus_master cap_list emulated 
configuration:     
driver    =    ahci 
latency    =    0 
maxlatency    =    1 
mingnt    =    3 
resources:     
irq    :    43 
ioport    :    9f0(size=8) 
ioport    :    bf0(size=4) 
ioport    :    970(size=8) 
ioport    :    b70(size=4) 
ioport    :    dc00(size=16) 
memory    :    fe02a000-fe02bfff 
id:     
disk:0 
description:     ATA Disk 
product:     ST3500830AS 
vendor:     Seagate 
physical id:      
0 
bus info:      
scsi@2:0.0.0 
logical name:      
/dev/sda 
version:     3.AA 
serial:     9QG5WMW3 
size:     465GiB (500GB) 
capabilities:     partitioned partitioned:dos 
configuration:     
ansiversion    =    5 
signature    =   
id:     
volume:0 
description:     Windows NTFS volume 
physical id:      
1 
bus info:      
scsi@2:0.0.0,1 
logical name:      
/dev/sda1 
version:     3.1 
serial:     
size:     98MiB 
capacity:     100MiB 
capabilities:     primary bootable ntfs initialized 
configuration:     
clustersize    =    4096 
created    =    2011-10-20 03:48:20 
filesystem    =    ntfs 
label    =    System Reserved 
state    =    clean 
id:     
volume:1 
description:     Windows NTFS volume 
physical id:      
2 
bus info:      
scsi@2:0.0.0,2 
logical name:      
/dev/sda2 
logical name:      
/host 
version:     3.1 
serial:     
size:     465GiB 
capacity:     465GiB 
capabilities:     primary ntfs initialized 
configuration:     
clustersize    =    4096 
created    =    2011-10-20 03:48:49 
filesystem    =    ntfs 
mount.fstype    =    fuseblk 
mount.options    =    rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 
state    =    mounted 
id:     
disk:1 
description:     ATA Disk 
product:     ST3500830AS 
vendor:     Seagate 
physical id:      
1 
bus info:      
scsi@4:0.0.0 
logical name:      
/dev/sdb 
version:     3.AA 
serial:    
size:     465GiB (500GB) 
capabilities:     partitioned partitioned:dos 
configuration:     
ansiversion    =    5 
signature    =    
id:     
volume 
description:     Windows NTFS volume 
physical id:      
1 
bus info:      
scsi@4:0.0.0,1 
logical name:      
/dev/sdb1 
version:     3.1 
serial:      
size:     465GiB 
capacity:     465GiB 
capabilities:     primary ntfs initialized 
configuration:     
clustersize    =    4096 
created    =    2009-02-15 08:38:11 
filesystem    =    ntfs 
label    =    Storage on D 
state    =    clean 
id:     
cdrom 
description:     DVD-RAM writer 
product:     iHAS624 B 
vendor:     ATAPI 
physical id:      
0.0.0 
bus info:      
scsi@5:0.0.0 
logical name:      
/dev/cdrom 
logical name:      
/dev/cdrw 
logical name:      
/dev/dvd 
logical name:      
/dev/dvdrw 
logical name:      
/dev/scd0 
logical name:      
/dev/sr0 
version:     GL27 
capabilities:     removable audio cd-r cd-rw dvd dvd-r dvd-ram 
configuration:     
ansiversion    =    5 
status    =    nodisc 
id:     
pci:1 
description:     PCI bridge 
product:     MCP78S [GeForce 8200] PCI Express Bridge 
vendor:     nVidia Corporation 
physical id:      
10 
bus info:      
pci@0000:00:10.0 
version:     a1 
width:     32 bits 
clock:     33MHz 
capabilities:     pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration:     
driver    =    pcieport 
resources:     
irq    :    40 
ioport    :    9000(size=8192) 
memory    :    fdb00000-fdcfffff 
ioport    :    d0000000(size=536870912) 
id:     
pci 
description:     PCI bridge 
product:     NF200 PCIe 2.0 switch for mainboards 
vendor:     nVidia Corporation 
physical id:      
0 
bus info:      
pci@0000:02:00.0 
version:     a2 
width:     32 bits 
clock:     33MHz 
capabilities:     pci pm pciexpress normal_decode bus_master cap_list 
resources:     
ioport    :    9000(size=8192) 
memory    :    fdb00000-fdcfffff 
ioport    :    d0000000(size=536870912) 
id:     
pci:0 
description:     PCI bridge 
product:     NF200 PCIe 2.0 switch for mainboards 
vendor:     nVidia Corporation 
physical id:      
0 
bus info:      
pci@0000:03:00.0 
version:     a2 
width:     32 bits 
clock:     33MHz 
capabilities:     pci pm pciexpress normal_decode bus_master cap_list 
resources:     
ioport    :    a000(size=4096) 
memory    :    fdc00000-fdcfffff 
ioport    :    eff00000(size=1048576) 
id:     
pci:1 
description:     PCI bridge 
product:     NF200 PCIe 2.0 switch for mainboards 
vendor:     nVidia Corporation 
physical id:      
2 
bus info:      
pci@0000:03:02.0 
version:     a2 
width:     32 bits 
clock:     33MHz 
capabilities:     pci pm pciexpress normal_decode bus_master cap_list 
resources:     
ioport    :    9000(size=4096) 
memory    :    fdb00000-fdbfffff 
ioport    :    d0000000(size=268435456) 
id:     
display 
description:     VGA compatible controller 
product:     Cedar PRO [Radeon HD 5450] 
vendor:     ATI Technologies Inc 
physical id:      
0 
bus info:      
pci@0000:05:00.0 
version:     00 
width:     64 bits 
clock:     33MHz 
capabilities:     pm pciexpress msi vga_controller bus_master cap_list rom 
configuration:     
driver    =    fglrx_pci 
latency    =    0 
resources:     
irq    :    45 
memory    :    d0000000-dfffffff 
memory    :    fdbc0000-fdbdffff 
ioport    :    9c00(size=256) 
memory    :    fdba0000-fdbbffff 
id:     
multimedia 
description:     Audio device 
product:     Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] 
vendor:     ATI Technologies Inc 
physical id:      
0.1 
bus info:      
pci@0000:05:00.1 
version:     00 
width:     64 bits 
clock:     33MHz 
capabilities:     pm pciexpress msi bus_master cap_list 
configuration:     
driver    =    HDA Intel 
latency    =    0 
resources:     
irq    :    44 
memory    :    fdbfc000-fdbfffff 
id:     
pci:2 
description:     PCI bridge 
product:     MCP78S [GeForce 8200] PCI Bridge 
vendor:     nVidia Corporation 
physical id:      
13 
bus info:      
pci@0000:00:13.0 
version:     a1 
width:     32 bits 
clock:     33MHz 
capabilities:     pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration:     
driver    =    pcieport 
resources:     
irq    :    41 
ioport    :    8000(size=4096) 
memory    :    fda00000-fdafffff 
ioport    :    fd900000(size=1048576) 
id:     
pci:3 
description:     PCI bridge 
product:     MCP78S [GeForce 8200] PCI Bridge 
vendor:     nVidia Corporation 
physical id:      
14 
bus info:      
pci@0000:00:14.0 
version:     a1 
width:     32 bits 
clock:     33MHz 
capabilities:     pci pm msi ht pciexpress normal_decode bus_master cap_list 
configuration:     
driver    =    pcieport 
resources:     
irq    :    42 
ioport    :    6000(size=8192) 
memory    :    fd800000-fd8fffff 
ioport    :    fd700000(size=1048576) 
id:     
ide 
description:     IDE interface 
product:     88SE6121 SATA II Controller 
vendor:     Marvell Technology Group Ltd. 
physical id:      
0 
bus info:      
pci@0000:07:00.0 
version:     b2 
width:     32 bits 
clock:     33MHz 
capabilities:     ide pm msi pciexpress bus_master cap_list 
configuration:     
driver    =    pata_marvell 
latency    =    0 
resources:     
irq    :    16 
ioport    :    7c00(size=8) 
ioport    :    7800(size=4) 
ioport    :    7400(size=8) 
ioport    :    7000(size=4) 
ioport    :    6c00(size=16) 
memory    :    fd8ff000-fd8ff3ff 
id:     
pci:4 
description:     Host bridge 
product:     Family 10h Processor HyperTransport Configuration 
vendor:     Advanced Micro Devices [AMD] 
physical id:      
100 
bus info:      
pci@0000:00:18.0 
version:     00 
width:     32 bits 
clock:     33MHz 
id:     
pci:5 
description:     Host bridge 
product:     Family 10h Processor Address Map 
vendor:     Advanced Micro Devices [AMD] 
physical id:      
101 
bus info:      
pci@0000:00:18.1 
version:     00 
width:     32 bits 
clock:     33MHz 
id:     
pci:6 
description:     Host bridge 
product:     Family 10h Processor DRAM Controller 
vendor:     Advanced Micro Devices [AMD] 
physical id:      
102 
bus info:      
pci@0000:00:18.2 
version:     00 
width:     32 bits 
clock:     33MHz 
id:     
pci:7 
description:     Host bridge 
product:     Family 10h Processor Miscellaneous Control 
vendor:     Advanced Micro Devices [AMD] 
physical id:      
103 
bus info:      
pci@0000:00:18.3 
version:     00 
width:     32 bits 
clock:     33MHz 
id:     
pci:8 
description:     Host bridge 
product:     Family 10h Processor Link Control 
vendor:     Advanced Micro Devices [AMD] 
physical id:      
104 
bus info:      
pci@0000:00:18.4 
version:     00 
width:     32 bits 
clock:     33MHz 
id:     
network 
description:     Wireless interface 
physical id:      
1 
bus info:      
usb@2:3 
logical name:      
wlan0 
serial:     00:1f:1f:4e:8b:24 
capabilities:     ethernet physical wireless 
configuration:     
broadcast    =    yes 
driver    =    rtl8187 
driverversion    =    2.6.35-22-generic 
firmware    =    N/A 
ip    =    192.168
link    =    yes 
multicast    =    yes 
wireless    =    IEEE 802.11bg

---

### Post by beefheartvliet on 2011-10-23
I have sound in Dream Studio 11.04, That will do for now. Perhaps it's the PulseAudio Jack Sink. I'm still open to suggestions that I should try. 

Thanks

---

