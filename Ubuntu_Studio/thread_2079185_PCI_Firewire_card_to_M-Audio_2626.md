---
title: "PCI Firewire card to M-Audio 2626"
date: 2012-11-01
forum: Ubuntu Studio
---

### Post by debiant on 2012-11-01
Has anyone managed to get anywhere with this?  I haven't actually seen any sign that its even detected.  aplay and lspci don't show any firewire connection at all.
I've been through everything I can about Jack, ffado and Ardour but nothing seems to indicate there is any link between the computer and the sound module.
I don't feel that the ieee 1394 (firewire pci card) is working?  I'm completely stuck and would really appreciate any advice anyone can offer.
:guitar:

  I'd love to have a go at recording music in linux.

---

### Post by jejeman on 2012-11-01
Look here
[http://ubuntuforums.org/showthread.php?t=2078854](http://ubuntuforums.org/showthread.php?t=2078854)
and give us output from commands found in post #1, #2 & #3.

---

### Post by debiant on 2012-11-01
Hallo Jejeman, here is the output.  Some of the commands got nothing at all-obviously on to something! I have to go to work (nightshift) but I will be back on here tomorrow morning.  Really appreciate you offering to help.
:P


```
mike@mike-LM:~$ lspci | grep 1394
mike@mike-LM:~$ dmesg | grep ohci
[    0.981936] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.981961] ohci_hcd 0000:00:12.0: >OHCI Host Controller
[    0.981964] ohci_hcd 0000:00:12.0: >new USB bus registered, assigned bus number 4
[    0.982048] ohci_hcd 0000:00:12.0: >irq 18, io mem 0xfeb0a000
[    1.036719] usb usb4: >Manufacturer: Linux 3.5.0-17-lowlatency ohci_hcd
[    1.036877] ohci_hcd 0000:00:13.0: >OHCI Host Controller
[    1.036881] ohci_hcd 0000:00:13.0: >new USB bus registered, assigned bus number 5
[    1.036949] ohci_hcd 0000:00:13.0: >irq 20, io mem 0xfeb08000
[    1.091624] usb usb5: >Manufacturer: Linux 3.5.0-17-lowlatency ohci_hcd
[    1.091773] ohci_hcd 0000:00:14.5: >OHCI Host Controller
[    1.091777] ohci_hcd 0000:00:14.5: >new USB bus registered, assigned bus number 6
[    1.091833] ohci_hcd 0000:00:14.5: >irq 18, io mem 0xfeb06000
[    1.146524] usb usb6: >Manufacturer: Linux 3.5.0-17-lowlatency ohci_hcd
[    1.146671] ohci_hcd 0000:00:16.0: >OHCI Host Controller
[    1.146675] ohci_hcd 0000:00:16.0: >new USB bus registered, assigned bus number 7
[    1.146731] ohci_hcd 0000:00:16.0: >irq 22, io mem 0xfeb05000
[    1.201420] usb usb7: >Manufacturer: Linux 3.5.0-17-lowlatency ohci_hcd
[    1.658691] usb 5-2: >new low-speed USB device number 2 using ohci_hcd
[    2.039012] usb 5-3: >new full-speed USB device number 3 using ohci_hcd
mike@mike-LM:~$ ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Could not initialize device manager
01742438884: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
mike@mike-LM:~$ ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 3.5.0-17-lowlatency
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... False
  new 1394 stack active..... False
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2
   g++ ............... sh: 1: g++: not found
   PyQt4 (by pyuic4) . sh: 1: pyuic4: not found
   jackd ............. jackdmp 1.9.9
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
   gcc ............... gcc (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2
   g++ ............... g++ (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.9.3 for Qt version 4.8.2
   jackd ............. sh: 1: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.9
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.34.2
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  
   dbus-1 ............ 1.6.4
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 Hardware...
   Host controllers:
   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            21
Model:                 1
Stepping:              2
CPU MHz:               3611.830
BogoMIPS:              7223.66
Virtualisation:        AMD-V
L1d cache:             16K
L1i cache:             64K
L2 cache:              2048K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [129, 129, 129, 129, 129, 129, 129, 129], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    7: PID:  None, count: [1, 1, 1, 1, 1, 1, 1, 1], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count: [1, 1, 1, 1, 1, 1, 1, 1], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count: [134, 134, 134, 134, 134, 134, 134, 134], Sched None (priority None), drivers: ['snd_hda_intel']
 IRQ   17: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1']
 IRQ   18: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ohci_hcd:usb4', 'ohci_hcd:usb6']
 IRQ   19: PID:  None, count: [1699, 1699, 1699, 1699, 1699, 1699, 1699, 1699], Sched None (priority None), drivers: ['ahci']
 IRQ   20: PID:  None, count: [1068, 1068, 1068, 1068, 1068, 1068, 1068, 1068], Sched None (priority None), drivers: ['ohci_hcd:usb5']
 IRQ   21: PID:  None, count: [1, 1, 1, 1, 1, 1, 1, 1], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   22: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ohci_hcd:usb7']
 IRQ   23: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb3']
 IRQ   72: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ahci']
 IRQ   73: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ahci']
 IRQ   74: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   75: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   76: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   77: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   78: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   79: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   80: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   81: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   82: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   83: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   84: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   85: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   86: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   87: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   88: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   89: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   90: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   91: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   92: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   93: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   94: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   95: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   96: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   97: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   98: PID:  None, count: [6497, 6497, 6497, 6497, 6497, 6497, 6497, 6497], Sched None (priority None), drivers: ['eth0']
 IRQ   99: PID:  None, count: [35, 35, 35, 35, 35, 35, 35, 35], Sched None (priority None), drivers: ['radeon']
 IRQ  100: PID:  None, count: [47, 47, 47, 47, 47, 47, 47, 47], Sched None (priority None), drivers: ['snd_hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

FireWire kernel stack not present. Please compile the kernel with 
FireWire support.

mike@mike-LM:~$ dmesg | grep fw
mike@mike-LM:~$ ls /dev/fw*
ls: cannot access /dev/fw*: No such file or directory
mike@mike-LM:~$ 
```

---

### Post by jejeman on 2012-11-01
Looks like you don't have firwire controler.
Give us whole output from
```
lspci -nn
```

---

### Post by debiant on 2012-11-02
Is that a driver?

```
mike@mike-LM:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port E) [1002:5a19]
00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx1 port A) [1002:5a1d]
00:0b.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (NB-SB link) [1002:5a1f]
00:0d.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx1 port B) [1002:5a1e]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
00:15.2 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
00:15.3 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 3 [1022:1603]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 4 [1022:1604]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI PITCAIRN PRO [Radeon HD 7800 Series] [1002:6819]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Device [1002:aab0]
02:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
03:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 09)
0b:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
0c:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
mike@mike-LM:~$ ^C
mike@mike-LM:~$ ^C
mike@mike-LM:~$ 

```

---

### Post by jejeman on 2012-11-02
You don't have firewire controler. 
If you actually do, then something is wrong. Either card is broken or pci slot.
If you can, try to put it in another slot, or try another firewire card.
If card works on other OS, you still have to change it in order to work with linux.
Look in BIOS, maybe there is some settings you can change.

Regardles if firewire card will actually work with linux, it must be shown in PCI list.

---

### Post by debiant on 2012-11-02
Nothing in the BIOS-so its not being detected at all...

I shall try what you've suggested.

---

