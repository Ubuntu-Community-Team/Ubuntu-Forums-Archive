---
title: "starting JACK with FFADO"
date: 2008-12-11
forum: Ubuntu Studio
---

### Post by ubustu616 on 2008-12-11
I installed FFADO and followed the instructions on [http://subversion.ffado.org/wiki/InstallingFfadoFromSource](http://subversion.ffado.org/wiki/InstallingFfadoFromSource) up to the very last step of starting JACK.

I receive the error: could not find unknown driver 'firewire'

help

---

### Post by barisurum on 2008-12-12
Which soundcard do you have? Are you sure it is supported with ffado?

---

### Post by ubustu616 on 2008-12-12
i have an audiofire 12 echo which should work with ffado. here is my terminal. it wont get the mixers working or the server
```

lokahi@lokahi-studio:~$ ffado-dbus-server &
[1] 6970
lokahi@lokahi-studio:~$ -----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

04160432302:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
04160433571: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
04160439044: Fatal (devicemanager.cpp)[ 161] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?
04160439218: Error (ffado-dbus-server.cpp)[ 276] main: Could not initialize device manager
04160439444: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns
```

---

### Post by barisurum on 2008-12-12
Try:

post your

> lsmod | grep raw1394

> sudo modprobe raw1394

> lsmod | grep raw1394

If it returns raw1394 the second time the module is created. Try to jack again.

---

### Post by ubustu616 on 2008-12-12
that all checked out, but when i try to start jack this is what happens
```

lokahi@lokahi-studio:~$ jackd -d firewire -h
no message buffer overruns
Parameters for driver 'firewire' (all parameters are optional):
	-d, --device 	The FireWire device to use. (default: hw:0)
	-p, --period 	Frames per period (default: 1024)
	-n, --nperiods 	Number of periods of playback latency (default: 3)
	-r, --rate 	Sample rate (default: 48000)
	-i, --capture 	Provide capture ports. (default: 1)
	-o, --playback 	Provide playback ports. (default: 1)
	-I, --input-latency 	Extra input latency (frames) (default: 0)
	-O, --output-latency 	Extra output latency (frames) (default: 0)
	-x, --slave 	Act as a BounceDevice slave (default: 0)
	-X, --slave 	Operate in snoop mode (default: 0)
	-v, --verbose 	Verbose level for the firewire backend (default: 0)
lokahi@lokahi-studio:~$ jackd -R -d firewire -n 3 -p 64
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1057588960, from thread 1057588960] (1: Operation not permitted)
cannot create engine
lokahi@lokahi-studio:~$ jackd -d firewire -d hw:1
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
06218434425:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Dec 11 2008 17:18:11
06218435776: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
```

---

### Post by barisurum on 2008-12-12
Did you select the input output devices accordingly in jack setup? I recommend using qjackctl to do this.


[http://www.ffado.org/?q=node/8](http://www.ffado.org/?q=node/8)

If it doesn't help I recommend ffado docs at this point
because I'm no firewire expert, sorry.

---

### Post by ubustu616 on 2008-12-12
could it be that my firewire card is not supported by linux?

---

### Post by Stochastic on 2008-12-12
> **ubustu616 said:**
> could it be that my firewire card is not supported by linux?

It's perfectly supported (see: [http://ffado.org/?q=node/71](http://ffado.org/?q=node/71) ) it looks now like you have a permissions error.

First, what version of Ubuntu are you running?
Second, open a terminal and do ```
sudo nano /etc/udev/rules.d/40-permissions.rules
```
Find the lines that read something like: ```
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",                      GROUP="audio"
KERNEL=="dv1394*",                      GROUP="audio"
KERNEL=="video1394*",                   GROUP="audio"
```
and double check that all the groups listed to the right are audio.

Then go into System -> Administration -> Users and Groups, click 'unlock' and click 'manage groups'.  In this new window, check to see if there's an audio group.  If not, click 'add group' name it audio, and make sure your user is a member.  If you do already have an audio group, select it, click 'properties' and make sure your user is a member of the group.

After all that, restart your computer just to make sure everything has taken effect.

Does jack run now?

---

### Post by ubustu616 on 2008-12-12
I am running ubuntu 8.10, 

after running

sudo nano /etc/udev/rules.d/40-permissions.rules

i got

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",                      GROUP="audio"
KERNEL=="dv1394*",                      GROUP="audio"
KERNEL=="video1394*",                   GROUP="audio"

and i wasnt a member of audio but added it and restarted my computer. 





when starting up the ffado server this is what i got

lokahi@lokahi-studio:~$ ffado-dbus-server &
-----------------------------------------------
[1] 10222
lokahi@lokahi-studio:~$ FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

40841337764:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
40841339161: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
40841341009: Fatal (devicemanager.cpp)[ 161] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?
40841341201: Error (ffado-dbus-server.cpp)[ 276] main: Could not initialize device manager
40841341459: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns






i tried placing sudo before this command and this is what happened


lokahi@lokahi-studio:~$ sudo  ffado-dbus-server &
[1] 10224
lokahi@lokahi-studio:~$ -----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

40928027152:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
40928032846: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
40928038575: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928059411: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928060651: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928061786: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928062920: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928133045: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928134309: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928135454: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928136604: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928137739: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
40928188329: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
40928188542: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193393286 (0x7F1200001486)
40928188601: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193432850 (0x7F120000AF12)
40928188657: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
40928188725: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
40928188778: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388034 (0x7F1200000002)
40928188832: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
40928188938: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
40928189001: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193393286 (0x7F1200001486)
40928189054: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193432850 (0x7F120000AF12)
40928189107: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
40928189160: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
40928189218: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388034 (0x7F1200000002)
40928189272: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
40928189584: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
40928189716: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
40928189788: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193393286 (0x7F1200001486)
40928189843: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193432850 (0x7F120000AF12)
40928189897: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
40928189950: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
40928190008: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388034 (0x7F1200000002)
40928190061: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
40928191198: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
40928191340: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
40928191642: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
40928191702: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
40928192287: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
40928192366: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
40928192845: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
40928193110: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
40928193167: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
40928193218: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
40928193275: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
40928193325: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
40928193667: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928193742: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
40928194010: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
40928194071: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
40928194357: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928194420: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
40928194690: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
40928194753: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
40928195019: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928195082: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
40928195347: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
40928195600: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928195624: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,1)
40928195831: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
40928196081: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928196105: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,2)
40928196323: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
40928196348: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
40928196606: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928196631: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
40928197763: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
40928198106: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
40928198139: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,1)
40928198377: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
40928198404: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
40928198660: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
40928198706: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
40928198937: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
40928199156: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
40928199186: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
40928199458: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
40928199483: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
40928199502: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
40928199520: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
40928199553: Warning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
40928199573: Warning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
40928199603: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
40928199622: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
40928199649: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
40928199668: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
40928199686: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
40928199705: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
40928199729: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
40928199747: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
40928199765: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
40928199783: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
40928199806: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
40928199824: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
40928199842: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
40928199860: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
40928199882: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
40928199887: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
40928199900: Error (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
40928199906: Error (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
40928199917: Error (devicemanager.cpp)[ 606] discover: could not discover device
40928203527: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
40928203624: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
40928203678: Debug (Element.cpp)[ 121] show: Element DeviceManager
40928203741: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
40928203997:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
40928265046:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
40928265246: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...








i thought maybe this had fixed it but after trying the mixer command i still got:

lokahi@lokahi-studio:~$ ffado-mixer &
[2] 10275
lokahi@lokahi-studio:~$ ERROR:main:
ERROR:main:
ERROR:main:===========================================================
ERROR:main:ERROR: Could not communicate with the FFADO DBus service...
ERROR:main:===========================================================
ERROR:main:
ERROR:main:
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

41037900285:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
41037901579: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
41037901592: Fatal (devicemanager.cpp)[ 161] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?
41037901598: Error (ffado-dbus-server.cpp)[ 276] main: Could not initialize device manager
41037901722: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns
ERROR:main:
ERROR:main:
ERROR:main:===========================================================
ERROR:main:ERROR: Could not communicate with the FFADO DBus service...
ERROR:main:===========================================================
ERROR:main:
ERROR:main:




when trying jack through the terminal this is what happened:

lokahi@lokahi-studio:~$ jackd -h
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry OR -r ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss', `sun', or `portaudio'.

       jackd -d backend --help
             to display options for each backend

lokahi@lokahi-studio:~$ jackd -d firewire -h
no message buffer overruns
Parameters for driver 'firewire' (all parameters are optional):
	-d, --device 	The FireWire device to use. (default: hw:0)
	-p, --period 	Frames per period (default: 1024)
	-n, --nperiods 	Number of periods of playback latency (default: 3)
	-r, --rate 	Sample rate (default: 48000)
	-i, --capture 	Provide capture ports. (default: 1)
	-o, --playback 	Provide playback ports. (default: 1)
	-I, --input-latency 	Extra input latency (frames) (default: 0)
	-O, --output-latency 	Extra output latency (frames) (default: 0)
	-x, --slave 	Act as a BounceDevice slave (default: 0)
	-X, --slave 	Operate in snoop mode (default: 0)
	-v, --verbose 	Verbose level for the firewire backend (default: 0)
lokahi@lokahi-studio:~$ jackd -R -d firewire -n 3 -p 64
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1441442080, from thread -1441442080] (1: Operation not permitted)
cannot create engine
lokahi@lokahi-studio:~$ 



thanks for future help

---

### Post by ubustu616 on 2008-12-12
here's another shot at it

```

lokahi@lokahi-studio:~$ ffado-dbus-server &
[1] 6641
lokahi@lokahi-studio:~$ -----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

00955837190:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
00955879850: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
00955879990: Fatal (devicemanager.cpp)[ 161] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?
00955880069: Error (ffado-dbus-server.cpp)[ 276] main: Could not initialize device manager
00955880267: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns

[1]+  Exit 255                ffado-dbus-server
lokahi@lokahi-studio:~$ ls -l /dev/raw1394
ls: cannot access /dev/raw1394: No such file or directory
lokahi@lokahi-studio:~$ sudo  ls -l /dev/raw1394
[sudo] password for lokahi: 
ls: cannot access /dev/raw1394: No such file or directory
lokahi@lokahi-studio:~$  lsmod | grep 1394
ohci1394               41524  0 
ieee1394              110592  2 sbp2,ohci1394
lokahi@lokahi-studio:~$ cd /root
lokahi@lokahi-studio:/root$  modprobe raw1394
FATAL: Error inserting raw1394 (/lib/modules/2.6.27-9-generic/kernel/drivers/ieee1394/raw1394.ko): Operation not permitted
lokahi@lokahi-studio:/root$ sudo  modprobe raw1394
lokahi@lokahi-studio:/root$ lsmod | grep 1394
raw1394                35208  0 
ohci1394               41524  0 
ieee1394              110592  3 raw1394,sbp2,ohci1394
lokahi@lokahi-studio:/root$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2008-12-12 20:57 /dev/raw1394
lokahi@lokahi-studio:/root$ id
uid=1000(lokahi) gid=1000(lokahi) groups=4(adm),20(dialout),24(cdrom),46(plugdev),100(users),108(lpadmin),123(admin),124(sambashare),1000(lokahi),1001(audio)
lokahi@lokahi-studio:/root$ cd /etc/udev/rules.d
lokahi@lokahi-studio:/etc/udev/rules.d$ grep raw1394 *
40-permissions.rules:# Please note that raw1394 gives unrestricted, raw access to every single
40-permissions.rules:KERNEL=="raw1394",			GROUP="audio"
lokahi@lokahi-studio:/etc/udev/rules.d$ cd /root
lokahi@lokahi-studio:/root$ udevcontrol reload_rules
bash: udevcontrol: command not found
lokahi@lokahi-studio:/root$ sudo udevcontrol reload_rules
sudo: udevcontrol: command not found
lokahi@lokahi-studio:/root$ cd /etc/udev/rules.d
lokahi@lokahi-studio:/etc/udev/rules.d$ udevcontrol reload_rules
bash: udevcontrol: command not found
lokahi@lokahi-studio:/etc/udev/rules.d$ cd /root
lokahi@lokahi-studio:/root$ udevadm control --reload_rules
root privileges required
lokahi@lokahi-studio:/root$ sudo udevadm control --reload_rules
lokahi@lokahi-studio:/root$ ffado-dbus-server &
[1] 6763
lokahi@lokahi-studio:/root$ -----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

01417064425:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
01417067851: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
01417078610: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417079796: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417080949: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417082089: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417083236: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417153745: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417154956: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417156101: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417157235: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417158369: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01417210760: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01417210932: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193393286 (0x7F7600001486)
01417210987: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193432850 (0x7F760000AF12)
01417211039: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
01417211098: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
01417211147: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388034 (0x7F7600000002)
01417211197: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
01417211298: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01417211354: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193393286 (0x7F7600001486)
01417211402: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193432850 (0x7F760000AF12)
01417211452: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
01417211501: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
01417211597: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388034 (0x7F7600000002)
01417211646: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
01417211947: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
01417212097: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01417212156: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193393286 (0x7F7600001486)
01417212214: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193432850 (0x7F760000AF12)
01417212264: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
01417212313: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
01417212367: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388034 (0x7F7600000002)
01417212417: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
01417213496: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
01417213561: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
01417213819: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
01417213869: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
01417214386: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
01417214439: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
01417214880: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
01417215112: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
01417215159: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
01417215205: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
01417215257: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
01417215303: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
01417215607: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417215666: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
01417215913: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
01417215963: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
01417216565: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417216631: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
01417216888: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
01417216940: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
01417217207: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417217258: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
01417217508: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01417217763: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417217781: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,1)
01417217991: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01417218244: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417218261: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,2)
01417218483: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01417218501: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
01417218748: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417218766: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
01417218980: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
01417219204: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01417219226: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,1)
01417219428: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
01417219448: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
01417219685: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
01417219711: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
01417219921: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
01417220114: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
01417220134: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
01417220363: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
01417220380: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
01417220394: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
01417220408: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
01417220432: Warning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
01417220448: Warning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
01417220470: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
01417220484: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
01417220505: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
01417220519: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
01417220533: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
01417220547: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
01417220566: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01417220580: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
01417220594: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01417220608: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
01417220627: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01417220640: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
01417220654: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
01417220668: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
01417220692: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
01417220696: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
01417220708: Error (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
01417220715: Error (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
01417220726: Error (devicemanager.cpp)[ 606] discover: could not discover device
01417220884: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
01417220892: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
01417220898: Debug (Element.cpp)[ 121] show: Element DeviceManager
01417220908: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
01417220974:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
01417234586:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
01417234721: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...

lokahi@lokahi-studio:/root$ ffado-mixer &
[2] 6779
lokahi@lokahi-studio:/root$ DEBUG:dbus:connecting to: Updated on /org/ffado/Control/DeviceManager (server: org.ffado.Control)
lokahi@lokahi-studio:/root$ cd
lokahi@lokahi-studio:~$ ffado-mixer &
[3] 6794
[2]   Done                    ffado-mixer  (wd: /root)
(wd now: ~)
lokahi@lokahi-studio:~$ DEBUG:dbus:connecting to: Updated on /org/ffado/Control/DeviceManager (server: org.ffado.Control)

[3]+  Done                    ffado-mixer
lokahi@lokahi-studio:~$  jackd -h
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry OR -r ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss', `sun', or `portaudio'.

       jackd -d backend --help
             to display options for each backend

lokahi@lokahi-studio:~$ jackd -d firewire -h
no message buffer overruns
Parameters for driver 'firewire' (all parameters are optional):
	-d, --device 	The FireWire device to use. (default: hw:0)
	-p, --period 	Frames per period (default: 1024)
	-n, --nperiods 	Number of periods of playback latency (default: 3)
	-r, --rate 	Sample rate (default: 48000)
	-i, --capture 	Provide capture ports. (default: 1)
	-o, --playback 	Provide playback ports. (default: 1)
	-I, --input-latency 	Extra input latency (frames) (default: 0)
	-O, --output-latency 	Extra output latency (frames) (default: 0)
	-x, --slave 	Act as a BounceDevice slave (default: 0)
	-X, --slave 	Operate in snoop mode (default: 0)
	-v, --verbose 	Verbose level for the firewire backend (default: 0)
lokahi@lokahi-studio:~$ jackd -R -d firewire -n 3 -p 64
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1449522912, from thread 1449522912] (1: Operation not permitted)
cannot create engine
lokahi@lokahi-studio:~$ jackd -d firewire -n 3 -p 2048
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
01614355123:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Dec 11 2008 17:18:11
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
lokahi@lokahi-studio:~$
```

---

### Post by Stochastic on 2008-12-13
Just so you know, the best way to put such extensive console output into the forum is in code blocks (put the word code inside square braces, to start the block, then /code inside square braces will end the block - or use the # icon in the forum editor to insert the code block).

As for your issue, please don't execude ```
jackd -h
``` as this isn't even a valid flag for jack. Do: ```
jackd -d firewire
``` to see if ffado will work.

Also because you seem to be having firewire access issues, you should do ```
sudo apt-get install libraw1394-8 libiec61883-0
``` just to make sure things are installed.

---

### Post by 1467 on 2008-12-19
i got it to work !!!

i made a script to install it for you i hope it works

---

### Post by ubustu616 on 2009-01-04
I am making every effort to get this to work. so much so that i swapped my amd64 with my father's i386. I AM STILL UNSUCCESSFUL!!! It seems like i keep making a step towards success as if it is the last step and i am blind folded without hope (besides this forum.) i have installed ubuntu studio 8.10. i tried installing 8.04 ubuntu studio but the driver for my hard drive could not be found. 

now to the installation. i followed the trac FFADO from [http://subversion.ffado.org/wiki](http://subversion.ffado.org/wiki)

while installing ffado i had to delete the code below and replace it with env['PYUIC'] = True. (this is from an installation tutorial.)

```

# PyQT checks
if conf.CheckForApp( "which pyuic" ) and conf.CheckForPyModule( 'dbus' ) and conf.CheckForPyModule( 'qt' ):
env['PYUIC'] = True

if conf.CheckForApp( "xdg-desktop-menu --help" ):
env['XDG_TOOLS'] = True
else:
print """
I couldn't find the program 'xdg-desktop-menu'. Together with xdg-icon-resource
this is needed to add the fancy entry to your menu. But the mixer will be installed, you can start it by executing "ffadomixer".
"""

else:
print """
I couldn't find all the prerequisites ('pyuic' and the python-modules 'dbus' and
'qt', the packages could be named like dbus-python and PyQt) to build the mixer.
Therefor the mixer won't get installed.
"""
```


installing jack seemed easy and correct but after trying to start the ffado dbus and mixer i got errors. it also does not recognize driver firewire.

```

bowditch@bowditch:~/.jack/jack$ lsmod | grep 1394
raw1394                32348  0 
ohci1394               37936  0 
ieee1394               96324  3 raw1394,sbp2,ohci1394
bowditch@bowditch:~/.jack/jack$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2009-01-04 16:22 /dev/raw1394
bowditch@bowditch:~/.jack/jack$ id
uid=1000(bowditch) gid=1000(bowditch) groups=4(adm),20(dialout),24(cdrom),46(plugdev),110(lpadmin),119(admin),124(sambashare),1000(bowditch),1001(audio)
bowditch@bowditch:~/.jack/jack$ cd /etc/udev/rules.d
bowditch@bowditch:/etc/udev/rules.d$ grep raw1394 *  
40-permissions.rules:# Please note that raw1394 gives unrestricted, raw access to every single
40-permissions.rules:KERNEL=="raw1394",			GROUP="audio"
bowditch@bowditch:/etc/udev/rules.d$ sudo udevadm control --reload_rules
bowditch@bowditch:/etc/udev/rules.d$ ffado-dbus-server &
[1] 23544
bowditch@bowditch:/etc/udev/rules.d$ -----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

04014661194:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
04014664827: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
04014670530: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014671661: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014672804: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014673938: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014675057: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014725579: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014726723: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014727845: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014728976: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014730119: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
04014785783: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
04014785880: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
04014785910: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
04014785939: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
04014785976: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
04014786000: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
04014786024: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
04014786110: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
04014786141: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
04014786167: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
04014786192: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
04014786216: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
04014786246: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
04014786270: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
04014786642: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
04014786738: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
04014786769: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
04014786793: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
04014786817: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
04014786841: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
04014786871: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
04014786895: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
04014788082: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
04014788112: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
04014788372: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
04014788397: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
04014788946: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
04014788977: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
04014789488: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
04014789723: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
04014789754: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
04014789780: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
04014789817: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
04014789843: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
04014790183: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014790223: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
04014790483: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
04014790523: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
04014790807: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014790848: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
04014791110: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
04014791145: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
04014791426: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014791461: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
04014791719: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
04014792009: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014792050: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,1)
04014792292: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
04014792578: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014792605: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,2)
04014792856: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
04014792883: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
04014793174: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014793201: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
04014793429: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
04014793686: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
04014793719: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,1)
04014793966: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
04014793994: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
04014794246: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
04014794281: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
04014794522: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
04014794753: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
04014794780: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
04014795040: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
04014795065: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
04014795086: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
04014795108: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
04014795140: Warning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
04014795164: Warning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
04014795194: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
04014795216: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
04014795245: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
04014795266: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
04014795287: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
04014795307: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
04014795335: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
04014795356: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
04014795377: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
04014795398: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
04014795425: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
04014795446: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
04014795468: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
04014795489: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
04014795515: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
04014795536: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
04014795563: Error (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
04014795585: Error (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
04014795610: Error (devicemanager.cpp)[ 606] discover: could not discover device
04014795756: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
04014795767: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
04014795775: Debug (Element.cpp)[ 121] show: Element DeviceManager
04014795787: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
04014795847:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
04014801943:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
04014801964: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
ffado-mixer &
[2] 23556
bowditch@bowditch:/etc/udev/rules.d$ bash: ffado-mixer: command not found
jackd -h
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss' or `portaudio'.

       jackd -d backend --help
             to display options for each backend

[2]+  Exit 127                ffado-mixer
bowditch@bowditch:/etc/udev/rules.d$ jackd -d firewire -h
jackd: unknown driver 'firewire'
bowditch@bowditch:/etc/udev/rules.d$ jackd -R -d firewire -n 3 -p 64
jackd: unknown driver 'firewire'
bowditch@bowditch:/etc/udev/rules.d$ sudo apt-get install autoconf]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package autoconf]
bowditch@bowditch:/etc/udev/rules.d$ sudo apt-get install autoconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
autoconf set to manually installed.
The following packages were automatically installed and are no longer required:
  python-qt4-dbus
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bowditch@bowditch:/etc/udev/rules.d$ cp /usr/bin/aclocal-1.10 /usr/bin/aclocal
cp: `/usr/bin/aclocal-1.10' and `/usr/bin/aclocal' are the same file
bowditch@bowditch:/etc/udev/rules.d$ 

```

please help, as this might be my last attempt for ubuntu

---

### Post by Stochastic on 2009-01-05
I don't know why you're still running ```
jackd -h
``` after I've explained that it's not a valid jack flag, but in various places it look like you're running into a permissions error while attempting to access the firewire device.  Your permissions file does look like it's in shape with "audio" as the proper group.  But I've found that many 8.10 installs don't have an audio group by default, and so you must add one before it's recognized:
- Go to System -> Administration -> Users & Groups
- Click Unlock (and enter password accordingly)
- Click 'Manage Groups'
- in that list of groups, do you see 'audio'?
         - if yes: select that group, click properties, and make sure your name has a check mark beside it (i.e. is part of that group).
         - if no: click 'add group', name it audio, and make sure your name is checked in the list of members of that group.


Also, in further posts, PLEASE post one command's output at a time (i.e. encapsulate each command's output in a code block), that will greatly help others to read your errors.


Edit: Nevermind about the groups check, it looks like I missed your id command that lists your groups.  It also looks (upon further reading of your most recent output) that you are still running jackd 0.109.2 and that you haven't compiled the latest jack version (with ffado support).  You also didn't install the ffado-mixer (a trivial accessory for many).  Try compiling jack again and post the output.  You may just want to wait until Jaunty is released; I'm **guessing** FFADO will be incorporated by then and then it should be a very simple setup process.

---

### Post by jukingeo on 2009-01-05
I been away from the Ubuntu forums for a while since I got my M-Audio Delta 44 to work in Linux, but overall I was hoping that eventually FFADO support would improve because I would like to try out the Focusrite Saffire LE.  However, I am surprised that almost 6 months later, that devices listed under the FFADO "SUPPORTED" lists are still causing problems for users.

I can understand that some devices that are listed as "reported to work" and lower on the scale may be a while to get operational, but I am dismayed to see that there is so much hassle to set up a "supported" device.

I ran into this same issue with sound cards that were supported under "ALSA".  I bought an  Echo Mona sound card BECAUSE it was on this list and it was supported.  However, after I had bought the device, I had nothing but nightmares in trying to get it to run. EVEN the Alsa developer who created the driver couldn't help me.  In the end, he stopped answering my emails.

All in all, that isn't good at all.

So far when it comes to Linux the only (repeated) success stories I have seen for Linux are:

*Sound Blaster Live (original OLD version and not DEll OEM. The older the better)
*SoundMAX on board sound
*Hammerfall RME
*M-Audio Delta Series

These options were tested on various machines and are pretty much plug-n-play for most Linux applications.

I am still hoping for Firewire support to improve in the future, but it looks to be very slow going.

In any regard, ubustu616, I do wish you luck in getting your sound device to work.  I will follow along because I am interested in hearing your results.

I will say one thing for Echo products.  They ARE very much pro and the Echo Mona I had for a short time worked beautiful in Windows.  It was built like a tank and had excellent A/D converters.  It was clearly the best sounding card I had (outside of my Alesis IO/26), and I was very much upset that I couldn't get it to run in Linux.  BTW, the Echo Mona was a PCI carded device and not firewire.

Geo

---

### Post by ubustu616 on 2009-01-05
thank you stochastic for you very quick reply. i really appreciate it.
here is my attempt to compile jack.

```

bowditch@bowditch:~$ cd /usr
bowditch@bowditch:/usr$ sudo svn co http://subversion.jackaudio.org/jack/trunk/jack jack
Checked out revision 3234.
bowditch@bowditch:/usr$ jackd --version
jackd version 0.109.2 tmpdir /dev/shm protocol 22
```
```
bowditch@bowditch:/usr$ cd jack
bowditch@bowditch:/usr/jack$ sudo ./autogen.sh
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: linking file `config/ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:7: installing `config/config.guess'
configure.ac:7: installing `config/config.sub'
bowditch@bowditch:/usr/jack$ sudo ./configure --prefix=/dev/shm
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking whether gcc and cc understand -c and -o together... yes
checking whether byte ordering is bigendian... no
checking platform dependencies... checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking /usr/include/nptl/pthread.h usability... no
checking /usr/include/nptl/pthread.h presence... no
checking for /usr/include/nptl/pthread.h... no
checking for getopt_long... yes
checking for gethostent... yes
checking for setsockopt... yes
checking for connect... yes
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for pthread_create... no
checking for pthread_create in -lpthread... yes
checking for on_exit... yes
checking for atexit... yes
checking for posix_memalign... yes
checking for sin in -lm... yes
Checking for ppoll()... yes
checking for clock_gettime... no
checking for clock_gettime in -lrt... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mlockall... yes
checking shared memory support... System V shmget().
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
checking whether we can compile MMX code... yes
yes
checking whether we can compile SSE code... yes
configure: WARNING: no optimization.........................
checking for pthread_barrier_init in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... no
configure: WARNING: *** the jackrec example client will not be built
checking for SAMPLERATE... no
configure: WARNING: *** the NetJack backend and internal client will not be built
checking for CELT... no
no
configure: WARNING: *** NetJack will not be built with celt support
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking for LIBFREEBOB... no
no
checking for LIBFFADO... yes
checking for ALSA... no
no
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking readline/chardefs.h usability... no
checking readline/chardefs.h presence... no
checking for readline/chardefs.h... no
configure: WARNING: *** the jack_transport example client will not be built
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config/Makefile
config.status: creating config/cpu/Makefile
config.status: creating config/cpu/alpha/Makefile
config.status: creating config/cpu/cris/Makefile
config.status: creating config/cpu/generic/Makefile
config.status: creating config/cpu/i386/Makefile
config.status: creating config/cpu/i486/Makefile
config.status: creating config/cpu/ia64/Makefile
config.status: creating config/cpu/m68k/Makefile
config.status: creating config/cpu/mips/Makefile
config.status: creating config/cpu/powerpc/Makefile
config.status: creating config/cpu/s390/Makefile
config.status: creating config/os/Makefile
config.status: creating config/os/generic/Makefile
config.status: creating config/os/gnu-linux/Makefile
config.status: creating config/os/macosx/Makefile
config.status: creating config/sysdeps/Makefile
config.status: creating doc/Makefile
config.status: creating doc/reference.doxygen
config.status: creating drivers/Makefile
config.status: creating drivers/alsa/Makefile
config.status: creating drivers/alsa-midi/Makefile
config.status: creating drivers/dummy/Makefile
config.status: creating drivers/oss/Makefile
config.status: creating drivers/sun/Makefile
config.status: creating drivers/portaudio/Makefile
config.status: creating drivers/coreaudio/Makefile
config.status: creating drivers/freebob/Makefile
config.status: creating drivers/firewire/Makefile
config.status: creating drivers/netjack/Makefile
config.status: creating example-clients/Makefile
config.status: creating tools/Makefile
config.status: creating man/Makefile
config.status: creating jack.pc
config.status: creating jack.spec
config.status: creating jack/Makefile
config.status: creating jack/version.h
config.status: creating jackd/Makefile
config.status: creating jackd/jackd.1
config.status: creating libjack/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

jack-audio-connection-kit 0.116.1 :

| Build with ALSA support............................... : false
| Build with old FireWire (FreeBob) support............. : false
| Build with new FireWire (FFADO) support............... : true
| Build with OSS support................................ : true
| Build with Sun audio support.......................... : false
| Build with CoreAudio support.......................... : false
| Build with PortAudio support.......................... : false
| Build with NetJack support............................ : false
| Build with Celt support............................... : false
| Build with dynamic buffer size support................ : yes
| Compiler optimization flags........................... : -g
| Compiler full flags................................... : -I$(top_srcdir)/config -I$(top_srcdir) -I$(top_srcdir) -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g
| Install dir for libjack + backends.................... : ${exec_prefix}/lib/jack
|
| Default driver backend................................ : "firewire"
| Shared memory interface............................... : "System V"
| IPC Temporary directory............................... : /dev/shm
| Install prefix........................................ : /dev/shm
| Default tmp dir....................................... : /dev/shm

```

and the outcome

```
bowditch@bowditch:/usr/jack$ jackd --version
jackd version 0.109.2 tmpdir /dev/shm protocol 22
```
 
how do i install the ffado mixer?

---

### Post by Stochastic on 2009-01-06
Ok, well you've only configured the building of Jack, you have yet to build jack.  After ```
./configure --prefix=/dev/shm
``` (which doesn't need sudo) you still need to do ```
make
``` then ```
sudo make install
```

But I should give you a head's up - this will (according to your configure output) build Jack with no ALSA support among other things.  That's fine if you don't need those features, but just make sure you don't.

Please post the output of those two commands.

---

### Post by babarosa on 2009-01-06
Hi ubustu616,

I feel sorry you still struggle with that topic
[http://ubuntuforums.org/showthread.php?t=1010065&highlight=ffado](http://ubuntuforums.org/showthread.php?t=1010065&highlight=ffado)

Additionally to stochastic's competent advices let's try the following (I know some of the tipps already were mentioned):
I also had to deal with some tinkering and these are my experiences which helped me to get it to work very stable and fine now:
"... Could not get libraw1394 handle" That message in your second post shows **you are near to success** so let us start here again.

[LIST][*]Which ubuntu version do you use? Do you know you can use repo versions from [www.ffado.org](www.ffado.org) for gutsy/hardy and 64studio?
[*] If you compile, you have to compile **ffado first** (!) and then jack. Compiling with alsa-support is essentiell!
[*] Plug in your firewire interface and check if in /dev the folder dv1394 and the file raw1394 exist.
[*] Generate with sudo nautilus in **/etc/udev/rules.d** the following file:
you can take any file and replace the entire contents with: 
[B]KERNEL="raw1394", NAME="%k"
KERNEL="dv1394*", NAME="dv1394/%n" 
KERNEL="video1394*", NAME="video1394/%n"[/B]
and then save it as **40-linux1394.rules**
[*] Not only add and give rights to "audio"-group, but also to "plugdev", "disk" and "video"-group and your own group (e.g. I am "babarosa" and I have to check this group also!) This tipp solved my problems, actually it is not only audio-group you have to give rights to!
[http://www.servimg.com/image_preview.php?i=11&u=12842335](http://www.servimg.com/image_preview.php?i=11&u=12842335)
[http://www.servimg.com/image_preview.php?i=12&u=12842335](http://www.servimg.com/image_preview.php?i=12&u=12842335)
[http://www.servimg.com/image_preview.php?i=13&u=12842335](http://www.servimg.com/image_preview.php?i=13&u=12842335)
[*] plug in your interface and type "sudo ldconfig"
[*] type "ffado-mixer" into the console
[/LIST]

Please take my notices as a help for orientation and checking if anything is missing, sadly versions are changing rapidly (I am using Xubuntu 8.04.1):

```

**_ffado_**
sudo apt-get install subversion
sudo apt-get install build-essential
sudo apt-get install scons
sudo apt-get install libiec61883-0
sudo apt-get install libiec61883-dev
sudo apt-get install libavc1394-0
sudo apt-get install libavc1394-dev
sudo apt-get install libxml++2.6c2a
sudo apt-get install libxml++2.6-dev
sudo apt-get install liblo0
sudo apt-get install liblo0-dev
sudo apt-get install docbook-utils
sudo apt-get install libexpat-dev
sudo apt-get install libdbus-1-dev
sudo apt-get install pyqt-tools (ist für qt3)
sudo apt-get install python-dbus
sudo apt-get install python-qt3
sudo apt-get install libraw1394-8
sudo apt-get install libraw1394-dev
sudo apt-get install dbus
sudo apt-get install dbus-x11
sudo apt-get install qt4-designer (für QJackCtl)
sudo apt-get install qt4-dev-tools (für QjackCtl)
sudo apt-get install qt4-qtconfig (für QjackCtl)
sudo apt-get install qt3-designer
sudo apt-get install qt3-dev-tools
(sudo apt-get install sip4)
sudo apt-get install pyqt4-dev-tools
sudo apt-get install python-dbus
sudo apt-get install polymer (using this style qt-applications look very nice)

dir
cd libffado-2.0-beta6
scons
(scons ENABLE_OPTIMIZATIONS=True DEBUG=False)
sudo scons install

_**jack**_
sudo apt-get install libtool automake libalsa-ocaml-dev libasound2 libasound2-dev

cd jack
svn co http://subversion.jackaudio.org/jack/trunk/jack jack
cd jack
./autogen.sh --prefix=/usr
make
sudo make install

**_QJackCtl_**
Download the qjackctl package from "http://qjackctl.sourceforge.net/" and unpack it

cd qjackctl-0.3.3
./configure
make
sudo make install


```

I want to tell you I also struggled quite some time and was frustrated (documentation was outdated combined with ignorance when I offered a "how-to"). The other side is that you learn important features, gather experience and will have a lot of fun soon. Keep patience ):P

Regards, Michael

---

### Post by ubustu616 on 2009-01-06
make

```
bowditch@bowditch:/usr/jack$ make
make  all-recursive
make[1]: Entering directory `/usr/jack'
Making all in jack
make[2]: Entering directory `/usr/jack/jack'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/jack/jack'
Making all in libjack
make[2]: Entering directory `/usr/jack/libjack'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/jack/libjack'
Making all in jackd
make[2]: Entering directory `/usr/jack/jackd'
make  all-am
make[3]: Entering directory `/usr/jack/jackd'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/jack/jackd'
make[2]: Leaving directory `/usr/jack/jackd'
Making all in drivers
make[2]: Entering directory `/usr/jack/drivers'
Making all in dummy
make[3]: Entering directory `/usr/jack/drivers/dummy'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/jack/drivers/dummy'
Making all in oss
make[3]: Entering directory `/usr/jack/drivers/oss'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/jack/drivers/oss'
Making all in firewire
make[3]: Entering directory `/usr/jack/drivers/firewire'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/jack/drivers/firewire'
Making all in netjack
make[3]: Entering directory `/usr/jack/drivers/netjack'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/jack/drivers/netjack'
make[3]: Entering directory `/usr/jack/drivers'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/jack/drivers'
make[2]: Leaving directory `/usr/jack/drivers'
Making all in example-clients
make[2]: Entering directory `/usr/jack/example-clients'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/jack/example-clients'
Making all in tools
make[2]: Entering directory `/usr/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/jack/tools'
Making all in config
make[2]: Entering directory `/usr/jack/config'
make[3]: Entering directory `/usr/jack/config'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/jack/config'
make[2]: Leaving directory `/usr/jack/config'
Making all in man
make[2]: Entering directory `/usr/jack/man'
make  all-am
make[3]: Entering directory `/usr/jack/man'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/jack/man'
make[2]: Leaving directory `/usr/jack/man'
make[2]: Entering directory `/usr/jack'
make[2]: Leaving directory `/usr/jack'
make[1]: Leaving directory `/usr/jack'
bowditch@bowditch:/usr/jack$ 
```

sudo make install

```
bowditch@bowditch:/usr/jack$ sudo make install
Making install in jack
make[1]: Entering directory `/usr/jack/jack'
make[2]: Entering directory `/usr/jack/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/include/jack" || /bin/mkdir -p "/dev/shm/include/jack"
 /usr/bin/install -c -m 644 'intclient.h' '/dev/shm/include/jack/intclient.h'
 /usr/bin/install -c -m 644 'jack.h' '/dev/shm/include/jack/jack.h'
 /usr/bin/install -c -m 644 'ringbuffer.h' '/dev/shm/include/jack/ringbuffer.h'
 /usr/bin/install -c -m 644 'statistics.h' '/dev/shm/include/jack/statistics.h'
 /usr/bin/install -c -m 644 'thread.h' '/dev/shm/include/jack/thread.h'
 /usr/bin/install -c -m 644 'timestamps.h' '/dev/shm/include/jack/timestamps.h'
 /usr/bin/install -c -m 644 'transport.h' '/dev/shm/include/jack/transport.h'
 /usr/bin/install -c -m 644 'types.h' '/dev/shm/include/jack/types.h'
 /usr/bin/install -c -m 644 'midiport.h' '/dev/shm/include/jack/midiport.h'
make[2]: Leaving directory `/usr/jack/jack'
make[1]: Leaving directory `/usr/jack/jack'
Making install in libjack
make[1]: Entering directory `/usr/jack/libjack'
make[2]: Entering directory `/usr/jack/libjack'
test -z "/dev/shm/lib" || /bin/mkdir -p "/dev/shm/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjack.la' '/dev/shm/lib/libjack.la'
libtool: install: /usr/bin/install -c .libs/libjack.so.0.0.28 /dev/shm/lib/libjack.so.0.0.28
libtool: install: (cd /dev/shm/lib && { ln -s -f libjack.so.0.0.28 libjack.so.0 || { rm -f libjack.so.0 && ln -s libjack.so.0.0.28 libjack.so.0; }; })
libtool: install: (cd /dev/shm/lib && { ln -s -f libjack.so.0.0.28 libjack.so || { rm -f libjack.so && ln -s libjack.so.0.0.28 libjack.so; }; })
libtool: install: /usr/bin/install -c .libs/libjack.lai /dev/shm/lib/libjack.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-exec-hook
make[3]: Entering directory `/usr/jack/libjack'
Removing JACK shared memory registry key  0x282929
ipcrm -M 0x282929
ipcrm: invalid key (0x282929)
make[3]: [install-exec-hook] Error 1 (ignored)
make[3]: Leaving directory `/usr/jack/libjack'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/jack/libjack'
make[1]: Leaving directory `/usr/jack/libjack'
Making install in jackd
make[1]: Entering directory `/usr/jack/jackd'
make  install-am
make[2]: Entering directory `/usr/jack/jackd'
make[3]: Entering directory `/usr/jack/jackd'
test -z "/dev/shm/lib" || /bin/mkdir -p "/dev/shm/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjackserver.la' '/dev/shm/lib/libjackserver.la'
libtool: install: /usr/bin/install -c .libs/libjackserver.so.0.0.28 /dev/shm/lib/libjackserver.so.0.0.28
libtool: install: (cd /dev/shm/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so.0 || { rm -f libjackserver.so.0 && ln -s libjackserver.so.0.0.28 libjackserver.so.0; }; })
libtool: install: (cd /dev/shm/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so || { rm -f libjackserver.so && ln -s libjackserver.so.0.0.28 libjackserver.so; }; })
libtool: install: /usr/bin/install -c .libs/libjackserver.lai /dev/shm/lib/libjackserver.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/dev/shm/bin" || /bin/mkdir -p "/dev/shm/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jackd' '/dev/shm/bin/jackd'
libtool: install: /usr/bin/install -c .libs/jackd /dev/shm/bin/jackd
make  install-exec-hook
make[4]: Entering directory `/usr/jack/jackd'
Nothing to make for install-exec-hook.
make[4]: Leaving directory `/usr/jack/jackd'
test -z "/dev/shm/share/man/man1" || /bin/mkdir -p "/dev/shm/share/man/man1"
 /usr/bin/install -c -m 644 './jackd.1' '/dev/shm/share/man/man1/jackd.1'
 /usr/bin/install -c -m 644 './jackstart.1' '/dev/shm/share/man/man1/jackstart.1'
make[3]: Leaving directory `/usr/jack/jackd'
make[2]: Leaving directory `/usr/jack/jackd'
make[1]: Leaving directory `/usr/jack/jackd'
Making install in drivers
make[1]: Entering directory `/usr/jack/drivers'
Making install in dummy
make[2]: Entering directory `/usr/jack/drivers/dummy'
make[3]: Entering directory `/usr/jack/drivers/dummy'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/lib/jack" || /bin/mkdir -p "/dev/shm/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_dummy.la' '/dev/shm/lib/jack/jack_dummy.la'
libtool: install: /usr/bin/install -c .libs/jack_dummy.so /dev/shm/lib/jack/jack_dummy.so
libtool: install: /usr/bin/install -c .libs/jack_dummy.lai /dev/shm/lib/jack/jack_dummy.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/usr/jack/drivers/dummy'
make[2]: Leaving directory `/usr/jack/drivers/dummy'
Making install in oss
make[2]: Entering directory `/usr/jack/drivers/oss'
make[3]: Entering directory `/usr/jack/drivers/oss'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/lib/jack" || /bin/mkdir -p "/dev/shm/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_oss.la' '/dev/shm/lib/jack/jack_oss.la'
libtool: install: /usr/bin/install -c .libs/jack_oss.so /dev/shm/lib/jack/jack_oss.so
libtool: install: /usr/bin/install -c .libs/jack_oss.lai /dev/shm/lib/jack/jack_oss.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/usr/jack/drivers/oss'
make[2]: Leaving directory `/usr/jack/drivers/oss'
Making install in firewire
make[2]: Entering directory `/usr/jack/drivers/firewire'
make[3]: Entering directory `/usr/jack/drivers/firewire'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/lib/jack" || /bin/mkdir -p "/dev/shm/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_firewire.la' '/dev/shm/lib/jack/jack_firewire.la'
libtool: install: /usr/bin/install -c .libs/jack_firewire.so /dev/shm/lib/jack/jack_firewire.so
libtool: install: /usr/bin/install -c .libs/jack_firewire.lai /dev/shm/lib/jack/jack_firewire.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/usr/jack/drivers/firewire'
make[2]: Leaving directory `/usr/jack/drivers/firewire'
Making install in netjack
make[2]: Entering directory `/usr/jack/drivers/netjack'
make[3]: Entering directory `/usr/jack/drivers/netjack'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/lib/jack" || /bin/mkdir -p "/dev/shm/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_net.la' '/dev/shm/lib/jack/jack_net.la'
libtool: install: /usr/bin/install -c .libs/jack_net.so /dev/shm/lib/jack/jack_net.so
libtool: install: /usr/bin/install -c .libs/jack_net.lai /dev/shm/lib/jack/jack_net.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/usr/jack/drivers/netjack'
make[2]: Leaving directory `/usr/jack/drivers/netjack'
make[2]: Entering directory `/usr/jack/drivers'
make[3]: Entering directory `/usr/jack/drivers'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/jack/drivers'
make[2]: Leaving directory `/usr/jack/drivers'
make[1]: Leaving directory `/usr/jack/drivers'
Making install in example-clients
make[1]: Entering directory `/usr/jack/example-clients'
make[2]: Entering directory `/usr/jack/example-clients'
test -z "/dev/shm/bin" || /bin/mkdir -p "/dev/shm/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_simple_client' '/dev/shm/bin/jack_simple_client'
libtool: install: /usr/bin/install -c .libs/jack_simple_client /dev/shm/bin/jack_simple_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_transport_client' '/dev/shm/bin/jack_transport_client'
libtool: install: /usr/bin/install -c .libs/jack_transport_client /dev/shm/bin/jack_transport_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_impulse_grabber' '/dev/shm/bin/jack_impulse_grabber'
libtool: install: /usr/bin/install -c .libs/jack_impulse_grabber /dev/shm/bin/jack_impulse_grabber
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_metro' '/dev/shm/bin/jack_metro'
libtool: install: /usr/bin/install -c .libs/jack_metro /dev/shm/bin/jack_metro
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_showtime' '/dev/shm/bin/jack_showtime'
libtool: install: /usr/bin/install -c .libs/jack_showtime /dev/shm/bin/jack_showtime
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midisine' '/dev/shm/bin/jack_midisine'
libtool: install: /usr/bin/install -c .libs/jack_midisine /dev/shm/bin/jack_midisine
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midiseq' '/dev/shm/bin/jack_midiseq'
libtool: install: /usr/bin/install -c .libs/jack_midiseq /dev/shm/bin/jack_midiseq
test -z "/dev/shm/lib/jack" || /bin/mkdir -p "/dev/shm/lib/jack"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'inprocess.la' '/dev/shm/lib/jack/inprocess.la'
libtool: install: /usr/bin/install -c .libs/inprocess.so /dev/shm/lib/jack/inprocess.so
libtool: install: /usr/bin/install -c .libs/inprocess.lai /dev/shm/lib/jack/inprocess.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'intime.la' '/dev/shm/lib/jack/intime.la'
libtool: install: /usr/bin/install -c .libs/intime.so /dev/shm/lib/jack/intime.so
libtool: install: /usr/bin/install -c .libs/intime.lai /dev/shm/lib/jack/intime.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /dev/shm/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /dev/shm/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/usr/jack/example-clients'
make[1]: Leaving directory `/usr/jack/example-clients'
Making install in tools
make[1]: Entering directory `/usr/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
make[2]: Entering directory `/usr/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
test -z "/dev/shm/bin" || /bin/mkdir -p "/dev/shm/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_load' '/dev/shm/bin/jack_load'
libtool: install: /usr/bin/install -c .libs/jack_load /dev/shm/bin/jack_load
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_unload' '/dev/shm/bin/jack_unload'
libtool: install: /usr/bin/install -c .libs/jack_unload /dev/shm/bin/jack_unload
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_monitor_client' '/dev/shm/bin/jack_monitor_client'
libtool: install: /usr/bin/install -c .libs/jack_monitor_client /dev/shm/bin/jack_monitor_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_connect' '/dev/shm/bin/jack_connect'
libtool: install: /usr/bin/install -c .libs/jack_connect /dev/shm/bin/jack_connect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_disconnect' '/dev/shm/bin/jack_disconnect'
libtool: install: /usr/bin/install -c .libs/jack_disconnect /dev/shm/bin/jack_disconnect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_lsp' '/dev/shm/bin/jack_lsp'
libtool: install: /usr/bin/install -c .libs/jack_lsp /dev/shm/bin/jack_lsp
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_freewheel' '/dev/shm/bin/jack_freewheel'
libtool: install: /usr/bin/install -c .libs/jack_freewheel /dev/shm/bin/jack_freewheel
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_evmon' '/dev/shm/bin/jack_evmon'
libtool: install: /usr/bin/install -c .libs/jack_evmon /dev/shm/bin/jack_evmon
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_alias' '/dev/shm/bin/jack_alias'
libtool: install: /usr/bin/install -c .libs/jack_alias /dev/shm/bin/jack_alias
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/jack/tools'
make[1]: Leaving directory `/usr/jack/tools'
Making install in config
make[1]: Entering directory `/usr/jack/config'
make[2]: Entering directory `/usr/jack/config'
make[3]: Entering directory `/usr/jack/config'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/jack/config'
make[2]: Leaving directory `/usr/jack/config'
make[1]: Leaving directory `/usr/jack/config'
Making install in man
make[1]: Entering directory `/usr/jack/man'
make  install-am
make[2]: Entering directory `/usr/jack/man'
make[3]: Entering directory `/usr/jack/man'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/share/man/man1" || /bin/mkdir -p "/dev/shm/share/man/man1"
 /usr/bin/install -c -m 644 './alsa_in.1' '/dev/shm/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/dev/shm/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/dev/shm/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/dev/shm/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/dev/shm/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/dev/shm/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/dev/shm/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/dev/shm/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/dev/shm/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/dev/shm/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/dev/shm/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/dev/shm/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/dev/shm/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/dev/shm/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/dev/shm/share/man/man1/jack_unload.1'
 /usr/bin/install -c -m 644 './alsa_in.1' '/dev/shm/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/dev/shm/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/dev/shm/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/dev/shm/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/dev/shm/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/dev/shm/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/dev/shm/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/dev/shm/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/dev/shm/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/dev/shm/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/dev/shm/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/dev/shm/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/dev/shm/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/dev/shm/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/dev/shm/share/man/man1/jack_unload.1'
make[3]: Leaving directory `/usr/jack/man'
make[2]: Leaving directory `/usr/jack/man'
make[1]: Leaving directory `/usr/jack/man'
make[1]: Entering directory `/usr/jack'
make[2]: Entering directory `/usr/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/dev/shm/lib/pkgconfig" || /bin/mkdir -p "/dev/shm/lib/pkgconfig"
 /usr/bin/install -c -m 644 'jack.pc' '/dev/shm/lib/pkgconfig/jack.pc'
make[2]: Leaving directory `/usr/jack'
make[1]: Leaving directory `/usr/jack'
bowditch@bowditch:/usr/jack$ 

```

outcome

```
bowditch@bowditch:/usr/jack$ jackd --version
jackd version 0.109.2 tmpdir /dev/shm protocol 22
bowditch@bowditch:/usr/jack$ 

```

---

### Post by Stochastic on 2009-01-06
it looks like you need to execute ```
make clean
``` before doing ```
make
sudo make install
```
that will erase any previous botched make attempts and give us a fresh slate to work off of.

please post the output of make and make install after you've done make clean

---

### Post by ubustu616 on 2009-01-06
thanks barbosa for the encouragement. 

here is me trying to compile qjackctl 0.3.4



```
bowditch@bowditch:/usr/jack/jackd/qjackctl-0.3.4$ ./configure
./configure: 53: cannot create conf20834.sh: Permission denied
./configure: 53: cannot create conf20834.sh: Permission denied
chmod: cannot access `conf20834.sh': No such file or directory
./configure: line 44: conf20834.sh: Permission denied
./configure: line 45: conf20834.sh: Permission denied
chmod: cannot access `conf20834.sh': No such file or directory
mkdir: cannot create directory `conf20834.dir': Permission denied
./configure: line 499: conf20834.file: Permission denied
./configure: line 1364: config.log: Permission denied
./configure: line 1374: config.log: Permission denied
bowditch@bowditch:/usr/jack/jackd/qjackctl-0.3.4$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for Qt library version >= 4.1... yes
checking for qmake... /usr/share/qt4/bin/qmake
checking for moc... /usr/share/qt4/bin/moc
checking for uic... /usr/share/qt4/bin/uic
checking for lupdate... /usr/share/qt4/bin/lupdate
checking for lrelease... /usr/share/qt4/bin/lrelease
checking for main in -lm... yes
checking for main in -lX11... yes
checking for main in -lXext... yes
checking for lroundf in -lm... yes
checking for main in -ljack... yes
checking for main in -lasound... yes
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking jack/jack.h usability... yes
checking jack/jack.h presence... yes
checking for jack/jack.h... yes
checking jack/statistics.h usability... yes
checking jack/statistics.h presence... yes
checking for jack/statistics.h... yes
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking jack/midiport.h usability... yes
checking jack/midiport.h presence... yes
checking for jack/midiport.h... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for system... yes
checking for jack_transport_query in -ljack... yes
checking for jack_is_realtime in -ljack... yes
checking for jack_get_xrun_delayed_usecs in -ljack... yes
checking for jack_get_max_delayed_usecs in -ljack... yes
checking for jack_midi_event_get in -ljack... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating qjackctl.pro
config.status: creating qjackctl.spec
config.status: creating qjackctl.desktop
config.status: creating config.h

  QjackCtl 0.3.4

  Build target . . . . . . . . . . . . . . . . . . .: release

  JACK Audio Connection Kit support  . . . . . . . .: yes
  JACK Realtime support  . . . . . . . . . . . . . .: yes
  JACK Transport support . . . . . . . . . . . . . .: yes
  JACK XRUN delay support  . . . . . . . . . . . . .: yes
  JACK Maximum scheduling delay support  . . . . . .: yes
  JACK MIDI support  . . . . . . . . . . . . . . . .: yes
  ALSA MIDI Sequencer support  . . . . . . . . . . .: yes
  System tray icon support . . . . . . . . . . . . .: yes

  Install prefix . . . . . . . . . . . . . . . . . .: /usr/local

Now type 'make', followed by 'make install' as root.

bowditch@bowditch:/usr/jack/jackd/qjackctl-0.3.4$ make
Failure to open file: /usr/jack/jackd/qjackctl-0.3.4//qjackctl.mak
Unable to generate makefile for: qjackctl.pro
make: *** [qjackctl.mak] Error 5
bowditch@bowditch:/usr/jack/jackd/qjackctl-0.3.4$ 
```

i went through your list and made sure i had all of the dependencies.

---

### Post by babarosa on 2009-01-07
It is annoying, isn't it?

[LIST]
[*] I am doubtfully about your path "/usr/jack/jackd/qjackctl-0.3.4$". Why do you not simply unpack the qjackctl-package to bowditch so you start compiling at bowditch@bowditch:~/qjackctl-0.3.4$

cd qjackctl-**0.3.4**
**export QTDIR=/usr/share/qt4**
./configure
make
sudo make install

Maybe you overwrote a file (maybe anything concerning qt?) so would you mind starting the whole compiling process of ffado, jack and qjackctl again :twisted:? You do not have to download anything again, start the commands (anyway for further system setups you should keep records of the commands, ...)
[*] I came across a potential bug report concerning gentoo and qjackctl 0.3.4 ([http://bugs.gentoo.org/attachment.cgi?id=175530](http://bugs.gentoo.org/attachment.cgi?id=175530)). This guy came even further and then the compiling process died!
[*] That's why I recommend downloading qjackctl-**0.3.3**.tar.gz from [http://qjackctl.sourceforge.net/qjackctl-dl1.html](http://qjackctl.sourceforge.net/qjackctl-dl1.html), unpack it to the main directory bowditch and start again.

cd qjackctl-**0.3.3**
**export QTDIR=/usr/share/qt4**
./configure
make
sudo make install
[/LIST]

Good luck, Michael

P.S. You are compiling QJackCtl, does this mean you already succeded with ffado?

---

### Post by ubustu616 on 2009-01-07
compiling ffado

```
bowditch@bowditch:~/.ffado/libffado-2.0-rc1$ scons
scons: Reading SConscript files ...
Checking for a working C-compiler (cached) yes
Checking for a working C++-compiler (cached) yes
Checking for pkg-config (at least version 0.0.0)... (cached) yes
Checking for C header file expat.h... (cached) yes
Checking for XML_ExpatVersion() in C library expat... (cached) yes
Checking for libraw1394 (1.3.0 or higher)... 	(cached) yes
Checking for dbus-1 (1.0 or higher)... 	(cached) yes
Checking for libxml++-2.6 (2.13.0 or higher)... 	(cached) yes
Checking for libiec61883 (1.1.0 or higher)... 	(cached) yes
Checking for lrint(3.2) in C library m... (cached) yes
Checking for lrintf(3.2) in C library m... (cached) yes
Trying to find the system triple: (cached) i686-pc-linux-gnu
Doing a DEBUG build
Detected DIST_TARGET = i686
Doing a 32-bit build
rm -f /usr/local/bin/ffadomixer
scons: done reading SConscript files.
scons: Building targets ...
scons: `src' is up to date.
scons: `support' is up to date.
scons: `tests' is up to date.
scons: done building targets.
bowditch@bowditch:~/.ffado/libffado-2.0-rc1$ sudo scons install
[sudo] password for bowditch: 
scons: Reading SConscript files ...
Checking for a working C-compiler (cached) yes
Checking for a working C++-compiler (cached) yes
Checking for pkg-config (at least version 0.0.0)... (cached) yes
Checking for C header file expat.h... (cached) yes
Checking for XML_ExpatVersion() in C library expat... (cached) yes
Checking for libraw1394 (1.3.0 or higher)... 	(cached) yes
Checking for dbus-1 (1.0 or higher)... 	(cached) yes
Checking for libxml++-2.6 (2.13.0 or higher)... 	(cached) yes
Checking for libiec61883 (1.1.0 or higher)... 	(cached) yes
Checking for lrint(3.2) in C library m... (cached) yes
Checking for lrintf(3.2) in C library m... (cached) yes
Trying to find the system triple: (cached) i686-pc-linux-gnu
Doing a DEBUG build
Detected DIST_TARGET = i686
Doing a 32-bit build
rm -f /usr/local/bin/ffadomixer
scons: done reading SConscript files.
scons: Building targets ...
scons: `install' is up to date.
scons: done building targets.
bowditch@bowditch:~/.ffado/libffado-2.0-rc1$ 

```

configuring jack

```
bowditch@bowditch:~/.ffado/jack$ cd /home/bowditch/.ffado/
bowditch@bowditch:~/.ffado$ svn co http://subversion.jackaudio.org/jack/trunk/jack jack
Checked out revision 3235.
bowditch@bowditch:~/.ffado/jack$ ./autogen.sh
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: linking file `config/ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:7: installing `config/config.guess'
configure.ac:7: installing `config/config.sub'
bowditch@bowditch:~/.ffado/jack$ ./configure --with-default-tmpdir=/dev/shm
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking whether gcc and cc understand -c and -o together... yes
checking whether byte ordering is bigendian... no
checking platform dependencies... checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking /usr/include/nptl/pthread.h usability... no
checking /usr/include/nptl/pthread.h presence... no
checking for /usr/include/nptl/pthread.h... no
checking for getopt_long... yes
checking for gethostent... yes
checking for setsockopt... yes
checking for connect... yes
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for pthread_create... no
checking for pthread_create in -lpthread... yes
checking for on_exit... yes
checking for atexit... yes
checking for posix_memalign... yes
checking for sin in -lm... yes
Checking for ppoll()... yes
checking for clock_gettime... no
checking for clock_gettime in -lrt... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mlockall... yes
checking shared memory support... System V shmget().
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
checking whether we can compile MMX code... yes
yes
checking whether we can compile SSE code... yes
configure: WARNING: no optimization.........................
checking for pthread_barrier_init in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... no
configure: WARNING: *** the jackrec example client will not be built
checking for SAMPLERATE... no
configure: WARNING: *** the NetJack backend and internal client will not be built
checking for CELT... no
no
configure: WARNING: *** NetJack will not be built with celt support
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking for LIBFREEBOB... no
no
checking for LIBFFADO... yes
checking for ALSA... yes
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking readline/chardefs.h usability... no
checking readline/chardefs.h presence... no
checking for readline/chardefs.h... no
configure: WARNING: *** the jack_transport example client will not be built
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config/Makefile
config.status: creating config/cpu/Makefile
config.status: creating config/cpu/alpha/Makefile
config.status: creating config/cpu/cris/Makefile
config.status: creating config/cpu/generic/Makefile
config.status: creating config/cpu/i386/Makefile
config.status: creating config/cpu/i486/Makefile
config.status: creating config/cpu/ia64/Makefile
config.status: creating config/cpu/m68k/Makefile
config.status: creating config/cpu/mips/Makefile
config.status: creating config/cpu/powerpc/Makefile
config.status: creating config/cpu/s390/Makefile
config.status: creating config/os/Makefile
config.status: creating config/os/generic/Makefile
config.status: creating config/os/gnu-linux/Makefile
config.status: creating config/os/macosx/Makefile
config.status: creating config/sysdeps/Makefile
config.status: creating doc/Makefile
config.status: creating doc/reference.doxygen
config.status: creating drivers/Makefile
config.status: creating drivers/alsa/Makefile
config.status: creating drivers/alsa-midi/Makefile
config.status: creating drivers/dummy/Makefile
config.status: creating drivers/oss/Makefile
config.status: creating drivers/sun/Makefile
config.status: creating drivers/portaudio/Makefile
config.status: creating drivers/coreaudio/Makefile
config.status: creating drivers/freebob/Makefile
config.status: creating drivers/firewire/Makefile
config.status: creating drivers/netjack/Makefile
config.status: creating example-clients/Makefile
config.status: creating tools/Makefile
config.status: creating man/Makefile
config.status: creating jack.pc
config.status: creating jack.spec
config.status: creating jack/Makefile
config.status: creating jack/version.h
config.status: creating jackd/Makefile
config.status: creating jackd/jackd.1
config.status: creating libjack/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

jack-audio-connection-kit 0.116.1 :

| Build with ALSA support............................... : true
| Build with old FireWire (FreeBob) support............. : false
| Build with new FireWire (FFADO) support............... : true
| Build with OSS support................................ : true
| Build with Sun audio support.......................... : false
| Build with CoreAudio support.......................... : false
| Build with PortAudio support.......................... : false
| Build with NetJack support............................ : false
| Build with Celt support............................... : false
| Build with dynamic buffer size support................ : yes
| Compiler optimization flags........................... : -g
| Compiler full flags................................... : -I$(top_srcdir)/config -I$(top_srcdir) -I$(top_srcdir) -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g
| Install dir for libjack + backends.................... : ${exec_prefix}/lib/jack
|
| Default driver backend................................ : "alsa"
| Shared memory interface............................... : "System V"
| IPC Temporary directory............................... : /dev/shm
| Install prefix........................................ : /usr/local
| Default tmp dir....................................... : /dev/shm
```

make jack

```
bowditch@bowditch:~/.ffado/jack$ make
make  all-recursive
make[1]: Entering directory `/home/bowditch/.ffado/jack'
Making all in jack
make[2]: Entering directory `/home/bowditch/.ffado/jack/jack'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jack'
Making all in libjack
make[2]: Entering directory `/home/bowditch/.ffado/jack/libjack'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
Making all in jackd
make[2]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make  all-am
make[3]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
Making all in drivers
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers'
Making all in alsa-midi
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
Making all in alsa
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
Making all in dummy
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
Making all in oss
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
Making all in firewire
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
Making all in netjack
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
Making all in example-clients
make[2]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
Making all in tools
make[2]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/tools'
Making all in config
make[2]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/config'
Making all in man
make[2]: Entering directory `/home/bowditch/.ffado/jack/man'
make  all-am
make[3]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Leaving directory `/home/bowditch/.ffado/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack'
```

sudo make install jack



```
bowditch@bowditch:~/.ffado/jack$ sudo make install
[sudo] password for bowditch: 
Making install in jack
make[1]: Entering directory `/home/bowditch/.ffado/jack/jack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/jack" || /bin/mkdir -p "/usr/local/include/jack"
 /usr/bin/install -c -m 644 'intclient.h' '/usr/local/include/jack/intclient.h'
 /usr/bin/install -c -m 644 'jack.h' '/usr/local/include/jack/jack.h'
 /usr/bin/install -c -m 644 'ringbuffer.h' '/usr/local/include/jack/ringbuffer.h'
 /usr/bin/install -c -m 644 'statistics.h' '/usr/local/include/jack/statistics.h'
 /usr/bin/install -c -m 644 'thread.h' '/usr/local/include/jack/thread.h'
 /usr/bin/install -c -m 644 'timestamps.h' '/usr/local/include/jack/timestamps.h'
 /usr/bin/install -c -m 644 'transport.h' '/usr/local/include/jack/transport.h'
 /usr/bin/install -c -m 644 'types.h' '/usr/local/include/jack/types.h'
 /usr/bin/install -c -m 644 'midiport.h' '/usr/local/include/jack/midiport.h'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jack'
Making install in libjack
make[1]: Entering directory `/home/bowditch/.ffado/jack/libjack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/libjack'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjack.la' '/usr/local/lib/libjack.la'
libtool: install: /usr/bin/install -c .libs/libjack.so.0.0.28 /usr/local/lib/libjack.so.0.0.28
libtool: install: (cd /usr/local/lib && { ln -s -f libjack.so.0.0.28 libjack.so.0 || { rm -f libjack.so.0 && ln -s libjack.so.0.0.28 libjack.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libjack.so.0.0.28 libjack.so || { rm -f libjack.so && ln -s libjack.so.0.0.28 libjack.so; }; })
libtool: install: /usr/bin/install -c .libs/libjack.lai /usr/local/lib/libjack.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-exec-hook
make[3]: Entering directory `/home/bowditch/.ffado/jack/libjack'
Removing JACK shared memory registry key  0x282929
ipcrm -M 0x282929
ipcrm: invalid key (0x282929)
make[3]: [install-exec-hook] Error 1 (ignored)
make[3]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
Making install in jackd
make[1]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make  install-am
make[2]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make[3]: Entering directory `/home/bowditch/.ffado/jack/jackd'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjackserver.la' '/usr/local/lib/libjackserver.la'
libtool: install: /usr/bin/install -c .libs/libjackserver.so.0.0.28 /usr/local/lib/libjackserver.so.0.0.28
libtool: install: (cd /usr/local/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so.0 || { rm -f libjackserver.so.0 && ln -s libjackserver.so.0.0.28 libjackserver.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so || { rm -f libjackserver.so && ln -s libjackserver.so.0.0.28 libjackserver.so; }; })
libtool: install: /usr/bin/install -c .libs/libjackserver.lai /usr/local/lib/libjackserver.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jackd' '/usr/local/bin/jackd'
libtool: install: /usr/bin/install -c .libs/jackd /usr/local/bin/jackd
make  install-exec-hook
make[4]: Entering directory `/home/bowditch/.ffado/jack/jackd'
Nothing to make for install-exec-hook.
make[4]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './jackd.1' '/usr/local/share/man/man1/jackd.1'
 /usr/bin/install -c -m 644 './jackstart.1' '/usr/local/share/man/man1/jackstart.1'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
Making install in drivers
make[1]: Entering directory `/home/bowditch/.ffado/jack/drivers'
Making install in alsa-midi
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
Making install in alsa
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_alsa.la' '/usr/local/lib/jack/jack_alsa.la'
libtool: install: /usr/bin/install -c .libs/jack_alsa.so /usr/local/lib/jack/jack_alsa.so
libtool: install: /usr/bin/install -c .libs/jack_alsa.lai /usr/local/lib/jack/jack_alsa.la
libtool: install: warning: remember to run `libtool --finish /dev/shm/lib/jack'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
Making install in dummy
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_dummy.la' '/usr/local/lib/jack/jack_dummy.la'
libtool: install: /usr/bin/install -c .libs/jack_dummy.so /usr/local/lib/jack/jack_dummy.so
libtool: install: /usr/bin/install -c .libs/jack_dummy.lai /usr/local/lib/jack/jack_dummy.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
Making install in oss
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_oss.la' '/usr/local/lib/jack/jack_oss.la'
libtool: install: /usr/bin/install -c .libs/jack_oss.so /usr/local/lib/jack/jack_oss.so
libtool: install: /usr/bin/install -c .libs/jack_oss.lai /usr/local/lib/jack/jack_oss.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
Making install in firewire
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_firewire.la' '/usr/local/lib/jack/jack_firewire.la'
libtool: install: /usr/bin/install -c .libs/jack_firewire.so /usr/local/lib/jack/jack_firewire.so
libtool: install: /usr/bin/install -c .libs/jack_firewire.lai /usr/local/lib/jack/jack_firewire.la
libtool: install: warning: remember to run `libtool --finish /dev/shm/lib/jack'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
Making install in netjack
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_net.la' '/usr/local/lib/jack/jack_net.la'
libtool: install: /usr/bin/install -c .libs/jack_net.so /usr/local/lib/jack/jack_net.so
libtool: install: /usr/bin/install -c .libs/jack_net.lai /usr/local/lib/jack/jack_net.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
Making install in example-clients
make[1]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
make[2]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_simple_client' '/usr/local/bin/jack_simple_client'
libtool: install: /usr/bin/install -c .libs/jack_simple_client /usr/local/bin/jack_simple_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_transport_client' '/usr/local/bin/jack_transport_client'
libtool: install: /usr/bin/install -c .libs/jack_transport_client /usr/local/bin/jack_transport_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_impulse_grabber' '/usr/local/bin/jack_impulse_grabber'
libtool: install: /usr/bin/install -c .libs/jack_impulse_grabber /usr/local/bin/jack_impulse_grabber
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_metro' '/usr/local/bin/jack_metro'
libtool: install: /usr/bin/install -c .libs/jack_metro /usr/local/bin/jack_metro
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_showtime' '/usr/local/bin/jack_showtime'
libtool: install: /usr/bin/install -c .libs/jack_showtime /usr/local/bin/jack_showtime
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midisine' '/usr/local/bin/jack_midisine'
libtool: install: /usr/bin/install -c .libs/jack_midisine /usr/local/bin/jack_midisine
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midiseq' '/usr/local/bin/jack_midiseq'
libtool: install: /usr/bin/install -c .libs/jack_midiseq /usr/local/bin/jack_midiseq
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'inprocess.la' '/usr/local/lib/jack/inprocess.la'
libtool: install: /usr/bin/install -c .libs/inprocess.so /usr/local/lib/jack/inprocess.so
libtool: install: /usr/bin/install -c .libs/inprocess.lai /usr/local/lib/jack/inprocess.la
libtool: install: warning: remember to run `libtool --finish /dev/shm/lib/jack'
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'intime.la' '/usr/local/lib/jack/intime.la'
libtool: install: /usr/bin/install -c .libs/intime.so /usr/local/lib/jack/intime.so
libtool: install: /usr/bin/install -c .libs/intime.lai /usr/local/lib/jack/intime.la
libtool: install: warning: remember to run `libtool --finish /dev/shm/lib/jack'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
Making install in tools
make[1]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
make[2]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_load' '/usr/local/bin/jack_load'
libtool: install: /usr/bin/install -c .libs/jack_load /usr/local/bin/jack_load
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_unload' '/usr/local/bin/jack_unload'
libtool: install: /usr/bin/install -c .libs/jack_unload /usr/local/bin/jack_unload
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_monitor_client' '/usr/local/bin/jack_monitor_client'
libtool: install: /usr/bin/install -c .libs/jack_monitor_client /usr/local/bin/jack_monitor_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_connect' '/usr/local/bin/jack_connect'
libtool: install: /usr/bin/install -c .libs/jack_connect /usr/local/bin/jack_connect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_disconnect' '/usr/local/bin/jack_disconnect'
libtool: install: /usr/bin/install -c .libs/jack_disconnect /usr/local/bin/jack_disconnect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_lsp' '/usr/local/bin/jack_lsp'
libtool: install: /usr/bin/install -c .libs/jack_lsp /usr/local/bin/jack_lsp
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_freewheel' '/usr/local/bin/jack_freewheel'
libtool: install: /usr/bin/install -c .libs/jack_freewheel /usr/local/bin/jack_freewheel
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_evmon' '/usr/local/bin/jack_evmon'
libtool: install: /usr/bin/install -c .libs/jack_evmon /usr/local/bin/jack_evmon
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_alias' '/usr/local/bin/jack_alias'
libtool: install: /usr/bin/install -c .libs/jack_alias /usr/local/bin/jack_alias
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/tools'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/tools'
Making install in config
make[1]: Entering directory `/home/bowditch/.ffado/jack/config'
make[2]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/config'
Making install in man
make[1]: Entering directory `/home/bowditch/.ffado/jack/man'
make  install-am
make[2]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './alsa_in.1' '/usr/local/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/usr/local/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/usr/local/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/usr/local/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/usr/local/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/usr/local/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/usr/local/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/usr/local/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/usr/local/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/usr/local/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/usr/local/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/usr/local/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/usr/local/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/usr/local/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/usr/local/share/man/man1/jack_unload.1'
 /usr/bin/install -c -m 644 './alsa_in.1' '/usr/local/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/usr/local/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/usr/local/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/usr/local/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/usr/local/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/usr/local/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/usr/local/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/usr/local/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/usr/local/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/usr/local/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/usr/local/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/usr/local/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/usr/local/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/usr/local/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/usr/local/share/man/man1/jack_unload.1'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[1]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'jack.pc' '/usr/local/lib/pkgconfig/jack.pc'
make[2]: Leaving directory `/home/bowditch/.ffado/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack'
bowditch@bowditch:~/.ffado/jack$ 
```




configuring qjackctl

```
bowditch@bowditch:~/.ffado/jack$ cd /home/bowditch/.ffado/qjackctl-0.3.3/
bowditch@bowditch:~/.ffado/qjackctl-0.3.3$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for Qt library version >= 4.1... yes
checking for qmake... /usr/share/qt4/bin/qmake
checking for moc... /usr/share/qt4/bin/moc
checking for uic... /usr/share/qt4/bin/uic
checking for main in -lm... yes
checking for main in -lX11... yes
checking for main in -lXext... yes
checking for lroundf in -lm... yes
checking for main in -ljack... yes
checking for main in -lasound... yes
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking jack/jack.h usability... yes
checking jack/jack.h presence... yes
checking for jack/jack.h... yes
checking jack/statistics.h usability... yes
checking jack/statistics.h presence... yes
checking for jack/statistics.h... yes
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking jack/midiport.h usability... yes
checking jack/midiport.h presence... yes
checking for jack/midiport.h... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for system... yes
checking for jack_transport_query in -ljack... yes
checking for jack_is_realtime in -ljack... yes
checking for jack_get_xrun_delayed_usecs in -ljack... yes
checking for jack_get_max_delayed_usecs in -ljack... yes
checking for jack_midi_event_get in -ljack... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating qjackctl.pro
config.status: creating qjackctl.spec
config.status: creating qjackctl.desktop
config.status: creating config.h
config.status: config.h is unchanged

  QjackCtl 0.3.3

  Build target . . . . . . . . . . . . . . . . . . .: release

  JACK Audio Connection Kit support  . . . . . . . .: yes
  JACK Realtime support  . . . . . . . . . . . . . .: yes
  JACK Transport support . . . . . . . . . . . . . .: yes
  JACK XRUN delay support  . . . . . . . . . . . . .: yes
  JACK Maximum scheduling delay support  . . . . . .: yes
  JACK MIDI support  . . . . . . . . . . . . . . . .: yes
  ALSA MIDI Sequencer support  . . . . . . . . . . .: yes
  System tray icon support . . . . . . . . . . . . .: yes

  Install prefix . . . . . . . . . . . . . . . . . .: /usr/local

Now type 'make', followed by 'make install' as root.
```

make jack (this is my second time doing this for the post and it went well the first time)

```
bowditch@bowditch:~/.ffado/qjackctl-0.3.3$ make
make[1]: Entering directory `/home/bowditch/.ffado/qjackctl-0.3.3'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `/home/bowditch/.ffado/qjackctl-0.3.3'
bowditch@bowditch:~/.ffado/qjackctl-0.3.3$ 
```

sudo make install (diddo)

[email]bowditch@bowditch:~/.ffado[/email]/qjackctl-0.3.3$ sudo make install
make[1]: Entering directory `/home/bowditch/.ffado/qjackctl-0.3.3'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `/home/bowditch/.ffado/qjackctl-0.3.3'
removed `/usr/local/bin/qjackctl'
`qjackctl' -> `/usr/local/bin/qjackctl'
removed `/usr/local/share/pixmaps/qjackctl.png'
`icons/qjackctl.png' -> `/usr/local/share/pixmaps/qjackctl.png'
removed `/usr/local/share/applications/qjackctl.desktop'
`qjackctl.desktop' -> `/usr/local/share/applications/qjackctl.desktop'
[email]bowditch@bowditch:~/.ffado[/email]/qjackctl-0.3.3$ 

ffado-dbus-server & (there are some errors here)
```

bowditch@bowditch:~/.ffado/jack$ ffado-dbus-server &
[1] 26102
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

94711335062:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
bowditch@bowditch:~/.ffado/jack$ 94711338558: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
94711344270: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711345383: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711346504: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711347620: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711348738: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711406152: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711407284: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711408400: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711409502: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711410601: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
94711459436: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
94711459500: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
94711459520: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
94711459532: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
94711459557: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
94711459566: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
94711459573: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
94711459645: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
94711459664: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
94711459673: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
94711459680: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
94711459687: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
94711459707: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
94711459715: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
94711460048: Debug (devicemanager.cpp)[ 594] discover: driver found for device 1
94711460129: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
94711460149: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
94711460157: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
94711460164: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
94711460171: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
94711460190: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
94711460200: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
94711461367: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
94711461382: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
94711461640: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
94711461653: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (1,1,0,0,0)
94711462207: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
94711462220: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (1,1,0,1,0)
94711462734: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
94711462964: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
94711462974: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
94711462980: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
94711462991: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
94711462998: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
94711463312: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711463332: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,0)
94711463597: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
94711463611: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
94711463886: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711463902: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,0)
94711464149: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
94711464164: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
94711464434: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711464449: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,0)
94711464711: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
94711464986: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711465001: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,1)
94711465225: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
94711465492: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711465506: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,2)
94711465744: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
94711465758: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
94711466030: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711466045: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,0)
94711466277: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
94711466551: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
94711466571: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,1)
94711466797: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
94711466813: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
94711467090: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
94711467112: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
94711467349: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
94711467587: Error (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
94711467601: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
94711467851: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
94711467863: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
94711467870: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
94711467875: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
94711467895: Warning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
94711467909: Warning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
94711467923: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
94711467934: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
94711467951: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
94711467958: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
94711467969: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
94711467974: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
94711468013: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
94711468024: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
94711468030: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
94711468034: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
94711468049: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
94711468054: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
94711468059: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
94711468064: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
94711468077: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
94711468083: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
94711468095: Error (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
94711468102: Error (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
94711468115: Error (devicemanager.cpp)[ 606] discover: could not discover device
94711468257: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
94711468268: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
94711468275: Debug (Element.cpp)[ 121] show: Element DeviceManager
94711468287: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
94711468351:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
94711475650:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
94711475687: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
```


ffado-mixer &

```
ffado-mixer &
[2] 26110
bowditch@bowditch:~/.ffado/jack$ bash: ffado-mixer: command not found
```

trying to start jack

```
bowditch@bowditch:~/.ffado/jack$ bash: ffado-mixer: command not found
jackd -d firewire -n 3 -p 2048
jackd: error while loading shared libraries: libjackserver.so.0: cannot open shared object file: No such file or directory
[2]+  Exit 127                ffado-mixer
bowditch@bowditch:~/.ffado/jack$ 

```

wow, i really dont know how guys can put up with me. THANKS!!!

---

### Post by Stochastic on 2009-01-08
BEFORE running this:
> bowditch@bowditch:~/.ffado/jack$ make
MAKE SURE YOU RUN
```
make clean
```

Then please try reposting the output of jack.

Don't bother attempting to build qjackctl until you have jack built properly and can get it to run from the command line.

---

### Post by ubustu616 on 2009-01-09
make clean

```
bowditch@bowditch:~/.ffado/jack$ make clean
Making clean in man
make[1]: Entering directory `/home/bowditch/.ffado/jack/man'
rm -rf .libs _libs
rm -rf alsa_in.1 alsa_out.1 jack_bufsize.1 jack_connect.1 jack_disconnect.1 jack_freewheel.1 jack_impulse_grabber.1 jack_load.1 jack_lsp.1 jack_metro.1 jack_monitor_client.1 jackrec.1 jack_showtime.1 jack_transport.1 jack_unload.1
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack/man'
Making clean in config
make[1]: Entering directory `/home/bowditch/.ffado/jack/config'
Making clean in .
make[2]: Entering directory `/home/bowditch/.ffado/jack/config'
rm -rf .libs _libs
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/config'
Making clean in tools
make[1]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
 rm -f jack_load jack_load
 rm -f jack_unload jack_unload
 rm -f jack_monitor_client jack_monitor_client
 rm -f jack_connect jack_connect
 rm -f jack_disconnect jack_disconnect
 rm -f jack_lsp jack_lsp
 rm -f jack_freewheel jack_freewheel
 rm -f jack_evmon jack_evmon
 rm -f jack_alias jack_alias
rm -rf .libs _libs
 rm -f jack_thread_wait jack_thread_wait
rm -f *.o
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack/tools'
Making clean in example-clients
make[1]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
 rm -f jack_simple_client jack_simple_client
 rm -f jack_transport_client jack_transport_client
 rm -f jack_impulse_grabber jack_impulse_grabber
 rm -f jack_metro jack_metro
 rm -f jack_showtime jack_showtime
 rm -f jack_midisine jack_midisine
 rm -f jack_midiseq jack_midiseq
test -z "inprocess.la intime.la" || rm -f inprocess.la intime.la
rm -f "./so_locations"
rm -f "./so_locations"
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
Making clean in drivers
make[1]: Entering directory `/home/bowditch/.ffado/jack/drivers'
Making clean in netjack
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
rm -rf .libs _libs
test -z "jack_net.la" || rm -f jack_net.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
Making clean in firewire
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
rm -rf .libs _libs
test -z "jack_firewire.la" || rm -f jack_firewire.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
Making clean in oss
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
rm -rf .libs _libs
test -z "jack_oss.la" || rm -f jack_oss.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
Making clean in dummy
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
rm -rf .libs _libs
test -z "jack_dummy.la" || rm -f jack_dummy.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
Making clean in alsa
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
rm -rf .libs _libs
test -z "jack_alsa.la" || rm -f jack_alsa.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
Making clean in alsa-midi
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
rm -rf .libs _libs
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
Making clean in .
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers'
rm -rf .libs _libs
rm -f *.lo
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
Making clean in jackd
make[1]: Entering directory `/home/bowditch/.ffado/jack/jackd'
 rm -f jackd jackd
test -z "libjackserver.la" || rm -f libjackserver.la
rm -f "./so_locations"
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
Making clean in libjack
make[1]: Entering directory `/home/bowditch/.ffado/jack/libjack'
test -z "libjack.la" || rm -f libjack.la
rm -f "./so_locations"
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
Making clean in jack
make[1]: Entering directory `/home/bowditch/.ffado/jack/jack'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jack'
Making clean in .
make[1]: Entering directory `/home/bowditch/.ffado/jack'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory `/home/bowditch/.ffado/jack'
bowditch@bowditch:~/.ffado/jack$ 
```

make 

```
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
Making all in alsa
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-alsa_driver.lo -MD -MP -MF .deps/jack_alsa_la-alsa_driver.Tpo -c -o jack_alsa_la-alsa_driver.lo `test -f 'alsa_driver.c' || echo './'`alsa_driver.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-alsa_driver.lo -MD -MP -MF .deps/jack_alsa_la-alsa_driver.Tpo -c alsa_driver.c  -fPIC -DPIC -o .libs/jack_alsa_la-alsa_driver.o
mv -f .deps/jack_alsa_la-alsa_driver.Tpo .deps/jack_alsa_la-alsa_driver.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-generic_hw.lo -MD -MP -MF .deps/jack_alsa_la-generic_hw.Tpo -c -o jack_alsa_la-generic_hw.lo `test -f 'generic_hw.c' || echo './'`generic_hw.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-generic_hw.lo -MD -MP -MF .deps/jack_alsa_la-generic_hw.Tpo -c generic_hw.c  -fPIC -DPIC -o .libs/jack_alsa_la-generic_hw.o
mv -f .deps/jack_alsa_la-generic_hw.Tpo .deps/jack_alsa_la-generic_hw.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-memops.lo -MD -MP -MF .deps/jack_alsa_la-memops.Tpo -c -o jack_alsa_la-memops.lo `test -f 'memops.c' || echo './'`memops.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-memops.lo -MD -MP -MF .deps/jack_alsa_la-memops.Tpo -c memops.c  -fPIC -DPIC -o .libs/jack_alsa_la-memops.o
mv -f .deps/jack_alsa_la-memops.Tpo .deps/jack_alsa_la-memops.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-hammerfall.lo -MD -MP -MF .deps/jack_alsa_la-hammerfall.Tpo -c -o jack_alsa_la-hammerfall.lo `test -f 'hammerfall.c' || echo './'`hammerfall.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-hammerfall.lo -MD -MP -MF .deps/jack_alsa_la-hammerfall.Tpo -c hammerfall.c  -fPIC -DPIC -o .libs/jack_alsa_la-hammerfall.o
mv -f .deps/jack_alsa_la-hammerfall.Tpo .deps/jack_alsa_la-hammerfall.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-hdsp.lo -MD -MP -MF .deps/jack_alsa_la-hdsp.Tpo -c -o jack_alsa_la-hdsp.lo `test -f 'hdsp.c' || echo './'`hdsp.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-hdsp.lo -MD -MP -MF .deps/jack_alsa_la-hdsp.Tpo -c hdsp.c  -fPIC -DPIC -o .libs/jack_alsa_la-hdsp.o
mv -f .deps/jack_alsa_la-hdsp.Tpo .deps/jack_alsa_la-hdsp.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-ice1712.lo -MD -MP -MF .deps/jack_alsa_la-ice1712.Tpo -c -o jack_alsa_la-ice1712.lo `test -f 'ice1712.c' || echo './'`ice1712.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-ice1712.lo -MD -MP -MF .deps/jack_alsa_la-ice1712.Tpo -c ice1712.c  -fPIC -DPIC -o .libs/jack_alsa_la-ice1712.o
mv -f .deps/jack_alsa_la-ice1712.Tpo .deps/jack_alsa_la-ice1712.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-usx2y.lo -MD -MP -MF .deps/jack_alsa_la-usx2y.Tpo -c -o jack_alsa_la-usx2y.lo `test -f 'usx2y.c' || echo './'`usx2y.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-usx2y.lo -MD -MP -MF .deps/jack_alsa_la-usx2y.Tpo -c usx2y.c  -fPIC -DPIC -o .libs/jack_alsa_la-usx2y.o
mv -f .deps/jack_alsa_la-usx2y.Tpo .deps/jack_alsa_la-usx2y.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-alsa_rawmidi.lo -MD -MP -MF .deps/jack_alsa_la-alsa_rawmidi.Tpo -c -o jack_alsa_la-alsa_rawmidi.lo `test -f '../alsa-midi/alsa_rawmidi.c' || echo './'`../alsa-midi/alsa_rawmidi.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-alsa_rawmidi.lo -MD -MP -MF .deps/jack_alsa_la-alsa_rawmidi.Tpo -c ../alsa-midi/alsa_rawmidi.c  -fPIC -DPIC -o .libs/jack_alsa_la-alsa_rawmidi.o
mv -f .deps/jack_alsa_la-alsa_rawmidi.Tpo .deps/jack_alsa_la-alsa_rawmidi.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT jack_alsa_la-alsa_seqmidi.lo -MD -MP -MF .deps/jack_alsa_la-alsa_seqmidi.Tpo -c -o jack_alsa_la-alsa_seqmidi.lo `test -f '../alsa-midi/alsa_seqmidi.c' || echo './'`../alsa-midi/alsa_seqmidi.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT jack_alsa_la-alsa_seqmidi.lo -MD -MP -MF .deps/jack_alsa_la-alsa_seqmidi.Tpo -c ../alsa-midi/alsa_seqmidi.c  -fPIC -DPIC -o .libs/jack_alsa_la-alsa_seqmidi.o
mv -f .deps/jack_alsa_la-alsa_seqmidi.Tpo .deps/jack_alsa_la-alsa_seqmidi.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -I../alsa-midi -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version  -o jack_alsa.la -rpath /usr/local/lib/jack jack_alsa_la-alsa_driver.lo jack_alsa_la-generic_hw.lo jack_alsa_la-memops.lo jack_alsa_la-hammerfall.lo jack_alsa_la-hdsp.lo jack_alsa_la-ice1712.lo jack_alsa_la-usx2y.lo jack_alsa_la-alsa_rawmidi.lo jack_alsa_la-alsa_seqmidi.lo -lasound  -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/jack_alsa_la-alsa_driver.o .libs/jack_alsa_la-generic_hw.o .libs/jack_alsa_la-memops.o .libs/jack_alsa_la-hammerfall.o .libs/jack_alsa_la-hdsp.o .libs/jack_alsa_la-ice1712.o .libs/jack_alsa_la-usx2y.o .libs/jack_alsa_la-alsa_rawmidi.o .libs/jack_alsa_la-alsa_seqmidi.o   /usr/lib/libasound.so -lrt -lm -lpthread -ldl    -Wl,-soname -Wl,jack_alsa.so -o .libs/jack_alsa.so
libtool: link: ( cd ".libs" && rm -f "jack_alsa.la" && ln -s "../jack_alsa.la" "jack_alsa.la" )
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
Making all in dummy
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT dummy_driver.lo -MD -MP -MF .deps/dummy_driver.Tpo -c -o dummy_driver.lo dummy_driver.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT dummy_driver.lo -MD -MP -MF .deps/dummy_driver.Tpo -c dummy_driver.c  -fPIC -DPIC -o .libs/dummy_driver.o
mv -f .deps/dummy_driver.Tpo .deps/dummy_driver.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version  -o jack_dummy.la -rpath /usr/local/lib/jack dummy_driver.lo  -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/dummy_driver.o   -lm -lpthread -ldl    -Wl,-soname -Wl,jack_dummy.so -o .libs/jack_dummy.so
libtool: link: ( cd ".libs" && rm -f "jack_dummy.la" && ln -s "../jack_dummy.la" "jack_dummy.la" )
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
Making all in oss
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -I/usr/lib/oss/include -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT oss_driver.lo -MD -MP -MF .deps/oss_driver.Tpo -c -o oss_driver.lo oss_driver.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I/usr/lib/oss/include -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT oss_driver.lo -MD -MP -MF .deps/oss_driver.Tpo -c oss_driver.c  -fPIC -DPIC -o .libs/oss_driver.o
mv -f .deps/oss_driver.Tpo .deps/oss_driver.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -I/usr/lib/oss/include -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version  -o jack_oss.la -rpath /usr/local/lib/jack oss_driver.lo  -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/oss_driver.o   -lm -lpthread -ldl    -Wl,-soname -Wl,jack_oss.so -o .libs/jack_oss.so
libtool: link: ( cd ".libs" && rm -f "jack_oss.la" && ln -s "../jack_oss.la" "jack_oss.la" )
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
Making all in firewire
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -I/usr/local/include   -I/usr/include/alsa   -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT ffado_driver.lo -MD -MP -MF .deps/ffado_driver.Tpo -c -o ffado_driver.lo ffado_driver.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I/usr/local/include -I/usr/include/alsa -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT ffado_driver.lo -MD -MP -MF .deps/ffado_driver.Tpo -c ffado_driver.c  -fPIC -DPIC -o .libs/ffado_driver.o
mv -f .deps/ffado_driver.Tpo .deps/ffado_driver.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -I/usr/local/include   -I/usr/include/alsa   -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version  -o jack_firewire.la -rpath /usr/local/lib/jack ffado_driver.lo -L/usr/local/lib -lffado   -lasound -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/ffado_driver.o   -L/usr/local/lib -lffado /usr/lib/libasound.so -lrt -lm -lpthread -ldl    -Wl,-soname -Wl,jack_firewire.so -o .libs/jack_firewire.so
libtool: link: ( cd ".libs" && rm -f "jack_firewire.la" && ln -s "../jack_firewire.la" "jack_firewire.la" )
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
Making all in netjack
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT net_driver.lo -MD -MP -MF .deps/net_driver.Tpo -c -o net_driver.lo net_driver.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT net_driver.lo -MD -MP -MF .deps/net_driver.Tpo -c net_driver.c  -fPIC -DPIC -o .libs/net_driver.o
mv -f .deps/net_driver.Tpo .deps/net_driver.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT netjack_packet.lo -MD -MP -MF .deps/netjack_packet.Tpo -c -o netjack_packet.lo netjack_packet.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT netjack_packet.lo -MD -MP -MF .deps/netjack_packet.Tpo -c netjack_packet.c  -fPIC -DPIC -o .libs/netjack_packet.o
netjack_packet.c: In function ‘render_payload_to_jack_ports_float’:
netjack_packet.c:861: warning: unused variable ‘src_node’
netjack_packet.c: In function ‘render_jack_ports_to_payload_float’:
netjack_packet.c:943: warning: unused variable ‘src_node’
netjack_packet.c: In function ‘render_payload_to_jack_ports_16bit’:
netjack_packet.c:1040: warning: unused variable ‘floatbuf’
netjack_packet.c:1022: warning: unused variable ‘src_node’
netjack_packet.c: In function ‘render_jack_ports_to_payload_16bit’:
netjack_packet.c:1093: warning: unused variable ‘src_node’
netjack_packet.c: In function ‘render_payload_to_jack_ports_8bit’:
netjack_packet.c:1179: warning: unused variable ‘floatbuf’
netjack_packet.c:1161: warning: unused variable ‘src_node’
netjack_packet.c: In function ‘render_jack_ports_to_payload_8bit’:
netjack_packet.c:1229: warning: unused variable ‘src_node’
mv -f .deps/netjack_packet.Tpo .deps/netjack_packet.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../../config -I../.. -I../.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version   -o jack_net.la -rpath /usr/local/lib/jack net_driver.lo netjack_packet.lo  -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/net_driver.o .libs/netjack_packet.o   -lm -lpthread -ldl    -Wl,-soname -Wl,jack_net.so -o .libs/jack_net.so
libtool: link: ( cd ".libs" && rm -f "jack_net.la" && ln -s "../jack_net.la" "jack_net.la" )
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
Making all in example-clients
make[2]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT inprocess.lo -MD -MP -MF .deps/inprocess.Tpo -c -o inprocess.lo inprocess.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT inprocess.lo -MD -MP -MF .deps/inprocess.Tpo -c inprocess.c  -fPIC -DPIC -o .libs/inprocess.o
mv -f .deps/inprocess.Tpo .deps/inprocess.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version  -lrt  -o inprocess.la -rpath /usr/local/lib/jack inprocess.lo  -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/inprocess.o   -lrt -lm -lpthread -ldl    -Wl,-soname -Wl,inprocess.so -o .libs/inprocess.so
libtool: link: ( cd ".libs" && rm -f "inprocess.la" && ln -s "../inprocess.la" "inprocess.la" )
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT intime.lo -MD -MP -MF .deps/intime.Tpo -c -o intime.lo intime.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -MT intime.lo -MD -MP -MF .deps/intime.Tpo -c intime.c  -fPIC -DPIC -o .libs/intime.o
mv -f .deps/intime.Tpo .deps/intime.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -module -avoid-version  -lrt  -o intime.la -rpath /usr/local/lib/jack intime.lo  -lm -lpthread -ldl 
libtool: link: gcc -shared  .libs/intime.o   -lrt -lm -lpthread -ldl    -Wl,-soname -Wl,intime.so -o .libs/intime.so
libtool: link: ( cd ".libs" && rm -f "intime.la" && ln -s "../intime.la" "intime.la" )
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT simple_client.o -MD -MP -MF .deps/simple_client.Tpo -c -o simple_client.o simple_client.c
mv -f .deps/simple_client.Tpo .deps/simple_client.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_simple_client simple_client.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_simple_client simple_client.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT transport_client.o -MD -MP -MF .deps/transport_client.Tpo -c -o transport_client.o transport_client.c
mv -f .deps/transport_client.Tpo .deps/transport_client.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_transport_client transport_client.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_transport_client transport_client.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT impulse_grabber.o -MD -MP -MF .deps/impulse_grabber.Tpo -c -o impulse_grabber.o impulse_grabber.c
mv -f .deps/impulse_grabber.Tpo .deps/impulse_grabber.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_impulse_grabber impulse_grabber.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_impulse_grabber impulse_grabber.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT metro.o -MD -MP -MF .deps/metro.Tpo -c -o metro.o metro.c
mv -f .deps/metro.Tpo .deps/metro.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_metro metro.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_metro metro.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT showtime.o -MD -MP -MF .deps/showtime.Tpo -c -o showtime.o showtime.c
mv -f .deps/showtime.Tpo .deps/showtime.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_showtime showtime.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_showtime showtime.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT midisine.o -MD -MP -MF .deps/midisine.Tpo -c -o midisine.o midisine.c
mv -f .deps/midisine.Tpo .deps/midisine.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_midisine midisine.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_midisine midisine.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT midiseq.o -MD -MP -MF .deps/midiseq.Tpo -c -o midiseq.o midiseq.c
mv -f .deps/midiseq.Tpo .deps/midiseq.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_midiseq midiseq.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_midiseq midiseq.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
make[2]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
Making all in tools
make[2]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT ipload.o -MD -MP -MF .deps/ipload.Tpo -c -o ipload.o ipload.c
mv -f .deps/ipload.Tpo .deps/ipload.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_load ipload.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_load ipload.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT ipunload.o -MD -MP -MF .deps/ipunload.Tpo -c -o ipunload.o ipunload.c
mv -f .deps/ipunload.Tpo .deps/ipunload.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_unload ipunload.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_unload ipunload.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT monitor_client.o -MD -MP -MF .deps/monitor_client.Tpo -c -o monitor_client.o monitor_client.c
mv -f .deps/monitor_client.Tpo .deps/monitor_client.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_monitor_client monitor_client.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_monitor_client monitor_client.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT connect.o -MD -MP -MF .deps/connect.Tpo -c -o connect.o connect.c
mv -f .deps/connect.Tpo .deps/connect.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_connect connect.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_connect connect.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_disconnect connect.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_disconnect connect.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT lsp.o -MD -MP -MF .deps/lsp.Tpo -c -o lsp.o lsp.c
mv -f .deps/lsp.Tpo .deps/lsp.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_lsp lsp.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_lsp lsp.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT freewheel.o -MD -MP -MF .deps/freewheel.Tpo -c -o freewheel.o freewheel.c
mv -f .deps/freewheel.Tpo .deps/freewheel.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_freewheel freewheel.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_freewheel freewheel.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT evmon.o -MD -MP -MF .deps/evmon.Tpo -c -o evmon.o evmon.c
mv -f .deps/evmon.Tpo .deps/evmon.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_evmon evmon.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_evmon evmon.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT alias.o -MD -MP -MF .deps/alias.Tpo -c -o alias.o alias.c
mv -f .deps/alias.Tpo .deps/alias.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_alias alias.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_alias alias.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
gcc -DHAVE_CONFIG_H -I. -I..    -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -MT tw.o -MD -MP -MF .deps/tw.Tpo -c -o tw.o tw.c
mv -f .deps/tw.Tpo .deps/tw.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g  -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall  -g -lrt  -o jack_thread_wait tw.o ../libjack/libjack.la -lm -lpthread -ldl 
libtool: link: gcc -I.. -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -I../config -I.. -I.. -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g -o .libs/jack_thread_wait tw.o  ../libjack/.libs/libjack.so -lrt -lm -lpthread -ldl
make[2]: Leaving directory `/home/bowditch/.ffado/jack/tools'
Making all in config
make[2]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/config'
Making all in man
make[2]: Entering directory `/home/bowditch/.ffado/jack/man'
Built alsa_in.1 from template
Built alsa_out.1 from template
Built jack_bufsize.1 from template
Built jack_connect.1 from template
Built jack_disconnect.1 from template
Built jack_freewheel.1 from template
Built jack_impulse_grabber.1 from template
Built jack_load.1 from template
Built jack_lsp.1 from template
Built jack_metro.1 from template
Built jack_monitor_client.1 from template
Built jackrec.1 from template
Built jack_showtime.1 from template
Built jack_transport.1 from template
Built jack_unload.1 from template
make  all-am
make[3]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Leaving directory `/home/bowditch/.ffado/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack'
bowditch@bowditch:~/.ffado/jack$ 

```

sudo make install

```
bowditch@bowditch:~/.ffado/jack$ sudo make install
[sudo] password for bowditch: 
Making install in jack
make[1]: Entering directory `/home/bowditch/.ffado/jack/jack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/jack" || /bin/mkdir -p "/usr/local/include/jack"
 /usr/bin/install -c -m 644 'intclient.h' '/usr/local/include/jack/intclient.h'
 /usr/bin/install -c -m 644 'jack.h' '/usr/local/include/jack/jack.h'
 /usr/bin/install -c -m 644 'ringbuffer.h' '/usr/local/include/jack/ringbuffer.h'
 /usr/bin/install -c -m 644 'statistics.h' '/usr/local/include/jack/statistics.h'
 /usr/bin/install -c -m 644 'thread.h' '/usr/local/include/jack/thread.h'
 /usr/bin/install -c -m 644 'timestamps.h' '/usr/local/include/jack/timestamps.h'
 /usr/bin/install -c -m 644 'transport.h' '/usr/local/include/jack/transport.h'
 /usr/bin/install -c -m 644 'types.h' '/usr/local/include/jack/types.h'
 /usr/bin/install -c -m 644 'midiport.h' '/usr/local/include/jack/midiport.h'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jack'
Making install in libjack
make[1]: Entering directory `/home/bowditch/.ffado/jack/libjack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/libjack'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjack.la' '/usr/local/lib/libjack.la'
libtool: install: /usr/bin/install -c .libs/libjack.so.0.0.28 /usr/local/lib/libjack.so.0.0.28
libtool: install: (cd /usr/local/lib && { ln -s -f libjack.so.0.0.28 libjack.so.0 || { rm -f libjack.so.0 && ln -s libjack.so.0.0.28 libjack.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libjack.so.0.0.28 libjack.so || { rm -f libjack.so && ln -s libjack.so.0.0.28 libjack.so; }; })
libtool: install: /usr/bin/install -c .libs/libjack.lai /usr/local/lib/libjack.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-exec-hook
make[3]: Entering directory `/home/bowditch/.ffado/jack/libjack'
Removing JACK shared memory registry key  0x282929
ipcrm -M 0x282929
ipcrm: invalid key (0x282929)
make[3]: [install-exec-hook] Error 1 (ignored)
make[3]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
Making install in jackd
make[1]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make  install-am
make[2]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make[3]: Entering directory `/home/bowditch/.ffado/jack/jackd'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjackserver.la' '/usr/local/lib/libjackserver.la'
libtool: install: /usr/bin/install -c .libs/libjackserver.so.0.0.28 /usr/local/lib/libjackserver.so.0.0.28
libtool: install: (cd /usr/local/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so.0 || { rm -f libjackserver.so.0 && ln -s libjackserver.so.0.0.28 libjackserver.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so || { rm -f libjackserver.so && ln -s libjackserver.so.0.0.28 libjackserver.so; }; })
libtool: install: /usr/bin/install -c .libs/libjackserver.lai /usr/local/lib/libjackserver.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jackd' '/usr/local/bin/jackd'
libtool: install: /usr/bin/install -c .libs/jackd /usr/local/bin/jackd
make  install-exec-hook
make[4]: Entering directory `/home/bowditch/.ffado/jack/jackd'
Nothing to make for install-exec-hook.
make[4]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './jackd.1' '/usr/local/share/man/man1/jackd.1'
 /usr/bin/install -c -m 644 './jackstart.1' '/usr/local/share/man/man1/jackstart.1'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
Making install in drivers
make[1]: Entering directory `/home/bowditch/.ffado/jack/drivers'
Making install in alsa-midi
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
Making install in alsa
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_alsa.la' '/usr/local/lib/jack/jack_alsa.la'
libtool: install: /usr/bin/install -c .libs/jack_alsa.so /usr/local/lib/jack/jack_alsa.so
libtool: install: /usr/bin/install -c .libs/jack_alsa.lai /usr/local/lib/jack/jack_alsa.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
Making install in dummy
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_dummy.la' '/usr/local/lib/jack/jack_dummy.la'
libtool: install: /usr/bin/install -c .libs/jack_dummy.so /usr/local/lib/jack/jack_dummy.so
libtool: install: /usr/bin/install -c .libs/jack_dummy.lai /usr/local/lib/jack/jack_dummy.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
Making install in oss
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_oss.la' '/usr/local/lib/jack/jack_oss.la'
libtool: install: /usr/bin/install -c .libs/jack_oss.so /usr/local/lib/jack/jack_oss.so
libtool: install: /usr/bin/install -c .libs/jack_oss.lai /usr/local/lib/jack/jack_oss.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
Making install in firewire
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_firewire.la' '/usr/local/lib/jack/jack_firewire.la'
libtool: install: /usr/bin/install -c .libs/jack_firewire.so /usr/local/lib/jack/jack_firewire.so
libtool: install: /usr/bin/install -c .libs/jack_firewire.lai /usr/local/lib/jack/jack_firewire.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
Making install in netjack
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_net.la' '/usr/local/lib/jack/jack_net.la'
libtool: install: /usr/bin/install -c .libs/jack_net.so /usr/local/lib/jack/jack_net.so
libtool: install: /usr/bin/install -c .libs/jack_net.lai /usr/local/lib/jack/jack_net.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
Making install in example-clients
make[1]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
make[2]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_simple_client' '/usr/local/bin/jack_simple_client'
libtool: install: /usr/bin/install -c .libs/jack_simple_client /usr/local/bin/jack_simple_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_transport_client' '/usr/local/bin/jack_transport_client'
libtool: install: /usr/bin/install -c .libs/jack_transport_client /usr/local/bin/jack_transport_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_impulse_grabber' '/usr/local/bin/jack_impulse_grabber'
libtool: install: /usr/bin/install -c .libs/jack_impulse_grabber /usr/local/bin/jack_impulse_grabber
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_metro' '/usr/local/bin/jack_metro'
libtool: install: /usr/bin/install -c .libs/jack_metro /usr/local/bin/jack_metro
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_showtime' '/usr/local/bin/jack_showtime'
libtool: install: /usr/bin/install -c .libs/jack_showtime /usr/local/bin/jack_showtime
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midisine' '/usr/local/bin/jack_midisine'
libtool: install: /usr/bin/install -c .libs/jack_midisine /usr/local/bin/jack_midisine
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midiseq' '/usr/local/bin/jack_midiseq'
libtool: install: /usr/bin/install -c .libs/jack_midiseq /usr/local/bin/jack_midiseq
test -z "/usr/local/lib/jack" || /bin/mkdir -p "/usr/local/lib/jack"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'inprocess.la' '/usr/local/lib/jack/inprocess.la'
libtool: install: /usr/bin/install -c .libs/inprocess.so /usr/local/lib/jack/inprocess.so
libtool: install: /usr/bin/install -c .libs/inprocess.lai /usr/local/lib/jack/inprocess.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'intime.la' '/usr/local/lib/jack/intime.la'
libtool: install: /usr/bin/install -c .libs/intime.so /usr/local/lib/jack/intime.so
libtool: install: /usr/bin/install -c .libs/intime.lai /usr/local/lib/jack/intime.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
Making install in tools
make[1]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
make[2]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_load' '/usr/local/bin/jack_load'
libtool: install: /usr/bin/install -c .libs/jack_load /usr/local/bin/jack_load
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_unload' '/usr/local/bin/jack_unload'
libtool: install: /usr/bin/install -c .libs/jack_unload /usr/local/bin/jack_unload
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_monitor_client' '/usr/local/bin/jack_monitor_client'
libtool: install: /usr/bin/install -c .libs/jack_monitor_client /usr/local/bin/jack_monitor_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_connect' '/usr/local/bin/jack_connect'
libtool: install: /usr/bin/install -c .libs/jack_connect /usr/local/bin/jack_connect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_disconnect' '/usr/local/bin/jack_disconnect'
libtool: install: /usr/bin/install -c .libs/jack_disconnect /usr/local/bin/jack_disconnect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_lsp' '/usr/local/bin/jack_lsp'
libtool: install: /usr/bin/install -c .libs/jack_lsp /usr/local/bin/jack_lsp
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_freewheel' '/usr/local/bin/jack_freewheel'
libtool: install: /usr/bin/install -c .libs/jack_freewheel /usr/local/bin/jack_freewheel
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_evmon' '/usr/local/bin/jack_evmon'
libtool: install: /usr/bin/install -c .libs/jack_evmon /usr/local/bin/jack_evmon
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_alias' '/usr/local/bin/jack_alias'
libtool: install: /usr/bin/install -c .libs/jack_alias /usr/local/bin/jack_alias
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/tools'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/tools'
Making install in config
make[1]: Entering directory `/home/bowditch/.ffado/jack/config'
make[2]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/config'
Making install in man
make[1]: Entering directory `/home/bowditch/.ffado/jack/man'
make  install-am
make[2]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './alsa_in.1' '/usr/local/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/usr/local/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/usr/local/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/usr/local/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/usr/local/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/usr/local/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/usr/local/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/usr/local/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/usr/local/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/usr/local/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/usr/local/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/usr/local/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/usr/local/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/usr/local/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/usr/local/share/man/man1/jack_unload.1'
 /usr/bin/install -c -m 644 './alsa_in.1' '/usr/local/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/usr/local/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/usr/local/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/usr/local/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/usr/local/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/usr/local/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/usr/local/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/usr/local/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/usr/local/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/usr/local/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/usr/local/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/usr/local/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/usr/local/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/usr/local/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/usr/local/share/man/man1/jack_unload.1'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[1]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'jack.pc' '/usr/local/lib/pkgconfig/jack.pc'
make[2]: Leaving directory `/home/bowditch/.ffado/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack'
bowditch@bowditch:~/.ffado/jack$ 

```

jackd --version

```
bowditch@bowditch:~/.ffado/jack$ jackd --version
jackd: error while loading shared libraries: libjackserver.so.0: cannot open shared object file: No such file or directory
bowditch@bowditch:~/.ffado/jack$ 

```

---

### Post by Stochastic on 2009-01-09
Can you post the results of ```
bowditch@bowditch:~/.ffado/jack$ ./jackd/jackd -V
```

EDIT:
If that doesn't return the expected version, you should repeat that last process (building after a make clean) but insert "./configure <any options you want>" after "make clean" and before "make".  If the results differ, please post.

---

### Post by ubustu616 on 2009-01-09
./jackd/jackd -V

```
bowditch@bowditch:~/.ffado/jack$ ./jackd/jackd -V
jackd version 0.116.1 tmpdir /dev/shm protocol 24
bowditch@bowditch:~/.ffado/jack$ 


```

make clean. same result as above.

./configure. not sure if anything changed.

```
bowditch@bowditch:~/.ffado/jack$ ./configure --prefix=/home/bowditch/.ffado/jack 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking whether gcc and cc understand -c and -o together... yes
checking whether byte ordering is bigendian... no
checking platform dependencies... checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking /usr/include/nptl/pthread.h usability... no
checking /usr/include/nptl/pthread.h presence... no
checking for /usr/include/nptl/pthread.h... no
checking for getopt_long... yes
checking for gethostent... yes
checking for setsockopt... yes
checking for connect... yes
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for pthread_create... no
checking for pthread_create in -lpthread... yes
checking for on_exit... yes
checking for atexit... yes
checking for posix_memalign... yes
checking for sin in -lm... yes
Checking for ppoll()... yes
checking for clock_gettime... no
checking for clock_gettime in -lrt... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mlockall... yes
checking shared memory support... System V shmget().
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
checking whether we can compile MMX code... yes
yes
checking whether we can compile SSE code... yes
configure: WARNING: no optimization.........................
checking for pthread_barrier_init in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... no
configure: WARNING: *** the jackrec example client will not be built
checking for SAMPLERATE... no
configure: WARNING: *** the NetJack backend and internal client will not be built
checking for CELT... no
no
configure: WARNING: *** NetJack will not be built with celt support
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking for LIBFREEBOB... no
no
checking for LIBFFADO... yes
checking for ALSA... yes
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking readline/chardefs.h usability... no
checking readline/chardefs.h presence... no
checking for readline/chardefs.h... no
configure: WARNING: *** the jack_transport example client will not be built
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config/Makefile
config.status: creating config/cpu/Makefile
config.status: creating config/cpu/alpha/Makefile
config.status: creating config/cpu/cris/Makefile
config.status: creating config/cpu/generic/Makefile
config.status: creating config/cpu/i386/Makefile
config.status: creating config/cpu/i486/Makefile
config.status: creating config/cpu/ia64/Makefile
config.status: creating config/cpu/m68k/Makefile
config.status: creating config/cpu/mips/Makefile
config.status: creating config/cpu/powerpc/Makefile
config.status: creating config/cpu/s390/Makefile
config.status: creating config/os/Makefile
config.status: creating config/os/generic/Makefile
config.status: creating config/os/gnu-linux/Makefile
config.status: creating config/os/macosx/Makefile
config.status: creating config/sysdeps/Makefile
config.status: creating doc/Makefile
config.status: creating doc/reference.doxygen
config.status: creating drivers/Makefile
config.status: creating drivers/alsa/Makefile
config.status: creating drivers/alsa-midi/Makefile
config.status: creating drivers/dummy/Makefile
config.status: creating drivers/oss/Makefile
config.status: creating drivers/sun/Makefile
config.status: creating drivers/portaudio/Makefile
config.status: creating drivers/coreaudio/Makefile
config.status: creating drivers/freebob/Makefile
config.status: creating drivers/firewire/Makefile
config.status: creating drivers/netjack/Makefile
config.status: creating example-clients/Makefile
config.status: creating tools/Makefile
config.status: creating man/Makefile
config.status: creating jack.pc
config.status: creating jack.spec
config.status: creating jack/Makefile
config.status: creating jack/version.h
config.status: creating jackd/Makefile
config.status: creating jackd/jackd.1
config.status: creating libjack/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

jack-audio-connection-kit 0.116.1 :

| Build with ALSA support............................... : true
| Build with old FireWire (FreeBob) support............. : false
| Build with new FireWire (FFADO) support............... : true
| Build with OSS support................................ : true
| Build with Sun audio support.......................... : false
| Build with CoreAudio support.......................... : false
| Build with PortAudio support.......................... : false
| Build with NetJack support............................ : false
| Build with Celt support............................... : false
| Build with dynamic buffer size support................ : yes
| Compiler optimization flags........................... : -g
| Compiler full flags................................... : -I$(top_srcdir)/config -I$(top_srcdir) -I$(top_srcdir) -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -Wall -g
| Install dir for libjack + backends.................... : ${exec_prefix}/lib/jack
|
| Default driver backend................................ : "alsa"
| Shared memory interface............................... : "System V"
| IPC Temporary directory............................... : /dev/shm
| Install prefix........................................ : /home/bowditch/.ffado/jack
| Default tmp dir....................................... : /dev/shm

bowditch@bowditch:~/.ffado/jack$ 
```

make. seemed the same.

sudo make install.

```
libtool: install: /usr/bin/install -c .libs/libjack.so.0.0.28 /home/bowditch/.ffado/jack/lib/libjack.so.0.0.28
libtool: install: (cd /home/bowditch/.ffado/jack/lib && { ln -s -f libjack.so.0.0.28 libjack.so.0 || { rm -f libjack.so.0 && ln -s libjack.so.0.0.28 libjack.so.0; }; })
libtool: install: (cd /home/bowditch/.ffado/jack/lib && { ln -s -f libjack.so.0.0.28 libjack.so || { rm -f libjack.so && ln -s libjack.so.0.0.28 libjack.so; }; })
libtool: install: /usr/bin/install -c .libs/libjack.lai /home/bowditch/.ffado/jack/lib/libjack.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-exec-hook
make[3]: Entering directory `/home/bowditch/.ffado/jack/libjack'
Removing JACK shared memory registry key  0x282929
ipcrm -M 0x282929
ipcrm: invalid key (0x282929)
make[3]: [install-exec-hook] Error 1 (ignored)
make[3]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/libjack'
Making install in jackd
make[1]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make  install-am
make[2]: Entering directory `/home/bowditch/.ffado/jack/jackd'
make[3]: Entering directory `/home/bowditch/.ffado/jack/jackd'
test -z "/home/bowditch/.ffado/jack/lib" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libjackserver.la' '/home/bowditch/.ffado/jack/lib/libjackserver.la'
libtool: install: /usr/bin/install -c .libs/libjackserver.so.0.0.28 /home/bowditch/.ffado/jack/lib/libjackserver.so.0.0.28
libtool: install: (cd /home/bowditch/.ffado/jack/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so.0 || { rm -f libjackserver.so.0 && ln -s libjackserver.so.0.0.28 libjackserver.so.0; }; })
libtool: install: (cd /home/bowditch/.ffado/jack/lib && { ln -s -f libjackserver.so.0.0.28 libjackserver.so || { rm -f libjackserver.so && ln -s libjackserver.so.0.0.28 libjackserver.so; }; })
libtool: install: /usr/bin/install -c .libs/libjackserver.lai /home/bowditch/.ffado/jack/lib/libjackserver.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/home/bowditch/.ffado/jack/bin" || /bin/mkdir -p "/home/bowditch/.ffado/jack/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jackd' '/home/bowditch/.ffado/jack/bin/jackd'
libtool: install: /usr/bin/install -c .libs/jackd /home/bowditch/.ffado/jack/bin/jackd
make  install-exec-hook
make[4]: Entering directory `/home/bowditch/.ffado/jack/jackd'
Nothing to make for install-exec-hook.
make[4]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
test -z "/home/bowditch/.ffado/jack/share/man/man1" || /bin/mkdir -p "/home/bowditch/.ffado/jack/share/man/man1"
 /usr/bin/install -c -m 644 './jackd.1' '/home/bowditch/.ffado/jack/share/man/man1/jackd.1'
 /usr/bin/install -c -m 644 './jackstart.1' '/home/bowditch/.ffado/jack/share/man/man1/jackstart.1'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/jackd'
Making install in drivers
make[1]: Entering directory `/home/bowditch/.ffado/jack/drivers'
Making install in alsa-midi
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa-midi'
Making install in alsa
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/lib/jack" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_alsa.la' '/home/bowditch/.ffado/jack/lib/jack/jack_alsa.la'
libtool: install: /usr/bin/install -c .libs/jack_alsa.so /home/bowditch/.ffado/jack/lib/jack/jack_alsa.so
libtool: install: /usr/bin/install -c .libs/jack_alsa.lai /home/bowditch/.ffado/jack/lib/jack/jack_alsa.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/alsa'
Making install in dummy
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/lib/jack" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_dummy.la' '/home/bowditch/.ffado/jack/lib/jack/jack_dummy.la'
libtool: install: /usr/bin/install -c .libs/jack_dummy.so /home/bowditch/.ffado/jack/lib/jack/jack_dummy.so
libtool: install: /usr/bin/install -c .libs/jack_dummy.lai /home/bowditch/.ffado/jack/lib/jack/jack_dummy.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/dummy'
Making install in oss
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/oss'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/lib/jack" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_oss.la' '/home/bowditch/.ffado/jack/lib/jack/jack_oss.la'
libtool: install: /usr/bin/install -c .libs/jack_oss.so /home/bowditch/.ffado/jack/lib/jack/jack_oss.so
libtool: install: /usr/bin/install -c .libs/jack_oss.lai /home/bowditch/.ffado/jack/lib/jack/jack_oss.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/oss'
Making install in firewire
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/lib/jack" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_firewire.la' '/home/bowditch/.ffado/jack/lib/jack/jack_firewire.la'
libtool: install: /usr/bin/install -c .libs/jack_firewire.so /home/bowditch/.ffado/jack/lib/jack/jack_firewire.so
libtool: install: /usr/bin/install -c .libs/jack_firewire.lai /home/bowditch/.ffado/jack/lib/jack/jack_firewire.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/firewire'
Making install in netjack
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/lib/jack" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/jack"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'jack_net.la' '/home/bowditch/.ffado/jack/lib/jack/jack_net.la'
libtool: install: /usr/bin/install -c .libs/jack_net.so /home/bowditch/.ffado/jack/lib/jack/jack_net.so
libtool: install: /usr/bin/install -c .libs/jack_net.lai /home/bowditch/.ffado/jack/lib/jack/jack_net.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers/netjack'
make[2]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Entering directory `/home/bowditch/.ffado/jack/drivers'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/drivers'
Making install in example-clients
make[1]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
make[2]: Entering directory `/home/bowditch/.ffado/jack/example-clients'
test -z "/home/bowditch/.ffado/jack/bin" || /bin/mkdir -p "/home/bowditch/.ffado/jack/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_simple_client' '/home/bowditch/.ffado/jack/bin/jack_simple_client'
libtool: install: /usr/bin/install -c .libs/jack_simple_client /home/bowditch/.ffado/jack/bin/jack_simple_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_transport_client' '/home/bowditch/.ffado/jack/bin/jack_transport_client'
libtool: install: /usr/bin/install -c .libs/jack_transport_client /home/bowditch/.ffado/jack/bin/jack_transport_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_impulse_grabber' '/home/bowditch/.ffado/jack/bin/jack_impulse_grabber'
libtool: install: /usr/bin/install -c .libs/jack_impulse_grabber /home/bowditch/.ffado/jack/bin/jack_impulse_grabber
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_metro' '/home/bowditch/.ffado/jack/bin/jack_metro'
libtool: install: /usr/bin/install -c .libs/jack_metro /home/bowditch/.ffado/jack/bin/jack_metro
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_showtime' '/home/bowditch/.ffado/jack/bin/jack_showtime'
libtool: install: /usr/bin/install -c .libs/jack_showtime /home/bowditch/.ffado/jack/bin/jack_showtime
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midisine' '/home/bowditch/.ffado/jack/bin/jack_midisine'
libtool: install: /usr/bin/install -c .libs/jack_midisine /home/bowditch/.ffado/jack/bin/jack_midisine
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_midiseq' '/home/bowditch/.ffado/jack/bin/jack_midiseq'
libtool: install: /usr/bin/install -c .libs/jack_midiseq /home/bowditch/.ffado/jack/bin/jack_midiseq
test -z "/home/bowditch/.ffado/jack/lib/jack" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/jack"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'inprocess.la' '/home/bowditch/.ffado/jack/lib/jack/inprocess.la'
libtool: install: /usr/bin/install -c .libs/inprocess.so /home/bowditch/.ffado/jack/lib/jack/inprocess.so
libtool: install: /usr/bin/install -c .libs/inprocess.lai /home/bowditch/.ffado/jack/lib/jack/inprocess.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'intime.la' '/home/bowditch/.ffado/jack/lib/jack/intime.la'
libtool: install: /usr/bin/install -c .libs/intime.so /home/bowditch/.ffado/jack/lib/jack/intime.so
libtool: install: /usr/bin/install -c .libs/intime.lai /home/bowditch/.ffado/jack/lib/jack/intime.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /home/bowditch/.ffado/jack/lib/jack
----------------------------------------------------------------------
Libraries have been installed in:
   /home/bowditch/.ffado/jack/lib/jack

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/example-clients'
Making install in tools
make[1]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
make[2]: Entering directory `/home/bowditch/.ffado/jack/tools'
Makefile:803: warning: overriding commands for target `dist-check-readline'
Makefile:797: warning: ignoring old commands for target `dist-check-readline'
test -z "/home/bowditch/.ffado/jack/bin" || /bin/mkdir -p "/home/bowditch/.ffado/jack/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_load' '/home/bowditch/.ffado/jack/bin/jack_load'
libtool: install: /usr/bin/install -c .libs/jack_load /home/bowditch/.ffado/jack/bin/jack_load
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_unload' '/home/bowditch/.ffado/jack/bin/jack_unload'
libtool: install: /usr/bin/install -c .libs/jack_unload /home/bowditch/.ffado/jack/bin/jack_unload
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_monitor_client' '/home/bowditch/.ffado/jack/bin/jack_monitor_client'
libtool: install: /usr/bin/install -c .libs/jack_monitor_client /home/bowditch/.ffado/jack/bin/jack_monitor_client
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_connect' '/home/bowditch/.ffado/jack/bin/jack_connect'
libtool: install: /usr/bin/install -c .libs/jack_connect /home/bowditch/.ffado/jack/bin/jack_connect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_disconnect' '/home/bowditch/.ffado/jack/bin/jack_disconnect'
libtool: install: /usr/bin/install -c .libs/jack_disconnect /home/bowditch/.ffado/jack/bin/jack_disconnect
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_lsp' '/home/bowditch/.ffado/jack/bin/jack_lsp'
libtool: install: /usr/bin/install -c .libs/jack_lsp /home/bowditch/.ffado/jack/bin/jack_lsp
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_freewheel' '/home/bowditch/.ffado/jack/bin/jack_freewheel'
libtool: install: /usr/bin/install -c .libs/jack_freewheel /home/bowditch/.ffado/jack/bin/jack_freewheel
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_evmon' '/home/bowditch/.ffado/jack/bin/jack_evmon'
libtool: install: /usr/bin/install -c .libs/jack_evmon /home/bowditch/.ffado/jack/bin/jack_evmon
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'jack_alias' '/home/bowditch/.ffado/jack/bin/jack_alias'
libtool: install: /usr/bin/install -c .libs/jack_alias /home/bowditch/.ffado/jack/bin/jack_alias
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bowditch/.ffado/jack/tools'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/tools'
Making install in config
make[1]: Entering directory `/home/bowditch/.ffado/jack/config'
make[2]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Entering directory `/home/bowditch/.ffado/jack/config'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/config'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/config'
Making install in man
make[1]: Entering directory `/home/bowditch/.ffado/jack/man'
make  install-am
make[2]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Entering directory `/home/bowditch/.ffado/jack/man'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/share/man/man1" || /bin/mkdir -p "/home/bowditch/.ffado/jack/share/man/man1"
 /usr/bin/install -c -m 644 './alsa_in.1' '/home/bowditch/.ffado/jack/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/home/bowditch/.ffado/jack/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/home/bowditch/.ffado/jack/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_unload.1'
 /usr/bin/install -c -m 644 './alsa_in.1' '/home/bowditch/.ffado/jack/share/man/man1/alsa_in.1'
 /usr/bin/install -c -m 644 './alsa_out.1' '/home/bowditch/.ffado/jack/share/man/man1/alsa_out.1'
 /usr/bin/install -c -m 644 './jack_bufsize.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_bufsize.1'
 /usr/bin/install -c -m 644 './jack_connect.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_connect.1'
 /usr/bin/install -c -m 644 './jack_disconnect.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_disconnect.1'
 /usr/bin/install -c -m 644 './jack_freewheel.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_freewheel.1'
 /usr/bin/install -c -m 644 './jack_impulse_grabber.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_impulse_grabber.1'
 /usr/bin/install -c -m 644 './jack_load.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_load.1'
 /usr/bin/install -c -m 644 './jack_lsp.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_lsp.1'
 /usr/bin/install -c -m 644 './jack_metro.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_metro.1'
 /usr/bin/install -c -m 644 './jack_monitor_client.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_monitor_client.1'
 /usr/bin/install -c -m 644 './jackrec.1' '/home/bowditch/.ffado/jack/share/man/man1/jackrec.1'
 /usr/bin/install -c -m 644 './jack_showtime.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_showtime.1'
 /usr/bin/install -c -m 644 './jack_transport.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_transport.1'
 /usr/bin/install -c -m 644 './jack_unload.1' '/home/bowditch/.ffado/jack/share/man/man1/jack_unload.1'
make[3]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[2]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[1]: Leaving directory `/home/bowditch/.ffado/jack/man'
make[1]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Entering directory `/home/bowditch/.ffado/jack'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/bowditch/.ffado/jack/lib/pkgconfig" || /bin/mkdir -p "/home/bowditch/.ffado/jack/lib/pkgconfig"
 /usr/bin/install -c -m 644 'jack.pc' '/home/bowditch/.ffado/jack/lib/pkgconfig/jack.pc'
make[2]: Leaving directory `/home/bowditch/.ffado/jack'
make[1]: Leaving directory `/home/bowditch/.ffado/jack'
bowditch@bowditch:~/.ffado/jack$ 
bowditch@bowditch:~/.ffado/jack$ 

```

it still came out to 

```
bowditch@bowditch:~/.ffado/jack$ ./jackd/jackd -V
jackd version 0.116.1 tmpdir /dev/shm protocol 24
bowditch@bowditch:~/.ffado/jack$ 


```


shoot!

---

### Post by Stochastic on 2009-01-09
Okay, so you've built jack and it is the right version.  The > bowditch@bowditch:~/.ffado/jack$ jackd --version
jackd: error while loading shared libraries: libjackserver.so.0: cannot open shared object file: No such file or directory
error you got was stemming from the jackd executable not being moved to /usr/bin/ (location of global executables) in the installation process, the jackd hidden in the local folder seems to at least be able to tell you it's the right version.  Before we move or link to that executable let's do a test run on it.

Try ```
bowditch@bowditch:~/.ffado/jack$ ./jackd/jackd -d firewire
``` does your audio card work?  Do you get any error messages?

---

### Post by babarosa on 2009-01-09
Hi guys,

"... wow, i really dont know how guys can put up with me ..."
Maybe I should say, how you can put up with my advices.

I was not idle in the meantime, I set up a v8.10 system for testing my advices. But after installing v8.10 rt-kernel, network manager and my umts-modem do not work together at all, the system freezes all the time, it is not usable.
My recommendation finally would have been to set up a v8.04.1 system, I am sure it will work. i also came to the idea to look for an additional installation of jack due to the installation of audio apps (audacity, ...)

To avoid something like "Too many cooks spoil the broth" in the meantime, for the moment I only would like to draw your attention to this site of ffado, maybe it gives additional hints: [http://subversion.ffado.org/wiki/AvoidingParallelInstallations](http://subversion.ffado.org/wiki/AvoidingParallelInstallations) 

Regards, Michael

---

### Post by ubustu616 on 2009-01-11
[http://subversion.ffado.org/wiki/Avo...lInstallations](http://subversion.ffado.org/wiki/Avo...lInstallations) is where i initially started and i am very familiar now with that site. i also already tried to install 8.04.1 but as i mentioned in the previous post, while getting to the partitioner stage, it would not recognize my hard drive disk and and said it could not find the driver. i know that the installation cd i good because i used it before. very strange.

---

### Post by babarosa on 2009-01-12
Hello Ubustu,

a lot of people work with v8.10 and are comfortable with it (the misbehaviour between umts-modem, networkmanager and rt-kernel is a known bug).
Did you accomplish Stochastic's commands? You should do so.
Looking at your console output, to my mind the compilation of ffado seems to be okay.

The ./configure of jack also looks ok to me, but your prefix > ./configure --prefix=**/home/bowditch/.ffado/jack** 
makes me sceptical - my innitial "command" wanted you to do
> ./autogen.sh --**prefix=/usr**
make
sudo make install, thus the installation takes place in 
> **Install prefix........................................ : /home/bowditch/.ffado/jack**

Then libraries are installed to 
> /home/bowditch/.ffado/jack/lib

I expect them to be installed to usr/local/bin or something like that. Maybe that is the reason why the make and make install abort without a result (any further help is appreciated).

I think your system is messed up a lot. I do not want to leave you alone with the problem, nor does the community. Would you mind setting up a completely fresh system of v8.10 including your favorite office applications and the rt-kernel but NO other audio, video and multimedia applications (they eventually install an additional version of jack). 

[COLOR="Red"]Now save your system with "remastersys" ([http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)). Doing so you can try and compile at your hearts content and if the system is messed up again, within appr. 25 minutes you can set up your initial system including all private adjustments for a new try.[/COLOR]

Then we start another try if you are willing to continue exploring. Actually it has to work because a lot of linux users have ffado, jack and qjackctl on v8.10 working very fine. The possibilities using jack as a universal audio router is genious ( a lot of applications wait to be discovered :-({|= )
Again, compilation problems concerning ffado are best reported at ffado-mailing list. Maybe the answer takes some time but Pieter and his team are very helpful and guiding.

Sorry for the troubles and good luck.
Greetings, Michael

---

### Post by babarosa on 2009-01-14
Addendum:
Yesterday I downloaded the most recent versions of ffado 1.999.40, jackd 0.116.1 and qjackctl 0.3.4 and compiled them on my xubuntu 8.04.1 system. It worked/works flawlessly and very stable (I always test with simultaneous recording of 5 tracks at 32bit/44 KHz/latency 7ms/25 minutes - no xruns with my celeron 2GHz notebook).

The self compiled ffado has even a better performance then that one from the repos because the debugging mode is setable to off.

As soon as I finish refurbishing my list of commands I will put it on my website for download, okay?

---

### Post by ubustu616 on 2009-01-14
Okay, so I reinstalled 8.10 and am determined to get it right this time. I got up to installing ffado with scons 

```
bowditch@bowditch:/usr/local/src/libffado-2.0-rc1$ scons
scons: Reading SConscript files ...
Checking for a working C-compiler (cached) yes
Checking for a working C++-compiler (cached) yes
Checking for pkg-config (at least version 0.0.0)... (cached) yes
Checking for C header file expat.h... (cached) yes
Checking for XML_ExpatVersion() in C library expat... (cached) yes
Checking for libraw1394 (1.3.0 or higher)... 	(cached) yes
Checking for dbus-1 (1.0 or higher)... 	(cached) yes
Checking for libxml++-2.6 (2.13.0 or higher)... 	(cached) yes
Checking for libiec61883 (1.1.0 or higher)... 	(cached) yes
Checking for lrint(3.2) in C library m... (cached) yes
Checking for lrintf(3.2) in C library m... (cached) yes
Checking whether 'which pyuic4' executes (cached) no
Checking whether 'which pyuic' executes (cached) no
Checking whether 'xdg-desktop-menu --help' executes (cached) yes

	I couldn't find all the prerequisites ('pyuic' / 'pyuic4' and the python-modules 'dbus' and
	'qt' / 'PyQt4', the packages could be named like dbus-python and PyQt) to build the mixer.
	Therefor neither the qt3 nor the qt4 mixer will get installed.
	
Trying to find the system triple: (cached) i686-pc-linux-gnu
Doing a DEBUG build
Detected DIST_TARGET = i686
Doing a 32-bit build
rm -f /usr/local/bin/ffadomixer
scons: done reading SConscript files.
scons: Building targets ...
scons: `src' is up to date.
scons: `support' is up to date.
scons: `tests' is up to date.
scons: done building targets.
bowditch@bowditch:/usr/local/src/libffado-2.0-rc1$ 

```

i installed every possible package that i could find for the dependencies for the mixer but nothing. any advice?

---

### Post by Stochastic on 2009-01-14
> **ubustu616 said:**
> Okay, so I reinstalled 8.10 and am determined to get it right this time. I got up to installing ffado with scons


WHAT!?!?!????  You had it built locally, why didn't you just try 
```
bowditch@bowditch:~/.ffado/jack$ ./jackd/jackd -d firewire
``` like I had suggested?  It probably would have worked.  What prompted you to reinstall?

---

### Post by babarosa on 2009-01-14
;) Hi ubustu, fine that you are still onboard.

Now it takes place that "too many cooks spoil the broth", doesn't it?

> I couldn't find all the prerequisites ('pyuic' / 'pyuic4' and the python-modules 'dbus' and
	'qt' / 'PyQt4', the packages could be named like dbus-python and PyQt) to build the mixer.
	Therefor neither the qt3 nor the qt4 mixer will get installed.


Before performing scons enter

sudo apt-get build-dep libfreebob

sudo apt-get install scons libiec61883-0 libiec61883-dev libavc1394-0 libavc1394-dev libxml++2.6c2a libxml++2.6-dev liblo0 liblo0-dev docbook-utils libexpat-dev libdbus-1-dev pyqt-tools python-dbus python-qt3

sudo apt-get install libraw1394-8 libraw1394-dev dbus dbus-x11  qt4-designer  qt4-dev-tools  qt4-qtconfig qt3-designer qt3-dev-tools pyqt4-dev-tools python-dbus polymer

Now you should have got everything you need (I hope so)!

Regards, Michael

---

### Post by s2156945 on 2009-01-14
I'm on board too.

I'm not a noob, linux since '96.

I've been using jack at work with a Delta 1010 for an industrial application (road tunnel announcement systems).

The Delta1010 is being phased out, so switching to the nearest linux compatible thing, AudioFire 12.

I've compile jack and installed it over the top of the packaged jackd:

```
woody@audioserver:~$ jackd --version
jackd version 0.116.1 tmpdir /dev/shm protocol 24
```

Also compiles ffado 2.0-rc1 which detects my card:

```
woody@audioserver:/root/downloads/libffado-2.0-rc1/tests$ ./ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.40-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00004c0100003a8d  0x0000004C  0x00000000   Linux - ohci1394  - 
   1       0x0014860ed800ccde  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12
no message buffer overruns
woody@audioserver:/root/downloads/libffado-2.0-rc1/tests$ 
```

I also am part of the audio group which has rw on the raw1394 device:
```
woody@audioserver:/root/downloads/libffado-2.0-rc1/tests$ ls -al /dev/raw1394 
crw-rw---- 1 root audio 171, 0 2009-01-15 11:47 /dev/raw1394
woody@audioserver:/root/downloads/libffado-2.0-rc1/tests$ id
uid=1000(woody) gid=1000(woody) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(woody)
woody@audioserver:/root/downloads/libffado-2.0-rc1/tests$ 

```

ffado-dbus-server runs:
```

26912768957:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
26912774540: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
26912780945: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912786573: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912787923: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912789188: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912790410: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912850083: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912851935: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912853257: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912854588: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912855931: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
26912909475: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
26912910182: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
26912910322: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
26912910386: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
26912910466: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
26912910517: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
26912910666: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
26912911047: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
26912911196: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
26912911264: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
26912911321: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
26912911461: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
26912911656: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
26912911732: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
26912912595: Debug (devicemanager.cpp)[ 594] discover: driver found for device 1
26912913150: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
26912913297: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
26912913360: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
26912913420: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
26912913470: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
26912913523: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
26912913691: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
26912918103: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
26912918134: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
26912918975: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
26912919010: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (1,1,0,0,0)
26912924143: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
26912924174: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (1,1,0,1,0)
26912925491: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
26912926025: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
26912926052: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
26912926099: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
26912926141: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
26912926177: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
26912927084: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912927228: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,0)
26912927832: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
26912927949: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
26912928562: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912928728: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,0)
26912929272: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
26912929399: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
26912929965: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912930082: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,0)
26912930648: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
26912931327: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912931444: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,1)
26912931934: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
26912932784: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912932916: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,2)
26912933536: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
26912933665: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
26912940093: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912940249: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,0)
26912940876: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
26912941783: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
26912941951: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,1)
26912942497: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
26912942616: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
26912943172: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
ESC[0m26912943331: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
26912943838: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
ESC[0m26912944487: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
ESC[0m26912944627: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
26912945214: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
26912945376: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
26912945577: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
26912945660: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
26912945744: ESC[31mWarning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
ESC[0m26912945877: ESC[31mWarning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
ESC[0m26912946017: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
26912946198: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
26912946294: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
26912946347: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
26912946506: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
26912946640: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
26912946752: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
26912946835: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
26912946960: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
26912947065: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
26912947195: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
26912947343: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
26912947405: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
26912947538: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
26912947609: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
26912947655: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
26912947840: ESC[31mError (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
ESC[0m26912947919: ESC[31mError (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
ESC[0m26912947988: ESC[31mError (devicemanager.cpp)[ 606] discover: could not discover device
ESC[0m26912948541: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
26912948811: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
26912948958: Debug (Element.cpp)[ 121] show: Element DeviceManager
26912949166: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
26912949510:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
26912959721:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
26912960053: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
27281266089: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x80916b0...
27281266127: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
27281266149: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
27281291737: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
27281291848: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
27281291912: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
27281291925: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
27281291939: Debug (Element.cpp)[ 121] show: Element DeviceManager
27281291952: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
27281292015: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...
27285708020: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
27285708080: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
27285708096: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
27290728026: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000200, length = 1
27290729138: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x80916b0...
27290729167: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
27290729185: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
27290764123: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
27290770996: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290772267: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290773493: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290774727: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290775956: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290824616: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
27290832636: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290834754: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290836453: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290840785: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290842212: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
27290890512: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
27290890593: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
27290890613: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
27290890631: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
27290890651: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
27290890671: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
27290890690: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
27290890810: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
27290890827: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
27290890848: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
27290890863: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
27290890875: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
27290890886: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
27290890904: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
27290891139: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
27290891277: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
27290891299: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
27290891330: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
27290891345: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
27290891361: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
27290891375: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
27290891398: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
27290893619: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
27290893646: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
27290894067: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
27290894100: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
27290895492: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
27290895517: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
27290897269: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
27290898883: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
27290898959: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
27290898972: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
27290898982: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
27290899038: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
27290901439: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290901500: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
27290902861: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
27290902991: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
27290904705: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290904750: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
27290905463: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
27290905543: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
27290906249: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290906285: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
27290906996: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
27290907722: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290907759: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,1)
27290908519: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
27290909414: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290909466: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,2)
27290910068: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
27290910099: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
27290910722: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290910769: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
27290911185: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
27290911701: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27290911729: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,1)
27290912135: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
27290912160: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
27290912525: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
ESC[0m27290912544: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
27290912985: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
ESC[0m27290913441: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
ESC[0m27290913473: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
27290913960: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
27290914009: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
27290914021: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
27290914033: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
27290914051: ESC[31mWarning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
ESC[0m27290914070: ESC[31mWarning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
ESC[0m27290914102: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
27290914113: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
27290914124: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27290914142: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
27290914151: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
27290914162: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
27290914173: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
27290914200: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27290914212: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
27290914223: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections27290914262: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
27290914272: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
27290914281: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
27290914299: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
27290914318: ESC[31mError (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
ESC[0m27290914328: ESC[31mError (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
ESC[0m27290914341: ESC[31mError (devicemanager.cpp)[ 606] discover: could not discover device
ESC[0m27290914513: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
27290914531: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
27290914543: Debug (Element.cpp)[ 121] show: Element DeviceManager
27290914555: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
27290914619: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...
27295708020: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
27295708060: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
27295708072: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
27356660027: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000200, length = 1
27356661182: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x80916b0...
27356661211: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
27356661228: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
27356693920: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
27356694172: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
27356694237: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
27356694255: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
27356694270: Debug (Element.cpp)[ 121] show: Element DeviceManager
27356694299: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
27356694372: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...
27365708018: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
27365708051: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
27365708063: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
27372478852: Debug (devicemanager.cpp)[ 228] busresetHandler: Bus reset detected on service 0x80916b0...
27372478884: Debug (devicemanager.cpp)[ 230] busresetHandler:  handling busreset...
27372478901: Debug (IsoHandlerManager.cpp)[ 503] handleBusReset: bus reset...
27372517663: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
27372524101: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372525326: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372526567: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372527795: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372529269: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372578096: Debug (ffado-dbus-server.cpp)[ 209] preUpdateHandler: got pre-update notification...
27372584615: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372585826: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372587066: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372588705: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372589947: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
27372643780: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
27372644081: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
27372644107: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
27372644129: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
27372644146: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
27372644182: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
27372644199: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
27372644377: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
27372644399: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
27372644432: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
27372644445: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
27372644459: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
27372644474: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
27372644498: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
27372644738: Debug (devicemanager.cpp)[ 594] discover: driver found for device 1
27372644902: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
27372644928: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
27372644975: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 44818 (0x0000AF12)
27372644993: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
27372645038: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire12
27372645053: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
27372645082: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
27372649600: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
27372649660: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
27372650146: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
 to propagate from, skipping.
27290914233: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
27290914250: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27372650193: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (1,1,0,0,0)
27372651512: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
27372651566: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (1,1,0,1,0)
27372652621: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
27372653276: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
27372653308: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
27372653319: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 3
27372653329: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
27372653356: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
27372653928: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372653969: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,0)
27372654564: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
27372654610: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
27372655203: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372655244: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,0)
27372655731: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
27372655794: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
27372656858: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372656899: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,0)
27372657501: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
27372658063: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372658093: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,1)
27372658569: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
27372659138: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372659183: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,0,2)
27372659926: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
27372659967: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
27372660520: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372660575: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,0)
27372661071: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
27372661719: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
27372661789: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (1,31,255,1,1)
27372662467: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
27372662532: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
27372663116: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'PCR Unknown Output'
ESC[0m27372663167: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
27372663706: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
ESC[0m27372664175: ESC[31mError (avc_plug.cpp)[ 681] getSignalSource: reported signal source plug not found for 'External Unknown Output'
ESC[0m27372664210: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
27372664719: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
27372664793: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
27372664808: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
27372664821: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
27372664846: ESC[31mWarning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
ESC[0m27372664873: ESC[31mWarning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
ESC[0m27372664921: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
27372664933: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
27372664948: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27372664968: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
27372664978: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
27372664989: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
27372665001: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
27372665026: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27372665039: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
27372665052: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27372665061: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
27372665091: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
27372665101: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
27372665114: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
27372665124: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
27372665168: Debug (avc_plug.cpp)[ 722] propagateFromConnectedPlug: No input connections to propagate from, skipping.
27372665190: ESC[31mError (avc_avdevice.cpp)[ 150] discoverGeneric: Unit doesn't have a Music subunit.
ESC[0m27372665201: ESC[31mError (fireworks_device.cpp)[ 144] discover: Could not discover GenericAVC::AvDevice
ESC[0m27372665214: ESC[31mError (devicemanager.cpp)[ 606] discover: could not discover device
ESC[0m27372665445: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
27372665468: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
27372665481: Debug (Element.cpp)[ 121] show: Element DeviceManager
27372665496: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
27372665590: Debug (ffado-dbus-server.cpp)[ 218] postUpdateHandler: got post-update notification...
27375708017: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
27375708049: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
27375708060: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...

```

lots of messages in there, not sure if any of it is bad.

Anyway, jackd can't run with firewire:
```

woody@audioserver:~$ jackd -d firewire
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
03314507704:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Jan 13 2009 15:33:07
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
woody@audioserver:~$ 

```

Any ideas?

oh, ubuntu 8.04.1 fresh install.

NEC PCI firewire card:```

01:02.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [60] Power Management version 2

```

Audiofire12 is new, I haven't firmware updated it or anything.  It does pass through audio from input to output whether it's plugged in or not.

cheers,
Woody

---

### Post by ubustu616 on 2009-01-14
For a while I thought I was the only one out there with an audiofire 12. Thanks s2156945 for joining!

---

### Post by Stochastic on 2009-01-15
s2156945, it will probably be easier to follow the issues here if you start your own thread on the matter and post a link to it here - this will prevent multiple issues from clouding the solutions.  Oh, and could you run jackd with the -v flag for verbose message output?

In general, I should make mention here that this is still beta software, and I don't think anyone has gotten used to reading the ffado-dbus output other than the ffado devs, who can be reached by mailing list or by IRC chat.  They may be the best to help out anyone truly stuck with an unknown error (not someone who re-installs because they're tired of the current troubleshooting path).

---

### Post by ubustu616 on 2009-01-23
here are the results stochtastic. everything is how it was.

```
bowditch@bowditch:/usr/jack$ sudo ./jackd/jackd -d firewire
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
00790834646:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Jan 14 2009 13:06:43
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
bowditch@bowditch:/usr/jack$ 
```

---

### Post by Stochastic on 2009-01-27
hmm, that doesn't say much, could you try it again but with the verbose flag on:  -v

The command should be ```
./jackd/jackd -v -d firewire
```

oh, and you shouldn't need the sudo portion.

Edit, actually, now that khashayar has these packaged for intrepid in his PPA repository, and since you're having so much troubles getting this working, you might want to uninstall ffado and jack by navigating to their respective source directories and doing ```
sudo make uninstall
```
then add his repository - directions and warnings can be found here: [https://launchpad.net/~khashayar/+archive](https://launchpad.net/~khashayar/+archive)
then, install ffado and jack, and remove his repository from your sources.

---

### Post by babarosa on 2009-02-26
Hi ubustu616!

Would you mind telling me/us if you finally succeeded?
I still have it on my duties list to guide you through the compiling process [-o<

Regards,
Michael

---

### Post by gilli4 on 2009-11-12
Hi all,
while having googled for the problems that occour during the jack installation, I stumble on this page.

I'm on Ubuntu Jaunty, having a Terratec Phase X24 FW.
The reason why I don't want to use the served packages, is because they either seem too old (wrong/no support for my hardware mixer) and because the newer ones might have some improvements performance wise, because I'm having trouble with it.

Before attempting to compile everything on my own, I even tried to use the packages from Khashayar's repo. But they are also only from Feb09 (mostly) and they cause some dependency problems (libffado2 vs. libffado0) while I'm trying to install them.

So I decided to only compile and install libffado and use the given jack with it. This won't work, because jack always comes along with its own libffado, which is an older version.

So, bottom line, I'm stuck installing jack 0.116.2 because:
```

/bin/bash: /home/gilzad/install/jack: No such file or directory
make[2]: *** [install-libLTLIBRARIES] Fehler 127
make[2]: Verlasse Verzeichnis '/home/gilzad/install/jack stuff/jack-audio-connection-kit/libjack'
make[1]: *** [install-am] Fehler 2
make[1]: Verlasse Verzeichnis '/home/gilzad/install/jack stuff/jack-audio-connection-kit/libjack'
make: *** [install-recursive] Fehler 1

```

In my German distro the word "Fehler" means "error".

The strangest thing is the very first line of my pasting. Why does make complain that my installation dir is not existing? It's the directory where the clone of the branch lays in.

Before I ran "make install", I cared about autogen.sh's hints, then I ran ./configure which went well and even compiling would only say that there's nothing to do for "install-exec-am". Only the installation fails.

Can anyone help? Thanks in advance.

Gilzad

---

### Post by babarosa on 2009-11-13
Hi Gilzad,

I sent you a PN, we will do the compiling of ffado, jackd and qjackctl in german language, okay?

I participate in this forum very little anymore.

Greetings, Michael

---

### Post by AutoStatic on 2009-11-13
> **gilli4 said:**
> I'm on Ubuntu Jaunty, having a Terratec Phase X24 FW.
The reason why I don't want to use the served packages, is because they either seem too old (wrong/no support for my hardware mixer) and because the newer ones might have some improvements performance wise, because I'm having trouble with it.AFAIK you don't need to compile anything. The TerraTec Phase24 seems to be fully supported by the FFADO drivers that come with Jaunty: [http://www.ffado.org/?q=node/42](http://www.ffado.org/?q=node/42)

---

### Post by gilli4 on 2009-11-13
> **AutoStatic said:**
> AFAIK you don't need to compile anything. The TerraTec Phase24 seems to be fully supported by the FFADO drivers that come with Jaunty: [http://www.ffado.org/?q=node/42](http://www.ffado.org/?q=node/42)

Thank you AutoStatic,
yes, I can confirm that the Phase x24 FW does work with the supplied drivers of Jaunty. But I can't confirm that it's "fully" supported because with ffado I had a lot of xruns and I would not be able to compensate them by increasing the buffer, since any buffer size greater than 256 would make the driver crash. With the freebob backend, I could run the card without xruns at least (2 periods, buffer size of 1024), but the latency is just not sufficient for making music and the hardware mixer is not working. For the second version they state that a _[separate mixer for Phase X24 and Phase 24]("http://www.ffado.org/?q=release/rc2")_ is implemented, which might solve the _[problem of the hardware mixer that seemed to be not supported earlier]("http://www.ffado.org/?q=node/43#comment-12")_.

---

### Post by AutoStatic on 2009-11-13
On Jaunty:
```
aptitude show libffado0
Package: libffado0
State: installed
Automatically installed: yes
Version: 2.0~rc1-0ubuntu2
Priority: optional
Section: universe/libs
Maintainer: Ubuntu Studio Devel Team <ubuntu-studio-devel@lists.ubuntu.com>
Uncompressed Size: 2728k
Depends: libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1),
         libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.18.0), libiec61883-0
         (>= 1.1.0), libraw1394-8, libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>=
         4.1.1), libxml++2.6-2 (>= 2.24.0), libxml2 (>= 2.6.27)
Description: FFADO API
 FFADO is a Linux driver for FireWire (IEEE1394) audio devices. 
 
 The FFADO library permits discovering and configuring such devices and provides
 an API for streaming clients. 
 
 This package holds the shared library.
Homepage: http://www.ffado.org
```

So the separate mixer should be implemented and the Phase24 should be fully supported.

---

### Post by gilli4 on 2009-11-13
Thank you once again, AutoStatic,

you're right, I just checked it myself and the version offered in the Jaunty repo is 2.0rc1 . I thought I had verified the version by the output I got when I called *jackd -dfirewire*, which was a mistake.

However, the xrun problem remains, and for RC2 they state that there's less CPU usage. So maybe I'll have a better performance if I stick to compile and install the newest version. Good to know that I can still fall back on your suggestion.

---

### Post by gilli4 on 2009-11-16
Before I send some official thanks to babarosa for helping me compiling and installing jackd & ffado the right way, I will write down what made me have XRUNS each 6 seconds and how to solve this:

Short version: I had to unload the following drivers:
```

#rmmod [_dcdbas_]("http://www.mjmwired.net/kernel/Documentation/dcdbas.txt")
#rmmod [_bridge_]("http://tldp.org/HOWTO/BRIDGE-STP-HOWTO/what-is-a-bridge.html")
#rmmod [_stp_]("http://tldp.org/HOWTO/BRIDGE-STP-HOWTO/what-is-a-bridge.html")

```

On my RT-Kernel it was enough to unload and blacklist [SIZE="3"][FONT="Courier New"]dcdbas[/FONT][/SIZE].

Long version:
If you have periodic XRUNs, then it's mostly a thread to blame for it. Thus it's a good idea to kill processes. The idea, that it could be a driver, came from [_here_]("http://www.mail-archive.com/ubuntu-studio-users@lists.ubuntu.com/msg03954.html").


1) To find out which driver causes the XRUNs, one can load jackd with safe parameters that would show the xruns appearing regularly. In my case this would be:
```

$jackd -v -R -d firewire -p128 -n4

```

2) Then, on another terminal, you have to log in as **root** and list the loaded modules to determine which ones you might want to unload:
```

#lsmod

```

3) Now you unload the suspicious driver:
```

#rmmod <driver name determined in step 2>

```

4) Afterwards you'll have a look in the terminal, where jack is running, to see whether the XRUNs still occur. Repeat steps 2-4 until the xruns disappear.

As a side note: We should be careful unloading drivers we don't know, since we're messing with the kernel space here. Also some devices might stop working, because - well - we're unloading their drivers.




**Sorting out the last XRUNs**

If you occasionally get dropouts with this output from jackd without a sign of a high CPU load:
```

ProcessAsync: read error, skip cycle firewire

```

..then you'll have to change the group of your choice to [SIZE="3"][FONT="Courier New"]disk[/FONT][/SIZE] (instead of [SIZE="3"][FONT="Courier New"]audio[/FONT][/SIZE] or [FONT="Courier New"][SIZE="3"]video[/SIZE][/FONT]).

I learned this from [_here_]("http://www.64studio.com/node/1124#comment-5302") when I searched for the mentioned error message.
Even though the discussion over there is related to the 64bit version, I can state that it does solve the problem on my 32bit version of Ubuntu Studio as well.

On _[this page]("http://www.g-raffa.eu/Cinelerra/HOWTO/troubleshooting.html")_ I found out that on Jaunty the file for the udev rules is [SIZE="3"][FONT="Courier New"]/lib/udev/rules.d/50-udev-default.rules[/FONT][/SIZE], where you have to add [SIZE="3"][FONT="Courier New"]KERNEL=="raw1394", GROUP="disk"[/FONT][/SIZE] to the [SIZE="3"][FONT="Courier New"]#firewire[/FONT][/SIZE] section.
Do not create a file in [SIZE="3"][FONT="Courier New"]/etc/udev/rules.d/[/FONT][/SIZE] for this purpose, if you're on Jaunty.


Best luck,

Gilzad

---

### Post by jukingeo on 2010-03-31
re: Ubuntu Studio FFADO support for Hardy Herron (8.04). Prospective device: Focusrite Sapphire LE (not yet purchased).

Hello all,

It has been a bit since I been here in the Ubuntu forums because just prior to the holidays I did something 'stupid' in Ubuntu and it damaged the install and I had to reinstall it.  I had projects to do prior to the holidays, so I didn't get Ubuntu back on my system until last month.

Now that I am back, I am curious if there has been updates to Hardy (8.04) that would allow FFADO to be used without too much 'hoop jumping'.  When I first started with Ubuntu Studio a couple years ago, it was set up with FreeBob for firewire support.  I know that FFADO has replaced that now, but I wasn't sure if through the massive amounts of updates that I received when I reinstalled Ubuntu Studio that perhaps I have 'less' to do to properly set up FFADO.  So that is why I am posting back here.

My main goal with FFADO is so that I can set up a 'canned' system in which I could use the Focusrite Sapphire LE on just about any system that has a firewire port.

My preference is to use firewire over USB because of the major problems with USB sound in Linux.  It seems as if firewire hardware is much easier to set up reliably in Linux.

Thanx,

Geo

---

### Post by AutoStatic on 2010-04-01
Hello Geo, it should be possible, either with a self compiled version of FFADO or the one from [Khashayar's PPA]("https://launchpad.net/~khashayar/+archive/ppa"). But I would personally recommend to opt for Karmic 9.10.

---

### Post by jukingeo on 2010-04-02
> **AutoStatic said:**
> Hello Geo, it should be possible, either with a self compiled version of FFADO or the one from [Khashayar's PPA]("https://launchpad.net/~khashayar/+archive/ppa"). But I would personally recommend to opt for Karmic 9.10.

The reason for my staying with 8.04 is the long term support.   Also 9.10 is still quite new and generally the new release of Ubuntu is always unstable.   Remember, I have Ubuntu STUDIO and not regular Ubuntu.   It is just with all the hardware configuring to do, I would rather stick with a more stable OS.  8.04 has been out for a while and it has the long term support, so I would like to stick with it.

Thanx,

Geo

---

### Post by Scott L on 2010-04-03
> **jukingeo said:**
> The reason for my staying with 8.04 is the long term support.   Also 9.10 is still quite new and generally the new release of Ubuntu is always unstable.   Remember, I have Ubuntu STUDIO and not regular Ubuntu.   It is just with all the hardware configuring to do, I would rather stick with a more stable OS.  8.04 has been out for a while and it has the long term support, so I would like to stick with it.

Thanx,

Geo


Hmm.  I don't know that I would call Ubuntu Studio 9.10 Karmic Koala "new" still.

Also, I believe that Ubuntu Studio Karmic has received several compliments for its stability and -rt kernel.  All in all, it was a rather successful release in my opinion.  Several advances in that release.

However, I too have kept a 8.04 Hardy partition for recording purposes.  In [my PPA]("https://launchpad.net/%7Eslavender/+archive/ppa") you will find the following built for Hardy:

[LIST]
[*]libffado-2.0~rc1
[*]JACK-0.116-1 (built with ffado)
[*]Ardour-2.8.2
[/LIST]
I also have built lv2core-3.0 for Hardy and I _think_ Ardour-2.8.2 was built with LV2 support but I cannot presently remember.

In less than a month we can also expect 10.04 Lucid to be released, which is also a LTS version.  And already it is stacking up to be another excellent release.  Many advances and improvements in this one also.

Cheers

---

### Post by jukingeo on 2010-04-03
> **Scott L said:**
> 

In less than a month we can also expect 10.04 Lucid to be released, which is also a LTS version.  And already it is stacking up to be another excellent release.  Many advances and improvements in this one also.

Cheers

I probably will hold out for that one.  I am hoping they are going to FINALLY fix the "no sound on resume" glitch when you computer resumes after suspend/hibernate.  That seems to be a huge problem that goes all the way back to 6:10.

Well, I am hoping that Lucid will be stable.   I really have not been able to operate Ubuntu Studio the way I like because of the hardware support.  While I do have a card that is operating fine, I would like something that is more readily transferred from machine to machine.  In Linux the best thing for that is a firewire sound card.   But sadly my system still has the Freebob default.   I know there is a way to get FFADO on my system, but I think it involves using a different version of Jack and it needs to be 'built' with the FFADO support.    While I am willing to go through with it, I am wondering too if I should just wait it out for the next Long Term Release of Ubuntu.

Do you know when the expected release date is?

Thank You,

Geo

---

### Post by trulan on 2010-04-03
Lucid release schedule:
[http://ubuntuforums.org/showthread.php?t=1304172](http://ubuntuforums.org/showthread.php?t=1304172)

---

### Post by babarosa on 2010-04-04
Jukingeo,

I used to compile the latest versions of FFADO, jackd and QJackCtl on my v8.04 Xubuntu system, which performed rock solid. I can help you out if you do not want to wait for v10.04 plus one month for reaching stability.

Since v9.10 came with a new intel graphic cards driver, I additionally can use my vst plugins, which was not possible with v8.04 because of gfx-3D-issues. Karmic Koala is in my mind a very stable and fine working version.

Regards,
Michael

---

### Post by jukingeo on 2010-04-05
> **babarosa said:**
> Jukingeo,

I used to compile the latest versions of FFADO, jackd and QJackCtl on my v8.04 Xubuntu system, which performed rock solid. I can help you out if you do not want to wait for v10.04 plus one month for reaching stability.

Most certainly.  I would appreciate that.  While I WILL upgrade to 10.04, I probably will do so on a different machine and keep the 8.04 system intact.  I had SOME scary experiences with 8.04 when it first came out.  Now I find it hard to part with especially since it has the long term support.  So I didn't feel the need to upgrade at this time.

> 
Since v9.10 came with a new intel graphic cards driver, I additionally can use my vst plugins, which was not possible with v8.04 because of gfx-3D-issues.

Yes, I have noticed the 3d/OpenGL issues with ATI are considerable.  As of yet, I cannot really play any games in Ubuntu, some of my applications are affected as well, for instance, my graphic displays in Mixxx do not work.  MAME doesn't work either.  The proprietary drivers cause system lockups and trying to rework X11 yeilds only marginal improvements.

I had much better success with Nvidia graphics cards.  So now with the newer versions of Ubuntu they finally addressed the graphic card issue with ATI?

> 
[/B] Karmic Koala is in my mind a very stable and fine working version.

Regards,
Michael

To be honest with you, if I had a 'regular' system, I would probably go for it, but I don't.  I have a studio based set up and it was VERY hard to get it running under Linux in the first place.  Then I do something stupid and whacked my Linux partition.  While I have it back, it still isn't 100%  But yeah if you could help me get my Jack working again with FFADO, that would be great.

Thank You,

Geo

---

### Post by babarosa on 2010-04-05
Geo,

I sent you a private message.

---

### Post by Saftpackl on 2010-04-06
Hello people =)

I bought a Terratec Phase X24, because ffado called it to be "fully supported".
If I try to connect jack (using qjackctl), theres an error:

```
18:53:30.272 Startup script...
18:53:30.273 artsshell -q terminate
sh: artsshell: not found
18:53:30.675 Startup script terminated mit Rückgabewert = 32512.
18:53:30.675 JACK startet...
18:53:30.675 /usr/bin/jackd -R -P70 -dfirewire -dhw:3,0 -r44100 -p128 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 407754480, from thread 407754480] (1: Operation not permitted)
cannot create engine
18:53:30.691 JACK wurde mit PID = 4278 gestartet.
18:53:30.717 JACK wurde angehalten erfolgreich.
18:53:30.717 Post-shutdown script...
18:53:30.717 killall jackd
jackd: no process found
18:53:31.126 Post-shutdown script terminated mit Rückgabewert = 256.
18:53:33.839 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Overall operation failed. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.
```

The last paragraph means something like:"As Client, theres no connection possible to Jack server."

Also, if I try to open the "ffado-mixer" for the phase x24, there's this error:

```
ERROR:main:===========================================================
ERROR:main:ERROR: Could not communicate with the FFADO DBus service...
ERROR:main:===========================================================

```

I'm using Ubuntu Studio 9.10 (64bit) and followed this guide:
[https://help.ubuntu.com/community/FireWire]("https://help.ubuntu.com/community/FireWire")

I don't know whats wrong, hope you can help me. =)

thanks in advance!

[B]EDIT: The mixer is working now, after restarting I plugged out the firewire and replugged it and the mixer recognized it. Jack still isn't starting..

EDIT2: I tried running "sudo qjackctl" and it worked without any problems... strange, because my user is in audio, video and disk group 
Also, I have to replugg the audio interface everytime I reboot o.O

Any Ideas? :D[/B]

---

### Post by trulan on 2010-04-06
> **Saftpackl said:**
> 
```
cannot use real-time scheduling (FIFO at priority 10) [for thread 407754480, from thread 407754480] (1: Operation not permitted)
```[B]
EDIT2: I tried running "sudo qjackctl" and it worked without any problems... [/B]
So it's definitely a permissions problem.  What does your /etc/security/limits.conf look like?  Look for lines referring to audio and rtprio.  You could post the entire file here if you want to.  Here's the relevant lines from mine:
```
@audio - rtprio 90
@audio - memlock unlimited
```

---

### Post by Saftpackl on 2010-04-16
> **trulan said:**
> So it's definitely a permissions problem.  What does your /etc/security/limits.conf look like?  Look for lines referring to audio and rtprio.  You could post the entire file here if you want to.  Here's the relevant lines from mine:
```
@audio - rtprio 90
@audio - memlock unlimited
```

hi!

here's my limits.conf:
```
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4




@audio - memlock unlimited
@audio - rtprio 90

# End of file
```

I added the "@audio - rtprio 90" and "@audio - memlock unlimited", before there only was something like "@audio - memlock [number]", but still no luck

I found out that i don't have a file like "/etc/udev/permissions.rules" or "/etc/udev/rules.d/40-permissions.rules", i got udev, but in ../rules.d/ there's only "70-persistent-cd.rules" and "70-persistent-net.rules" o.O
I thought that udev got some standard rules for most of the devices

---

### Post by AutoStatic on 2010-04-16
The udev rule is needed so you have access to the raw1394 device node as a normal user. Did you create it already? And did you add the raw1394 module to the */etc/modules* file?

---

### Post by Saftpackl on 2010-04-16
> **AutoStatic said:**
> The udev rule is needed so you have access to the raw1394 device node as a normal user. Did you create it already? And did you add the raw1394 module to the */etc/modules* file?

No, I'm not sure where i shall create it now, because there is no file atm

raw1394 is in /etc/modules, i think ubuntu studio put it there, because theres some "gui" thing that should help you getting your fw-device running as fast as possible :P

So, should I create a new /etc/udev/permissions.rules and put something there?

EDIT: YEAH, I got it running now =) Thanks for your help!
I created a new udev rule in /etc/udev/rules.d/ and set audio-permissions to the /dev/raw1394
**See [this guide!!]("http://www.christeck.de/wp/2009/08/01/running-a-firewire-audio-device-on-linux/") =)**

---

### Post by AutoStatic on 2010-04-16
> **Saftpackl said:**
> So, should I create a new /etc/udev/permissions.rules and put something there?Yes, but it's better to name it *40-permissions.rules* otherwise udev won't load it.

---

### Post by Saftpackl on 2010-04-17
Yes, I named it like that
Thanks for the tip! =)

---

