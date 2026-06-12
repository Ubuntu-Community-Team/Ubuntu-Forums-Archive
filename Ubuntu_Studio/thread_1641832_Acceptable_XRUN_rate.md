---
title: "Acceptable XRUN rate?"
date: 2010-12-09
forum: Ubuntu Studio
---

### Post by woolyg on 2010-12-09
Hi all,

I'm new to Ardour / Jack / Ubuntu Studio, and am trying to tweak my environment so that its as stable as can be.

My question is - what's an acceptable Xrun rate?

I'm recording at 96k, with the following settings:

Priority:70
Frames/Period:512
Sample Rate:96000
Periods/Buffer:3
Port Maximum:256
Timeout:500 Msec
Start Delay (secs): 2
Interface: hw:0
Audio: Duplex
Input Channels: 8
Output Channels:8

In JACK, the Xrun is showing at 2( 8 ), after using a session for about 10 mins (I basically added 1 audio track, and sent it to a bus, and applied some effects, reverb, delay, etc, to the bus). Is this acceptable? Should it always be at 0 for a quality recording?

Since starting this post, the data has raised to 2(13), and I'm not even in the active Ardour window.

Should I re-tweak my settings to try to mitigate Xruns - if so, how?

All input appreciated, still tyring to get my head around this whole thing.

Regards,
WoolyG

---

### Post by AutoStatic on 2010-12-09
> **woolyg said:**
> My question is - what's an acceptable Xrun rate?No xrun at all.

> **woolyg said:**
> In JACK, the Xrun is showing at 2( 8 ), after using a session for about 10 mins (I basically added 1 audio track, and sent it to a bus, and applied some effects, reverb, delay, etc, to the bus). Is this acceptable? Should it always be at 0 for a quality recording?Yes. And with your JACK settings that should be possible.

> **woolyg said:**
> Should I re-tweak my settings to try to mitigate Xruns - if so, how?It's probably not your JACK settings but the overall configuration of your system. You might want to check here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

But what are the specs of your system? And which kernel are you using? Could you post the outcome of the terminal command **ffado-diag** (you&#314;l need to install the ffado-tools package first if it's not installed yet)?

Best,

Jeremy

---

### Post by cchhrriiss121212 on 2010-12-09
Using 96KHz is not worth it IMO, people cannot hear at this level of detail. You will see better stability with 48KHz.

---

### Post by woolyg on 2010-12-09
Thanks AutoStatic,

I'll get those details asap and post them back here.

---

### Post by woolyg on 2010-12-09
Here's the output of ffado-diag:
-----------------------------------------------





FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
Base system...
kernel version............ 2.6.35-23-generic
FIXME: implement test for RT kernel
RT patched............... False
old 1394 stack present.... True
old 1394 stack loaded..... False
old 1394 stack active..... False
new 1394 stack present.... True
new 1394 stack loaded..... True
new 1394 stack active..... True
/dev/raw1394 node present. False
Prerequisites (dynamic at run-time)...
gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
g++ ............... sh: g++: not found
PyQt4 (by pyuic4) . sh: pyuic4: not found
jackd ............. no message buffer overruns
path ............ /usr/bin/jackd
flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
flags ........... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
flags ........... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
flags ........... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
flags ........... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
dbus-1 ............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
flags ........... Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
Prerequisites (static at compile-time)...
gcc ............... gcc (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
g++ ............... g++ (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
jackd ............. sh: jackd: not found
path ............ 
flags ........... Package jack was not found in the pkg-config search path.
libraw1394 ........ 2.0.5
flags ........... -lraw1394 
libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
flags ........... Package libavc1394 was not found in the pkg-config search path.
libiec61883 ....... 1.2.0
flags ........... -liec61883 -lraw1394 
libxml++-2.6 ...... 2.30.0
flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0 
dbus-1 ............ 1.2.24
flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -L/lib -ldbus-1 -lpthread -lrt 
Hardware...
Host controllers:
05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10 [OHCI])
Subsystem: ASUSTeK Computer Inc. IEEE 1394a Firewire Controller [1043:8294]
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
Interrupt: pin A routed to IRQ 19
Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: firewire_ohci
Kernel modules: firewire-ohci, ohci1394

CPU info:
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
stepping : 10
cpu MHz : 3003.000
cache size : 6144 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 2
apicid : 0
initial apicid : 0
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips : 5998.84
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:

processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
stepping : 10
cpu MHz : 2003.000
cache size : 6144 KB
physical id : 0
siblings : 2
core id : 1
cpu cores : 2
apicid : 1
initial apicid : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips : 5999.22
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:

Configuration...
IRQ information
Hardware Interrupts:
--------------------
IRQ 0: PID: None, count: [44, 44], Sched None (priority None), drivers: ['timer']
IRQ 1: PID: None, count: [1, 1], Sched None (priority None), drivers: ['i8042']
IRQ 6: PID: None, count: [2, 2], Sched None (priority None), drivers: ['floppy']
IRQ 8: PID: None, count: [1, 1], Sched None (priority None), drivers: ['rtc0']
IRQ 9: PID: None, count: [0, 0], Sched None (priority None), drivers: ['acpi']
IRQ 12: PID: None, count: [3, 3], Sched None (priority None), drivers: ['i8042']
IRQ 16: PID: None, count: [39, 39], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'pata_marvell', 'nouveau']
IRQ 18: PID: None, count: [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb5', 'uhci_hcd:usb8']
IRQ 19: PID: None, count: [35142, 35142], Sched None (priority None), drivers: ['ata_piix', 'ata_piix', 'uhci_hcd:usb7', 'firewire_ohci']
IRQ 21: PID: None, count: [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
IRQ 23: PID: None, count: [1, 1], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb6']
IRQ 44: PID: None, count: [686, 686], Sched None (priority None), drivers: ['hda_intel']
IRQ 45: PID: None, count: [37, 37], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

---

### Post by trulan on 2010-12-09
Could you post the output of:
```
cat /proc/interrupts
```The reason I ask is, on my laptop the wireless card shares an irq with the firewire chip, and if wireless is turned on I get a lot of xruns.  There's no reason you should put up with any xruns at all with your system specs - you've got a lot more of a computer than I do.

Here's the specs you posted in the other thread, just for everybody's reference:
> **woolyg said:**
> The process I'm using is:

1. Boot up OS
2. Turn firepod on
3. Start JACK
.. and it's working fine.

Simple enough, and it's working fine.

It's a pretty good hardware setup:
Intel Core 2 3GHz
4GB paged ram, 8GB installed (utilised in other OS on machine)
Asus P5Q Mobo, S775, 1600Mhz FSB
Asus EN9600GT Black Pearl 512M Graphics

..and I'm utilising the in-built firewire port on the motherboard to port out to the firepod.

---

### Post by woolyg on 2010-12-09
Hey Trulan,
Should I run this command while JACK is running, yeah?

I'll get this info as soon as I can.
Thanks.

---

### Post by AutoStatic on 2010-12-10
```
Configuration...
IRQ information
Hardware Interrupts:
--------------------
IRQ 0: PID: None, count: [44, 44], Sched None (priority None), drivers: ['timer']
IRQ 1: PID: None, count: [1, 1], Sched None (priority None), drivers: ['i8042']
IRQ 6: PID: None, count: [2, 2], Sched None (priority None), drivers: ['floppy']
IRQ 8: PID: None, count: [1, 1], Sched None (priority None), drivers: ['rtc0']
IRQ 9: PID: None, count: [0, 0], Sched None (priority None), drivers: ['acpi']
IRQ 12: PID: None, count: [3, 3], Sched None (priority None), drivers: ['i8042']
IRQ 16: PID: None, count: [39, 39], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'pata_marvell', 'nouveau']
IRQ 18: PID: None, count: [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb5', 'uhci_hcd:usb8']
IRQ 19: PID: None, count: [35142, 35142], Sched None (priority None), drivers: ['ata_piix', 'ata_piix', 'uhci_hcd:usb7', 'firewire_ohci']
IRQ 21: PID: None, count: [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
IRQ 23: PID: None, count: [1, 1], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb6']
IRQ 44: PID: None, count: [686, 686], Sched None (priority None), drivers: ['hda_intel']
IRQ 45: PID: None, count: [37, 37], Sched None (priority None), drivers: ['eth0']
```So the FireWire controller shares an IRQ with your SATA controllers and an USB port. Using rtirq might help maybe. But then you'll need a real-time kernel, not sure where you can get it for 10.10 though as it's not available in the standard repositories. rtirq-init is available though. So 10.10 doesn't conme with a real-time kernel but it does come with an init script that can only be used with real-time kernels :???:

---

### Post by trulan on 2010-12-10
Oops, sorry. forget my last post, I didn't realize the irq information was all there in the ffado-diag report. 

And now I'm not sure what to say - even an RT kernel with all the tweakings doesn't help me when firewire is fighting for its irq with wireless.

---

### Post by hanzomon4 on 2011-01-21
I'm also having a high number of xruns with a presonus firebox. I'm running 10.10 on a macbook pro 2008 model. 

```

FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-24-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... sh: g++: not found
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags ........... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
     flags ........... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags ........... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags ........... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1 ............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
     flags ........... Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.5
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.2.24
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
0d:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 02) (prog-if 10 [OHCI])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 248 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at 97104000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at 97100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 2200.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 4389.54
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 4388.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [167458, 167458], Sched None (priority None), drivers: ['timer']
 IRQ    8: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [5378, 5378], Sched None (priority None), drivers: ['acpi']
 IRQ   14: PID:  None, count:       [2316, 2316], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count:       [2184, 2184], Sched None (priority None), drivers: ['uhci_hcd:usb4', 'uhci_hcd:usb5', 'ath9k', 'nvidia']
 IRQ   18: PID:  None, count:       [7636, 7636], Sched None (priority None), drivers: ['ata_piix', 'uhci_hcd:usb6']
 IRQ   19: PID:  None, count:   [646058, 646058], Sched None (priority None), drivers: ['firewire_ohci']
 IRQ   20: PID:  None, count:         [132, 132], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb3']
 IRQ   21: PID:  None, count:     [17660, 17660], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb7']
 IRQ   40: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pciehp']
 IRQ   41: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pciehp']
 IRQ   42: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pciehp']
 IRQ   43: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pciehp']
 IRQ   44: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pciehp']
 IRQ   45: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['sky2']
 IRQ   46: PID:  None, count:         [362, 362], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.



```
```

# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc firewire snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

# On kernel configurations that support it,
# which services should be NOT threaded 
# (space separated list).
RTIRQ_NON_THREADED="rtc firewire snd"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
# RTIRQ_HIGH_LIST="timer"


```

My jack settings (pic attached) seem reasonable. Anything seem out of place?

---

### Post by AutoStatic on 2011-01-22
Hi hanzomon, try a periods/buffer setting of 3, that should work better for FireWire and USB devices. And did you fix or disable CPU scaling? You could try doing that also. And what I find a huge showstopper is the apt-xapian-index package, I always uninstall that one (this will disable the 'Quick search' option in Synaptic). And did you already take a look here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

---

### Post by mango42 on 2011-01-22
> **AutoStatic said:**
> And did you fix or disable CPU scaling?

I seem to remember that you know a way of making this setting permanent on a per-user basis (rather than having to enter password every time CPU speed is changed)?

Back on topic, I use Xruns 'creatively' on this old Thinkpad ;-)

ps: Super grateful thanks to you, I do believe I *finally** having a working Saffire 40 (* the main problem being waiting for someone to come along with a windows machine with firewire so I could reset the firmware!) - off to test it with your PPA of the brandy-new 0.4.8 Qtractor right now :KS

---

### Post by hanzomon4 on 2011-01-22
Thanks sir, that worked out great. I'm still getting xruns but only under heavy load, when adding plugins to ardour while the transport is running, and rarely for no  discernible reason. That's with latency of 17ms, although I can push it to 8, with the stock kernel. I'd call that a win for now.

---

### Post by hanzomon4 on 2011-01-23
urgh... I'm still getting xruns, I noticed that cpu usage is much higher on my firewire audio then on my internal, is that normal?

---

### Post by AutoStatic on 2011-01-24
> **mango42 said:**
> I seem to remember that you know a way of making this setting permanent on a per-user basis (rather than having to enter password every time CPU speed is changed)?Yes, then I have to dig up some scripts, probably just a sudo command to activate the performance governor. But you'll still have to enter a password (unless you use a keyring), a user is by default not allowed to change the governor of a CPU.

> **mango42 said:**
> ps: Super grateful thanks to you, I do believe I *finally** having a working Saffire 40 (* the main problem being waiting for someone to come along with a windows machine with firewire so I could reset the firmware!) - off to test it with your PPA of the brandy-new 0.4.8 Qtractor right now :KSYou're welcome! 0.4.8 works great here, finally I can actually do something with LV2 plug-ins that have GTK UI's (like the Invada plug-ins and the recent [IR LV2 plug-in]("http://factorial.hu/plugins/lv2/ir")).

Best,

Jeremy

---

### Post by AutoStatic on 2011-01-24
> **hanzomon4 said:**
> urgh... I'm still getting xruns, I noticed that cpu usage is much higher on my firewire audio then on my internal, is that normal?No. What Desktop Environment (DE) are you using? KDE, Gnome? And do you use Compiz (ie. do you have desktop effects enabled)? And try disabling the NetworkManager with **sudo service network-manager stop** or by disabling Wifi altogether with **sudo modprobe -r ath9k**. Apparently the background scanning activities of NetworkManager could cause xruns.

Best,

Jeremy

---

### Post by hanzomon4 on 2011-01-24
Yeah, gnome+compiz, nvidia gfx. I tried disabling wifi and bluetooth. It's weird because my internal card's idle cpu usage in jack is like 0.9% with the firewire it's like 1.50 to 3%

---

### Post by AutoStatic on 2011-01-24
> **hanzomon4 said:**
> Yeah, gnome+compiz, nvidia gfx.Did you try disabling Compiz?

> **hanzomon4 said:**
> I tried disabling wifi and bluetooth.And did it help?

> **hanzomon4 said:**
> It's weird because my internal card's idle cpu usage in jack is like 0.9% with the firewire it's like 1.50 to 3%Ah, when reading "much higher" I thought, no that's not normal, but we're talking 0.5 to 2% difference. That's nothing to worry about I guess.

---

### Post by hanzomon4 on 2011-01-25
Haven't disabled compiz yet. Disabling Bluetooth didn't make a difference and disabling wifi helped a little. I would get an xrun if wifi lost connection.

I had made a mistake with the governor by setting it to performance instead of locking it set clock. After evaluating what I was doing I've come to the conclusion that I was simply over taxing my system. For test I had been running seq24, 4 qsynths, 2 hydrogens, and ardour for recording it all. I only have 2gigs of ram and a 2.2 core 2 duo circa 2008.

---

### Post by AutoStatic on 2011-01-25
Qsynth could be a major xrun generator and running 4 of those is asking for trouble ;) And the performance governor locks the CPU to its highest frequency.

---

### Post by hanzomon4 on 2011-01-25
yeah it's a beast but it sounds so good! by the way thanks so much for your help

---

### Post by mango42 on 2011-01-31
How do I run the **rtirq** script to get the result shown on the alsa page at [http://alsa.opensrc.org/Rtirq](http://alsa.opensrc.org/Rtirq) ?

This is my result so far:-

```
root@xxxxxxx:/etc/init.d# sh rtirq
rtirq: 65: source: not found
rtirq: 74: Syntax error: "(" unexpected
```

User error for sure - I'm probably on the wrong page entirely ;-)

I've just done a fresh (fastest yet, including wifi and system updates) install of UbuntuStudio 10.04 and decided to get the internal soundcard working before the firewire (which I know works now so long as I leave the ffado mixer entirely out of the equation!). Unfortunately **cat /proc/interrupts** shows:-

```
22: 390 IO-APIC-fasteoi  sata_nv, NVidia CK804
```

...and I've forgotten me sata_nv's and pata_amd's relative significance...

---

### Post by AutoStatic on 2011-01-31
> **mango42 said:**
> How do I run the **rtirq** script to get the result shown on the alsa page at [http://alsa.opensrc.org/Rtirq](http://alsa.opensrc.org/Rtirq) ?**sudo /etc/init.d/rtirq restart**

rtirq is an init script so you can't start it by running **sh rtirq**.

Best,

Jeremy

---

### Post by mango42 on 2011-01-31
At this rate, I'll be putting you high in my song credits, FWIW! :KS

I used **$ sh rtirq.sh** from that alsa page - teaches me, once again, to check when pages were last updated, I guess.

Anyway, no matter what I do, I'm still getting massive xruns running nothing but Jackd. Perhaps I should specify "NVidia CK804" instead of just **snd** on the RTIRQ_NAME_LIST="rtc snd usb i8042" line?

ps: Just in case you are wondering why I should even *want* to do this when I have such a gorgeous sounding Saffire; the reason is simple - my cottage runs entirely on solar power and at this time of the year, every watt counts, despite washing machines taking priority even over rtirq-init! ;-)

---

### Post by AutoStatic on 2011-01-31
> **mango42 said:**
> At this rate, I'll be putting you high in my song credits, FWIW! :KS ;) Cool!

> **mango42 said:**
> Anyway, no matter what I do, I'm still getting massive xruns running nothing but Jackd. Perhaps I should specify "NVidia CK804" instead of just **snd** on the RTIRQ_NAME_LIST="rtc snd usb i8042" line?snd should do the trick, but you could try replacing it with CK804. I don't think it will make a difference though. FYI, I have issues with my onboard soundcard and JACK also. These issues disappear when I install the linux-backports-modules-alsa-lucid-generic package but since there is no such package for the real-time kernel I can't really use my onboard card with such a kernel.

> **mango42 said:**
> ps: Just in case you are wondering why I should even *want* to do this when I have such a gorgeous sounding Saffire; the reason is simple - my cottage runs entirely on solar power and at this time of the year, every watt counts, despite washing machines taking priority even over rtirq-init! ;-)Yeah, our panels are doing nothing either. But thanks for bringing this up, reminds me I have to make an appointment with the company I ordered another 3 panels with ;)
So yes, I understand your point completely, even though our household doesn't run completely on solar power.

Best,

Jeremy

---

### Post by trulan on 2011-02-01
> **mango42 said:**
> Anyway, no matter what I do, I'm still getting massive xruns running nothing but Jackd. Perhaps I should specify "NVidia CK804" instead of just **snd** on the RTIRQ_NAME_LIST="rtc snd usb i8042" line?
No don't do that - every space in the RTIRQ_NAME_LIST denotes a new object, so if you put 'NVidia CK804' in there, it will attempt to set 'NVidia' to one priority and 'CK804' to another.  And who knows what else NVidia may be in there, so that could really mess things up.  Putting 'CK804' in there shouldn't hurt anything, but 'snd' should do the same thing.

---

