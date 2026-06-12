---
title: "edirol fa-66 and ubuntu"
date: 2011-03-26
forum: Ubuntu Studio
---

### Post by jakze on 2011-03-26
Hi. I have huge problem with configurations my jack/ffado 

When i run my jack it work a few seconds and it stopping. Anybody know where is cause? 

It is log

```
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
05066408532:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:17:24
17:04:31.545 JACK connection change.
17:04:31.547 Server configuration saved to "/home/bbb/.jackdrc".
17:04:31.548 Statistics reset.
17:04:31.558 Client activated.
17:04:31.570 JACK connection graph change.
JackGraphManager::Connect different port types port_src = 15 port_dst = 14
JackEngine::XRun: client = audacious-jack_5186_000 was not run: state = 1
JackAudioDriver::ProcessGraphAsync: Process error
17:04:31.657 XRUN callback (1).
JackPosixMutex::Unlock res = 1
17:04:31.767 JACK connection change.
JackEngine::XRun: client = audacious-jack_5186_000 was not run: state = 1
JackPosixMutex::Unlock res = 1
JackAudioDriver::ProcessGraphAsync: Process error
17:04:33.570 XRUN callback (1 skipped).
17:04:40.304 XRUN callback (3).
JackPosixMutex::Unlock res = 1
JackFFADODriver::ffado_driver_wait - unhandled xrun
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, stopping...
17:05:00.241 Client deactivated.
17:05:00.242 JACK is stopping...
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
JackEngine::ClientDeactivate wait error ref = 2 name = qjackctl
JackProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out
JackEngine::ClientCloseAux wait error ref = 2
jack main caught signal 15
no message buffer overruns
17:05:00.377 JACK was stopped successfully.
17:05:00.378 Post-shutdown script...
17:05:00.378 killall jackd
jackd: no process found
17:05:00.791 Post-shutdown script terminated with exit status=256.
```

---

### Post by Pablo_F on 2011-03-26
> JACK server starting in non-realtime mode

Don't do this. Be patient.

You need to start jack in realtime mode. But before this, you need to give your user realtime priority and memlock privileges. Two steps:

In a terminal:

**sudo dpkg-reconfigure -p high jackd2**

Answer YES.

Then:

**sudo adduser your_user_name audio**

Reboot the computer. 

Before further attempts, run the ffado diagnosis tool:

**faddo-diag**

and paste here the output.

Cheers, Pablo

---

### Post by jakze on 2011-03-26
Hi. thanks for answer :)

ffado-diag

```
bbb@bbb-Vostro-3700:~$ ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-28-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ...........  -ljack  
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
   dbus-1 ............ 1.4.0
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
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
14:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01) (prog-if 10 [OHCI])
	Subsystem: Dell Device [1028:0442]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 18
	Region 0: Memory at fbc00000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4522.13
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.97
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.97
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 2262.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 5
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [26, 26, 26, 26], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count: [143, 143, 143, 143], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:   [33, 33, 33, 33], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count: [1187, 1187, 1187, 1187], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'hda_intel', 'nvidia']
 IRQ   17: PID:  None, count:   [21, 21, 21, 21], Sched None (priority None), drivers: ['eth1']
 IRQ   18: PID:  None, count:   [25, 25, 25, 25], Sched None (priority None), drivers: ['firewire_ohci', 'ips']
 IRQ   19: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['mmc0']
 IRQ   23: PID:  None, count: [14149, 14149, 14149, 14149], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   45: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['pciehp']
 IRQ   46: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   47: PID:  None, count: [1028, 1028, 1028, 1028], Sched None (priority None), drivers: ['ahci']
 IRQ   48: PID:  None, count:   [98, 98, 98, 98], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.





```


I tried with real-time, old stuck too etc. it doesn't make a difference.

---

### Post by bluesscream on 2011-03-26
hi jakze,

 > Base system...
  kernel version............ 2.6.35-28-generic

Maverick?

  > old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True

> === REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.


For your abovementioned kernel's firewire configuration 
ffado version should be >= 2, jack-firewire >1.9,
they should be in Maverick's standard repos. 
If you are on Lucid, you'll find them i.e. in falktx' ppas
Might be you'll have to add a group named firewire with your user as member.
Setting up your system for old stack is more complicated - blacklisting, dev chgrp, editing udev rules...

good luck

---

### Post by AutoStatic on 2011-03-27
Hello jakze, you're FireWire controller is sharing its interrupt with a  RAID controller so maybe installing a real-time kernel and the **rtirq-init** package might help. Then proceed from here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) Step 5.
Real-time kernels for Maverick here: [https://launchpad.net/~kxstudio-team/+archive/kernel?field.series_filter=maverick](https://launchpad.net/~kxstudio-team/+archive/kernel?field.series_filter=maverick)
I think it's best to get the 2.6.33 real-time kernel.

Best,

Jeremy

---

### Post by jakze on 2011-03-27
Thanks for help

> **AutoStatic said:**
>  you're FireWire controller is sharing its interrupt with a  RAID controller so maybe installing a real-time kernel and the **rtirq-init** 

hi. I did both things a few times ;)

It's my rtirq - Any proposition for it?  

```
#
# Copyright (c) 2004-2009 rncbc aka Rui Nuno Capela.
#
#   This program is free software; you can redistribute it and/or
#   modify it under the terms of the GNU General Public License
#   as published by the Free Software Foundation; either version 2
#   of the License, or (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License along
#   with this program; if not, write to the Free Software Foundation, Inc.,
#   51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#
# /etc/sysconfig/rtirq
# /etc/default/rtirq
#
# Configuration for IRQ thread tunning,
# for realtime-preempt enabled kernels.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License version 2 or later.
#

# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc0 ohci1394 snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

# On kernel configurations that support it,
# which services should be NOT threaded 
# (space separated list).
RTIRQ_NON_THREADED="rtc ohci1394 snd"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
# RTIRQ_HIGH_LIST="timer"
```


ffado-diag

```
bbb@bbb-Vostro-3700:~$ ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.33-29-realtime
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
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ...........  -ljack  
   libraw1394 ........ 2.0.6
     flags ...........  -lraw1394  
   libavc1394 ........ 0.5.3
     flags ...........  -lavc1394 -lrom1394 -lraw1394  
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.4.0
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
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
14:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01) (prog-if 10 [OHCI])
	Subsystem: Dell Device [1028:0442]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 18
	Region 0: Memory at fbc00000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 2261.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.49
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.78
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.76
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 5
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4521.76
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [139, 139, 139, 139], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:       [6, 6, 6, 6], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:       [1, 1, 1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count: [327, 327, 327, 327], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count: [3654, 3654, 3654, 3654], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'hda_intel', 'nvidia']
 IRQ   17: PID:  None, count:   [22, 22, 22, 22], Sched None (priority None), drivers: ['eth1']
 IRQ   18: PID:  None, count: [19121, 19121, 19121, 19121], Sched None (priority None), drivers: ['ohci1394']
 IRQ   19: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['mmc0']
 IRQ   23: PID:  None, count:   [41, 41, 41, 41], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   30: PID:  None, count: [1243, 1243, 1243, 1243], Sched None (priority None), drivers: ['ahci']
 IRQ   31: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   32: PID:  None, count: [1029, 1029, 1029, 1029], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.
bbb@bbb-Vostro-3700:~$ 

```


qjacklt & audacious

```
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 70
02027611165:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:17:24
16:30:56.932 JACK connection change.
16:30:56.934 Server configuration saved to "/home/bbb/.jackdrc".
16:30:56.934 Statistics reset.
16:30:56.941 Client activated.
16:30:56.950 JACK connection graph change.
16:30:57.773 JACK connection graph change.
JackGraphManager::Connect different port types port_src = 15 port_dst = 14
16:30:57.953 JACK connection change.
JackFFADODriver::ffado_driver_wait - unhandled xrun
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, stopping...
```

---

### Post by AutoStatic on 2011-03-27
Everything looks good, you're now using the old stack again I see. And the RAID controller seems to be gone, did you unload the kernel module?

```
JackGraphManager::Connect different port types port_src = 15 port_dst = 14
```This is what's causing the error probably. Does this happen when you start Audacious? I stopped using Audacious a while ago in favor of Aqualung, mainly because it doesn't play well with JACK. What are your current JACK settings by the way?

Best,

Jeremy

---

### Post by jakze on 2011-03-27
My settings are exactly like [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) 

It is strange because it works about 10s and jack is stopping/freezing. 

I tried ubuntu 10.4, 10.10 and many kernels, every-times i get the same result.

:-k   

vlc & qjacklt

```
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 70
03866815070:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:17:24
17:01:36.320 JACK connection change.
17:01:36.321 Server configuration saved to "/home/bbb/.jackdrc".
17:01:36.322 Statistics reset.
17:01:36.328 Client activated.
17:01:36.341 JACK connection graph change.
17:01:37.878 JACK connection graph change.
17:01:37.937 JACK connection change.
17:01:40.688 XRUN callback (1).
JackPosixMutex::Unlock res = 1
JackEngine::XRun: client vlc_3937 finished after current callback
JackAudioDriver::ProcessGraphAsync: Process error
17:01:42.527 XRUN callback (2).
JackPosixMutex::Unlock res = 1
17:01:42.583 JACK connection graph change.
17:01:42.745 JACK connection change.
JackPosixMutex::Unlock res = 1
17:01:44.899 XRUN callback (3).
JackFFADODriver::ffado_driver_wait - unhandled xrun
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, stopping...
```

---

### Post by AutoStatic on 2011-03-27
What are your current JACK settings?

Best,

Jeremy

---

### Post by jakze on 2011-03-29
(two days later :))

Hi. 
Jack settings: [https://help.ubuntu.com/community/FireWire?action=AttachFile&do=get&target=jack_control.png](https://help.ubuntu.com/community/FireWire?action=AttachFile&do=get&target=jack_control.png)

I suppose that problem makes my "Ricoh Co Ltd FireWire Host Controller (rev 01)" 

:(

Anybody use this controller?

Regards

---

### Post by jejeman on 2011-03-29
How did you managed to get 8 channels when fa-66 has only 6? Also, are you using the same settings for sample rate on card and in jack?

---

### Post by jakze on 2011-03-29
> How did you managed to get 8 channels when fa-66 has only 6?

I used "default" :)

> Also, are you using the same settings for sample rate on card and in jack?

Yes. :)

---

### Post by jejeman on 2011-03-29
I do not think that your using "default" because it writes 8 not default in the option field.
Try to set the number to 6.

---

### Post by jakze on 2011-03-29
> I do not think that your using "default" because it writes 8 not default in the option field

Blessed are those who have not seen and yet have believed :) I know what i say. 

I tried to set 6 (special for you :) ) no change :(

---

### Post by AutoStatic on 2011-03-30
> **jakze said:**
> Jack settings: [https://help.ubuntu.com/community/FireWire?action=AttachFile&do=get&target=jack_control.png](https://help.ubuntu.com/community/FireWire?action=AttachFile&do=get&target=jack_control.png)Thanks. Try setting Periods/Buffer to 3 instead of 2. Also try setting the Input and Output channels to (default). And you're now using JACK with prio 70 but could you give the output of **ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i -e "irq" -e "jack"** with JACK running?

> **jakze said:**
> I suppose that problem makes my "Ricoh Co Ltd FireWire Host Controller (rev 01)"[http://subversion.ffado.org/wiki/HostControllers#Ricoh](http://subversion.ffado.org/wiki/HostControllers#Ricoh)
So that could be the issue.

Best,

Jeremy

---

### Post by jakze on 2011-03-30
> **AutoStatic said:**
> Thanks. Try setting Periods/Buffer to 3 instead of 2. Also try setting the Input and Output channels to (default). And you're now using JACK with prio 70 but could you give the output of **ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i -e "irq" -e "jack"** with JACK running?



```
bbb@bbb-Vostro-3700:~$ ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i -e "irq" -e "jack"
    3  TS      -  19   0 [ksoftirqd/0]
    9  TS      -  19   0 [ksoftirqd/1]
   13  TS      -  19   0 [ksoftirqd/2]
   16  TS      -  19   0 [ksoftirqd/3]
 1012  TS      -  19   0 /usr/sbin/irqbalance
 1895  TS      -  19   0 pasuspender /usr/bin/qjackctl
 1898  TS      -  19   0 /usr/bin/qjackctl
 1898  TS      -  19   0 /usr/bin/qjackctl
 1898  TS      -  19   0 /usr/bin/qjackctl
 1898  TS      -  19   0 /usr/bin/qjackctl
 1898  TS      -  19   0 /usr/bin/qjackctl
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  FF      1  41   - /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  FF     75 115   - /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  FF      1  41   - /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  FF     76 116   - /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  FF     74 114   - /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  FF     70 110   - /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1942  TS      -  19   0 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
 1960  TS      -  19   0 grep --color=auto -i -e irq -e jack

```

---

### Post by AutoStatic on 2011-03-30
Thanks again. I don't see any threaded IRQ handlers. Were you running a realtime kernel when you issued that command? And adjusting the Periods/Buffer setting to 3 didn't help? I see you ran the ps command while JACK was running with -n2 (-n is teh parameter for buffers/period).

Best,

Jeremy

---

### Post by jejeman on 2011-04-07
Here are my settings.
I`m using:
FireWire (IEEE 1394): NEC Corporation uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller (rev 01)
ubuntu studio 10.04
and the same audio card ofcourse.

---

### Post by AutoStatic on 2011-04-07
jejeman, that will probably work until you start stressing your system a bit. If you get xruns then try a Periods/Frame setting of 3 as recommended in the JACK man page.

Best,

Jeremy

---

