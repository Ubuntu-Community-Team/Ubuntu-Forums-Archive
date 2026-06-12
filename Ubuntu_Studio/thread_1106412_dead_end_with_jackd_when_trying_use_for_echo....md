---
title: "dead end with jackd when trying use for echo..."
date: 2009-03-25
forum: Ubuntu Studio
---

### Post by mordrax on 2009-03-25
Hello, I am new with Linux, however tryed pretty long time (few weeks) to start my audiofire echo 2 soundcard with linux and read so many guides and supports on internet, that learned quite lot about (in my subjective angle of view, so not too much probably !)) But from any dead ends before I was able to get out, but now it looks no way further, becouse I tryied everything several time again, delete several time and install from symantec, install by myself and still same problem on the end, everything looks working well (ffado, ffado-dbus-server) or not to different from other outputs I have seen here, but on the end everytime this:


kotanyiii@kotanyiii-laptop:~$ jackd -d firewire
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
03318244096:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Jan 22 2009 12:30:31
firewire ERR: Could not prepare streaming device!
cannot load driver module firewire
no message buffer overruns
kotanyiii@kotanyiii-laptop:~$

---

### Post by mordrax on 2009-03-25
Maybe I should say, that firewire looks ok, because ffado already recognised the sound card and is in the same group as me. I have the latest versions of everything, but tried even with older versions of jack and I compiled it by myself as well. That can be maybe problem, that was left some piece of old software/library, which was not probably deleted, although I tried to do as possible (uninstall, delete). But this last version of ffado and jackd I installed with symantec from ppa source. My firewire device is ieee1394 and I installed the latest ubuntu just month ago... thnx for any help...

---

### Post by josephhitt on 2009-05-24
Same problem here, but using a MOTU 828mkII.

I try ffado out every few months, it's getting closer but still not there (at least I don't have to compile it from source any more, I gave up on that due to the dependencies and lack of time to spend tinkering with it)...

At this point I think the problems are mainly distro/packaging/security setup problems.  For example, Ubuntu does not setup correct permissions to the raw firewire device, nor to allow jackd to run.   (this was with fresh install of Jaunty 9.04).

I haven't tried sifting through ffado.cpp, but I'm guessing maybe the raw driver doesn't like my hardware...?  I'm using the card on-board my intel dg45id motherboard.  I have another firewire pci card I could try though...maybe if I get some time I can do that later.

```

sudo jackd -d firewire -r48000

no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
71210048843:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
firewire ERR: Could not prepare streaming device!
cannot load driver module firewire
no message buffer overruns
```

---

### Post by dawiba on 2009-05-24
I don't know if you've looked already, but [this page](http://subversion.ffado.org/wiki/InstallingFfadoFromSource) got me up and running with a Focusrite Saffire LE.

It also offers links to some troubleshooting guides.

---

### Post by Stochastic on 2009-05-24
To get past this error I had to do the following steps:
-install ubuntustudio-controls (sudo apt-get install ubuntustudio-controls)
-open ubuntustudio-controls (System->Administration->Ubuntu Studio Controls)
-check the "enable raw1394" box
-click apply
-click close
-reboot

I did have ubuntustudio-audio package installed too, which has the ffado drivers from the Ubuntu Universe repository.  So you may also need to install ffado-dbus-server ffado-mixer-qt4 and ffado-tools.


If you've done this and are still having troubles, try posting the output of these commands```
grep -H -n raw1394 /lib/udev/rules.d/*
grep -H -n raw1394 /etc/udev/rules.d/*
grep -H -n raw1394 /etc/modules
modprobe -l raw1394
```

---

### Post by dmike on 2009-06-08
I was getting this same error message with my Edirol FA-66. ffado saw the device, the group permissions were set properly, but still I got the message "cannot load driver module firewire."

I was about to give up when I noticed something potentially relevant: jack was set (by default) to a 44.1k sample rate, but the FA-66 was set (via a hardware switch) to 48k. Eureka! I set jack to use 48k and everything works perfectly now.

So if you have similar problems, double-check *all* of your interface settings. Apparently there are minor settings issues that can generate this kind of vague error message.

---

### Post by thorgal on 2009-06-09
this kind of vague message sucks. If you had a sample rate mismatch, then it should spit out a relevant message so you don't have to spend days in fiddling around with irrelevant things. Something the devs should think about ...

---

### Post by mordrax on 2009-10-04
So did anyone get further, I tried again after some time with Jaunty Ubuntu now, where ffado is already part of it and got again to the same point. But problem will be probably somewhere in ffado or with firewire not with jack, because jackd write the same message no matter if firewire is on or off. 

This is what write ffado-dbus-server:

kotanyiii@kotanyiii-laptop:~$ ffado-dbus-server &
[1] 6420
kotanyiii@kotanyiii-laptop:~$ -----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.40-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

01452856126:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
01452876434: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
01452883614: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452884839: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452886065: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452887378: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452888662: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452947767: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452949072: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452950370: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452951697: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01452952989: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
01453005422: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01453005476: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
01453005489: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 2802 (0x00000AF2)
01453005500: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
01453005527: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire2
01453005538: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
01453005548: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
01453005625: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01453005650: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
01453005661: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 2802 (0x00000AF2)
01453005672: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
01453005681: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire2
01453005696: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
01453005706: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
01453005941: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
01453006030: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01453006054: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 5254 (0x00001486)
01453006065: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 2802 (0x00000AF2)
01453006075: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Echo
01453006084: Debug (Configuration.cpp)[ 208] showSetting:     modelname = AudioFire2
01453006100: Debug (Configuration.cpp)[ 184] showSetting:     driver = 2 (0x00000002)
01453006110: Debug (Configuration.cpp)[ 208] showSetting:     mixer = AudioFireMixer
01453007595: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
01453007682: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
01453008138: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
01453008228: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
01453008925: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
01453009015: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
01453009687: Debug (avc_musicsubunit.cpp)[  64] discover: Discovering MusicSubunit...
01453009772: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
01453010633: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453010719: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,0,0)
01453011145: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453011233: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,12,0,0,0)
01453012087: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453012176: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,0,1)
01453012590: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453012679: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,12,0,0,1)
01453013544: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453013632: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,0,2)
01453014047: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453014135: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,12,0,0,2)
01453014996: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453017052: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,0,3)
01453021959: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453022005: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,1,0)
01453022359: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453022400: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,12,0,1,0)
01453023235: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453023274: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,1,1)
01453023612: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453023653: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,12,0,1,1)
01453024493: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453024532: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,1,2)
01453024879: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453024919: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,12,0,1,2)
01453025753: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block
01453025792: Debug (avc_plug.cpp)[ 181] discover: discover: Could not init plug from descriptor (0,12,0,1,3)
01453026389: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
01453026680: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
01453026719: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
01453026746: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 4
01453026770: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
01453026794: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
01453027159: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453027194: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
01453027533: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
01453027567: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
01453027932: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453027967: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
01453028296: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
01453028332: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
01453028740: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453028776: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,0)
01453029103: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01453029488: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453029531: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,1)
01453029801: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01453030162: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453030191: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,0,2)
01453030532: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01453031145: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
01453031172: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
01453031509: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453031556: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,0)
01453031840: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
01453032194: Debug (avc_plug.cpp)[ 373] discoverStreamFormat: No matching cluster info found for index 1
01453032224: Debug (avc_plug.cpp)[ 234] discover: Could not discover stream format (0,31,255,1,1)
01453032557: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
01453032586: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
01453032896: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
01453033457: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
01453033770: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
01453034928: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
01453034958: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
01453034981: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
01453035011: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
01453035038: Warning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
01453035064: Warning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found
01453035099: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
01453035130: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
01453035157: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
01453035181: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
01453035204: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01453035238: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01453035262: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01453035283: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
01453035307: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
01453035336: Debug (avc_plug.cpp)[ 734] propagateFromConnectedPlug: No output connections to propagate from, skipping.
01453035359: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
01453035382: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
01453094686: Debug (devicemanager.cpp)[ 631] discover: discovery of node 0 on port 0 done...
01453094753: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
01453094818: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
01453094846: Debug (Element.cpp)[ 121] show: Element DeviceManager
01453094869: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
01453094952: Debug (devicemanager.cpp)[1105] showDeviceInfo: --- Device  0 ---
01453094983: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01453095005: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01453095026: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01453095048: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000002
01453095076: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000000
01453095097: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000000
01453095119: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01453095141: Debug (efc_cmds_hardware.cpp)[ 127] showEfcCmd: EFC HW CAPS info:
01453095169: Debug (efc_cmds_hardware.cpp)[ 128] showEfcCmd:  Flags   : 0x00000021
01453095191: Debug (efc_cmds_hardware.cpp)[ 129] showEfcCmd:  GUID    : 0014860269E1F10E
01453095213: Debug (efc_cmds_hardware.cpp)[ 130] showEfcCmd:  HwType  : 0x00000AF2
01453095236: Debug (efc_cmds_hardware.cpp)[ 131] showEfcCmd:  Version : 0
01453095264: Debug (efc_cmds_hardware.cpp)[ 132] showEfcCmd:  Vendor  : Echo Digital Audio
01453095286: Debug (efc_cmds_hardware.cpp)[ 133] showEfcCmd:  Model   : AudioFire2
01453095307: Debug (efc_cmds_hardware.cpp)[ 135] showEfcCmd:  Supported Clocks   : 0x00000009
01453095329: Debug (efc_cmds_hardware.cpp)[ 136] showEfcCmd:  # 1394 Playback    : 6
01453095357: Debug (efc_cmds_hardware.cpp)[ 137] showEfcCmd:  # 1394 Record      : 4
01453095378: Debug (efc_cmds_hardware.cpp)[ 138] showEfcCmd:  # Physical out     : 6
01453095399: Debug (efc_cmds_hardware.cpp)[ 139] showEfcCmd:  # Physical in      : 4
01453095420: Debug (efc_cmds_hardware.cpp)[ 142] showEfcCmd:  # Output Groups    : 3
01453095452: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 0: Type 0x00, count 2
01453095474: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 1: Type 0x05, count 2
01453095496: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 2: Type 0x01, count 2
01453095518: Debug (efc_cmds_hardware.cpp)[ 147] showEfcCmd:  # Input Groups     : 2
01453095546: Debug (efc_cmds_hardware.cpp)[ 150] showEfcCmd:      Group 0: Type 0x00, count 2
01453095568: Debug (efc_cmds_hardware.cpp)[ 150] showEfcCmd:      Group 1: Type 0x01, count 2
01453095591: Debug (efc_cmds_hardware.cpp)[ 152] showEfcCmd:  # Midi out         : 1
01453095612: Debug (efc_cmds_hardware.cpp)[ 153] showEfcCmd:  # Midi in          : 1
01453095639: Debug (efc_cmds_hardware.cpp)[ 154] showEfcCmd:  Max Sample Rate    : 96000
01453095661: Debug (efc_cmds_hardware.cpp)[ 155] showEfcCmd:  Min Sample Rate    : 32000
01453095682: Debug (efc_cmds_hardware.cpp)[ 156] showEfcCmd:  DSP version        : 0x00000000
01453095703: Debug (efc_cmds_hardware.cpp)[ 157] showEfcCmd:  ARM version        : 0x04010000
01453095732: Debug (efc_cmds_hardware.cpp)[ 158] showEfcCmd:  # Mix play chann.  : 6
01453095753: Debug (efc_cmds_hardware.cpp)[ 159] showEfcCmd:  # Mix rec chann.   : 4
01453095783: Debug (ffadodevice.cpp)[ 224] showDevice: Attached to port.......: 0 (ohci1394)
01453095807: Debug (ffadodevice.cpp)[ 225] showDevice: Node...................: 0
01453095836: Debug (ffadodevice.cpp)[ 227] showDevice: Vendor name............: Echo Digital Audio
01453095858: Debug (ffadodevice.cpp)[ 229] showDevice: Model name.............: AudioFire2
01453095885: Debug (ffadodevice.cpp)[ 231] showDevice: GUID...................: 0014860269e1f10e
01453095913: Debug (ffadodevice.cpp)[ 236] showDevice: Assigned ID....: dev0
01453095946: Debug (devicemanager.cpp)[1108] showDeviceInfo: Clock sync sources:
01453096305: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01453096314: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01453096321: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01453096336: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000072
01453096344: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01453096350: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01453096357: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01453096370: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01453096377: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 0
01453096384: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 44100
01453096391: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 4294967295
01453097547: Debug (devicemanager.cpp)[1117] showDeviceInfo:  Type: Internal          , Id:  0, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal sync
01453097561: Debug (devicemanager.cpp)[1117] showDeviceInfo:  Type: SPDIF             , Id:  3, Valid: 0, Active: 0, Locked 1, Slipping: 0, Description: SPDIF
01453097603:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
01453168976:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
01453169035: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...

just in case someone see in it something, there are few sentences red in original

these:
01453010633: Error (avc_musicsubunit.cpp)[  91] initPlugFromDescriptor: Could not find plug info block

and

these two:
01453035038: Warning (avc_unit.cpp)[ 704] discoverSyncModes: No sync input plug for MSU subunit found
01453035064: Warning (avc_unit.cpp)[ 716] discoverSyncModes: No sync output plug for MSU subunit found

thx

th

---

### Post by mordrax on 2009-10-04
Just to add, that ffado mixer appears without problem and when I disconnect card immediately disappears, so there is some communication. So actually last thing what I was thinking was that I have some problem with that real time scheduling. I tried to set it according all the guides I found and than even experiment in qtjack quite lot, but true is that I dont understand fully how I know that it is set and work ok...

thx for any help. I really tried and google everything and my girlfriend thinks now, that I am some mad computer freak that is living just for his computer :)  but I just want to do some music, because my graphic cards is not working in windows, so can work just in linux and have to wait maybe two month for new computer...

---

### Post by mordrax on 2009-10-04
ok so I just realized, that in the moment when I start ffado-mix, in the terminal window of ffado-dbus-server will come up lot of red warnings, I am pasting here the whole text:

01607825764: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01607825778: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01607825784: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01607825796: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000007A
01607825801: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01607825806: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01607825811: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01607825819: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01607825824: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 0
01607825829: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 48000
01607825833: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 4294967295
01607827779: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01607827789: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01607827794: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01607827800: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000082
01607827811: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01607827816: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01607827821: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01607827825: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01607827834: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 0
01607827839: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 48000
01607827843: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 4294967295
01607829837: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01607829853: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01607829859: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01607829864: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000008A
01607829869: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01607829877: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01607829882: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01607829887: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01607829892: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 0
01607829900: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 48000
01607829905: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 4294967295
01607831778: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01607831788: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01607831798: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01607831804: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000092
01607831809: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01607831814: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01607831822: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01607831827: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01607831832: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 0
01607831836: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 48000
01607831845: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 4294967295
01607833207: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
01607833215: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01607833221: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01607833230: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000009A
01607833235: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
01607833240: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
01607833244: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
01607833254: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
01607833259: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 0
01607833263: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 48000
01607833268: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 4294967295
01608238811: Warning (efc_cmds_mixer.cpp)[ 108] deserialize: Deserialization failed
01608238837: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01608238924: Error (fireworks_device.cpp)[ 203] doEfcOverAVC: EfcOverAVCCmd command failed
01608238939: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 7
01608238960: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01608238967: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01608238975: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000118
01608238982: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000006
01608238994: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000005
01608239001: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000002
01608239008: Debug (efc_cmds_mixer.cpp)[ 246] showEfcCmd: EFC GET PlaybackMix Solo:
01608239017: Debug (efc_cmds_mixer.cpp)[ 247] showEfcCmd:  Channel     : 0
01608239029: Debug (efc_cmds_mixer.cpp)[ 248] showEfcCmd:  Value       : 0
01608239037: Error (fireworks_control.cpp)[ 476] getValue: Cmd failed
01608244873: Warning (efc_cmds_mixer.cpp)[ 108] deserialize: Deserialization failed
01608244889: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01608244956: Error (fireworks_device.cpp)[ 203] doEfcOverAVC: EfcOverAVCCmd command failed
01608244967: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 7
01608244973: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01608244977: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01608244987: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000011A
01608244991: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000006
01608244996: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000005
01608245011: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000002
01608245023: Debug (efc_cmds_mixer.cpp)[ 246] showEfcCmd: EFC GET PlaybackMix Solo:
01608245029: Debug (efc_cmds_mixer.cpp)[ 247] showEfcCmd:  Channel     : 16777216
01608245034: Debug (efc_cmds_mixer.cpp)[ 248] showEfcCmd:  Value       : 0
01608245039: Error (fireworks_control.cpp)[ 476] getValue: Cmd failed
01608247653: Warning (efc_cmds_mixer.cpp)[ 108] deserialize: Deserialization failed
01608247668: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01608247720: Error (fireworks_device.cpp)[ 203] doEfcOverAVC: EfcOverAVCCmd command failed
01608247730: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 7
01608247743: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01608247748: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01608247753: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000011C
01608247757: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000006
01608247765: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000005
01608247770: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000002
01608247775: Debug (efc_cmds_mixer.cpp)[ 246] showEfcCmd: EFC GET PlaybackMix Solo:
01608247780: Debug (efc_cmds_mixer.cpp)[ 247] showEfcCmd:  Channel     : 33554432
01608247788: Debug (efc_cmds_mixer.cpp)[ 248] showEfcCmd:  Value       : 0
01608247793: Error (fireworks_control.cpp)[ 476] getValue: Cmd failed
01608260067: Warning (efc_cmds_mixer.cpp)[ 108] deserialize: Deserialization failed
01608260087: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01608260159: Error (fireworks_device.cpp)[ 203] doEfcOverAVC: EfcOverAVCCmd command failed
01608260168: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 7
01608260174: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01608260178: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01608260191: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000122
01608260196: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000006
01608260201: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000005
01608260209: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000002
01608260221: Debug (efc_cmds_mixer.cpp)[ 246] showEfcCmd: EFC GET PlaybackMix Solo:
01608260226: Debug (efc_cmds_mixer.cpp)[ 247] showEfcCmd:  Channel     : 50331648
01608260234: Debug (efc_cmds_mixer.cpp)[ 248] showEfcCmd:  Value       : 0
01608260241: Error (fireworks_control.cpp)[ 476] getValue: Cmd failed
01608263058: Warning (efc_cmds_mixer.cpp)[ 108] deserialize: Deserialization failed
01608263075: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01608263132: Error (fireworks_device.cpp)[ 203] doEfcOverAVC: EfcOverAVCCmd command failed
01608263141: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 7
01608263159: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01608263164: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01608263170: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000124
01608263178: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000006
01608263189: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000005
01608263194: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000002
01608263199: Debug (efc_cmds_mixer.cpp)[ 246] showEfcCmd: EFC GET PlaybackMix Solo:
01608263207: Debug (efc_cmds_mixer.cpp)[ 247] showEfcCmd:  Channel     : 67108864
01608263219: Debug (efc_cmds_mixer.cpp)[ 248] showEfcCmd:  Value       : 0
01608263225: Error (fireworks_control.cpp)[ 476] getValue: Cmd failed
01608271468: Warning (efc_cmds_mixer.cpp)[ 108] deserialize: Deserialization failed
01608271486: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
01608271554: Error (fireworks_device.cpp)[ 203] doEfcOverAVC: EfcOverAVCCmd command failed
01608271563: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 7
01608271569: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
01608271574: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
01608271586: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x0000012A
01608271591: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000006
01608271596: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000005
01608271603: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000002
01608271615: Debug (efc_cmds_mixer.cpp)[ 246] showEfcCmd: EFC GET PlaybackMix Solo:
01608271621: Debug (efc_cmds_mixer.cpp)[ 247] showEfcCmd:  Channel     : 83886080
01608271629: Debug (efc_cmds_mixer.cpp)[ 248] showEfcCmd:  Value       : 0
01608271635: Error (fireworks_control.cpp)[ 476] getValue: Cmd failed

---

### Post by mordrax on 2009-10-13
OK, so problem solved. I found little bit newer ffado (before 1.99940, newer is 1.99942 or similar small difference), so I uninstall and install by hand. It found that I have old or missing libxml++-2.6, so find that, than it found, that my card had old firmware, so I went to windows and upgraded and O la la, jackd went fine. So hard to say where was trounle but it works. 
   Now I dont no how to play just normal mp3 or movie player (like rhythmbox or some player), there are no output offers like jackd in linux sound preferences, but worked with audacity, I hear that, so it is important...

---

