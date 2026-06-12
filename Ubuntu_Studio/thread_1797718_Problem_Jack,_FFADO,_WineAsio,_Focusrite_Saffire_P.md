---
title: "Problem: Jack, FFADO, WineAsio, Focusrite Saffire Pro 14"
date: 2011-07-05
forum: Ubuntu Studio
---

### Post by Axxl Force on 2011-07-05
Hello Ubuntu Community,

I'm using 10.04 running the 2.6.31-11-rt kernel. My goal is to use a "Focusrite Saffire Pro 14" firewire audiointerface with Reaper, because I'm sick of being forced to use this crappy M$ stuff anymore... it drives me nuts!

I'm quite new to Linux and espacially to lowlatency audio drivers und I've reached a point where I can't go any further by myself.

I've understood, that I need Jack running as a server with FFADO as some kind of "plugin" and WineAsio which maps it to the ASIO API I wanna use with Reaper.

What I've not understood is wether I have to compile my own versions of Jack and FFADO, because I can simply download it trough the software centre, but my feeling says, that this way is not going to work. But when I try to make FFADO using scons I get a bunch of errors about missing dependencies, which is not true...

What I've tried so far does'nt work! Jack is unable to connect to the firewire module and there is no sign of the Focusrite Interface anywhere in Jack, FFADO or WineAsio ...

Do I have to compile my own Jack and FFADO Versions and in which order? If yes, how do I get scons to resolve it's dependencies (the packages are properly installed). Where do I determine, that I want to use the Saffire 14 Pro?

Here's what Jack says right now:

```

15:13:13.789 /usr/bin/jackd -r -dfirewire -r44100 -p256 -n3 -o2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2498652
15:13:13.813 JACK wurde mit PID = 5531 gestartet.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
15:13:14.185 JACK wurde angehalten erfolgreich.
15:13:15.937 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Overall operation failed. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.[/blockquote]
15:13:13.789 /usr/bin/jackd -r -dfirewire -r44100 -p256 -n3 -o2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2498652
15:13:13.813 JACK wurde mit PID = 5531 gestartet.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
15:13:14.185 JACK wurde angehalten erfolgreich.
15:13:15.937 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Overall operation failed. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.
```

thanks in advance!
Axxl

---

### Post by Pablo_F on 2011-07-05
Hi, 

I am not sure if you need more recent versions of jackd and ffado, but before attempting to compile, try the ffado tests and diagnosis tools.

First, you will need to run jackd in realtime mode. And don't set the number of output channels, use "(default)".

To run the ffado tools do:

sudo apt-get install faddo-tools
ffado-test Discover
ffado-test ListDevices
ffado-diag

Paste here the outputs if you are unsure.

As for the problem with scons, to compile a program you need to install the development packages of the dependencies of the program. But it is a bit tricky anyway.

---

### Post by Axxl Force on 2011-07-05
Thanks for your help, Pablo!

afaik there's only a newer version of jackd.

If I'd like to install it I will have to build it myself right?

It seems that the firewire controller itself has some major problem. Here's what ffado-test said:


ffado-test Discover:
```
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Could not initialize device manager
01182004172: Fatal (devicemanager.cpp)[ 165] initialize: No firewire adapters (ports) found.
no message buffer overruns

```

ffado-test ListDevices:
```
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

no message buffer overruns

```

ffado-diag:
```
Traceback (most recent call last):
  File "/usr/bin/ffado-diag", line 29, in <module>
    from listirqinfo import IRQ,SoftIRQ,IRQInfo
ImportError: No module named listirqinfo

```

Do I need a different driver for my firewire controller? It's an onboard one. Where can I get it?

I have no clue about Linux and firewire so thanks a lot for your help!

best regards
Axxl

---

### Post by jejeman on 2011-07-05
Enable card in bios, then run this, and paste the results
```
lspci | grep -i Fire
```

---

### Post by Axxl Force on 2011-07-05
lspci | grep -i Fire:
```

05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

```

---

### Post by jejeman on 2011-07-05
What is happening when you use default lucid kernel?
I'm using default kernel
```
Linux HOST 2.6.32-32-preempt #62-Ubuntu SMP PREEMPT Wed Apr 20 22:22:41 UTC 2011 x86_64 GNU/Linux
```
and it's working just fine, I think you don't need that older rt kernel.

---

### Post by Axxl Force on 2011-07-06
I get the exatct same output running the 2.6.32-32-generic-pae Kernel.

But I found out that I'm unable to get it working under Win XP x86 and Win 7 x86 too on this machine. On my laptop however it works with XP.

Does this mean my firewire controller is not able to handle this device? Is there a possibility to get it working anyways under linux (firmware update)?

Do you think it will be worth getting a PCI firewire card maybe with a TI controller?


thanks
Axxl

---

### Post by jejeman on 2011-07-06
Regardless the audio card ffado test should be ok. Try to disconnect the audio card and run them again.
Do you use same firewire cable for desktop and laptop?

---

### Post by Axxl Force on 2011-07-06
No difference when I unplug the device... 

Yes, I use the same cable, but my laptop has a 4-Pin Firewire Port so I have to use an adapter.

I don't know what can be so fundamently false with my setup...

---

### Post by Pablo_F on 2011-07-06
Hope that Trulan chimes in or ask in the ffado users mailing list...

---

### Post by trulan on 2011-07-08
Hi all,

This is a pretty unusual problem - Ubuntu doesn't seem to be recognizing your firewire controller at all, and ffado-diag is completely failing, I've never seen that before.  Does this command give any output?
```
lsmod | grep 1394
```I have exactly the same firewire controller in my desktop (Agere Systems FW322/323 (rev 61)) and it has worked under every Ubuntu I have tried.  Certainly an unusual problem.

Could you also post the output of  this command:
```
cat /proc/interrupts
```

---

### Post by Axxl Force on 2011-07-11
Thanks trulan for kickin in!

Sry, I've had troubles with my power supply so I'm answering a little delayed... 


lsmod | grep 1394
```

ohci1394               27238  0 
ieee1394               81213  1 ohci1394
alex@AlexDesktop:~$ lsmod | grep 1394
ohci1394               27238  0 
ieee1394               81213  1 ohci1394

```

cat /proc/interrupts
```

           CPU0       CPU1       
  0:         54         11   IO-APIC-edge      timer
  1:          5          1   IO-APIC-edge      i8042
  3:          1          1   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          6          3   IO-APIC-edge      i8042
 16:     198753      23476   IO-APIC-fasteoi   uhci_hcd:usb3, pata_marvell
 17:         49         45   IO-APIC-fasteoi   HDA Intel
 18:       8033      44150   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:        181        156   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb7, ohci1394
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        869       5123   IO-APIC-fasteoi   HDA Intel
 23:     557475        173   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 28:          1          1   PCI-MSI-edge      eth0
 29:     427904          3   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
NMI:          0          0   Non-maskable interrupts
LOC:    3137972    3155649   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:     120864     112247   Rescheduling interrupts
CAL:        642        242   Function call interrupts
TLB:      20628       8737   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         20         20   Machine check polls
ERR:          3
MIS:          0

```

As I wrote before it does not work with Windows either! So I think I will have to perform a firmware upgrade. Any tips on that?

best regards
Axxl

---

### Post by trulan on 2011-07-12
> **Axxl Force said:**
> 
```

           CPU0       CPU1
 19:        181        156   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb7, ohci1394

```
Aaah!  There's way too much stuff on that IRQ.  I hate it how manufacturers seem to tack the firewire controller on like it's an afterthought.  I really don't see how it's going to work with two ata controllers (hard drives) and the firewire controller trying to share an interrupt, even with an RT kernel that's asking an awful lot.  Let's see, it's an onboard card so you can't just move it to another slot...maybe try a good  firewire controller card?

Also, in looking back over the thread again, the fact that ffado-diag is failing is likely due to an improper/incomplete installation of Jack and ffado.  I would install them from the repositories (software center would work, I like Synaptic better) rather than trying to build them yourself, I've found compiling jack and ffado to be a bit tricky.

---

### Post by Axxl Force on 2011-07-12
Ok, I got news. I uninstalled FFADO and Jack and reinstalled it using Autostatic's libffado because it seems that the version from the 10.04 repository does not support the DICE Chipset.

Anyway, it kind of works now. Take a look:

sudo ffado-diag

```

FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 2.6.32-32-generic-pae
  old 1394 stack present.... True
  old 1394 stack loaded..... True
  old 1394 stack active..... True
  new 1394 stack present.... True
  new 1394 stack loaded..... False
  new 1394 stack active..... False
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   g++ ............... g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. jackd version 0.118.0 tmpdir /dev/shm protocol 24
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
   gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   g++ ............... g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.2 for Qt version 4.6.2
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.4
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.2.16
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8294]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               3799.648
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:           [46, 46], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [3, 3], Sched None (priority None), drivers: ['i8042']
 IRQ    3: PID:  None, count:             [2, 2], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:             [2, 2], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count:   [126903, 126903], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'pata_marvell']
 IRQ   17: PID:  None, count:           [46, 46], Sched None (priority None), drivers: ['HDA Intel']
 IRQ   18: PID:  None, count:     [81355, 81355], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb5', 'uhci_hcd:usb8']
 IRQ   19: PID:  None, count:         [124, 124], Sched None (priority None), drivers: ['ata_piix', 'ata_piix', 'uhci_hcd:usb7', 'ohci1394']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   22: PID:  None, count:         [684, 684], Sched None (priority None), drivers: ['HDA Intel']
 IRQ   23: PID:  None, count:   [561500, 561500], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb6']
 IRQ   28: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['eth0']
 IRQ   29: PID:  None, count:   [165789, 165789], Sched None (priority None), drivers: ['fglrx']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

```

But I expierince the same problem like in Win XP and Win 7. The audio device is connect but after a few seconds (1 to 5 seconds) the connection is being lost. And sometimes it doesn't work at all. I have a "FW"-LED on my audio interface which clearly indicates that. Changing some settings does not help. Here is a snapshot:

```

16:53:31.875 /usr/bin/jackd -r -t10000 -dfirewire -r44100 -p256 -n4
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
16:53:31.884 JACK wurde mit PID = 5192 gestartet.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.999.0- built Jul  8 2011 09:20:55
03969900017: [31mWarning (dice_eap.cpp)[ 113] init: no EAP mixer (device does not support EAP)
[0m DICE Parameter Space info:
  Global  : offset=0x0028 size=0360
  TX      : offset=0x0190 size=0568
                nb=   1 size=0280
  RX      : offset=0x03C8 size=1128
                nb=   1 size=0280
  UNUSED1 : offset=0x0830 size=0016
  UNUSED2 : offset=0x0000 size=0000
 Global param space:
  Owner            : 0xE0000000FFC1FFFF
  Notification     : 0x00000040
  Nick name        : Pro14-000959
  Clock Select     : 0x01 0x0C
  Enable           : false
  Clock Status     : locked 0x01
  Extended Status  : 0x00000000
  Samplerate       : 0x0000AC44 (44100)
  Version          : 0x01000400
  Version          : 0x01000400 (1.0.4.0)
  Clock caps       : 0x1108001E
  Clock sources    :
    AES1
    AES2
    SPDIF-OPT
    SPDIF
    AES_ANY
    ADAT
    ADAT_AUX
    Word Clock
    Unused
    Unused
    Unused
    Unused
    Internal
 TX param space:
  Nb of xmit        : 1
  Transmitter 0:
   ISO channel       :  -1
   ISO speed         :   2
   Nb audio channels :   8
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     IP 1
     IP 2
     IP 3
     IP 4
     SPDIF L
     SPDIF R
     Loop 1
     Loop 2
 RX param space:
  Nb of recv        : 1
  Receiver 0:
   ISO channel       :   1
   Sequence start    :   0
   Nb audio channels :  12
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     Mon 1
     Mon 2
     Line 3
     Line 4
     SPDIF L
     SPDIF R
     DAW 7
     DAW 8 
     DAW 9
     DAW 10
     DAW 11
     DAW 12
16:53:33.938 Serverkonfiguration nach "/home/alex/.jackdrc" gespeichert.
16:53:33.938 Statistik zurückgesetzt.
16:53:33.939 Client aktiviert
16:53:33.940 JACK-Verbindung geändert.
16:53:33.941 Schaubild der JACK-Verbindungen geändert.
16:53:38.294 XRUN callback (1).
16:53:39.876 XRUN callback (2).
16:53:39.943 XRUN callback (1 skipped).
16:53:41.021 XRUN callback (3).
16:53:41.944 XRUN callback (1 skipped).
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
16:53:46.894 Schaubild der JACK-Verbindungen geändert.
16:53:46.947 JACK-Verbindung geändert.
jack main caught signal 12
no message buffer overruns
cannot continue execution of the processing graph (DatenÃ¼bergabe unterbrochen (broken pipe))
zombified - calling shutdown handler
16:53:47.099 Benachrichtigung zum Herunterfahren.
16:53:47.099 JACK fährt herunter...
16:53:47.099 JACK wird gezwungen...
16:53:47.300 JACK wurde angehalten erfolgreich.
16:53:47.300 Post-shutdown script...
16:53:47.300 killall jackd
jackd: Kein Prozess gefunden
16:53:47.705 Post-shutdown script terminated mit Rückgabewert = 256.
```

Again: I think I will have to perform a firmware update on my FW-controller but I can not find a link to download it anywhere in the internet. But I assume there is a firmware update availible because some dude in this [*Thread*](http://www.linuxmusicians.com/viewtopic.php?f=6&t=2901&st=0&sk=t&sd=a&sid=ae1db1dd790cc1ee24b3687ec22b0309) claims he had done it to his FW322/323. Maybe I'm too dump to find it but maybe you guys have an idea...

thanks for your help!
Axxl

---

### Post by trulan on 2011-07-12
OK, so ffado is properly installed now, that's good.  However, I believe that it keeps dropping the firewire connection because the firewire controller and the hard driver are trying to use the same interrupt (IRQ 19, as shown in cat /proc/interrupts).  This IRQ conflict would also explain why it doesn't work in Windows.  It's a problem with the way your hardware is set up.  As far as I know, the only way around it is to get a firewire controller card (so you have some control over which interrupt it uses) or get a different computer.  Unless there's a way in your bios to choose which interrupt the firewire controller is on, but I doubt it.

---

