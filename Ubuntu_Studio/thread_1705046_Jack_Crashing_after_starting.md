---
title: "Jack Crashing after starting"
date: 2011-03-11
forum: Ubuntu Studio
---

### Post by Raikonex on 2011-03-11
After a few hours working on getting jack to work I've finally managed to get it to start. However it stops running shortly afterwards. I'm using a presonus FP10 as my soundcard and the status light turns blue after Jack starts, indicating that it's properly connected to the computer, but then jack shuts down and it goes back to red. I've posted the text from the message window below, I had no luck with google so I'm hoping someone here can help me

 p, li { white-space: pre-wrap; }  [COLOR=#999999]15:13:52.219 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:13:52.223 Statistics reset.[/COLOR]
 [COLOR=#66CC99]15:13:52.269 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]15:13:52.449 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:13:56.528 Startup script...[/COLOR]
 [COLOR=#990099]15:13:56.528 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:13:56.930 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:13:56.930 JACK is starting...[/COLOR]
 [COLOR=#990099]15:13:56.930 /usr/bin/jackd -dfirewire -r44100 -p1024 -n3[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]15:13:56.933 JACK was started with PID=26479.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 libffado 2.0.0 built Mar 31 2010 14:47:42
 [COLOR=#999933]15:13:59.067 Server configuration saved to "/home/tyler/.jackdrc".[/COLOR]
 [COLOR=#999999]15:13:59.068 Statistics reset.[/COLOR]
 [COLOR=#999999]15:13:59.104 Client activated.[/COLOR]
 [COLOR=#9999CC]15:13:59.105 JACK connection change.[/COLOR]
 [COLOR=#996633]15:13:59.106 Buffer size change (1024).[/COLOR]
 firewire ERR: wait status < 0! (= -1)
 DRIVER NT: could not run driver cycle
 [COLOR=#CC9966]15:14:01.733 JACK connection graph change.[/COLOR]
 jack main caught signal 12
 [COLOR=#CC6666]15:14:01.905 Shutdown notification.[/COLOR]
 [COLOR=#999999]15:14:01.905 JACK is stopping...[/COLOR]
 [COLOR=#999999]15:14:01.905 JACK is being forced...[/COLOR]
 no message buffer overruns
 cannot read server event (Success)
 cannot continue execution of the processing graph (Bad file descriptor)
 zombified - calling shutdown handler
 [COLOR=#999999]15:14:02.106 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]15:14:02.106 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:14:02.106 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]15:14:02.513 Post-shutdown script terminated with exit status=256.[/COLOR]

[COLOR=#999999][/COLOR]
[COLOR=#999999]
[/COLOR]

---

### Post by AutoStatic on 2011-03-11
Hello Raikonex,

```
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
```Probably you're FireWire controller shares its IRQ. Could you post the outcome of the terminal command **ffado-diag** ? Maybe you need to install the **ffado-tools** first if you didn't do so already.

Best,

Jeremy

---

### Post by Raikonex on 2011-03-11
Alright, It's pretty long, but hopefully you can find some useful information in here.  I also checked and I DO have ffado-tools installed.

FFADO diagnostic utility 0.1
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.32-24-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... True
  old 1394 stack active..... True
  new 1394 stack present.... True
  new 1394 stack loaded..... False
  new 1394 stack active..... False
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites (dynamic at run-time)...
   gcc................ gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   g++................ g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   PyQt............... sh: pyuic: not found
   jackd.............. jackd version 0.118.0 tmpdir /dev/shm protocol 24
     path............. /usr/bin/jackd
     flags............  -ljack -lpthread -lrt  
   libraw1394......... 2.0.4
     flags............  -lraw1394  
   libavc1394......... 0.5.3
     flags............  -lavc1394 -lrom1394 -lraw1394  
   libiec61883........ 1.2.0
     flags............  -liec61883 -lraw1394  
   libxml++-2.6....... 2.30.0
     flags............ -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1............. 1.2.16
     flags............ -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Prerequisites (static at compile-time)...
   gcc................ gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   g++................ g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   PyQt............... sh: pyuic: not found
   jackd.............. sh: jackd: not found
     path............. 
     flags............ Package jack was not found in the pkg-config search path.
   libraw1394......... 2.0.4
     flags............  -lraw1394  
   libavc1394......... Package libavc1394 was not found in the pkg-config search path.
     flags............ Package libavc1394 was not found in the pkg-config search path.
   libiec61883........ 1.2.0
     flags............  -liec61883 -lraw1394  
   libxml++-2.6....... 2.26.1
     flags............ -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1............. 1.2.16
     flags............ -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
04:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023] (prog-if 10)
    Subsystem: nVidia Corporation Device [10de:cb84]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
    Latency: 64 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at bfdff000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at bfdf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.02
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.53
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.45
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.46
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5591.98
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 5
initial apicid    : 5
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
stepping    : 5
cpu MHz        : 2801.514
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 7
initial apicid    : 7
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5603.53
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [46, 46, 46, 46, 46, 46, 46, 46], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count: [4, 4, 4, 4, 4, 4, 4, 4], Sched None (priority None), drivers: ['i8042']
 IRQ    4: PID:  None, count: [5, 5, 5, 5, 5, 5, 5, 5], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count: [6, 6, 6, 6, 6, 6, 6, 6], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count: [156567, 156567, 156567, 156567, 156567, 156567, 156567, 156567], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb7', 'nouveau']
 IRQ   18: PID:  None, count: [1509, 1509, 1509, 1509, 1509, 1509, 1509, 1509], Sched None (priority None), drivers: ['uhci_hcd:usb4', 'uhci_hcd:usb8', 'ath9k']
 IRQ   19: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ata_piix', 'uhci_hcd:usb5', 'uhci_hcd:usb6', 'ohci1394']
 IRQ   21: PID:  None, count: [39, 39, 39, 39, 39, 39, 39, 39], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'eth0']
 IRQ   22: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['HDA Intel']
 IRQ   23: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb9']
 IRQ   24: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['aerdrv']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

---

### Post by Raikonex on 2011-03-11
I've restarted my computer to see if that would help and now jack won't start at all, I'm getting this in the message window:

p, li { white-space: pre-wrap; } [COLOR=#999999]16:02:54.139 JACK was started with PID=2112.[/COLOR]
 loading driver ..
 libffado 2.0.0 built Mar 31 2010 14:47:42
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 [COLOR=#999999]16:02:54.294 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]16:02:54.295 Post-shutdown script...[/COLOR]
 [COLOR=#990099]16:02:54.295 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]16:02:54.701 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]16:02:56.318 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server.

[/COLOR]EDIT:

Using the commands modprobe raw1394 and chmod a+rw /dev/raw1394 seemed to have gotten it to start but it doesn't appear to be permanent after a reboot. It also doesn't fix the crashing problem

---

### Post by AutoStatic on 2011-03-11
Thanks,

```
IRQ 19: PID: None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ata_piix', 'uhci_hcd:usb5', 'uhci_hcd:usb6', 'ohci1394']
```So your FireWire controller shares its IRQ with two USB ports and a SATA controller. So you'll have to prioritize the FireWire controller. I'd suggest installing a real-time kernel, preferrably the one from Tango Studio: [http://tangostudio.tuxfamily.org/en/kernel-rt](http://tangostudio.tuxfamily.org/en/kernel-rt)

The you'll need the **rtirq-init** package and then proceed with step 5 form the help page here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

This will give the FireWire controller priority over the USB ports and the SATA controller and should prevent the JACK error from happening. Hopefully :)

Best,

Jeremy

---

### Post by Raikonex on 2011-03-11
Awesome! Thanks, I'll have a look at it and see what I can do, hopefully I'll be able to get it working

---

### Post by Raikonex on 2011-03-11
No luck. The new kernel seemed to have caused some problems with my display driver to but I managed to fix that, kinda.

only after running the commands modprobe raw1394 and chmod a+rw /dev/raw1394 did i get jack to start, but it still crashed after that. Here's what I got 

p, li { white-space: pre-wrap; } firewire ERR: Could not start streaming threads: -1
 DRIVER NT: could not start driver
 cannot start driver
 no message buffer overruns
 cannot read server event (Success)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)

---

### Post by Raikonex on 2011-03-12
I got it working! I reinstalled ubuntu and installed the ubuntu studio upgrade pack. I also set raw1394 permissions for the audio group which I think I may have forgotten to do previously.

---

### Post by AutoStatic on 2011-03-13
Great! Enjoy your setup!

Best,

Jeremy

---

