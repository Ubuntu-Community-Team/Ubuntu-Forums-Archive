---
title: "ffado juju jack edirol non-starter"
date: 2011-09-30
forum: Ubuntu Studio
---

### Post by AbstractFactory on 2011-09-30
Hi - first post here although I have been reading threads about the issues I'm having for over a year. I would have posted to an existing thread but I couldn't really find one that seemed right, although many similar.  

I have tried to get my Edirol FA 101 firewire audio interface working with various versions of Ubuntu Studio (Karmic - I think, Lucid, Maverick and now Natty), and have never been able to get Jackd / QjackCtl started.

I know the interface works because it ran fine out-of-the-box on win xp, using a Dell Inspiron with inbuilt firewire. I have tried it on my current Toshiba Satellite Pro 301 with a firewire expresscard (with a TI controller, fwiw) in Vista, and it can make noise, although unpleasantly distorted and weirdly slowed down as if the sample rate was set wrongly (I imagine it'd sound like that) although as far as I can tell it isn't wrong.

Anyway, I'd really like to get into using it with Ubuntu, my default O/S, or possibly another distro, so any help would be appreciated. Here's a summary of what I've done and some standard diagnostic output:

* added my user to audio and video groups
* set nice to -19, memlock to 100, enabled raw1394 access (using whatever the config file is and the ubuntu studio controls)
* added as second entry ohci1394 to RTIRQ_NAME_LIST in old raw1394 stack setup and now in natty removed that and added 'firewire'. I also added 'IEEE-1394a-2000' after seeing the thing about the 'yenta' controller, although I don't know for sure if that is the right name for mine or if it's necessary - it hasn't changed the error message anyway
* installed 3.0.0-12-lowlatency-pae kernel, before that 2.6.31-11 rt in lucid / maverick and possibly karmic
* checked that I do have libraw1394 v 2.0.6-1 installed as required by new firewire stack enabled rt in qjackctl and set the controls to standard settings as picked up on this forum and elsewhere EG priority 70, frames 128, interface hw:0, sample 48000 etc

Outputs:
*qjackctl*

 p, li { white-space: pre-wrap; }  [COLOR=#999999]23:34:30.337 Startup script...[/COLOR]
 [COLOR=#990099]23:34:30.338 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]23:34:30.740 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]23:34:30.740 JACK is starting...[/COLOR]
 [COLOR=#990099]23:34:30.741 /usr/bin/jackd -P70 -p128 -dfirewire -dhw:0 -r48000 -p128 -n3[/COLOR]
 [COLOR=#999999]23:34:30.746 JACK was started with PID=2148.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 70
 libffado 2.999.0- built Mar 28 2011 17:44:19
 [COLOR=#ff0000]23:35:05.288 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 firewire ERR: Could not start streaming threads
 Cannot start driver
 JackServer::Start() failed with -1
 Cannot read socket fd = 27 err = Connection reset by peer
 Could not read result type = 22
 Client name = qjackctl conflits with another running client
 Cannot connect to the server
 no message buffer overruns
 Failed to start server
 [COLOR=#999999]23:35:05.627 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]23:35:05.628 Post-shutdown script...[/COLOR]
 [COLOR=#990099]23:35:05.628 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]23:35:06.079 Post-shutdown script terminated with exit status=256.[/COLOR]


*lspci | grep 1394*

07:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)

*ffado-test ListDevices*

=== 1394 PORT 0 ===
Node id GUID VendorId ModelId Vendor - Model
00384939922: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 0 on port 0
1 0x0040ab0000c24b0f 0x000040AB 0x00010048 EDIROL - EDIROL FA-101
no message buffer overruns

*ffado-test Discover*

00459151193: Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
00459151297: Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
no message buffer overruns

*ffado-test-streaming*

libffado 2.999.0- built Mar 28 2011 17:44:19
00480258951: Warning (ffado.cpp)[ 121] ffado_streaming_init: Realtime scheduling is not enabled. This will cause significant reliability issues.
00480328253: Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
00480328354: Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
00480916095: Warning (avc_plug.cpp)[ 974] setSampleRate: output plug signal format command not accepted
00480935280: Error (avc_plug.cpp)[1085] setSampleRate: setSampleRatePlug: PCR Compound Input plug 0 does not support sample rate 44100
00480935380: Error (avc_avdevice.cpp)[ 261] setSamplingFrequency: setSampleRate: Setting sample rate failed
00480946368: Warning (avc_plug.cpp)[ 974] setSampleRate: output plug signal format command not accepted
00480967327: Error (avc_plug.cpp)[1085] setSampleRate: setSampleRatePlug: PCR Compound Input plug 0 does not support sample rate 44100
00480967409: Error (avc_avdevice.cpp)[ 261] setSamplingFrequency: setSampleRate: Setting sample rate failed
00480967472: Fatal (devicemanager.cpp)[ 806] initStreaming: Could not set sampling frequency to 44100
00480967509: Fatal (ffado.cpp)[ 181] ffado_streaming_init: Could not init the streaming system
00480967571: Error (teststreaming3.cpp)[ 314] main: Could not init Ffado Streaming layer
no message buffer overruns

*finally, ffado-diag (rather long, sorry)*

=== CHECK ===
 Base system...
  kernel version............ 3.0.0-12-lowlatency-pae
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
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
07:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) [104c:8235] (rev 01) (prog-if 10 [OHCI])
    Subsystem: Device [5678:1234]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 92604000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at 92600000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

   CPU info:
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               1000.000
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [258624, 258624], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [5, 5], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:           [71, 71], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:           [59, 59], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count:     [46759, 46759], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'uhci_hcd:usb7', 'firewire_ohci']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb8']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb6']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   23: PID:  None, count:     [17372, 17372], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb5']
 IRQ   42: PID:  None, count:       [6336, 6336], Sched None (priority None), drivers: ['ahci']
 IRQ   43: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   44: PID:  None, count:       [2010, 2010], Sched None (priority None), drivers: ['i915']
 IRQ   45: PID:  None, count:         [110, 110], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This is still kind of experimental. If you encounter problems, please also check
with the old stack.

*****************************************************************************

Anyone have any idea about what I'm doing wrong, or whether this just won't work with the hardware involved?

thanks

Dan

---

### Post by sgx on 2011-10-02
Hi, memlock should read 

@audio memlock unlimited

instead of 100, and proper spacing is needed in that file. Then,

try this command from a terminal:

jackd -P70 -dfirewire -r48000 -p128 -n3 -dhw:0


In qjackctl setup page, at the right, it says

Input device >
Output device >

click the > widgets to see what soundcards or chips are detected
compare them to the output of this command:

aplay -l

The hw: IDs in qjackctl may be different in different sessions, based
on hardware that is removed or added between sessions, so check the
>  widgets to see how to issue the jackd command above, in case hw:0
is not the device you suppose. (I have had the headphones in the wrong jack at times, not knowing a distro put my motherboard chip
ahead of my soundcard)

qjackctl saves that command as a textfile called .jackdrc in your home/username folder, when you save its settings.

Cheers

---

### Post by AbstractFactory on 2011-10-02
Thanks for that sgx.  I noticed that I actually had 2 entries for  memlock in limits.conf, which is probably because I had configured it  also with the ubuntu studio controls, which only offer a percentage  rating.  Anyway, I removed the other entry so it only has  @audio          -       memlock unlimited.  I see what you mean about  selecting the right hardware, and hadn't really considered that,  stupidly.  The aplay command shows this -

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Which I guess is the inbuilt sound chip.  Presumably as this is for Alsa  I wouldn't expect to see a firewire device either.  In the qjackctl  setup page, I have a number of devices listed - /dev/dsp, hw:0, hw:1,0 ,  /dev/audio, plughw:0 and (default).  Choosing any of these still  produces an error on jack startup, again with the 'could not start  streaming threads' error.  I did try to start from the command line with  your suggestion, and got much the same error, although of course the  hardware switch could be wrong

jackd -P70 -dfirewire -r48000 -p128 -n3 -dhw:0
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 70
libffado 2.999.0- built Mar 28 2011 17:44:19
firewire ERR: Could not start streaming threads
Cannot start driver
JackServer::Start() failed with -1
no message buffer overruns
Failed to start server

In the qjackctl setup I do have the input and output device controls,  but they are greyed-out, as in fact are lots of the controls - all the  checkboxes after 'unlock memory', except 'verbose messages', the word  length, wait, channels, midi driver and dither list boxes.  I don't know  why, other than perhaps these things don't apply to the inbuilt  soundcard - it's almost like it's just not seeing the firewire device,  but I don't really know.  

I would think it significant that all the ffado-test commands return largely errors and warnings - is there some way to configure ffado?

Dan

---

### Post by sgx on 2011-10-03
Older versions wanted your user to be in the disk group, also,
but you can check, just type the command

groups    in a terminal.
It is default in some distros.

In ubuntu Mint version, there is a line in /etc/limits.d folder,
saying to use

dpkg-reconfigure -p high jackd

to configure RT permissions

If you start jackd as root user using sudo, and there is no error, then you know it is a permissions issue. In qjackctl setup, in the misc tab, untick starting jackd automatically. Quit qjackctl, unplug the edirol, and run 

sudo jackd -d alsa -r 44100   it is a good basic command, that should
enable the motherboar soundchip.

If there is no error, use synaptic to install phasex and (and vkeybd if you have no midi keyboard) Then start qjackctl with

sudo qjackctl,  and also sudo phasex and sudo vkeybd etc
.
Connect things in the alsa and audio tabs. Play phasex with the
virtual or real midi keyboards. 

If this is working, note the listed hw: devices, then plug in the edirol, and if it's detected, choose it as the input device.

Stop jackd with qjackctl, restart it using sudo again, and start jackd from within qjackctl

Having the wrong input/output device should not cause the jackd error,
but might misdirect sound. The hw: ID can change between boots, if connected hardware is different.

There is a dial on the fa-101 to choose samplerate, this should be set
to your jackd setting, before booting.

guides:

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

I would also boot into a live-dvd ubuntu, and try things, you can install and edit normally, to experiment in the separate system.
Cheers

---

### Post by AbstractFactory on 2011-10-04
Thanks for that sgx.  I am in the disk group, and I had tried to start it as root, and get a similar error except it says 'unable to create virtual device' which is what I get if I start qjackctl with the sample rate set to a different rate than the fa101 when running it as normal user.

What I did notice yesterday was that the fa101 doesn't seem to show up in the setup dialog's interface list - it makes no difference if it's plugged in, the list of items is the same, so it seems that it's just not being seen.  

Also, if I enable the alsa driver instead of firewire, all the controls in the setup page are usable, and I can browse a list of the actual hardware in the 'input device' controls, unlike when I have the firewire driver enabled, when as said, many of the setup dialog controls are disabled.

I'm going to try this with AV linux, as much to see if it will work as anything - I'd rather stick to Ubuntu for everything, but getting away from the world of windows is the priority, especially as the fa101 just makes a terrible noise on vista.

cheers,
Dan

---

### Post by sgx on 2011-10-04
If AVLinux doesn't work out, pclinxos has been great for audio with my maudio card. It uses synaptic, and has ffado 2.1, jackd 116.xxx and qjackctl 3.6xxx and some synths/fx. It's a rolling release distro,
maintained for stability, instead of the newest releases.

[http://www.pclinuxos.com/forum/index.php/topic,95726.0.html](http://www.pclinuxos.com/forum/index.php/topic,95726.0.html)

is a 400 meg iso designed to run on PII 128 meg ram and up

Did you have a virgin install of Ubuntu 11.04? The guide indicates
firewire should work. If you got to 11.04 by a large update from a 10.xxx, a clean install would be worth a try.
Cheers

Did you google your specific firewire chipset for signs of compatibility?
there are some with issues, some share an irq with a troublesome videocard
or network chipset.

---

### Post by AbstractFactory on 2011-10-11
Thanks sgx - been away from this for a few days - I did manage to get the fa101 working on a dell inspiron which has built-in firewire (rather than an express card as on the machine I was using) and with AV linux, so I suspect that it is the express card / 1394 chipset that's causing the issues.  I think I'll try ubuntu on that inspiron too, and as you say search for info about my 1394 chipset. For what it's worth, the original ubuntu install was an upgrade (if that makes sense!) and I'd gone through 4 versions, but there's too much stuff on the box to want to go through the pain of rebuilding it right now - leave that for the holidays....

cheers,

Dan

---

