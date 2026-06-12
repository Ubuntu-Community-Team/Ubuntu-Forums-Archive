---
title: "Firewire problems with 13.10, Jack, FFADO and Firewire Interfaces"
date: 2014-01-01
forum: Ubuntu Studio
---

### Post by JsweheX on 2014-01-01
Hi guys.

I recently had a hard drive failure and upon replacing the hard drive I upgraded from 13.04 to 13.10 and I have had nothing but problems.

My setup consists of an Intel Core2Duo MacBook with Ubuntu Studio 13.10 (Kernel: 3.11.0-14-lowlatency) and a Phonic Firefly 808 (supported by FFADO, I've had it working in 13.04).

First, let's start out with the output from QJackCtl upon setting the driver to FireWire with the interface plugged in:

```
 [COLOR=#ff0000]04:19:59.303 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Wed Jan  1 04:19:59 2014: Starting jack server...
 Wed Jan  1 04:19:59 2014: JACK server starting in realtime mode with priority 10
 Wed Jan  1 04:19:59 2014: ERROR: firewire ERR: FFADO: Error creating virtual device
 Wed Jan  1 04:19:59 2014: ERROR: Cannot attach audio driver
 Wed Jan  1 04:19:59 2014: ERROR: JackServer::Open failed with -1
 Wed Jan  1 04:19:59 2014: ERROR: Failed to open server
 Wed Jan  1 04:20:00 2014: Saving settings to "/home/cp/.config/jack/conf.xml" ...
 [COLOR=#ff0000]04:20:08.751 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started


```

Alright, that's no good.

Here's the output from /cat/proc/interrupts:
```
cat /proc/interrupts
           CPU0       CPU1       
  0:     175337     175122   IO-APIC-edge      timer
  8:          0          1   IO-APIC-edge      rtc0
  9:       8297       8359   IO-APIC-fasteoi   acpi
 16:      35215      34995   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb5, eth1
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 20:        248        247   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3
 21:     181600     181758   IO-APIC-fasteoi   ata_piix, ehci_hcd:usb1, uhci_hcd:usb7
 40:          0          0   PCI-MSI-edge      PCIe PME, pciehp
 41:          0          0   PCI-MSI-edge      PCIe PME, pciehp
 42:          0          0   PCI-MSI-edge      PCIe PME, pciehp
 43:          1          0   PCI-MSI-edge      eth0
 44:        300        286   PCI-MSI-edge      ahci
 45:       2712       2724   PCI-MSI-edge      i915
 46:        245        244   PCI-MSI-edge      snd_hda_intel
NMI:        291        307   Non-maskable interrupts
LOC:     453549     459366   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:        291        307   Performance monitoring interrupts
IWI:       7836       7435   IRQ work interrupts
RTR:          0          0   APIC ICR read retries
RES:     946826     942751   Rescheduling interrupts
CAL:        165        319   Function call interrupts
TLB:       3981       7043   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         13         13   Machine check polls
ERR:          0
MIS:          0

```

And the result of lsmod | grep firewire:
```
firewire_ohci          40060  0 
firewire_core          64476  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

```


Here is the contents of /etc/modprobe.d/blacklist-firewire.conf
```
#Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2

```

I have also tried unlocking the blacklist firewire-* entries and blacklisting the top 5 followed by sudo update-initramfs -k all -u followed by a reboot to absolutely no avail.

Here is the result of ffado-diag
```
FFADO diagnostic utility 2.1.9999-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 3.11.0-14-lowlatency
    Preempt (low latency)... True
    RT patched.............. False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... False
  /dev/raw1394 node present. False
  User IDs:
uid=1000(cp) gid=1000(cp) groups=1000(cp),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),112(lpadmin),123(sambashare)
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
   g++ ............... sh: 1: g++: not found
   PyQt4 (by pyuic4) . sh: 1: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ...........  -ljack  
   libraw1394 ........ 2.1.0
     flags ...........  -lraw1394  
   libavc1394 ........ 0.5.4
     flags ...........  -lavc1394 -lrom1394 -lraw1394  
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
   dbus-1 ............ 1.6.12
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.7.2-20ubuntu1) 4.7.2
   g++ ............... g++ (Ubuntu/Linaro 4.7.2-20ubuntu1) 4.7.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.9.6 for Qt version 4.8.3
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
   dbus-1 ............ 1.6.8
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 uname -a...
   Linux cpmb 3.11.0-14-lowlatency #6-Ubuntu SMP PREEMPT Wed Nov 20 23:59:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Hardware...
   Host controllers:
04:03.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811] (rev 61) (prog-if 10 [OHCI])
    Subsystem: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B+ DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at d0300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               2400.000
BogoMIPS:              4788.09
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
NUMA node0 CPU(s):     0,1
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [185853, 185690], Sched None (priority None), drivers: ['timer']
 IRQ    8: PID:  None, count:             [0, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [8801, 8844], Sched None (priority None), drivers: ['acpi']
 IRQ   16: PID:  None, count:     [36427, 36211], Sched None (priority None), drivers: ['uhci_hcd:usb4', 'uhci_hcd:usb5', 'eth1']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb6']
 IRQ   20: PID:  None, count:         [248, 247], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb3']
 IRQ   21: PID:  None, count:   [193297, 193397], Sched None (priority None), drivers: ['ata_piix', 'ehci_hcd:usb1', 'uhci_hcd:usb7']
 IRQ   40: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['PCIe PME', 'pciehp']
 IRQ   41: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['PCIe PME', 'pciehp']
 IRQ   42: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['PCIe PME', 'pciehp']
 IRQ   43: PID:  None, count:             [1, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   44: PID:  None, count:         [300, 286], Sched None (priority None), drivers: ['ahci']
 IRQ   45: PID:  None, count:       [2805, 2820], Sched None (priority None), drivers: ['i915']
 IRQ   46: PID:  None, count:         [245, 244], Sched None (priority None), drivers: ['snd_hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
If running a kernel earlier than 2.6.37 and problems are experienced, either 
try with the old Firewire kernel stack or upgrade to a newer kernel 
(preferrably 2.6.37 or later).

```

Here is the result of ffado-test Discover
```
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.1.9999-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Could not initialize device manager
1388581580526366: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
no message buffer overruns

```

I think my problem has to do with the fact that the module /dev/raw1394 is not present when either firewire stack is loaded. Could anybody help me further with what's going on? I've been trying to fix this on my own for a week straight now and I simply cannot get it to work!

Thanks in advance...

---

### Post by jejeman on 2014-01-01
Don't blacklist firewire-ohci.
Give
```
ls /dev/fw*
dmesg | grep -i fire
```

---

### Post by JsweheX on 2014-01-01
Thanks for the response. Here are the results of the requested commands:

ls /dev/fw*
```

ls: cannot access /dev/fw*: No such file or directory

```

dmesg | grep -i fire
```

[    2.142021] firewire_ohci 0000:04:03.0: failed to read phy reg 2
[    2.142054]  [<ffffffffa004521b>] read_phy_reg+0x9b/0xb0 [firewire_ohci]
[    2.142059]  [<ffffffffa00490ad>] ohci_enable+0x2bd/0x5b0 [firewire_ohci]
[    2.142064]  [<ffffffffa001c939>] fw_card_add+0x49/0x90 [firewire_core]
[    2.142068]  [<ffffffffa0049b51>] pci_probe+0x631/0x71b [firewire_ohci]
[    2.142110]  [<ffffffffa001001e>] fw_ohci_pci_driver_init+0x1e/0x1000 [firewire_ohci]
[    2.142287] firewire_ohci: probe of 0000:04:03.0 failed with error -16

```

As per your advice, and for additional information, I went ahead and modified the contents of the /etc/modprobe.d/blacklist-firewire.conf file to include the firewire-ohci and firewire-spb2:
```

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2

```

and proceeded to enter: sudo update-initramfs -k all -u and then I rebooted the computer.

Here's the updated output of your requested commands:

ls/dev/fw*
```

ls: cannot access /dev/fw*: No such file or directory

```

dmesg | grep -i fire brought no result

Any ideas?

---

### Post by jejeman on 2014-01-02
First, I've said DON'T black list firewire-ohci. If you black list it how can you expect firewire to work?
Change it back to 
```
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2
```Now, Ubuntu is using new firewire stack and that is firewire-ohci. Raw1394 is an old stack.
You sholud have modules loaded
```
$ lsmod | grep -i fire
firewire_ohci          41000  0 
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

```
Your first results for dmesg is good in terms that modules are loaded, but you have an error. Here is on my system
```
$ dmesg | grep -i fire
[    1.954085] firewire_ohci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.005094] firewire_ohci: Added fw-ohci device 0000:03:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    2.504820] firewire_core: created device fw0: GUID 00004c0107002f56, S400
```One can see that device node is created "fw0".
```
$ ls /dev/fw*
/dev/fw0
```Fw0 is firewire card (controler) it is a must to have.
I've notice that something is wrong in your interrupts list, there is no firewire module, you should have something like this for IRQ19, but no IRQ19 on your system.
```
16:       4788         57         80         56   IO-APIC-fasteoi   ehci_hcd:usb1, firewire_ohci, nvidia
```
```
$ lspci -kvnn | grep -i fire -A 5
03:00.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 [Firewarden] IEEE1394a OHCI 1.1 Link/3-port PHY Controller [1033:00f2] (rev 01) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation Device [1033:00ce]
	Flags: bus master, medium devsel, latency 128, IRQ 16
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
```

This is your error
```
[    2.142287] firewire_ohci: probe of 0000:04:03.0 failed with error -16
```You firewire card is not working. I suppose that is laptop you are using, so nothing about pulling out the card/putting it back I guess, or even change it.

---

### Post by JsweheX on 2014-01-02
Thank you for the breakdown of what all of this means. I'm still relatively new to linux distros, so I still need some hand holding.

My computer is a dual booted MacBook, so I tested whether or not it is my firewire card by booting into the OS X partition and double checking. My firewire port was recognized and my Phonic Firefly 808 showed up immediately upon plugging it in. So it isn't a hardware issue...

Should I try re-installing 13.04? I've tried to upgrade to 13.10 in the past and I couldn't get it to work then. Any more tips?

---

### Post by JsweheX on 2014-01-18
Alright, Ubuntu Studio 13.10 was not recognizing my firewire port. I have re-installed 13.04.

```

dmesg | grep -i fire
[    2.472147] firewire_ohci 0000:04:03.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    2.972207] firewire_core 0000:04:03.0: created device fw0: GUID 001ff3fffe2dad74, S400
```

```
ls /dev/fw*
/dev/fw0
```

```
lspci -kvnn | grep -i fire -A 5
04:03.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811] (rev 61) (prog-if 10 [OHCI])
    Subsystem: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811]
    Flags: bus master, fast Back2Back, medium devsel, latency 248, IRQ 19
    Memory at d0300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
```

However now ffado is not recognizing my firewire adpators:
```
ffado-dbus-server
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.1.9999-2470
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

1390048142061056:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
1390048142062528: Fatal (devicemanager.cpp)[ 187] initialize: No firewire adapters (ports) found.
1390048142062541: Error (ffado-dbus-server.cpp)[ 277] main: Could not initialize device manager
1390048142062624: Debug (ffado-dbus-server.cpp)[ 202] exitfunction: Debug output flushed...

```

This was not as difficult on my last install. Does anybody have any advice?

---

### Post by JsweheX on 2014-01-18
> **JsweheX said:**
> Alright, Ubuntu Studio 13.10 was not recognizing my firewire port. I have re-installed 13.04.

```

dmesg | grep -i fire
[    2.472147] firewire_ohci 0000:04:03.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    2.972207] firewire_core 0000:04:03.0: created device fw0: GUID 001ff3fffe2dad74, S400
```

```
ls /dev/fw*
/dev/fw0
```

```
lspci -kvnn | grep -i fire -A 5
04:03.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811] (rev 61) (prog-if 10 [OHCI])
    Subsystem: LSI Corporation FW322/323 [TrueFire] 1394a Controller [11c1:5811]
    Flags: bus master, fast Back2Back, medium devsel, latency 248, IRQ 19
    Memory at d0300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
```

However now ffado is not recognizing my firewire adpators:
```
ffado-dbus-server
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.1.9999-2470
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

1390048142061056:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
1390048142062528: Fatal (devicemanager.cpp)[ 187] initialize: No firewire adapters (ports) found.
1390048142062541: Error (ffado-dbus-server.cpp)[ 277] main: Could not initialize device manager
1390048142062624: Debug (ffado-dbus-server.cpp)[ 202] exitfunction: Debug output flushed...

```

This was not as difficult on my last install. Does anybody have any advice?

EDIT:
Just ran ffado-test ListDevices as root and turned up:
```

=== 1394 PORT 0 ===
Node    id    GUID                           VendorId       ModelId      Vendor - Model
0                0x001ff3fffe2dad74  0x00001FF3  0x00000000     Linux Firewire - 
```

However running anything else as root doesn't help, but it does seem my mixer is at least showing up now as root. However, I still get the same error as above from ffado-dbus-server and of course, jack will not start.

---

