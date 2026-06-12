---
title: "EDIROL FA-66 sound card"
date: 2011-01-29
forum: Ubuntu Studio
---

### Post by themoth on 2011-01-29
Hello everyone,
 I'm trying to run a EDIROL FA-66.
 I have a Ubuntu Studio 10.04 64bit on my computer.
 I followed the guide for configuring the device firewire.
 I write what I read in the message window of jack:
```
 p, li { white-space: pre-wrap; } [COLOR=#999999]22:01:57.547 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:01:57.625 Statistics reset.[/COLOR]
 [COLOR=#66cc99]22:01:57.656 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]22:01:57.853 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:02:06.732 Startup script...[/COLOR]
 [COLOR=#990099]22:02:06.733 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:02:07.134 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:02:07.134 JACK is starting...[/COLOR]
 [COLOR=#990099]22:02:07.134 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2 -i4 -o4[/COLOR]
 [COLOR=#999999]22:02:07.137 JACK was started with PID=1758.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    3044649
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 libffado 2.0.0 built Mar 31 2010 16:21:44
 [COLOR=#999933]22:02:09.261 Server configuration saved to "/home/tommaso/.jackdrc".[/COLOR]
 [COLOR=#999999]22:02:09.262 Statistics reset.[/COLOR]
 [COLOR=#999999]22:02:09.505 Client activated.[/COLOR]
 [COLOR=#cc9966]22:02:09.507 JACK connection graph change.[/COLOR]
 SSE2 detected
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)
 [COLOR=#999999]22:02:10.379 Client deactivated.[/COLOR]
 cannot
 [COLOR=#999999]22:02:10.380 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]22:02:10.380 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:02:10.381 killall jackd[/COLOR]
  continue execution of the processing graph (Pipe interrotta)
 cannot continue execution of the processing graph (Pipe interrotta)

```

 I do not understand how to solve this problem.
 Thanks to all.
 and sorry for my bad English.

---

### Post by gordintoronto on 2011-01-29
You should say what the source is for the things you are trying. Have you looked at:
[http://www.ardour.org/node/1732](http://www.ardour.org/node/1732)

It takes a little extra techie knowledge to use weird hardware.

---

### Post by themoth on 2011-01-30
I add some information may be helpful.

if I run "ffado-test discover" I get:
```

02241535322: Error (bebob_avdevice.cpp)[ 794] saveCache: Could not create "/home/tommaso/.ffado/cache" directory
no message buffer overruns

```

if I run "ffado-diag" I get:
```
=== CHECK ===
 Base system...
  kernel version............ 2.6.32-27-preempt
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
     flags............ Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394......... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags............ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
   libavc1394......... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
     flags............ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883........ Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags............ Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6....... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags............ Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1............. Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
     flags............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
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
08:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8294]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping    : 10
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5666.11
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping    : 10
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5665.78
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping    : 10
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5665.82
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping    : 10
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5665.80
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [279917, 279917, 279917, 279917], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:       [2, 2, 2, 2], Sched None (priority None), drivers: ['i8042']
 IRQ    4: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count: [77013, 77013, 77013, 77013], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count: [23359, 23359, 23359, 23359], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'pata_marvell', 'nvidia']
 IRQ   18: PID:  None, count: [245, 245, 245, 245], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb5', 'uhci_hcd:usb8', 'nvidia']
 IRQ   19: PID:  None, count:   [18, 18, 18, 18], Sched None (priority None), drivers: ['uhci_hcd:usb7', 'ohci1394']
 IRQ   21: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   22: PID:  None, count: [416, 416, 416, 416], Sched None (priority None), drivers: ['HDA Intel']
 IRQ   23: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb6']
 IRQ   28: PID:  None, count: [978, 978, 978, 978], Sched None (priority None), drivers: ['ahci']
 IRQ   29: PID:  None, count:   [18, 18, 18, 18], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

```
 cannot continue execution of the processing graph (Pipe interrotta)[/code]

I am reading the topic you suggested but it is a bit 'too advanced for me.
 thanks anyway.

---

### Post by AutoStatic on 2011-01-30
Looks good to me. But try a periods/buffer setting of 3 and don't set the number of capture and playback ports. And could you also post the output of **ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq"** ?

Best,

Jeremy

---

### Post by themoth on 2011-01-30
> **AutoStatic said:**
> Looks good to me. But try a periods/buffer setting of 3 and don't set the number of capture and playback ports. 

  Many thanks Jeremy.
I set a periods/buffer of 3, but I don't know where I can find the port's settings...
I'm sorry I'm glad you are so helpful with me .


> **AutoStatic said:**
> 
And could you also post the output of **ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq"** ?


```
$ ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq"
    4  TS      -  19   0 [ksoftirqd/0]
    7  TS      -  19   0 [ksoftirqd/1]
   10  TS      -  19   0 [ksoftirqd/2]
   13  TS      -  19   0 [ksoftirqd/3]
 1058  TS      -  19   0 /usr/sbin/irqbalance
 2093  TS      -  19   0 grep --color=auto -i irq

```

Many thanks Jeremy.

---

### Post by AutoStatic on 2011-01-30
> **themoth said:**
> I set a periods/buffer of 3, but I don't know where I can find the port's settings...Input/Output Channels in QjackCtl. You've set them to 4, just leave it on (default).

> **themoth said:**
> ```
$ ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq"
    4  TS      -  19   0 [ksoftirqd/0]
    7  TS      -  19   0 [ksoftirqd/1]
   10  TS      -  19   0 [ksoftirqd/2]
   13  TS      -  19   0 [ksoftirqd/3]
 1058  TS      -  19   0 /usr/sbin/irqbalance
 2093  TS      -  19   0 grep --color=auto -i irq

```Somehow I assumed you were running a real-time kernel, but I now see you're running a preempt kernel. In your case you might benefit from installing the **linux-rt** and **rtirq-init** packages. Could you try that? And then you need to modify the */etc/default/rtirq* file so that the RTIRQ_NAME_LIST line looks like this:```
RTIRQ_NAME_LIST="rtc ohci1394 usb i8042"
```Then reboot into the real-time kernel and try starting JACK again.

---

