---
title: "Behringer FCA202 and Syba PCI-e Firewire card"
date: 2012-10-31
forum: Ubuntu Studio
---

### Post by Pariah819 on 2012-10-31
Hello all,

I recently purchased a Shuttle PC to use for various video and audio tasks and I have been having trouble getting my FCA202 to work.  According to ffado.org this is a supported device but I'm thinking my problem is more firewire related than the actual FCA202.  I am running Ubuntu 12.04 LTS and have installed the video/audio applications individually.  Here is the output of a few commands that I've tried...

> 
lspci | grep 1394

06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 10)
> 
dmesg | grep ohci

[    2.927630] firewire_ohci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.927642] firewire_ohci 0000:06:00.0: setting latency timer to 64
[    2.988992] firewire_ohci: Added fw-ohci device 0000:06:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10
So I think the system is recognizing my Firewire card but I get the following error from FFADO...

> 
ffado-test Discover

02262568236: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
Any help would be greatly appreciated!

---

### Post by Pariah819 on 2012-10-31
I thought I would also post the results of another FFADO command...

```

> ffado-diag

FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 3.2.0-32-generic
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
   g++ ............... sh: 1: g++: not found
   PyQt4 (by pyuic4) . sh: 1: pyuic4: not found
   jackd ............. jackdmp 1.9.8
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
   gcc ............... gcc (Ubuntu/Linaro 4.6.2-14ubuntu2) 4.6.2
   g++ ............... g++ (Ubuntu/Linaro 4.6.2-14ubuntu2) 4.6.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.9.1 for Qt version 4.8.0
   jackd ............. sh: 1: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.7
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.34.1
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  
   dbus-1 ............ 1.4.16
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
06:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380] (rev 10) (prog-if 10 [OHCI])
    Subsystem: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f7c01000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at f7c00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 42
Stepping:              7
CPU MHz:               1600.000
BogoMIPS:              6585.00
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [72, 72, 72, 72], Sched None (priority None), drivers: ['timer']
 IRQ    8: PID:  None, count:       [1, 1, 1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   16: PID:  None, count: [175, 175, 175, 175], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'firewire_ohci']
 IRQ   23: PID:  None, count:   [45, 45, 45, 45], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   41: PID:  None, count: [29142, 29142, 29142, 29142], Sched None (priority None), drivers: ['ahci']
 IRQ   42: PID:  None, count: [5985, 5985, 5985, 5985], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   43: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   44: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   45: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   46: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   47: PID:  None, count: [141719, 141719, 141719, 141719], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   48: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   49: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   50: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   51: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   52: PID:  None, count: [751189, 751189, 751189, 751189], Sched None (priority None), drivers: ['eth0']
 IRQ   53: PID:  None, count:   [13, 13, 13, 13], Sched None (priority None), drivers: ['mei']
 IRQ   54: PID:  None, count: [23172, 23172, 23172, 23172], Sched None (priority None), drivers: ['i915']
 IRQ   55: PID:  None, count: [1456, 1456, 1456, 1456], Sched None (priority None), drivers: ['snd_hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This is still kind of experimental. If you encounter problems, please also check
with the old stack.

```It looks like the /dev/raw1394 is missing but I thought I had all the packages installed, is there something I'm missing?

---

### Post by jejeman on 2012-11-01
Give output
```
dmesg | grep fw
```
```
ls /dev/fw*
```
> It looks like the /dev/raw1394 is missingThat's normal for 12.04. New firewire stack is in use.

---

### Post by Pariah819 on 2012-11-01
@[COLOR=Black][jejeman]("http://ubuntuforums.org/member.php?u=609757")

I will give that a try when I get home from work later but I was pointed here [/COLOR][http://subversion.ffado.org/wiki/Hos...ollers#JMicron](http://subversion.ffado.org/wiki/Hos...ollers#JMicron) and it looks like my card chipset is problematic.
[COLOR=Black]
[/COLOR]> JMB381/JMB382/JMB383: very problematic   Works for artfwo, but sometimes hangs randomly and requires reboot (64x3  and 128x3 on Ubuntu 11.04, 2.6.38-8-generic kernel, libraw1394-2.0.7,  libffado-2.0.99+svn1968): 
 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]  So I may just have to pick up a different firewire card...

---

