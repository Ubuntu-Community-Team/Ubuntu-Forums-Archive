---
title: "Seems Firewire is now no longer supported in Ubuntu Studio"
date: 2016-08-18
forum: Ubuntu Studio
---

### Post by wavesound on 2016-08-18
Hi
How about FW not working in a studio box.
After many years of using Ubuntu I find I cannot use a Saffire pro26 as I get a Dbus error connecting,
this means I have no FFADO mixer, so no recording system.

To make it worse I researched the hardware and software before buying the saffire, said to be fully supported!
I also bought a FW card supported by FFado.

It seems all the info is years out of date.

Please advise how you multi track in Linux now.

I cannot use the saffire adats with my RME card as I cannot set the unit to use adat. 

Are you all using USB?

I used two DDX 3216 on adat for years but they are now gone after giving years of good service.

Totally lost on this at the moment.

For you who may understand this I have this:

**********************************
. /sys/bus/firewire/devices/fw*/*_name
/sys/bus/firewire/devices/fw0/model_name:Juju
/sys/bus/firewire/devices/fw0/vendor_name:Linux Firewire

*****************************
I thought I would see the saffire as fw1.
Am I right in assuming fw0 is the controller?

Cheers Bob

---

### Post by jejeman on 2016-08-19
fw0 should be controller.

I've switched to USB.
Here are my last toughts on firewire [https://ubuntuforums.org/showthread.php?t=2286798](https://ubuntuforums.org/showthread.php?t=2286798)

---

### Post by wavesound on 2016-08-19
Hi What USB interface do you use?
i'm looking at the Behringer X-air 18 and wondering would Jack and Ardour be happy with this
re mutitracking.
Any advice  would be helpful.
Cheers Bob

---

### Post by jejeman on 2016-08-20
I'm using PreSonus devices. Both AudioBox 44VSL and AudioBox 1818VSL works.

---

### Post by wavesound on 2016-08-21
Hi all
Still unable to get my saffire pro 26 to work in Studio.
I get a dbus error when trying to start FFADO mixer and  jack.

I'm on Ubuntu 16.6 studio.

After much trawling of the net I can show the output below in the hope it makes sense to someone.



ffado-dbus-server &

*******************

 Fatal (devicemanager.cpp)[ 187] initialize: No firewire adapters (ports) found.
1471792641110063: Error (ffado-dbus-server.cpp)[ 277] main: Could not initialize device manager
 

*************************

 ls /dev/fw*
/dev/fw0
[1]+  Exit 255                ffado-dbus-server



**********************


dmesg | grep -i fire
[    1.592535] firewire_ohci 0000:05:00.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    2.093690] firewire_core 0000:05:00.0: created device fw0: GUID 00000000000016ef, S400



********************

lsmod | grep -i fire
firewire_ohci          40960  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core

******************************


studio@studio-T5500:~$ lspci -kvnn | grep -i fire -A 5
05:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) [104c:8235] (rev 01) (prog-if 10 [OHCI])
	Subsystem: Device [5678:1234]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 26
	Memory at f7dfb000 (32-bit, non-prefetchable) [size=2K]
	Memory at f7dfc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire_ohci


*****************************************

ffado-dbus-server
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.2.1-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

1471793480108097:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
1471793480109560: Fatal (devicemanager.cpp)[ 187] initialize: No firewire adapters (ports) found.
1471793480109570: Error (ffado-dbus-server.cpp)[ 277] main: Could not initialize device manager
1471793480109582: Debug (ffado-dbus-server.cpp)[ 202] exitfunction: Debug output flushed...
no message buffer overruns
studio@studio-T5500:~$ 


***********************************
I'm a member of the Audio group.


cheers Bob (wavesound)

---

### Post by jejeman on 2016-08-21
Regardless of FFADO and JACK you need to have two "fw" device nodes. fw0 for controler and fw1 for the sound card.
I have no "real" advice. Check cable, change port etc. Try another firewire device (camera) to see if it creates fw1 node.

---

