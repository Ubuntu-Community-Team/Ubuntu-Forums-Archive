---
title: "Firebox on ubuntu-studio 8.04.1"
date: 2009-03-18
forum: Ubuntu Studio
---

### Post by Tch3tch on 2009-03-18
Hi all! It's my first post in the ubuntu's english forum and I hope, that my problem won't be to tricky... or maybe that it will (common! Some of you guys love tricky problems, don't you ? :P:P:P)

Anyway, I'll try to be as complete as I can.

I got a presonus Firebox, a firewire soundcard fully supported by Freebob/FFADO. STILL, it doesn't work... well not properly. 

When I launch Jack, the card becomes synchronized but jack stops after a while (few seconds, or as soon as I launch a jack's application such as Ardour). Yet the card is still synchronized (blue led on)! 

Here are the messages

WHEN I USE " jackd -R -P 50 -d firewire -p 1024 -v3" on the terminal

```

no message buffer overruns
Unknownage with option 'v'
Options for driver 'freebob':
	-d, --device 	The FireWire device to use. Format is: 'hw:port[,node]'. (default: hw:0)
	-p, --period 	Frames per period (default: 1024)
	-n, --nperiods 	Number of periods of playback latency (default: 3)
	-r, --rate 	Sample rate (default: 48000)
	-C, --capture 	Provide capture ports. (default: false)
	-P, --playback 	Provide playback ports. (default: false)
	-D, --duplex 	Provide both capture and playback ports. (default: true)
	-I, --input-latency 	Extra input latency (frames) (default: 0)
	-O, --output-latency 	Extra output latency (frames) (default: 0)
	-i, --inchannels 	Number of input channels to provide (note: currently ignored) (default: 0)
	-o, --outchannels 	Number of output channels to provide (note: currently ignored) (default: 0)
tch@tch-laptop:~$ jackd -R -P 50 -d firewire -p 1024 -v3
no message buffer overruns
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
00169973467:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Nov 22 2008 23:12:02
00171478925: Debug (bebob_mixer.cpp)[ 126] addElementForAllFunctionBlocks: Adding elements for functionblocks...
firewire MSG: Streaming thread running with Realtime scheduling, priority 54
firewire MSG: Registering audio capture port C0_dev0_Mic/InstIn 1
firewire MSG: Registering audio capture port C1_dev0_Mic/InstIn 2
firewire MSG: Registering audio capture port C2_dev0_LineIn L
firewire MSG: Registering audio capture port C3_dev0_LineIn R
firewire MSG: Registering audio capture port C4_dev0_SPDIFIn L
firewire MSG: Registering audio capture port C5_dev0_SPDIFIn R
firewire MSG: Registering midi capture port C6_dev0_MidiIn 1
firewire MSG: Registering audio playback port P0_dev0_MainOut 1L
firewire MSG: Registering audio playback port P1_dev0_MainOut 2R
firewire MSG: Registering audio playback port P2_dev0_LineOut 3L
firewire MSG: Registering audio playback port P3_dev0_LineOut 4R
firewire MSG: Registering audio playback port P4_dev0_LineOut 5L
firewire MSG: Registering audio playback port P5_dev0_LineOut 6R
firewire MSG: Registering audio playback port P6_dev0_SpdifOut L
firewire MSG: Registering audio playback port P7_dev0_SpdifOut R
firewire MSG: Registering midi playback port P8_dev0_MidiOut 1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
00174421752: Warning (IsoHandlerManager.cpp)[ 286] Execute: Timeout while waiting for activity
00175432370: Warning (IsoHandlerManager.cpp)[ 286] Execute: Timeout while waiting for activity
00175443066: Fatal (IsoHandlerManager.cpp)[ 342] Execute: (0x8080488, Transmit) Handler died: now: 511B3389, last: 4D17E0DA, diff: 49315503 (max: 49152000)
00175443094: Warning (StreamProcessor.cpp)[ 127] handlerDied: Handler died for 0x80a7f30
00175463749: Warning (devicemanager.cpp)[ 886] waitForPeriod: XRUN detected
00175463835: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175463853: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175463863: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175463875: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175463893: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175463903: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175463913: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175463922: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175463939: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175463951: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175463960: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175463970: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175463986: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175463996: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464010: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464021: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464036: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175464046: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464055: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464065: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464081: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175464090: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464099: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464109: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464124: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175464134: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464143: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464152: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464168: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175464178: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464187: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464196: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464212: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175464222: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464237: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464241: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464250: Error (IsoHandler.cpp)[ 646] prepare: Incorrect state, expected E_Initialized, got 4
00175464263: Fatal (IsoHandler.cpp)[ 692] enable: Could not prepare handler
00175464268: Error (StreamProcessor.cpp)[1167] scheduleStartDryRunning: Could not start handler for SP 0x80a7f30
00175464272: Error (StreamProcessorManager.cpp)[ 396] startDryRunning: Could not put SP 0x80a7f30 into the dry-running state
00175464277: Fatal (StreamProcessorManager.cpp)[ 954] handleXrun: Could not syncStartAll...
00175464281: Error (devicemanager.cpp)[ 891] waitForPeriod: Could not handle XRUN
00175464285: Error (ffado.cpp)[ 264] ffado_streaming_wait: Error condition while waiting (Unhandled XRUN)
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
no message buffer overruns


```

AND with QjackCTL and Firewire (FFADO) (lemme unplug and replug my card ;) ):

```

no message buffer overruns
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
00115302828:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Nov 22 2008 23:12:02
00116598068: Debug (bebob_mixer.cpp)[ 126] addElementForAllFunctionBlocks: Adding elements for functionblocks...
firewire MSG: Streaming thread running with Realtime scheduling, priority 69
firewire MSG: Registering audio capture port C0_dev0_Mic/InstIn 1
firewire MSG: Registering audio capture port C1_dev0_Mic/InstIn 2
firewire MSG: Registering audio capture port C2_dev0_LineIn L
firewire MSG: Registering audio capture port C3_dev0_LineIn R
firewire MSG: Registering audio capture port C4_dev0_SPDIFIn L
firewire MSG: Registering audio capture port C5_dev0_SPDIFIn R
firewire MSG: Registering midi capture port C6_dev0_MidiIn 1
firewire MSG: Registering audio playback port P0_dev0_MainOut 1L
firewire MSG: Registering audio playback port P1_dev0_MainOut 2R
firewire MSG: Registering audio playback port P2_dev0_LineOut 3L
firewire MSG: Registering audio playback port P3_dev0_LineOut 4R
firewire MSG: Registering audio playback port P4_dev0_LineOut 5L
firewire MSG: Registering audio playback port P5_dev0_LineOut 6R
firewire MSG: Registering audio playback port P6_dev0_SpdifOut L
firewire MSG: Registering audio playback port P7_dev0_SpdifOut R
firewire MSG: Registering midi playback port P8_dev0_MidiOut 1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
16:15:37.528 Server configuration saved to "/home/tch/.jackdrc".
16:15:37.529 Statistics reset.
16:15:37.759 Client activated.
16:15:37.761 JACK connection change.
16:15:37.764 JACK connection graph change.
16:15:41.036 Shutdown notification.
16:15:41.042 JACK is stopping...
16:15:41.043 JACK is being forced...
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
jack main caught signal 12
cannot read server event (SuccÃ¨s)
cannot complete execution of the processing graph (Ressource temporairement non disponible)
zombified - calling shutdown handler
no message buffer overruns
no message buffer overruns
16:15:41.244 JACK was stopped successfully.
16:15:41.244 Post-shutdown script...
16:15:41.245 killall jackd
jackd: aucun processus tuÃ©
16:15:41.672 Post-shutdown script terminated with exit status=256.

```

Well... when I lauch freebob my system freezes... I won't try too often if you don't mind


I also got a 8.10 version of ubuntu, but without the RT kernel, their's no way to avoid the huge sound cut and xruns... Still on ubuntu 8.10 freebob works perfectly...


I think I gave you all I knew... please tell me if you have any interesting (or boring) infos!

Many thanks

---

### Post by clubsoda on 2009-03-31
Did you see this?
[http://ubuntuforums.org/showthread.php?t=637279](http://ubuntuforums.org/showthread.php?t=637279)

---

