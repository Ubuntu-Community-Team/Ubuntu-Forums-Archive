---
title: "Stacked/Daisy Chained Audiofire12s?"
date: 2010-03-05
forum: Ubuntu Studio
---

### Post by tlstudio on 2010-03-05
Hi, I'm running an Echo Audiofire12 on 9.10 and it works beautifully (see my previous post on getting it working: [http://ubuntuforums.org/showthread.php?t=1382500](http://ubuntuforums.org/showthread.php?t=1382500)). I've recently acquired another AF12 for a great deal and would like to daisy chain it to the first one. I know this concept is supported from a hardware standpoint but how do I make it work in UbuStu? I know jack can only connect to one "device" at a time. Will FFADO treat the second AF12 as an extension of the first (just a thought because of the daisy chain vs connected to separate FW ports), essentially see them as one 24 channel device? Or (more likely) do I have to map them together as a virtual device? Are virtual devices even supported under FFADO like they are with ALSA? ([http://www.alsa-project.org/main/index.php/Asoundrc#Virtual_multi_channel_devices](http://www.alsa-project.org/main/index.php/Asoundrc#Virtual_multi_channel_devices))

Maybe it will all become clear once I have the second AF12 in my hands and actually plug it in. However, I haven't found any posts yet of anyone with this setup. Anyone in the same boat? Any insights would be appreciated!

Thanks,

Trev

---

### Post by tlstudio on 2010-03-08
Ok, so I plugged in the second AF12 - daisy chained off the first so there is only one cable plugged into the firewire port on the pc (from the first AF12). Powered up both AF12s and then the PC and it seemed to work great for a few seconds - jack and ardour automagically saw all 24 channels no problem - but then I opened a project in ardour and ardour/jack choked and there were a stream of "broken pipe" errors in the jack log window. I didn't have the word clocks connected, is that required in a daisy chain configuration? Perhaps that is all I'm missing? Please let me know.

Thanks!

Trev

---

### Post by tlstudio on 2010-03-10
Ok I found some info, but it is relatively hidden from PC (and linux) users. There is a section in the readme for the MAC OS X driver download that explains how to daisy chain multiple AFs - not in the user manual as I would have expected, and the section does not even exist in the PC driver readmes. Ridiculous. Ok so I was on the right track with requiring a word clock cable. I guess I figured if I daisy chain the AFs with a firewire cable it would do the trick, but apparently the only point to daisy chaining the AFs with firewire is to save fw ports on your PC. Anyway... word clock cable, check. 3ft cable on order, shortest prefab cable I could find. Until it arrives I guess I can only use one AF at a time. I'll post an update once the cable arrives and relay whether it solved the problem.

Cheers,

Trev

---

### Post by trulan on 2010-03-10
Sounds like you know what you are doing.  I have two presonus firepods, and to daisychain those, I do as you had tried first - plug one into the other, and one firewire cable into the computer.  I guess it's too simple of an interface to even know what a word clock cable is.  The only thing I have to change is the buffering settings in Jack.  Since the data being transferred is doubled, I also have to double my latency to get the same amount of stability.

---

### Post by edesmarais on 2010-03-22
Hi TlStudio, did you get this to work, cause i'm about to buy 2 of the echo audiofire 12 and i want to daisy chain them to get 24 i/o.

thanks
__[]("http://www.backports.ubuntuforums.org/member.php?u=998803")

---

### Post by tlstudio on 2010-03-22
Hi, I'm still waiting for the word clock cable to arrive. Should show up soon...

---

### Post by tlstudio on 2010-03-25
Ok, i have some news. i got the cable and connected the AFs together and used the ffado mixer to set one internal and the other to the word clock. Seems to work now, ran fine for the few minutes i messed around with it (playback & record). I'll spend more time with it to make sure it's solid and report back.

However i have a new problem, i had it before but hoped that the wordclock connection might solve it. The problem is that i want the "master" (in terms of wordclock) AF12 to be the first 12 i/o in jack and the "slave" to be the last 12 i/o (13-24). How can i set ffado/jack to consistently detect them this way? I've tried changing the order of the firewire cables to the firewire card in the pc but it doesn't make a difference. Ffado mixer seems to see them correctly, as in the "master" is the first tab and the "slave" is the second tab. However, when i fire up jack, it sees them backwards (slave is first 12, master is last 12). Any ideas?

Also another thing - and this is minor, more of an annoyance - is Ardour gives me an error that it can't find any Alsa devices. Well that makes sense because i'm only using ffado. :P Happens everytime i open Ardour. Is there any way to lose that error?

Thanks!

Trev

---

### Post by tlstudio on 2010-03-29
Anyone have any ideas on how to fix the firewire device order problem? playback 1 and 2 are sending signal to output 1 and 2 on the *second* audiofire instead of the first, the slave instead of the master... what determines this order and how can i change it? Please help!

Btw, these are the annoying ardour errors

```

[ERROR]: No devices found for driver "ALSA"
[WARNING]: no MIDI ports specified: no MMC or MTC control possible

```How do i get rid of these errors popping up every time i start ardour?

Thanks!

---

### Post by AutoStatic on 2010-03-29
Hello tlstudio, did you also install the ffado-tools package? If not could you do so and post the output of the command **ffado-test ListDevices** ?

---

### Post by trulan on 2010-03-29
> **tlstudio said:**
> Anyone have any ideas on how to fix the firewire device order problem? playback 1 and 2 are sending signal to output 1 and 2 on the *second* audiofire instead of the first, the slave instead of the master... what determines this order and how can i change it? Please help!
I wish I could help.  My firepods seem to put themselves in the same order regardless of how the cables are plugged in as well - the one pod is always channels 1-10 and the other is always channels 11-20 and no amount of firewire cable re-plugging will change that.  I am suspicious that ffado assigns the device order based on hardware ID numbers or something, but I really don't know.

---

### Post by AutoStatic on 2010-03-30
> **trulan said:**
> I am suspicious that ffado assigns the device order based on hardware ID numbers or something, but I really don't know.If so it should be possible to set the order I reckon. What does **ffado-test ListDevices** output in your case?

---

### Post by trulan on 2010-03-30
```
$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x324fc000088ef121  0x00324FC0  0x00000000   Linux - ohci1394  - 
   1       0x000a9200c6121078  0x00000A92  0x00010066   Presonus  - PreSonus FIREPOD 
   2       0x000a9200c5112047  0x00000A92  0x00010066   Presonus  - PreSonus FIREPOD 
no message buffer overruns
```

---

### Post by AutoStatic on 2010-03-30
So they have different GUID's. I have no access to a machine with Firewire at the moment but maybe it's possible to do something with HAL, udev or FFADO's own config file (*/usr/share/libffado/configuration*).

---

### Post by trulan on 2010-03-30
> **AutoStatic said:**
> So they have different GUID's. I have no access to a machine with Firewire at the moment but maybe it's possible to do something with HAL, udev or FFADO's own config file (*/usr/share/libffado/configuration*).
Right.  And the higher GUID number is always in node 1, regardless of how the cables are plugged in.  I guess it could have to do with preferring the firepod that was plugged in first, back when I just had one.  It could also be simply based on the number.

From what I can tell, it is udev that assigns the device nodes, but I know nothing about the inner workings of udev.

I did find this:  (from [https://ieee1394.wiki.kernel.org/index.php/FAQ](https://ieee1394.wiki.kernel.org/index.php/FAQ))
"...Safety concerns with raw1394 and ohci1394 have been addressed by the replacement drivers firewire-core (which allows finer-grained access control due to separate device files per FireWire node)..."
So currently all firewire nodes are in one device file?  And in the new stack they will be in separate device files, which would allow ffado or even the user to select which device to prefer, to order as master-slave, etc?  It all sounds to me like it will be a lot easier to reorder firewire devices once ffado is stable with the new firewire stack.  I am just speculating here, I really don't know how this actually works.

---

### Post by tlstudio on 2010-03-30
Hey guys, here is my ffado-test ListDevices output
```

-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x001486045b6575de  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12
   1       0x0014860468b700cf  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12
   2       0xff00000000000000  0x00FF0000  0x00000000   Linux - ohci1394  - 
no message buffer overruns

```And here is the ffado-test Discover output
```

-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

00200554673: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00200560506: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200561661: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200562818: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200563968: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200565136: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200618265: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200619428: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200621023: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200622172: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200623359: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200685246: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200686380: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200687520: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200688668: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200689808: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
00200745347: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00200745364: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0xFFFF80AD00001486)
00200745372: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0xFFFF80AD0000AF12)
00200745377: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00200745383: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00200745386: Debug (Configuration.cpp)[ 185] showSetting:     driver = 140733193388034 (0x7F5200000002)
00200745392: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00200745396: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 140733193388034 (0x7F5200000002)
00200745447: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00200745450: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00200745454: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00200745457: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00200745460: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00200745463: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00200745466: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00200745468: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00200745559: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
00200745584: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00200745589: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00200745592: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00200745597: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00200745599: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00200745603: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00200745605: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00200745608: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00200746761: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
00200746774: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00200747008: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00200747019: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
00200747503: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00200747514: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
00200748003: Debug (avc_musicsubunit.cpp)[  65] discover: Discovering MusicSubunit...
00200748013: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00200754374: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
00200754631: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
00200754635: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
00200754647: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 2
00200754648: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
00200754653: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
00200754911: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200754922: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,0,0)
00200755328: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
00200755336: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
00200755585: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200755590: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,1,0)
00200755817: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
00200755825: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
00200756079: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200756085: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,0,0)
00200756327: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
00200756602: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200756606: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,0,1)
00200756851: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
00200756855: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
00200757119: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200757122: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,1,0)
00200757369: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
00200758294: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200758299: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,31,255,1,1)
00200759288: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
00200759293: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
00200760288: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
00200760756: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00200760990: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00200764055: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
00200764061: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
00200764068: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
00200764070: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
00200764327: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
00200764333: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
00200764343: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
00200764348: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
00200764357: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
00200764362: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
00200764368: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
00200764373: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
00200816577: Debug (devicemanager.cpp)[ 631] discover: discovery of node 0 on port 0 done...
00200822362: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200823513: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200824676: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200826272: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200829260: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC1, addr = 0x0000FFFFF0000400, length = 256
00200883463: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00200883472: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00200883481: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00200883485: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00200883491: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00200883494: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00200883500: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00200883503: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00200883545: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00200883549: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00200883556: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00200883559: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00200883565: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00200883568: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00200883575: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00200883578: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00200883647: Debug (devicemanager.cpp)[ 594] discover: driver found for device 1
00200883672: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00200883677: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 140733193393286 (0x00001486)
00200883679: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 140733193432850 (0x0000AF12)
00200883684: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
00200883686: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire12
00200883689: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
00200883691: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
00200883695: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
00200884794: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
00200884806: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00200885021: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00200885030: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (1,1,0,0,0)
00200885490: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00200885500: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (1,1,0,1,0)
00200885971: Debug (avc_musicsubunit.cpp)[  65] discover: Discovering MusicSubunit...
00200885981: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00200892273: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
00200892505: Debug (avc_unit.cpp)[ 383] discoverPlugs: number of iso input plugs = 1
00200892519: Debug (avc_unit.cpp)[ 385] discoverPlugs: number of iso output plugs = 1
00200892523: Debug (avc_unit.cpp)[ 387] discoverPlugs: number of external input plugs = 2
00200892525: Debug (avc_unit.cpp)[ 389] discoverPlugs: number of external output plugs = 2
00200892528: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 0...
00200892803: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200892814: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,0,0)
00200893329: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Input' found
00200893337: Debug (avc_unit.cpp)[ 426] discoverPlugsPCR: Discovering PCR plugs, direction 1...
00200893607: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200893613: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,1,0)
00200893849: Debug (avc_unit.cpp)[ 448] discoverPlugsPCR: plug 'PCR Unknown Output' found
00200893854: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 0...
00200894106: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200894113: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,0,0)
00200895337: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
00200895601: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200895604: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,0,1)
00200895840: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Input' found
00200895843: Debug (avc_unit.cpp)[ 459] discoverPlugsExternal: Discovering External plugs, direction 1...
00200896106: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200896109: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,1,0)
00200896461: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
00200896728: Debug (avc_plug.cpp)[ 374] discoverStreamFormat: No matching cluster info found for index 1
00200896734: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (1,31,255,1,1)
00200896971: Debug (avc_unit.cpp)[ 479] discoverPlugsExternal: plug 'External Unknown Output' found
00200896976: Debug (avc_unit.cpp)[ 489] discoverPlugConnections: Discovering PCR plug connections...
00200897209: Debug (avc_unit.cpp)[ 500] discoverPlugConnections: Discovering External plug connections...
00200898944: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00200899201: Debug (avc_subunit.cpp)[ 148] discoverConnections: Discovering connections...
00200900138: Debug (avc_unit.cpp)[ 653] discoverSyncModes: No PCR sync input plug found
00200900145: Debug (avc_unit.cpp)[ 660] discoverSyncModes: No PCR sync output plug found
00200900151: Debug (avc_unit.cpp)[ 667] discoverSyncModes: No PCR iso input plug found
00200900153: Debug (avc_unit.cpp)[ 675] discoverSyncModes: No PCR iso output plug found
00200900412: Debug (avc_unit.cpp)[ 536] propagatePlugInfo: Propagating info to PCR plugs...
00200900418: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Input
00200900430: Debug (avc_unit.cpp)[ 542] propagatePlugInfo: plug: PCR Unknown Output
00200900435: Debug (avc_unit.cpp)[ 547] propagatePlugInfo: Propagating info to External plugs...
00200900443: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
00200900448: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Input
00200900469: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
00200900472: Debug (avc_unit.cpp)[ 553] propagatePlugInfo: plug: External Unknown Output
00200931472: Debug (devicemanager.cpp)[ 631] discover: discovery of node 1 on port 0 done...
00200931479: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00200931506: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
00200931514: Debug (Element.cpp)[ 121] show: Element DeviceManager
00200931520: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00200931550: Debug (devicemanager.cpp)[1202] showDeviceInfo: --- Device  0 ---
00200931552: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
00200931557: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
00200931558: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
00200931561: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000072
00200931562: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000000
00200931567: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000000
00200931569: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
00200931572: Debug (efc_cmds_hardware.cpp)[ 127] showEfcCmd: EFC HW CAPS info:
00200931573: Debug (efc_cmds_hardware.cpp)[ 128] showEfcCmd:  Flags   : 0x00000011
00200931576: Debug (efc_cmds_hardware.cpp)[ 129] showEfcCmd:  GUID    : 0014860468B700CF
00200931578: Debug (efc_cmds_hardware.cpp)[ 130] showEfcCmd:  HwType  : 0x0000AF12
00200931581: Debug (efc_cmds_hardware.cpp)[ 131] showEfcCmd:  Version : 5776851272204288
00200931582: Debug (efc_cmds_hardware.cpp)[ 132] showEfcCmd:  Vendor  : Echo Digital Audio
00200931585: Debug (efc_cmds_hardware.cpp)[ 133] showEfcCmd:  Model   : AudioFire12
00200931587: Debug (efc_cmds_hardware.cpp)[ 135] showEfcCmd:  Supported Clocks   : 0x00000005
00200931590: Debug (efc_cmds_hardware.cpp)[ 136] showEfcCmd:  # 1394 Playback    : 12
00200931591: Debug (efc_cmds_hardware.cpp)[ 137] showEfcCmd:  # 1394 Record      : 12
00200931595: Debug (efc_cmds_hardware.cpp)[ 138] showEfcCmd:  # Physical out     : 12
00200931596: Debug (efc_cmds_hardware.cpp)[ 139] showEfcCmd:  # Physical in      : 12
00200931599: Debug (efc_cmds_hardware.cpp)[ 142] showEfcCmd:  # Output Groups    : 1
00200931600: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 0: Type 0x00, count 12
00200931604: Debug (efc_cmds_hardware.cpp)[ 147] showEfcCmd:  # Input Groups     : 1
00200931605: Debug (efc_cmds_hardware.cpp)[ 150] showEfcCmd:      Group 0: Type 0x00, count 12
00200931608: Debug (efc_cmds_hardware.cpp)[ 152] showEfcCmd:  # Midi out         : 1
00200931609: Debug (efc_cmds_hardware.cpp)[ 153] showEfcCmd:  # Midi in          : 1
00200931612: Debug (efc_cmds_hardware.cpp)[ 154] showEfcCmd:  Max Sample Rate    : 192000
00200931613: Debug (efc_cmds_hardware.cpp)[ 155] showEfcCmd:  Min Sample Rate    : 32000
00200931616: Debug (efc_cmds_hardware.cpp)[ 156] showEfcCmd:  DSP version        : 0x04080000
00200931618: Debug (efc_cmds_hardware.cpp)[ 157] showEfcCmd:  ARM version        : 0x04080000
00200931621: Debug (efc_cmds_hardware.cpp)[ 158] showEfcCmd:  # Mix play chann.  : 12
00200931622: Debug (efc_cmds_hardware.cpp)[ 159] showEfcCmd:  # Mix rec chann.   : 12
00200931627: Debug (ffadodevice.cpp)[ 228] showDevice: Attached to port.......: 0 (ohci1394)
00200931629: Debug (ffadodevice.cpp)[ 229] showDevice: Node...................: 1
00200931633: Debug (ffadodevice.cpp)[ 231] showDevice: Vendor name............: Echo Digital Audio
00200931634: Debug (ffadodevice.cpp)[ 233] showDevice: Model name.............: AudioFire12
00200931638: Debug (ffadodevice.cpp)[ 235] showDevice: GUID...................: 0014860468b700cf
00200931641: Debug (ffadodevice.cpp)[ 240] showDevice: Assigned ID....: dev0
00200931696: Debug (devicemanager.cpp)[1205] showDeviceInfo: Clock sync sources:
00200932023: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
00200932032: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
00200932035: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
00200932040: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x000000E2
00200932042: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
00200932046: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
00200932048: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
00200932052: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
00200932054: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 140733193388032
00200932059: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 140733193432132
00200932061: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 140733193388032
00200933241: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: Internal          , Id:  0, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal sync
00200933248: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: WordClock         , Id:  2, Valid: 1, Active: 0, Locked 1, Slipping: 0, Description: Word Clock
00200933256: Debug (devicemanager.cpp)[1202] showDeviceInfo: --- Device  1 ---
00200933259: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
00200933264: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
00200933266: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
00200933270: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x00000002
00200933272: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000000
00200933276: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000000
00200933278: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
00200933282: Debug (efc_cmds_hardware.cpp)[ 127] showEfcCmd: EFC HW CAPS info:
00200933284: Debug (efc_cmds_hardware.cpp)[ 128] showEfcCmd:  Flags   : 0x00000011
00200933289: Debug (efc_cmds_hardware.cpp)[ 129] showEfcCmd:  GUID    : 001486045B6575DE
00200933291: Debug (efc_cmds_hardware.cpp)[ 130] showEfcCmd:  HwType  : 0x0000AF12
00200933296: Debug (efc_cmds_hardware.cpp)[ 131] showEfcCmd:  Version : 5776851272204288
00200933298: Debug (efc_cmds_hardware.cpp)[ 132] showEfcCmd:  Vendor  : Echo Digital Audio
00200933305: Debug (efc_cmds_hardware.cpp)[ 133] showEfcCmd:  Model   : AudioFire12
00200933307: Debug (efc_cmds_hardware.cpp)[ 135] showEfcCmd:  Supported Clocks   : 0x00000005
00200933312: Debug (efc_cmds_hardware.cpp)[ 136] showEfcCmd:  # 1394 Playback    : 12
00200933314: Debug (efc_cmds_hardware.cpp)[ 137] showEfcCmd:  # 1394 Record      : 12
00200933333: Debug (efc_cmds_hardware.cpp)[ 138] showEfcCmd:  # Physical out     : 12
00200933335: Debug (efc_cmds_hardware.cpp)[ 139] showEfcCmd:  # Physical in      : 12
00200933338: Debug (efc_cmds_hardware.cpp)[ 142] showEfcCmd:  # Output Groups    : 1
00200933339: Debug (efc_cmds_hardware.cpp)[ 145] showEfcCmd:      Group 0: Type 0x00, count 12
00200933342: Debug (efc_cmds_hardware.cpp)[ 147] showEfcCmd:  # Input Groups     : 1
00200933344: Debug (efc_cmds_hardware.cpp)[ 150] showEfcCmd:      Group 0: Type 0x00, count 12
00200933347: Debug (efc_cmds_hardware.cpp)[ 152] showEfcCmd:  # Midi out         : 1
00200933348: Debug (efc_cmds_hardware.cpp)[ 153] showEfcCmd:  # Midi in          : 1
00200933351: Debug (efc_cmds_hardware.cpp)[ 154] showEfcCmd:  Max Sample Rate    : 192000
00200933353: Debug (efc_cmds_hardware.cpp)[ 155] showEfcCmd:  Min Sample Rate    : 32000
00200933357: Debug (efc_cmds_hardware.cpp)[ 156] showEfcCmd:  DSP version        : 0x04080000
00200933358: Debug (efc_cmds_hardware.cpp)[ 157] showEfcCmd:  ARM version        : 0x04080000
00200933361: Debug (efc_cmds_hardware.cpp)[ 158] showEfcCmd:  # Mix play chann.  : 12
00200933362: Debug (efc_cmds_hardware.cpp)[ 159] showEfcCmd:  # Mix rec chann.   : 12
00200933366: Debug (ffadodevice.cpp)[ 228] showDevice: Attached to port.......: 0 (ohci1394)
00200933367: Debug (ffadodevice.cpp)[ 229] showDevice: Node...................: 0
00200933370: Debug (ffadodevice.cpp)[ 231] showDevice: Vendor name............: Echo Digital Audio
00200933372: Debug (ffadodevice.cpp)[ 233] showDevice: Model name.............: AudioFire12
00200933376: Debug (ffadodevice.cpp)[ 235] showDevice: GUID...................: 001486045b6575de
00200933379: Debug (ffadodevice.cpp)[ 240] showDevice: Assigned ID....: dev1
00200933424: Debug (devicemanager.cpp)[1205] showDeviceInfo: Clock sync sources:
00200933751: Debug (efc_cmd.cpp)[ 171] showEfcCmd: EFC Length: 6
00200933760: Debug (efc_cmd.cpp)[ 172] showEfcCmd: EFC Header:
00200933763: Debug (efc_cmd.cpp)[ 173] showEfcCmd:  Version         : 0x00000000
00200933768: Debug (efc_cmd.cpp)[ 174] showEfcCmd:  Sequence number : 0x000000EA
00200933770: Debug (efc_cmd.cpp)[ 175] showEfcCmd:  Category        : 0x00000003
00200933776: Debug (efc_cmd.cpp)[ 176] showEfcCmd:  Command         : 0x00000001
00200933778: Debug (efc_cmd.cpp)[ 177] showEfcCmd:  Return Value    : 0x00000000
00200933782: Debug (efc_cmds_hardware_ctrl.cpp)[  74] showEfcCmd: EFC Get Clock:
00200933784: Debug (efc_cmds_hardware_ctrl.cpp)[  75] showEfcCmd:  Clock       : 140733193388032
00200933788: Debug (efc_cmds_hardware_ctrl.cpp)[  76] showEfcCmd:  Samplerate  : 140733193432132
00200933791: Debug (efc_cmds_hardware_ctrl.cpp)[  77] showEfcCmd:  Index       : 140733193388032
00200935003: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: Internal          , Id:  0, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal sync
00200935010: Debug (devicemanager.cpp)[1214] showDeviceInfo:  Type: WordClock         , Id:  2, Valid: 0, Active: 0, Locked 1, Slipping: 0, Description: Word Clock
no message buffer overruns

```So my results are somewhat contrary to trulan's. The ListDevices output shows the devices in the correct GUID order and also the order I want them to appear in jack. The Discover output however shows that the higher GUID (second device in ListDevices) consistently gets the lower device id (dev0) and so (assuming this is why) becomes the first device according to jack, opposite of expected behavior in my opinion!

Also, a side note, I discovered (pun intended :)) something interesting when  running ffado-test Discover. If I have ffado-mixer open while I run  ffado-test Discover I get all kinds of errors and warnings like it can't  communicate with the AF devices. 
```

00695883229: Error (fireworks_device.cpp)[ 623] getClock: Could not get  clock info
00695905238: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP  transaction didn't succeed in 20 tries
00695905253: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP  transaction failed
00695905257: Error (fireworks_device.cpp)[ 216] doEfcOverAVC:  EfcOverAVCCmd command failed

```When I close ffado-mixer, Discover outputs normal again. Does ffado-mixer lock the firewire devices in some way? I find that jack is also hit  and miss when ffado-mixer is running.

Another observation, I have to run ffado-mixer each time I boot  to re-set the clock and sample rate settings because they don't get saved, is that "normal"?

Trev

---

### Post by tlstudio on 2010-03-30
The qjackctl log seems to confirm that jack is ordering the i/o by the ffado device id (dev0/dev1 as seen in the ffado-test Discover output)
```

firewire MSG: Registering audio capture port C0_dev0_Unknown
firewire MSG: Registering audio capture port C1_dev0_Unknown0
firewire MSG: Registering audio capture port C2_dev0_Unknown1
firewire MSG: Registering audio capture port C3_dev0_Unknown2
firewire MSG: Registering audio capture port C4_dev0_Unknown3
firewire MSG: Registering audio capture port C5_dev0_Unknown4
firewire MSG: Registering audio capture port C6_dev0_Unknown5
firewire MSG: Registering audio capture port C7_dev0_Unknown6
firewire MSG: Registering audio capture port C8_dev0_Unknown7
firewire MSG: Registering audio capture port C9_dev0_Unknown8
firewire MSG: Registering audio capture port C10_dev0_Unknown9
firewire MSG: Registering audio capture port C11_dev0_Unknown10
firewire MSG: Registering midi capture port C12_dev0_Unknown11
firewire MSG: Registering audio capture port C13_dev1_Unknown
firewire MSG: Registering audio capture port C14_dev1_Unknown0
firewire MSG: Registering audio capture port C15_dev1_Unknown1
firewire MSG: Registering audio capture port C16_dev1_Unknown2
firewire MSG: Registering audio capture port C17_dev1_Unknown3
firewire MSG: Registering audio capture port C18_dev1_Unknown4
firewire MSG: Registering audio capture port C19_dev1_Unknown5
firewire MSG: Registering audio capture port C20_dev1_Unknown6
firewire MSG: Registering audio capture port C21_dev1_Unknown7
firewire MSG: Registering audio capture port C22_dev1_Unknown8
firewire MSG: Registering audio capture port C23_dev1_Unknown9
firewire MSG: Registering audio capture port C24_dev1_Unknown10
firewire MSG: Registering midi capture port C25_dev1_Unknown11
firewire MSG: Registering audio playback port P0_dev0_Unknown
firewire MSG: Registering audio playback port P1_dev0_Unknown0
firewire MSG: Registering audio playback port P2_dev0_Unknown1
firewire MSG: Registering audio playback port P3_dev0_Unknown2
firewire MSG: Registering audio playback port P4_dev0_Unknown3
firewire MSG: Registering audio playback port P5_dev0_Unknown4
firewire MSG: Registering audio playback port P6_dev0_Unknown5
firewire MSG: Registering audio playback port P7_dev0_Unknown6
firewire MSG: Registering audio playback port P8_dev0_Unknown7
firewire MSG: Registering audio playback port P9_dev0_Unknown8
firewire MSG: Registering audio playback port P10_dev0_Unknown9
firewire MSG: Registering audio playback port P11_dev0_Unknown10
firewire MSG: Registering midi playback port P12_dev0_Unknown11
firewire MSG: Registering audio playback port P13_dev1_Unknown
firewire MSG: Registering audio playback port P14_dev1_Unknown0
firewire MSG: Registering audio playback port P15_dev1_Unknown1
firewire MSG: Registering audio playback port P16_dev1_Unknown2
firewire MSG: Registering audio playback port P17_dev1_Unknown3
firewire MSG: Registering audio playback port P18_dev1_Unknown4
firewire MSG: Registering audio playback port P19_dev1_Unknown5
firewire MSG: Registering audio playback port P20_dev1_Unknown6
firewire MSG: Registering audio playback port P21_dev1_Unknown7
firewire MSG: Registering audio playback port P22_dev1_Unknown8
firewire MSG: Registering audio playback port P23_dev1_Unknown9
firewire MSG: Registering audio playback port P24_dev1_Unknown10
firewire MSG: Registering midi playback port P25_dev1_Unknown11

```What gets me is ListDevices and Discover/jack are not consistent with the device order. I would be ok with letting the driver decide if only it was deciding logically #-o. I can rewire my rack now to make it work but for all I know a new driver might decide to change the order on me. ](*,)

trulan, I checked out that link, any idea of the status of the new stack and whether it will be ready for Lucid?

Cheers,

Trev

---

### Post by trulan on 2010-03-30
Lucid's not even getting a new real time kernel, so no new firewire stack as it needs at least kernel 2.6.32.  Now it would be possible to set up the new firewire stack on the generic kernel or on the 'low-latency' desktop kernel they are talking about shipping with Lucid Studio, but the ffado guys imply here ([http://www.ffado.org/?q=node/1316](http://www.ffado.org/?q=node/1316)) that the new firewire stack isn't quite ready to handle the demands of ffado.  I think both sets of firewire modules will be included in the Lucid generic kernel, but the new stack will be blacklisted by default.

But I don't know if this will affect your issue.  I get the feeling very quickly that you know more about this than I do.
;)

---

### Post by tlstudio on 2010-04-01
Thanks for the info. Sounds like the new stack might do the trick but it also sounds like it's a waiting game until the new stack/kernel are ready to play. In the mean time I can rewire the rack as a workaround.

I don't know about know more, I'm just learning. Relatively quickly. In a crash course sort of way. :P

Cheers,

Trev

---

### Post by AutoStatic on 2010-04-01
Hello Trev, maybe it's an option to join the ffado-users mailinglist: [http://www.ffado.org/?q=contact](http://www.ffado.org/?q=contact)
Or try the #ffado IRC on FreeNode.
I hope I have some time to take a look at it myself this weekend, but I also just installed Karmic on my main machine and I have to tweak that install first.

---

### Post by tlstudio on 2010-04-01
Nice work AutoStatic! I found the answer to the device order question in the ffado-user list, I knew there had to be a way, thanks for pointing me in the right direction! :D

[http://sourceforge.net/mailarchive/message.php?msg_name=49A866F5.1010402%40joow.be](http://sourceforge.net/mailarchive/message.php?msg_name=49A866F5.1010402%40joow.be)

To summarize, the answer is:[FONT=monospace]

[/FONT]jackd -R -d firewire -d "guid:0x12345678;guid:0x987654"


I haven't tried it yet but I'll give it a shot when I get to the studio later today. The only thing is I'm not sure how to enter this in qjackctl (the gui), any ideas?

Cheers,

Trev

---

### Post by AutoStatic on 2010-04-01
My guess is that you can enter the guid values in the Interfaces field, without the quotes.

---

### Post by tlstudio on 2010-04-01
Ok, I've had some success. Running jack with the guid string via command line works great. However, running it via qjackctl does not.

AutoStatic, I tried your theory of entering the guid string in the Interface field and it appears to me that it should work but it just doesn't, can't seem to connect to the AFs. I tried without quotes, with quotes, with quotes and a space in front... nothing worked.

In fact I tried qjackctl first and was so confused that it didn't work because the command that it uses to run jack shows up in the log window and looks exactly like it should, based on the example I posted earlier. So I copied that command from the log window and pasted into a terminal and lo and behold it works like a charm.

It's awesome that it works but without qjackctl I don't have a patch interface. Patchage doesn't want to run (doesn't like AFs?) and it will actually crash jack and mess it up enough that I have to restart the computer to get it to run again.

trulan, does the guid string work for you in qjackctl with your firepods?

Cheers,

Trev

---

### Post by AutoStatic on 2010-04-02
You can run JACK from the commandline and then start QjackCtl afterwards, it will detect a running JACK server and you should be able to use the patchbay or connections windows.
You could ask the author of QjackCtl, Rui Nuno Capela, how to enter the guid stuff in QjackCtl. Rui has his own blog ([http://www.rncbc.org/drupal/](http://www.rncbc.org/drupal/)) where he replies quickly on any questions and he also hangs around at the linux-audio-dev and jack-devel mailinglists.

---

### Post by trulan on 2010-04-02
Patchage doesn't like the version of Jack that comes with Karmic.  Try running Jack .118 from philip5's ppa.
[https://launchpad.net/~philip5/+archive/extra/]("https://launchpad.net/%7Ephilip5/+archive/extra/")
It's also worth getting the new version of Patchage while you're there.

The 4-pin firewire port on my laptop broke yesterday, my desktop only has a 6 pin firewire connector, and I only have one 6 pin to 6 pin firewire cable, so I can't test the guid string at the moment. :(

---

### Post by AutoStatic on 2010-04-03
> **trulan said:**
> The 4-pin firewire port on my laptop broke yesterday, my desktop only has a 6 pin firewire connector, and I only have one 6 pin to 6 pin firewire cable, so I can't test the guid string at the moment. :(Ouch, is it repairable?

---

### Post by trulan on 2010-04-03
> **AutoStatic said:**
> Ouch, is it repairable?
It depends how you define repairable.  It's a four year old Dell Inspiron that was a refurb to begin with. So it's just not worth it.  Plus I've found a good home for it where firewire won't be needed.  A new machine is on its way....:D

---

### Post by tlstudio on 2010-04-07
Ok so I posted on Rui's blog and he says he doesn't have experience with firewire devices and has no idea how to make it work, but he pointed me back to the ffado list so i'll try back there and see what comes up. in the mean time i can run jackd in a terminal first and qjackctl second as a workaround (thanks again AutoStatic!)

Thanks trulan for that bit of info regarding Patchage!

---

### Post by trulan on 2010-04-09
OK, new machine is here!  Off-topic, I was initially disappointed with its performance until I figured out that the firewire chip shares its irq with the wireless card.  So I can't use wireless internet and ffado at the same time.  This worked fine on the old machine - turn off wireless on this one and it performs like I had hoped.

On topic, the guid string does work for me, both in a terminal, like this:
```
jackd -P76 -dfirewire -d "guid:0x000a9200c5112047;guid:0x000a9200c6121078" -r44100 -p128 -n2
```And in qjackctl,  message window is in screenshot.  The command does not look the same, it doesn't show the quotes.  If I copy the command from the message window and run it in a terminal it fails.

Edit:  I just checked .jackdrc and the guid string does not have the quotes there either.  So if I were to copy the command from .jackdrc and run it in a terminal it would fail.  But, when run from qjackctl it works.

---

### Post by tlstudio on 2010-04-09
Congrats on the new music box! :)

Interesting, so I know you are running a newer jackd and ffado but what version of qjackctl are you running? Are they all from philip5's ppa that you posted earlier? If he's got newer versions of everything would it be a good idea to add the repository and update everything? At any rate it sounds like I have some updating to do!

Thanks again trulan!

Cheers,

Trev

---

### Post by trulan on 2010-04-09
> **tlstudio said:**
> Congrats on the new music box! :)

Interesting, so I know you are running a newer jackd and ffado but what version of qjackctl are you running? Are they all from philip5's ppa that you posted earlier?
Caught in the act!

That's not Ubuntu, that's AVLinux.  So the packages are from the Debian Sid repos (or maybe cutsom compiled, but I don't think so).  I guess I should have tested it under Ubuntu...

---

### Post by tlstudio on 2010-04-12
Problem solved! I added philip5's ppa as a repository and upgraded to the newer versions of everything except audacious (it breaks dependencies!). Everything is working great, I entered the guid string in qjackctl and jack fires up without any issues, the AFs are in the right order, patchage works again. Sweet. :)

Now if I can just get rid of those annoying Ardour startup errors! :-k

Thanks for all your help guys!

Cheers,

Trev

---

### Post by tlstudio on 2010-04-12
Btw, I like that the new Ardour organizes the plugins menu by category now instead of only by author. :)

---

### Post by trulan on 2010-04-12
Great!!  Glad it's all working for you!  I liked the plugin categories thing too.

It was posted in the ppa's thread on here that there is an issue with these newer versions of jackd and Ardour when using Jack Transport, I think it's that rewinding doesn't work.  I have never used Jack Transport, so for me, having Patchage working when using ffado is much more important.  Nevertheless, if using Ardour and Jack Transport is important to someone, it might be good to think twice about upgrading.

Happy audio production!!

---

