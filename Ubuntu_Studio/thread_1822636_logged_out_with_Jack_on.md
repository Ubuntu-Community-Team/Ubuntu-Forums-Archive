---
title: "logged out with Jack on"
date: 2011-08-10
forum: Ubuntu Studio
---

### Post by sidewalkcynic on 2011-08-10
So, I did a big no-no. I had a QJackctl and ZynSynth session going, and I logged out to show somebody how the log out works. Since then Jack does not work.

> JACK server starting in realtime mode with priority 10
libffado 2.999.0- built Mar 28 2011 17:44:19
firewire ERR: FFADO: Error creating virtual device
Cannot attach audio driver
JackServer::Open() failed with -1
no message buffer overruns
Failed to start server

I have been looking all over, and cannot find a fix to work.

---

### Post by jejeman on 2011-08-10
When user logouts all programs which were started by the user closes, or get killed.
I can't see how would that break jack.
Try to restart the machine. That will terminated anything hanging.

---

### Post by sidewalkcynic on 2011-08-10
I've rebooted several times already, reset defaults, and tried some command lines i came across on the Internet concerning the issue.

I don't know, but it would seem that something like QJack should have a more robust central diagnostic check.

I think I have found all that I want with the ZynAddSynth, Hydrogen, and Rosegarden; and I need the sensitve Jack to put those three together - I'm not looking to hook-up any guitars - wish it could be simpler. I can't believe all this extra crap that comes with the UbuntuStudio - who needs four sequencers and all this crap?

---

### Post by jejeman on 2011-08-11
> I can't believe all this extra crap that comes with the UbuntuStudio - who needs four sequencers and all this crap?Don't be rude.
I use seq24 and Muse, so I need that extra crap.

> firewire ERR: FFADO: Error creating virtual device
Maybe ffado got bad. Do diagnose.

---

### Post by sidewalkcynic on 2011-08-11
[code]FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 2.6.38-10-generic
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... False
  new 1394 stack active..... False
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
   g++ ............... g++ (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
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
   gcc ............... gcc (Ubuntu/Linaro 4.5.2-7ubuntu1) 4.5.2
   g++ ............... g++ (Ubuntu/Linaro 4.5.2-7ubuntu1) 4.5.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.8.3 for Qt version 4.7.2
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.6
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.33.1
     flags ........... -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include  -pthread -L/usr/lib/i386-linux-gnu -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.4.6
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/i386-linux-gnu/dbus-1.0/include  -L/usr/lib/i386-linux-gnu -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
   CPU info:
Architecture:          i686
CPU op-mode(s):        32-bit
CPU(s):                2
Thread(s) per core:    2
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 28
Stepping:              2
CPU MHz:               1600.000
L1d cache:             24K
L1i cache:             32K
L2 cache:              512K
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [110372, 110372], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:         [110, 110], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:         [371, 371], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:         [173, 173], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:     [13141, 13141], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count:     [12540, 12540], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb2', 'i915']
 IRQ   17: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb3']
 IRQ   18: PID:  None, count:     [28239, 28239], Sched None (priority None), drivers: ['uhci_hcd:usb4', 'ath']
 IRQ   19: PID:  None, count:         [680, 680], Sched None (priority None), drivers: ['uhci_hcd:usb5', 'mmc0', 'jmb38x_ms:slot0']
 IRQ   44: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   45: PID:  None, count:         [380, 380], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

FireWire kernel stack not present. Please compile the kernel with 
FireWire support.[/quote]I'll try the suggestions it gives

---

### Post by sidewalkcynic on 2011-08-11
I reinstalled everything I could find in that list, except for the realtime kernel.

```
19:15:14.746 Patchbay deactivated.
19:15:14.771 Statistics reset.
19:15:14.906 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
19:15:31.405 ALSA connection graph change.
19:15:31.849 ALSA connection graph change.
19:15:32.015 ALSA connection change.
19:15:45.549 ALSA connection change.
19:15:51.028 JACK is starting...
19:15:51.029 /usr/bin/jackd -dfirewire -r192000 -p16 -n3
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
19:15:51.116 JACK was started with PID=1735.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
libffado 2.999.0- built Mar 28 2011 17:44:19
firewire ERR: FFADO: Error creating virtual device
Cannot attach audio driver
JackServer::Open() failed with -1
no message buffer overruns
Failed to start server
19:15:51.975 JACK was stopped with exit status=255.
19:15:53.149 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

---

### Post by sgx on 2011-08-12
the command 

ps ux

will list what processes are running, and what resources they are using. 'pulse' anything should be given a command

killall name-of-pulse

The Input device > and Output device > 
might change, requiring you to reselect the desired devices.
Check for a backup file of .jackdrc, and use that, and you can rename the related .config files in the home directory, and reboot, causing new ones to be written.

I'm a fan of small distros like bodhi linux, pclinuxos minime,
or a puppy linux like macpup 5.25, (all sub-400 meg) to which you can add just the desired a/v tools, without four or five of everything. Several others take the opposite approach, so we can all find a good fit.

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

I have had good luck installing the .deb files from debian unstable,
bodhi and pclinuxos include synaptic, macpup has lucid repositories
in it's default package manager, which also manually installs .deb files
you download elsewhere.
Cheers

---

### Post by mikeh789 on 2011-08-12
i would try making a new user account, and see if JACK seems to act normal. might be a ~/.directory config somewhere that you could trash and let respawn (if it works in the new user account, and you want to fix the current user)...

---

