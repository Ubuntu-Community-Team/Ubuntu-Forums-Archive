---
title: "Cinelerra Glitchy Issues"
date: 2012-08-23
forum: Ubuntu Studio
---

### Post by pete0403 on 2012-08-23
Hi,

I'm using Cinelerra for the first time and I'm having problems.  I'm doing simple drag-and-drops of clips (audio + video) and adding dissolve/crossfade transitions.  My problem is that the transitions are incredibly glitchy.  The audio is crackling, and repeating during the transition and sometimes the same audio glitch will happen in the next transition as well even though it's different audio that's playing at that transition.  The video is jittery during transitions as well.  Rendering audio and video separately doesn't help.

Can anyone tell me what I'm doing wrong?  All preferences are set at their defaults, resource and rendering framerates are the same.

The system it's running on:
> id:    
linux1
description:     Desktop Computer
product:     System Product Name (To Be Filled By O.E.M.)
vendor:     System manufacturer
version:     System Version
serial:     System Serial Number
width:     64 bits
capabilities:     smbios-2.5 dmi-2.5 vsyscall32
configuration:    
boot    =    normal
chassis    =    desktop
family    =    To Be Filled By O.E.M.
sku    =    To Be Filled By O.E.M.
uuid    =    40164FF9-867D-DD11-B55E-002215DA0968

id:    
core
description:     Motherboard
product:     P5QL-CM
vendor:     ASUSTeK Computer INC.
physical id:     
0
version:     Rev X.0x
serial:     MT7088K08603438
slot:     To Be Filled By O.E.M.

id:    
firmware
description:     BIOS
vendor:     American Megatrends Inc.
physical id:     
0
version:     0304
date:     08/21/2008
size:     64KiB
capacity:     960KiB
capabilities:     isa pci pnp apm upgrade shadowing escd cdboot bootselect
socketedrom edd int13floppy1200 int13floppy720 int13floppy2880
int5printscreen int9keyboard int14serial int17printer int10video acpi
usb ls120boot zipboot biosbootspecification

id:    
cpu
description:     CPU
product:     Pentium(R) Dual-Core CPU E5200 @ 2.50GHz
vendor:     Intel Corp.
physical id:     
4
bus info:     
cpu@0
version:     Pentium(R) Dual-Core CPU E5200 @ 2.50GHz
serial:     To Be Filled By O.E.M.
slot:     LGA775
size:     1203MHz
capacity:     3800MHz
width:     64 bits
clock:     200MHz
capabilities:     x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce
cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse
sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good
nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm
lahf_lm cpufreq
configuration:    
cores    =    2
enabledcores    =    2
threads    =    2

id:    
cache:0
description:     L1 cache
physical id:     
5
slot:     L1-Cache
size:     64KiB
capacity:     64KiB
capabilities:     internal write-back data

id:    
cache:1
description:     L2 cache
physical id:     
6
slot:     L2-Cache
size:     2MiB
capacity:     2MiB
capabilities:     internal write-back unified

id:    
memory
description:     System Memory
physical id:     
31
slot:     System board or motherboard
size:     2GiB

id:    
bank:0
description:     DIMM DDR2 Synchronous 800 MHz (1.2 ns)
product:     PartNum0
vendor:     Manufacturer0
physical id:     
0
serial:     SerNum0
slot:     DIMM A1
size:     1GiB
width:     64 bits
clock:     800MHz (1.2ns)

id:    
bank:1
description:     DIMM DDR2 Synchronous 800 MHz (1.2 ns)
product:     PartNum1
vendor:     Manufacturer1
physical id:     
1
serial:     SerNum1
slot:     DIMM B1
size:     1GiB
width:     64 bits
clock:     800MHz (1.2ns)

id:    
multimedia
description:     Audio device
product:     82801JI (ICH10 Family) HD Audio Controller
vendor:     Intel Corporation
physical id:     
1b
bus info:     
pci@0000:00:1b.0
version:     00
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list
configuration:    
driver    =    snd_hda_intel
latency    =    0

resources:    
irq    :    45
memory    :    f9ff8000-f9ffbfff


---

### Post by pete0403 on 2012-08-23
I captured the video using dvgrab. Maybe I should have used .dv2 instead of .dv so I had separate audio and video files?
 
 
Edit: It's just the transitions. If I use keyframes to transition, it works fine. Weird.
 
Edit 2: I think it may have something to do with the way Cinelerra handles transitions when the edits don't overlap enough (using a freeze frame of the preceeding edit).  It's probably doing the same thing to the audio since it's rawDV.  I'm going to try adding edits to the timeline with an "in point" or just using different video/audio tracks and keyframes and see how that works out.  The guy who wrote that "Cinelerra for Grandma" site deserves the Nobel Prize.

---

