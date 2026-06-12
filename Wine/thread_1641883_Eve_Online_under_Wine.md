---
title: "Eve Online under Wine"
date: 2010-12-09
forum: Wine
---

### Post by Cant on 2010-12-09
I upgraded from Ubuntu 10.04 to 10.10 using the update manager. After I installed Eve Online it ran just fine under Wine with no problems at all. Then I did a clean install of Ubuntu using the LiveCD and reinstalled Eve. Now I get this when I start up: 

[img]http://i55.tinypic.com/30arh35.png[/img]

And this is what I get when I run it via terminal:
```
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
hermann@hermann-K70ID:~$ err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x480000 0 0x33fc40 4
EVE Client version 6.33 build 207554 starting  22:34:03
Multi-Language System: Client using language [EN]
fixme:win:EnumDisplayDevicesW ((null),0,0x338cfc,0x00000000), stub!
A traceback has been generated.  It has been logged in the log server as stacktrace #1
A traceback has been generated.  It has been logged in the log server as stacktrace #2
A traceback has been generated.  It has been logged in the log server as stacktrace #3
EVE Client version 6.33 build 207554 started  22:34:07
Starting services
Replacing service 'machoNet' with 'eveMachoNet'
Service machoNet: 0.002s
Replacing service 'dataconfig' with 'eveDataconfig'
Service dataconfig: 0.013s
Replacing service 'photo' with 'evePhoto'
Replacing service 'objectCaching' with 'eveObjectCaching'
Service objectCaching: 0.000s
Replacing service 'patch' with 'evePatch'
Replacing service 'browserHostManager' with 'eveBrowserHostManager'
Replacing service 'calendar' with 'eveCalendar'
Service addressbook: 0.000s
Service counter: 0.000s
Service clientStatsSvc: 0.000s
Service invCache: 0.000s
Service godma: 0.000s
Service photo: 0.000s
Service mailSvc: 0.000s
Service notificationSvc: 0.000s
Service LSC: 0.000s
Service patch: 0.000s
Service inv: 0.000s
Service michelle: 0.000s
Service pwn: 0.000s
Service focus: 0.000s
Service debug: 0.000s
Service jumpQueue: 0.000s
Service scanSvc: 0.000s
Service browserHostManager: 0.000s
Service jumpMonitor: 0.000s
Service calendar: 0.000s
Service liveUpdateSvc: 0.000s
Service monitor: 0.000s
Starting services - Done
Service moonScan: 0.000s
Service gameui: 0.000s
Replacing service 'device' with 'eveDevice'
Service device: 0.000s
Service make: 0.000s
Service event: 0.000s
Replacing service 'font' with 'eveFont'
Service font: 0.001s
Service registry: 0.000s
Replacing service 'audio' with 'eveAudio'
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x50028 0x00000000
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4e52c68,0x4e52bd8): stub
Service audio: 0.933s
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x50028, 0x13d2c8): stub
Service log: 0.000s
Replacing service 'cmd' with 'eveCmd'
Service ime: 0.001s
Service cmd: 0.008s
Service loading: 0.001s
Replacing service 'connection' with 'eveConnection'
Replacing service 'vivox' with 'evevivox'
Service connection: 0.000s
Service damage: 0.000s
Service logger: 0.022s
Service vivox: 0.000s
Service ownerprimer: 0.000s
Service petition: 0.000s
Service ui: 0.000s
Service form: 0.000s
Service window: 0.000s
Service z: 0.000s
Service war: 0.000s
Service consider: 0.000s
Service webtools: 0.000s
Service draw: 0.000s
Replacing service 'jukebox' with 'eveJukebox'
Service jukebox: 0.015s
Replacing service 'alert' with 'eveAlert'
Service alert: 0.001s
An exception has occurred.  It has been logged in the log server as exception #4
```

---

### Post by SamD42 on 2010-12-09
You need to reinstall the fonts it uses by the looks of it, so assuming you have winetricks installed (check synaptic) just run the following:

winetricks corefonts

Then try playing again

---

