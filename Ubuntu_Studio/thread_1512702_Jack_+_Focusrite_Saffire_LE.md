---
title: "Jack + Focusrite Saffire LE"
date: 2010-06-18
forum: Ubuntu Studio
---

### Post by MezzFA0 on 2010-06-18
Hi all,

I've been trying to wrap my head around getting a firewire sound card working in ubu studio 10 for the past 4 days and between countless google searches, forum posts and blogs I'm finally out of things to try.  The reason I need to do this is so I can take a live feed from a mixing desk for an upcoming charity event to be held in the middle of July and send it off to something like ustream.

I apologise if I'm posting this in the wrong place as I appreciate this will touch on jack, ubu and ffado support.  I also apologise for the length of this post as I'm trying to put down all relevant information.

In the very least I have made some progress.  I'm using a random Intel Core 2 with the following:

[LIST]
[*]PCI Firewire: 02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
[*]On board Audio: 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
[*]Focusrite Saffire LE (Firewire)
[/LIST]
After getting nowhere fast I have so far tried the following with no effect:

[LIST]
[*]Disabling onboard audio and reinstalling from scratch
[*]Using the instructions from ffado compiling from source on a random blog that I've lost the link for
[*]Messing about with lots of outdated documentation and trying to piece together something that works (A lot of the saffire le users seem to be using Ubu 8.1 back in 2008).
[/LIST]
I finally stumbled across the following pages and as such have done nothing more than follow these instructions exactly:

[http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu)

The sound card is now responsive however Jack is not happy.  Everything starts up and then dies after about 1 - 2 seconds.  I have tried changing the settings in jack as suggested after googling the error but this did not work either.  The output from Jack in verbose mode is as follows:

```
15:47:38.624 Startup script...
15:47:38.624 artsshell -q terminate
sh: artsshell: not found
15:47:39.026 Startup script terminated with exit status=32512.
15:47:39.026 JACK is starting...
15:47:39.026 /usr/bin/jackd -v -P80 -p512 -t1000 -dfirewire -r96000 -p256 -n3
15:47:39.029 JACK was started with PID=1793.
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1538289
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_net.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: firewire_pcm, id = 1 type 1 @ 0x8795620 fd = -1
new buffer size 256
resizing port buffer segment for type 0, one buffer = 1024 bytes
resizing port buffer segment for type 1, one buffer = 1024 bytes
00287933870:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1857 built Jun 18 2010 15:30:51
firewire MSG: Streaming thread running with Realtime scheduling, priority 80
firewire MSG: Registering audio capture port C0_00130e0100041699_Rec 1
registered port system:capture_1, offset = 1024
firewire MSG: Registering audio capture port C1_00130e0100041699_Rec 2
registered port system:capture_2, offset = 2048
firewire MSG: Registering audio capture port C2_00130e0100041699_Rec 3
registered port system:capture_3, offset = 3072
firewire MSG: Registering audio capture port C3_00130e0100041699_Rec 4
registered port system:capture_4, offset = 4096
firewire MSG: Registering audio capture port C4_00130e0100041699_Rec 5
registered port system:capture_5, offset = 5120
firewire MSG: Registering audio capture port C5_00130e0100041699_Rec 6
registered port system:capture_6, offset = 6144
firewire MSG: Registering midi capture port C6_00130e0100041699_Midi In
registered port firewire_pcm:C6_00130e0100041699_Midi In, offset = 1024
firewire MSG: Registering audio playback port P0_00130e0100041699_Play 1
registered port system:playback_1, offset = 0
firewire MSG: Registering audio playback port P1_00130e0100041699_Play 2
registered port system:playback_2, offset = 0
firewire MSG: Registering audio playback port P2_00130e0100041699_Play 3
registered port system:playback_3, offset = 0
firewire MSG: Registering audio playback port P3_00130e0100041699_Play 4
registered port system:playback_4, offset = 0
firewire MSG: Registering audio playback port P4_00130e0100041699_Play 5
registered port system:playback_5, offset = 0
firewire MSG: Registering audio playback port P5_00130e0100041699_Play 6
registered port system:playback_6, offset = 0
firewire MSG: Registering audio playback port P6_00130e0100041699_Play 7
registered port system:playback_7, offset = 0
firewire MSG: Registering audio playback port P7_00130e0100041699_Play 8
registered port system:playback_8, offset = 0
firewire MSG: Registering midi playback port P8_00130e0100041699_Midi Out
registered port firewire_pcm:P8_00130e0100041699_Midi Out, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
-- jack_rechain_graph()
-- jack_sort_graph
15:47:41.158 Server configuration saved to "/home/thevoiceasia/.jackdrc".
15:47:41.158 Statistics reset.
15:47:41.162 Client activated.
15:47:41.164 JACK connection change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb77b3000 fd = 18
start poll on 4 fd's
server thread back from poll
new client qjackctl using 19 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll

<--- snip last two lines are repeated several times --->

firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver
server thread back from poll
15:47:45.462 JACK connection graph change.
unloading driver
client event poll on 19 for qjackctl starts at 294325572
back from client event poll after 10 usecs
client event poll on 19 for qjackctl starts at 294325616
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325655
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325693
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325730
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325767
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325804
back from client event poll after 6 usecs
client event poll on 19 for qjackctl starts at 294325841
back from client event poll after 6 usecs
client event poll on 19 for qjackctl starts at 294325877
back from client event poll after 6 usecs
client event poll on 19 for qjackctl starts at 294325913
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325949
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294325985
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294326021
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294326057
back from client event poll after 7 usecs
client event poll on 19 for qjackctl starts at 294326094
back from client event poll after 6 usecs
client event poll on 19 for qjackctl starts at 294326130
back from client event poll after 7 usecs
no message buffer overruns
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
cannot read server event (Success)
cannot continue execution of the processing graph (Bad file descriptor)

<--- line repeated a lot --->

15:47:45.555 Client deactivated.
cannot continue execution of t
15:47:45.556 JACK was stopped successfully.
15:47:45.556 Post-shutdown script...
15:47:45.556 killall jackd
he processing graph (Bad file descriptor)
cannot continue execution of the processing graph (Bad file descriptor)

<--- line repeated a lot --->

jackd: no process found
```Some things I have noticed after running jack, my dmesg | tail outputs the following more times than I care to count:

```
[ 4776.234027] ieee1394: unsolicited response packet received - no tlabel match
```The ffado-mixer works with the device and seems to be doing its thing.

ffado-test ListDevices outputs the following:

```
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1857
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e0100041699  0x0000130E  0x00000000   Focusrite - SaffireLE
   1       0x001074720000b781  0x00001074  0x00000000   Linux - ohci1394  - 
no message buffer overruns

```ffado-test Discover outputs the following:

```

FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1857
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

05247113413: Debug (devicemanager.cpp)[ 358] discover: Starting discovery...
05247224629: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
05247224694: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 4878 (0x0000130E)
05247224713: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 0 (0x00000000)
05247224736: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Focusrite
05247224754: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Saffire (LE)
05247224774: Debug (Configuration.cpp)[ 185] showSetting:     driver = 1 (0x00000001)
05247224791: Debug (Configuration.cpp)[ 209] showSetting:     mixer = Saffire
05247224810: Debug (Configuration.cpp)[ 185] showSetting:     cmd_interval_time = 10000 (0x00002710)
05247224827: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 4 (0x00000004)
05247225090: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
05247225110: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 4878 (0x0000130E)
05247225131: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 0 (0x00000000)
05247225147: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Focusrite
05247225167: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Saffire (LE)
05247225183: Debug (Configuration.cpp)[ 185] showSetting:     driver = 1 (0x00000001)
05247225205: Debug (Configuration.cpp)[ 209] showSetting:     mixer = Saffire
05247225221: Debug (Configuration.cpp)[ 185] showSetting:     cmd_interval_time = 10000 (0x00002710)
05247225240: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 4 (0x00000004)
05247225277: Debug (devicemanager.cpp)[ 620] discover: driver found for device 0
05247227767: Error (ieee1394service.cpp)[ 750] doFcpTransaction: FCP transaction didn't succeed in 2 tries
05247227785: Warning (ieee1394service.cpp)[ 725] transactionBlock: FCP transaction failed
05247227806: Error (bebob_avdevice.cpp)[ 560] getConfigurationIdSampleRate: Stream format command failed
05247230237: Error (ieee1394service.cpp)[ 750] doFcpTransaction: FCP transaction didn't succeed in 2 tries
05247230260: Warning (ieee1394service.cpp)[ 725] transactionBlock: FCP transaction failed
05247230275: Error (bebob_avdevice.cpp)[ 597] getConfigurationIdNumberOfChannel: Number of channels command failed
05247232678: Error (ieee1394service.cpp)[ 750] doFcpTransaction: FCP transaction didn't succeed in 2 tries
05247232696: Warning (ieee1394service.cpp)[ 725] transactionBlock: FCP transaction failed
05247232715: Error (bebob_avdevice.cpp)[ 597] getConfigurationIdNumberOfChannel: Number of channels command failed
05247235076: Error (ieee1394service.cpp)[ 750] doFcpTransaction: FCP transaction didn't succeed in 2 tries
05247235096: Warning (ieee1394service.cpp)[ 725] transactionBlock: FCP transaction failed
05247235111: Error (bebob_avdevice.cpp)[ 629] getConfigurationIdSyncMode: Signal source command failed
05247235136: Debug (bebob_avdevice.cpp)[ 734] loadFromCache: filename /home/thevoiceasia/.ffado/cache/00130e0100041699/0000000000000000.xml
05247235161: Debug (bebob_avdevice.cpp)[ 738] loadFromCache: "/home/thevoiceasia/.ffado/cache/00130e0100041699/0000000000000000.xml" does not exist
05247235207: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
05247235225: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 4878 (0x0000130E)
05247235245: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 0 (0x00000000)
05247235261: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Focusrite
05247235281: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Saffire (LE)
05247235296: Debug (Configuration.cpp)[ 185] showSetting:     driver = 1 (0x00000001)
05247235316: Debug (Configuration.cpp)[ 209] showSetting:     mixer = Saffire
05247235332: Debug (Configuration.cpp)[ 185] showSetting:     cmd_interval_time = 10000 (0x00002710)
05247235351: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 4 (0x00000004)
05247237754: Error (ieee1394service.cpp)[ 750] doFcpTransaction: FCP transaction didn't succeed in 2 tries
05247237776: Warning (ieee1394service.cpp)[ 725] transactionBlock: FCP transaction failed
05247237791: Error (avc_unit.cpp)[ 250] enumerateSubUnits: Subunit info command failed
05247237810: Error (avc_unit.cpp)[ 177] discover: Could not enumarate sub units
05247237824: Error (bebob_avdevice.cpp)[ 192] discover: Could not discover unit
05247237845: Error (devicemanager.cpp)[ 632] discover: could not discover device
05247237923: Debug (devicemanager.cpp)[ 665] discover: Discovery finished...
05247237945: Debug (devicemanager.cpp)[1252] showDeviceInfo: ===== Device Manager =====
05247237961: Debug (Element.cpp)[ 121] show: Element DeviceManager
05247237979: Debug (devicemanager.cpp)[1260] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
no message buffer overruns

```If anyone can point me in the right direction it would be much appreciated.  If there is any more information that would be useful I can certainly supply it.

---

### Post by AutoStatic on 2010-06-18
Hello MezzFA0,

```
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver
```

This could indicate something is blocking the Firewire card. Could you post the outcome of the terminal commands **cat /proc/interrupts** ans **lspci**? Thanks. And I would also try lowering jackd's prio to 70 instead of 80.

Best,

Jeremy

---

### Post by MezzFA0 on 2010-06-19
Thanks for the reply Auto, here are the results of cat /proc/interrupts:

```
           CPU0       CPU1       
  0:         48          1   IO-APIC-edge      timer
  1:          2          2   IO-APIC-edge      i8042
  6:          1          1   IO-APIC-edge      floppy
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          3          3   IO-APIC-edge      i8042
 16:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 18:          1          2   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb8
 19:      24338       1218   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb5, uhci_hcd:usb7
 21:         42      14374   IO-APIC-fasteoi   uhci_hcd:usb4, ohci1394
 22:        958        299   IO-APIC-fasteoi   HDA Intel
 23:        253      84561   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 25:         12      22198   PCI-MSI-edge      eth0
 26:       2688         22   PCI-MSI-edge      i915
NMI:          0          0   Non-maskable interrupts
LOC:     120748      56115   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       1410       1213   Rescheduling interrupts
CAL:         93         72   Function call interrupts
TLB:        442        401   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          4          4   Machine check polls
ERR:          1
MIS:          0

```

Here is lspci:

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

One extra thing I've noticed since yesterday when first starting up if I run ffado-mixer it connects and works as normal, however the sound card doesn't really do much.  The way I test this is there are two mode switches on this card that switch from line to inst.  By default the buttons are none responsive and stuck in inst mode.  

If you then start jack the sound card clicks into life and the buttons work.  Then jack crashes leaving the sound card in the same 'usable' state.  

If you then close jack and ffado-mixer.  Then try and reopen ffado-mixer you get an error saying no supported devices found.  To get around this you can unplug the card from the firewire port, leave it a few seconds and plug it back in.  Then you can start all over again.

My only hope now is while on my travels that I haven't unwittingly fixed the problem but didn't realise that the firewire bus/sound card was stuck in this zombie state.

Thanks again for looking into this, it is much appreciated.

---

### Post by AutoStatic on 2010-06-19
IRQ's look ok, Firewire shares an interrupt with a USB port but that shouldn't be an issue as long as you don't use that port.
Does the Focusrite come with a power adapter? If so did you try it with the adapter too? And I reckon you also checked your cables, you really need some decent Firewire cables. What kind of Firewire ports are on your computer? 4 or 6 pins? If it's 4 pins you definitely need to use an external power adapter for your Focusrite.

---

### Post by MezzFA0 on 2010-06-19
There are 6 pins on the firewire ports.  Basically I don't need the adapter to power it up however have been using it anyway (tried it without with no change).

The firewire cable works fine with a Sony HD DV Cam so its not the cable.  I initially started by getting the DV cam to work thinking that would be the hard part before moving onto the sound.

How wrong that turned out to be.  Just to alay any fears, like I said the box has been completely flattened since then, its a vanilla install with only the sound card on it.

I've set up a vnc server on the system and removed the usb keyboard/mouse just in case (not really sure which port was usb 4 so stopped using usb).  This makes no difference.

Jack is actually killing my firewire device everytime it crashes.  I have to move it to a different firewire port to get it re-recognised by lspci and ffado.

I honestly have no idea where to go from here.  I may have to admit defeat as all these mythical Saffire LE users seem to have vanished into the ether.  The only alternative is to take a feed from the desk to line in and use the onboard card I guess.

Unfortunately that may need 3 different computers instead of 2 but so be it.

---

### Post by cchhrriiss121212 on 2010-06-19
This might be the source of your problem, if you are using 10.04:
> ***With the new Firewire stack in Ubuntu Kernel, at the moment, it is not possible to run FFADO sound cards nor use Firewire for DV capture with -generic and -lowlatency kernels. Please see instructions on this page to install -rt kernel on this page, wich has old working stack. Until the new firewire stack works well with FFADO et DV capture, this section needs a complete rewrite.***
Which is from [this studio prep guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation"). So you could try out an rt kernel.

---

### Post by Icebear on 2010-06-19
make sure you have the sample rate the same in jack as well ffado

I have pulled much of my hair out a couple times when they unknow to me one was acidently changed.

---

### Post by MezzFA0 on 2010-06-19
First of all thanks for all the support.  Unfortunately I'm not any further forward.

I could have sworn I was on the RT kernel but I was evidently not.  So that has been installed and booted into (2.6.31-10-rt).  No change.

ffado-mixer is set to 48,000 same as Jack (for some reason ffado mixer kept defaulting to that so I made Jack the same).

Before I start I'm saving the config to the device in ffado-mixer just to make sure.  I've also tried all sorts of different frame settings with no dice.

---

### Post by AutoStatic on 2010-06-19
> **MezzFA0 said:**
> I could have sworn I was on the RT kernel but I was evidently not.  So that has been installed and booted into (2.6.31-10-rt).  No change.You were already booted into the 2.6.31 kernel otherwise the card wouldn't have been recognised in the first place I reckon since the ffado drivers that come with 10.04 don't work with the juju stack from the 2.6.32 kernels. But I could be wrong here, haven't worked with Firewire on 10.04 yet.

> **MezzFA0 said:**
> ffado-mixer is set to 48,000 same as Jack (for some reason ffado mixer kept defaulting to that so I made Jack the same).AFAIK this should be detected automatically, on my machine I can't change the samplerate in ffado-mixer, it's greyed out.

You could try installing **rtirq-init** and add your Firewire controller to the */etc/default/rtirq* file. With **sudo gedit /etc/default/rtirq** you can open the file for editing and then you need to add ' ohci1394' (without the quotes but surrounded by spaces) to the folowing lines after 'rtc':
RTIRQ_NAME_LIST=
RTIRQ_NON_THREADED=

So that it looks like this:
```
RTIRQ_NAME_LIST="rtc ohci1394 i8042"
...
RTIRQ_NON_THREADED="rtc ohci1394"
```

Then save this file and restart rtirq with **sudo /etc/init.d/rtirq restart**
Also make sure jackd is running prio 70 otherwise it might get in the way of the prio of your Firewire controller.

---

### Post by MezzFA0 on 2010-06-19
You are correct, the default install of Ubu Studio 10 doesn't work properly with ffado.  I can see my firewire card on ffado-test ListDevices but Discover produces all sorts of nasty errors and basically nothing works.

Anyway for reasons of insanity I reinstalled Ubu Studio.  On a vanilla install uname -r returns:

2.6.32-21-generic

This is why I installed the rt kernel earlier today.  I even sat here (bored senseless) reading the install and it actually installs the RT headers but you have no option to boot into it.

The instructions here ([http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu)) actually walk you through reinstalling jack and ffado from source which is where I'd got to and hence why things sort of worked (briefly).

If you do ffado-test --version once you've followed these instructions you get 2.99.something whereas a vanilla ubustu 10 gives you 2.0.0.

I have already tried the RTIRQ stuff after reading a lot more around the RT kernel based on Chris' post with again no change.

I'm now off to install the RT kernel without following the subversion.ffado instructions to see what happens (its a long shot that probably won't work but its something to do other than google).  I noticed that there are two RT kernels in synaptic so I'm now installing the other one (Edit: My Mistake I saw the two different version numbers and got confused.  It looks like they're all related having double checked).

As for things to try next, I'm toying with the idea of getting myself a nice jacket from the men in white coats or buying a big hammer.  I'll let you know how it goes :P

---

### Post by Pablo_F on 2010-06-19
After installing a kernel, make sure grub is aware of it by doing a:

$sudo update-grub

Installing only the headers is useless, you need the image (linux-image).

---

### Post by MezzFA0 on 2010-06-20
Hi Pablo,

Rest assured that I have been making grub aware of the kernel.

I was just reiterating the fact that during an Ubuntu Studio 10.04 install you will see it installing the RT headers and things however it either doesn't install all of the required components or doesn't configure grub for it.

Anyway I am relatively new to the guts of Linux so I simply used synaptic to download the linux-rt packages and then ran startup manager to configure the RT kernel as the default boot.

As an update since yesterday, my long shot didn't work.  Installing the RT kernel and not updating ffado makes no difference for the Firewire Focusrite Saffire LE.

ffado-test Discover just dies.  You get no output unless the verbose level is high enough.

You have to install the latest ffado from the svn to get the device half working.

Unfortunately Jack still crashes in the same way with the Driver NT error.

Once again thanks for all the support received, I'll have to grind this one out or look for alternatives I guess.

---

### Post by AutoStatic on 2010-06-21
Hello MezzFA0,

I think it is best to stick to the following steps:
[LIST=1]
[*]Install the 2.6.31-10-rt kernel
[*]Install libffado, ffado-tools, ffado-mixer-qt4 and ffado-dbus-server from the default repositories (so don't compile from SVN)
[*]Configure your system: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
[*]In your specific case go through step 6 of the Firewire Help page
[/LIST]

You really don't need to compile the version from SVN, first of all because your device is [fully supported]("http://ffado.org/?q=node/16") and second because the 2.6.31-10-rt kernel has the old firewire stack enabled. On 10.04 you only need to compile FFADO from source or SVN if you want to use your card with the new juju Firewire stack or if you have a card that is not fully supported by the ffado drivers that come with Lucid.
If you still have errors after going through these steps we need to troubleshoot those. This card must run on your machine with 10.04!

---

### Post by MezzFA0 on 2010-06-21
Hi again Auto,

Thanks for the continued assistance.  Following your instructions here  is what I've done:

[LIST=1]
[*]Installed Ubuntu Studio 10.04 from the DVD
[*]Selected Audio and Video Creation
[*]Enabled real time access
[*]Booted into it once it finished installing
[*]Opened up Synaptic and installed: linux-rt which also bundles  linux-image-2.6.31-10-rt and linux-image-rt
[*]Ran update-grub and then manually booted into Ubuntu, with Linux  2.6.31-10-rt from the grub menu.
[*]All the packages listed in step 2 were already installed so I  reinstalled them just to be sure.  However libffado is only listed as  libffado2.
[*]Now onto the firewire stuff.  Enabled raw1394 from studio  controls.  Added myself to the audio and video groups (double checked in  the user priviledges for corresponding matches).
[*]Rebooted
[*]ls -al /dev/raw1394 showed root audio instead of root video.   Changed this with chgrp to properly reflect root video.
[*]Added the rtirq changes: RTIRQ_NAME_LIST="rtc ohci1394 snd usb  i8042"     RTIRQ_NON_THREADED="rtc ohci1394 snd"
[*]Rebooted
[/LIST]
 
Basically this is where I got to before I posted on the forums.

ffado-test ListDevices:
```
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e0100041699  0x0000130E  0x00000000   Focusrite -  SaffireLE
   1       0x001074720000b781  0x00001074  0x00000000   Linux -  ohci1394  - 
no message buffer overruns

```ffado-test Discover:

```
---------------------------

no message buffer overruns

```Which obviously isn't right.

ffado-dbus-server:
```
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

 Discovering devices...
05899444827: Error (bebob_avplug.cpp)[ 161] discover: Could not discover  stream format (0,31,255,0,1)
05899444848: Error (avc_unit.cpp)[ 474] discoverPlugsExternal: plug  discovering failed
05899444853: Error (avc_unit.cpp)[ 408] discoverPlugs: external input  plug discovering failed
05899444862: Error (avc_unit.cpp)[ 182] discover: Detecting plugs failed
05899444866: Error (bebob_avdevice.cpp)[ 192] discover: Could not  discover unit
05899444875: Error (devicemanager.cpp)[ 606] discover: could not  discover device
 Starting DBUS service...
 Running... (press ctrl-c to stop & exit)
```The way I got around the discover problem before was to install from  svn.  However that obviously still didn't work for jack.

Thanks again for your time either way.

---

### Post by Pablo_F on 2010-06-21
Maybe the old firewire stack is blacklisted? 

Edit as superuser:

/etc/modprobe.d/blacklist-firewire.conf

to contain:

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2

Seen at:

[http://www.ffado.org/?q=node/1316](http://www.ffado.org/?q=node/1316)

---

### Post by AutoStatic on 2010-06-21
The old stack is not blacklisted afaik (not on Lucid atm): [http://ubuntuforums.org/showthread.php?t=1508531](http://ubuntuforums.org/showthread.php?t=1508531)

---

### Post by mango42 on 2010-06-22
The moving between kernel versions vis-a-vis ffado is making my head whirl.

So I'm probably going to ask the dumbest question ever - which version of UbuntuStudio would be the most likely to produce at least some I/O with a Saffire PRO 40? 64bit 9.10, 10.04 or a do it yourself version the way **AutoStatic** does it?

I am at about the same point as **MezzFA0** with **ffado-test Discover** returning the same error messages, except for the difference in Focusrite models. I think I have performed *all* the necessary ritual incantations, including 40-permissions, /etc/udev/rules.d/50-udev-firewire.rules , blacklisting whatever, joining this(audio), that(video) and the other(disk)

Perhaps I should now try

```
sudo chown root:audio /dev/raw1394
```

or should I upgrade from 2.6.31-9-rt before trying anything else; or maybe revert from UbuntuStudio 9.10 to vanilla 9.10 and build from scratch?

---

### Post by AutoStatic on 2010-06-22
Hello mango42, the Saffire Pro 40 is not fully supported by the ffado version that comes with Karmic afaik. You will probably need 2.0.1 and apparently there's no package for it so you probably need to compile it yourself or ask philip5 or falkTX if they'd like to package it. 

And I'm on Lucid now and the old stack is not blacklisted, so for 10.04 with a 2.6.31-10-rt kernel supported Firewire devices should work with ffado.

---

### Post by MezzFA0 on 2010-06-22
I must say that I was hoping I'd have more luck than I did.  I specifically sourced hardware that was apparently supported.  Even going as far as checking the firewire card was a TI chipset.

But anyway I feel your pain :P  Due to time constraints, I'm about to call it quits to be honest and just use the on board sound card for ustreaming/broadcast archiving and employ a Windows Laptop for the other stuff (I just need to make an XLR to 3.5mm jack cable).

As for needing version 2.01 the SVN instructions on the subversion page were very easy to follow:

[http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu)

Right at the top are step by step 10.04 instructions which 'worked' for me.  I'm still convinced that the packaged ffado is dead in the water and that I'll need to use the newer versions (namely because at least ffado-mixer works with the newer version).

Good luck.

---

### Post by mango42 on 2010-06-23
Thanks for the positive responses. Guess I'm desperate enough to try the ffado SVN now (having reached the limit of credibility with feeding my mixdowns out of a laptop headphone socket). ;-)

Another very basic query, as I'm about to give up on Alienware altogether - which recent (<2years) laptop make and model has anyone here had the most success with running UbuntuStudio smoothly?

And finally an old *hardware* chestnut - is it really advisable to hotplug firewire devices,as some suggest? I think not, unless some serious design revision has taken place since I last looked a few years back.

---

### Post by MezzFA0 on 2010-06-28
I can't help you on the other questions but I've not had issues hot plugging firewire devices.  Granted most of my past experience with that is on Windows but in my ubu studio setup, as long as it was plugged in before I started the software everything was fine.

---

### Post by trulan on 2010-06-28
> **mango42 said:**
> Which recent (<2years) laptop make and model has anyone here had the most success with running UbuntuStudio smoothly?
Dell Latitude E5500 here, with Intel Core 2 Duo processor and 2 gigs ram.  It's a pretty basic, cheap machine.  The only two issues that I ran into were:
1. The Intel i915 graphics chip likes at least Xorg 7.5 - so nothing older that Lucid.
2. The onboard Ricoh firewire chip (which works marvelously despite many old rumors saying otherwise) shares its IRQ with the wireless card - so no firewire audio while the wireless switch is turned on.  (FWIW, the pc-card slot has its own IRQ, so this problem could be eliminated by using a pc-card instead of the ondoard.)
Before that I had an older Dell Inspiron, same Ricoh chip, also good success.

> And finally an old *hardware* chestnut - is it really advisable to hotplug firewire devices,as some suggest? I think not, unless some serious design revision has taken place since I last looked a few years back.I've never had any issues, as long as I plug them in and turn them on before starting Jack.

---

### Post by mango42 on 2010-06-29
> **trulan said:**
> ... ...Before that I had an older Dell Inspiron, same Ricoh chip, also good success.

I've never had any issues, as long as I plug them in and turn them on before starting Jack.

Thanks very much for the info, **trulan** - I guess when it comes to Ricoh chips, it must depend on which variety, as the one in T43 Thinkpads will have nothing to do with ExpressCard firewire whatsoever.

Now I've got JACK talking to this Saffire Pro40 on a 64bit machine, seems there's a whole other dimension to problems to overcome. Sure, it's early days yet and JACK locking up every few minutes implies the driver is not yet stable enough to entrust the output of my 'musical genius'... ;-) 

So I'm off to check out that E5500 (I wonder whether yours came with Ubuntu installed?)- then at least I'd be 'on the same page' as you when you make yet another wonderful stride forward!

:popcorn:

---

### Post by AutoStatic on 2010-06-29
I have a HP DV7-1070 which works well with Ubuntu and Firewire too. It's got a JMicron Firewire controller.

FYI, I've just ordered the Saffire Pro 40's little brother, the 24. Not for personal use, but for my work. I intend to set up an Ubuntu machine with this card. Ok, the machine that I'm going to use is not a notebook and I ordered a separate Belkin Firewire card with the Focusrite, but nonetheless maybe some useful info will come out.

---

### Post by mango42 on 2010-06-29
> **AutoStatic said:**
> I have a HP DV7-1070 which works well with Ubuntu and Firewire too. It's got a JMicron Firewire controller.

FYI, I've just ordered the Saffire Pro 40's little brother, the 24. Not for personal use, but for my work. I intend to set up an Ubuntu machine with this card. Ok, the machine that I'm going to use is not a notebook and I ordered a separate Belkin Firewire card with the Focusrite, but nonetheless maybe some useful info will come out.

I am sure it will - I for one look forward to your discoveries. On a side note, I was recently offered a similar HP laptop (nVidia 9x00-based?) but just before I got there someone had managed to leave a cigarette lighter on the keyboard with the lid partly closed and apparently 'someone else' accidentally sat on it....

On such chaos our world is run... ):P

---

### Post by trulan on 2010-06-29
> **mango42 said:**
> Thanks very much for the info, **trulan** - I guess when it comes to Ricoh chips, it must depend on which variety, as the one in T43 Thinkpads will have nothing to do with ExpressCard firewire whatsoever.
On that older Dell, the ExpressCard slot was useless for firewire under Windows and Ubuntu.  I've always used the onboard firewire chips with the little 4-pin plug.  That never actually worked under Windows XP either (it did work under a test install of Win7, but I had tasetd too much Ubuntu by then).

And no, the E5500 did not come with Ubuntu installed - it had Windows Vista Home Basic (that made it easy to justify totally wiping the HD - had some semi-useful version of windows been installed I might have had second thoughts about it.)

---

### Post by mango42 on 2010-06-30
> **"MezzFAO"]I've not had issues hot plugging firewire devices.[/QUOTE]

My apologies for missing your post and thanks for the confirmation. My head is probably stuck in the early '90's, chip-version-wise  said:**
> the E5500 did not come with Ubuntu installed - it had Windows Vista Home Basic (that made it easy to justify totally wiping the HD - had some semi-useful version of windows been installed I might have had second thoughts about it.)

I notice some suppliers are now offering an 'XP rollback', for an extra consideration, of course... :lolflag:

It's very odd, I rarely took to the commandline in windows yet always felt I was not in charge of my own computer and that I needed to fight the system the whole way yet, *despite some of my posts here*, even commandline hell on Linux is actually more fun than any amount of windows superficial glitz-but-no-guts. (Eg: try running two instances of Cubase on XP then run three instances of QTractor and/or Hydrogen under Jack on UbuntuStudio... no contest! ;-) ) and when all else fails, LiveCD comes to the rescue. Perfick!

---

### Post by orionhedges on 2010-09-16
Hi,

Am also having dramas getting a saffire LE to work with ubuntu 10.04.  FFADO mixer loads, detect the device and displays correctly.  However when I start Jack it fails almost immediately outputting the following:

23:29:19.031 Patchbay deactivated.
23:29:19.078 Statistics reset.
23:29:19.382 ALSA connection graph change.
23:29:19.579 ALSA connection change.
23:29:51.763 Startup script...
23:29:51.765 artsshell -q terminate
sh: artsshell: not found
23:29:52.167 Startup script terminated with exit status=32512.
23:29:52.168 JACK is starting...
23:29:52.168 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r48000 -p128 -n2
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    758211
23:29:52.201 JACK was started with PID=4522.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
00092820543:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1883 built Sep  5 2010 23:29:43
23:29:54.252 Server configuration saved to "/home/ori-cool/.jackdrc".
23:29:54.254 Statistics reset.
23:29:55.056 Client activated.
23:29:55.058 JACK connection change.
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
23:29:57.740 JACK connection graph change.
23:29:57.864 JACK connection change.
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

Unfortunately my knowledge doesn't extend to gaining any useful strategies from the above.  Any suggestions would be very welcome.

---

