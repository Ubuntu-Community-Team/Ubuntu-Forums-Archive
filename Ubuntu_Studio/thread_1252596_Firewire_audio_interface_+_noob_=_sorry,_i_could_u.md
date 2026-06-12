---
title: "Firewire audio interface + noob = sorry, i could use help x.x"
date: 2009-08-29
forum: Ubuntu Studio
---

### Post by Jordan122 on 2009-08-29
Hi,

So not knowing anything about linux at all I installed ubuntu studio and did all kinds of things trying to get my Alesis Io26 to work. I scourged forums and tried all these weird things, but to be honest everything was incredibly confusing for me since I have 0 knowledge of anything x.x

Theres another thread on here... 1071904 where a guy lhas success with the multimix alesis.

Im supposed to do what he does basically but I cant even figure out how to pack a driver or whatever ahaha also in Ubuntu Studio these drivers are already installed... Im just not sure what im doing exactly. x.x

Its not one of the supported pieces of hardware for ffado but I read some folks got it going, and Id really just cry my little eyes out if someone would help me do the same.

Jackd, FFADO, etc are very confusing to me, i dont understand really much of anything at all x.x sorry.
I did many things and really ahaha dont quite understand them all yet... if I type...

gscanbus i can see the Alesis name in the GUI o.o which comforts me >.> idk... the consol says...

jordan@psalms:~$ gscanbus

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory


not sure how much that matters ahaha

If I bust a jackd -d firewire (not even sure if this is a relevant command o.O)

jordan@psalms:~$ jackd -d firewire
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
10773603621:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
10778646281: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
10783686281: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns

again I have no idea what Im doing ahahaha >.> sorry


if I type in ffado-test-streaming

here are the red lines that show up >.>

10403164542: Warning (ffado.cpp)[ 121] ffado_streaming_init: Realtime scheduling is not enabled. This will cause significant reliability issues.

10408210269: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0

10413250272: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0

10413250442: Fatal (ffado.cpp)[ 174] ffado_streaming_init: There are no devices on the bus

10413369182: Error (teststreaming3.cpp)[ 315] main: Could not init Ffado Streaming layer

Heres the whole wretched thing >.> incase it helps (i had to remove the smily faces >.>)

jordan@psalms:~$ ffado-test-streaming
10403164303: Debug (teststreaming3.cpp)[ 265] main: verbose level = 6
10403164389: Debug (teststreaming3.cpp)[ 286] main: FFADO streaming test application (3)
10403164413:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
10403164504: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
10403164526: Debug (StreamProcessorManager.cpp)[1395] setVerboseLevel: Setting verbose level to 6...
10403164535: Debug (devicemanager.cpp)[1082] setVerboseLevel: Setting verbose level to 6...
10403164542: Warning (ffado.cpp)[ 121] ffado_streaming_init: Realtime scheduling is not enabled. This will cause significant reliability issues.
10403164554: Debug (ffado.cpp)[ 148] ffado_streaming_init: setting slave mode to 0
10403164583: Debug (ffado.cpp)[ 154] ffado_streaming_init: setting snoop mode to 0
10403164843: Debug (Configuration.cpp)[  62] openFile: Could not open file: ~/.ffado/configuration
10403165995: Debug (devicemanager.cpp)[ 168] initialize: Found 1 firewire adapters (ports)
10403166038: Debug (IsoHandlerManager.cpp)[1193] setVerboseLevel: Setting verbose level to 6...
10403166054: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
10403166070: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
10403166078: Debug (IsoHandlerManager.cpp)[ 534] setThreadParameters: (0x99f136) switch to: (rt=0, prio=1)...
10403166121: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
10403166164: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase
10403166174: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
10403166205: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
10403166236: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_xmit
10403166252: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
10403166284: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
10403166316: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_recv
10403166325: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
10403166343: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
10403166356: Debug (CycleTimerHelper.cpp)[ 242] setThreadParameters: (0x99f13a switch to: (rt=0, prio=1)...
10403166396: Debug (Watchdog.cpp)[ 200] start: (0x99f1530) Starting watchdog...
10403166406: Debug (Watchdog.cpp)[ 201] start: Create hartbeat task/thread for 0x99f1530...
10403166423: Debug (Watchdog.cpp)[ 215] start:  hartbeat task: 0x99f1568, thread 0x99f15a0...
10403166431: Debug (Watchdog.cpp)[ 217] start: Create check task/thread for 0x99f1530...
10403166439: Debug (Watchdog.cpp)[ 231] start:  check task: 0x99f15c0, thread 0x99f15f8...
10403166597: Debug (Watchdog.cpp)[ 249] start: (0x99f1530) Watchdog running...
10403166733: Debug (ieee1394service.cpp)[ 280] initialize: This system supports the raw1394_read_cycle_timer call, using it.
10403166822: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.min_split_timeout_usecs
10403166858: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.min_split_timeout_usecs
10403166867: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.min_split_timeout_usecs' not found
10403166887: Debug (ieee1394service.cpp)[ 917] getSplitTimeoutUsecs: reading SPLIT_TIMEOUT on node 0x1...
10403166931: Debug (ieee1394service.cpp)[ 924] getSplitTimeoutUsecs:  READ HI: 0x01000000
10403166957: Debug (ieee1394service.cpp)[ 931] getSplitTimeoutUsecs:  READ LO: 0x00000000
10403166966: Debug (ieee1394service.cpp)[ 325] initialize: Minimum SPLIT_TIMEOUT: 1000000. Current: 1000000
10403166985: Debug (CycleTimerHelper.cpp)[ 126] Start: Start 0x99f13a8...
10403166994: Debug (CycleTimerHelper.cpp)[ 159] initValues: (0x99f13a Init values...
10403167001: Debug (CycleTimerHelper.cpp)[ 166] initValues: Read CTR...
10403167013: Debug (CycleTimerHelper.cpp)[ 177] initValues:  read : CTR:  1092342048, local:  1251528446171511
10403167027: Debug (CycleTimerHelper.cpp)[ 183] initValues:   ctr   : 0x411BD120   800382240 (032s 4541cy 0288ticks)
10403167037: Debug (CycleTimerHelper.cpp)[ 189] initValues: requesting DLL re-init...
10403168124: Debug (CycleTimerHelper.cpp)[ 306] initDLL:  (0x99f13a First run
10403168135: Debug (CycleTimerHelper.cpp)[ 309] initDLL:   usecs/update: 200000, ticks/update: 4915200, m_dll_e2: 4915200.000000
10403168182: Debug (CycleTimerHelper.cpp)[ 312] initDLL:   usecs current: 1251528446172620.000000, next: 1251528446372620.000000
10403168199: Debug (CycleTimerHelper.cpp)[ 315] initDLL:   ticks current: 800409521.000000, next: 805324721.000000
10403168212: Debug (CycleTimerHelper.cpp)[ 199] initValues: ready...
10403168223: Debug (Watchdog.cpp)[ 281] registerThread: (0x99f1530) Adding thread 0x99f3930
10403168288: Debug (CycleTimerHelper.cpp)[ 206] Init: Initialize 0x99f13a8...
10403168303: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0x99f39e
10403168331: Debug (CycleTimerHelper.cpp)[ 389] Execute: (0x99f13a have to retry CTR read, diff unrealistic: diff: 800414613, max: +/- 3072 (try: 10) 0
10403168352: Debug (IsoHandlerManager.cpp)[1193] setVerboseLevel: Setting verbose level to 6...
10403168366: Debug (IsoHandlerManager.cpp)[ 575] init: Initializing ISO manager 0x99f1368...
10403168405: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
10403168438: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase
10403168448: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
10403168526: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
10403168559: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_xmit
10403168568: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
10403168478: Debug (CycleTimerHelper.cpp)[ 306] initDLL:  (0x99f13a First run
10403168617: Debug (CycleTimerHelper.cpp)[ 309] initDLL:   usecs/update: 200000, ticks/update: 4915200, m_dll_e2: 4915200.000000
10403168632: Debug (CycleTimerHelper.cpp)[ 312] initDLL:   usecs current: 1251528446172976.000000, next: 1251528446372976.000000
10403168647: Debug (CycleTimerHelper.cpp)[ 315] initDLL:   ticks current: 800418267.000000, next: 805333467.000000
10403168690: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
10403168731: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_recv
10403168741: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
10403168772: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
10403168804: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
10403168820: Debug (Configuration.cpp)[ 267] getValueForSetting: path 'ieee1394.isomanager.isotask_activity_timeout_usecs' not found
10403168828: Debug (IsoHandlerManager.cpp)[ 596] init: Create iso thread for 0x99f1368 transmit...
10403168837: Debug (IsoHandlerManager.cpp)[ 451] setVerboseLevel: Setting verbose level to 6...
10403168846: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
10403168860: Debug (IsoHandlerManager.cpp)[ 615] init: Create iso thread for 0x99f1368 receive...
10403168868: Debug (IsoHandlerManager.cpp)[ 451] setVerboseLevel: Setting verbose level to 6...
10403168876: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
10403168884: Debug (Watchdog.cpp)[ 281] registerThread: (0x99f1530) Adding thread 0x99f3b80
10403168900: Debug (Watchdog.cpp)[ 281] registerThread: (0x99f1530) Adding thread 0x99f3cc0
10403168910: Debug (PosixThread.cpp)[ 150] Start: (ISOXMT) Create non RT thread 0x99f3b80
10403168963: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISOXMT) ThreadHandler: start 0x99f3b80
10403168995: Debug (PosixThread.cpp)[ 150] Start: (ISORCV) Create non RT thread 0x99f3cc0
10403169048: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISORCV) ThreadHandler: start 0x99f3cc0
10403169108: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
10403169119: Debug (IsoHandlerManager.cpp)[ 534] setThreadParameters: (0x99f136 switch to: (rt=0, prio=1)...
10403169156: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
10403169197: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase
10403169207: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
10403169238: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
10403169269: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_xmit
10403169285: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
10403169316: Debug (Configuration.cpp)[ 285] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
10403169347: Debug (Configuration.cpp)[ 285] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_recv
10403169357: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
10403169372: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISOXMT, 0x99f3b80) Drop realtime
10403169395: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISORCV, 0x99f3cc0) Drop realtime
10403169405: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
10403169412: Debug (CycleTimerHelper.cpp)[ 242] setThreadParameters: (0x99f13a switch to: (rt=0, prio=1)...
10403169430: Debug (PosixThread.cpp)[ 230] DropRealTime: (CTRHLP, 0x99f3930) Drop realtime
10403169444: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0x99f3ed0)
10403169458: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
10403169482: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
10403169503: Debug (StreamProcessorManager.cpp)[1395] setVerboseLevel: Setting verbose level to 6...
10403169511: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
10403169519: Debug (IsoHandlerManager.cpp)[ 451] setVerboseLevel: Setting verbose level to 6...
10403169525: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
10403169538: Debug (IsoHandlerManager.cpp)[ 451] setVerboseLevel: Setting verbose level to 6...
10403169545: Debug (IsoHandlerManager.cpp)[1193] setVerboseLevel: Setting verbose level to 6...
10403169552: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
10403169559: Debug (devicemanager.cpp)[1082] setVerboseLevel: Setting verbose level to 6...
10403169575: Debug (devicemanager.cpp)[ 359] discover: Probing node 0...
10404168574: Debug (CycleTimerHelper.cpp)[ 486] Execute: Switching to low-bandwidth coefficients
10404176057: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10405184055: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10406192070: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10407200065: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10408208056: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10408210269: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
10408210323: Debug (devicemanager.cpp)[ 376] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
10408210340: Debug (devicemanager.cpp)[ 359] discover: Probing node 1...
10408210349: Debug (devicemanager.cpp)[ 362] discover: Skipping local node (1)...
10408210359: Debug (DeviceStringParser.cpp)[ 376] show: DeviceStringParser: 0x99f05d0
10408210388: Debug (devicemanager.cpp)[ 534] discover: Probing node 0...
10409216068: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10410224059: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10411232060: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10412240057: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10413248059: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
10413250272: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
10413250293: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
10413250314: Debug (devicemanager.cpp)[ 534] discover: Probing node 1...
10413250322: Debug (devicemanager.cpp)[ 537] discover: Skipping local node (1)...
10413250330: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
10413250338: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
10413250356: Debug (Element.cpp)[ 121] show: Element DeviceManager
10413250372: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
10413250386: Debug (ieee1394service.cpp)[1380] show: Port:  0
10413250394: Debug (ieee1394service.cpp)[1381] show:  Name: ohci1394
10413250407: Debug (ieee1394service.cpp)[1383] show:  CycleTimerHelper: 0x99f13a8, IsoManager: 0x99f1368, WatchDog: 0x99f1530
10413250416: Debug (ieee1394service.cpp)[1388] show:  Time: 01048186876 (042s 5206cy 2044ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
10413250442: Fatal (ffado.cpp)[ 174] ffado_streaming_init: There are no devices on the bus
10413250453: Debug (Configuration.cpp)[ 137] save: Not saving temporary config file: temporary
10413250461: Debug (Configuration.cpp)[ 134] save: Not saving readonly config file: /usr/share/libffado/configuration
10413250516: Debug (IsoHandlerManager.cpp)[1129] stopHandlers: enter...
10413250534: Debug (IsoHandlerManager.cpp)[ 979] pruneHandlers: enter...
10413250543: Debug (PosixThread.cpp)[ 178] Stop: (ISOXMT) Stop 0x99f3b80 (thread: 0xb55a7b90)
10413256791: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISOXMT) ThreadHandler: exit 0x99f3b80
10413256867: Debug (PosixThread.cpp)[ 182] Stop: (ISOXMT) Stopped 0x99f3b80 (thread: 0xb55a7b90)
10413256883: Debug (PosixThread.cpp)[ 178] Stop: (ISORCV) Stop 0x99f3cc0 (thread: 0xb4da6b90)
10413266864: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISORCV) ThreadHandler: exit 0x99f3cc0
10413266909: Debug (PosixThread.cpp)[ 182] Stop: (ISORCV) Stopped 0x99f3cc0 (thread: 0xb4da6b90)
10413266942: Debug (PosixThread.cpp)[ 178] Stop: (CTRHLP) Stop 0x99f3930 (thread: 0xb5da8b90)
10413368591: Debug (PosixThread.cpp)[  86] ThreadHandler: (CTRHLP) ThreadHandler: exit 0x99f3930
10413368646: Debug (PosixThread.cpp)[ 182] Stop: (CTRHLP) Stopped 0x99f3930 (thread: 0xb5da8b90)
10413368661: Debug (ieee1394service.cpp)[1084] remBusResetHandler: Removing busreset handler (0x99f39e
10413368685: Debug (ieee1394service.cpp)[1091] remBusResetHandler:  found
10413368869: Debug (PosixThread.cpp)[ 164] Kill: (WDGCHK) Kill 0x99f15f8 (thread: 0xb65a9b90)
10413369001: Debug (PosixThread.cpp)[ 168] Kill: (WDGCHK) Killed 0x99f15f8 (thread: 0xb65a9b90)
10413369025: Debug (PosixThread.cpp)[ 164] Kill: (WDGHBT) Kill 0x99f15a0 (thread: 0xb6daab90)
10413369123: Debug (PosixThread.cpp)[ 168] Kill: (WDGHBT) Killed 0x99f15a0 (thread: 0xb6daab90)
10413369182: Error (teststreaming3.cpp)[ 315] main: Could not init Ffado Streaming layer
no message buffer overruns



So yeah I know nothing and need help >.> thank you, ill write you pretty songs <.< How can I get this thing recognized or the driver loaded or whatever I need to do. x.x sorry im so ignorant.

---

### Post by trulan on 2009-08-29
Hi, I was where you are two months ago.  I know how you feel.

I have a presonus firepod, and it works magnificently with Ubuntu Studio, even on my laptop which couldn't run it at all in windows XP.

a few tips: (Note - I'm a gui user, I do everything I can through the menus.  The command line is still being learned here.)
1. You'll need to manually enable raw1394 access for this to work. This can be done with Ubuntu Studio Controls under System/Administration.
2. You'll need to make yourself a member of groups named 'Video' and 'Audio'.  This can be done through System/Administration/Users and Groups.
3. Unless you really like the command line interface, I would recommend using qjackctl to start jackd.  It's called "Jack Control" under Audio Production on a default U-Studio install.
4. Make sure 'Real Time' is checked in Jack Control settings, and that 'firewire' is selected for the driver.   A few more of the settings in there will need tweaked but that will do for now.

And, one question:  Which version of Ubuntu Studio are you using?  Hardy?  Jaunty?  I'm a bit confused because you mention ffado (which was introduced in Jaunty) and gscanbus (which was removed in Jaunty).

Anyway, welcome to the community, and hang in there!

---

### Post by royleith on 2009-08-29
Yes. What Trulan said, but I might have a bit more info.

As he said, use Studio Controls to enable Firewire raw. In addition, enable memlock and give it, say, 50% of your total RAM. It's only a maximum and it's common to set it to unlimited. Otherwise you will find jack complaining about not being able to get memlock. Finally, enable rtprio and set it to -19. (minus 19).

Next, look in /etc/udev/rules.d and see if there is a file of the form 60-raw1394.rules. The number just determines in what order udev instigates the rules. If you have no XX-raw1394.rules file then I suggest using sudo gedit to add one called 60-raw1394.rules and putting the following into it.

KERNEL=="raw1394", GROUP="audio"
KERNEL=="dv1394*", GROUP="audio"
KERNEL=="video1394*", GROUP="audio"

I assume that the last two are for Firewire connected digital cameras, but, hey, it's free and Christmas is not that far away! You must go to users and create the audio group and add yourself to the group if that is not already in place.

I think you need to restart at that point so that udev boots up with the new rules.

Once back, try the following in Terminal,

sudo lsmod | grep 1394

You should see something like,

raw1394  45184  16
dv1394   38144 0
ohci1394 50868 9 dv1394
ieee1394 122216 3 raw1394,dv1394,ohci1394

which means the important raw1394 module is loaded. If not, try

sudo modprobe raw1394

lspci | grep 1394 should confirm that your firewire interface is working

02:00.0 FireWire(IEEE 1394):Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Finally, 

ffado-test ListDevices

=== 1394 PORT 0 ===
Node id GUID VendorId ModelId Vendor - Model
0 0x00309500a0046058 0x00003095 0x00000000 Linux - ohci1394 -
1 0x00148697c4428959 0x00001486 0x0000AF12 Echo Digital Audio - AudioFire12

Actually, that's not what I get with either of my FireWire devices! My last bit of advice is to turn networking, especially wifi, off while using the FireWire for audio otherwise the audio will glitch because of 'xruns' (buffer overruns, I think) in jack.

I'm typing this in from my notes using my alternative Kubuntu installation and I haven't bothered to enable FireWire in Kubuntu. There is no point without an RT kernel.

Run qjackctl and use 'set up' to create a Firewire setting. Change the name of the default setting (alsa) to Firewire. Save it. Then change the device to Firewire (not Freebob) and save the changes again. Now, you will be able to choose either Firewire or (Default) from the options list by right clicking on the System Tray icon. If you get a message of 'unable to connect to device' with the FireWire setting then make sure that the default and the firewire settings are similar. Sometimes the firewire buffer numbers and size get set too low and jack complains. Once it is running reliably, you can then start to reduce the latency. The lowest target is a buffer setting of 3x64.

So that you don't have loads of jack windows to get in the way, go to the  qjackctl set up/misc. settings and enable qjackctl in the system tray and start it minimised. Dont set jack to start when qjackctl runs. If you add the icon to the panel you can start qjackctl from there. After starting jack, right click on the System Tray icon and choose whether you want to go Firewire or (default)- the setting for alsa. Finally, right-click and choose Start and see how it goes. If the red arrow turns green, you are up and running. Right click and choose patchpanel and add your system (audio) and midi ports (usually under alsa rather than midi). Then right-click to close patch panel and right-click to open connections. Patch an input to the output and try out a microphone.

Best of luck. You will feel great when it finally bursts into life.

---

### Post by Jordan122 on 2009-08-29
Thanks for the replies really!

I did not have any raw1394.rules file so I added one called 60-rawr1394.rules and copied what you wrote and placed it in there. I think I had manually assigned it to the group already using command prompt yesterday but I am not sure... one thing to note is... when I ...

jordan@psalms:~$ sudo lsmod | grep 1394
raw1394                32732  0 
ohci1394               38576  0 
ieee1394               94660  2 raw1394,ohci1394

Strange that raw shows a 0 there... is this normal?

finally,

jordan@psalms:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 1.999.40-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
00555554254: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
no message buffer overruns
jordan@psalms:~$ 



Ive seen that message could not parse configrom.cpp over and over again in my "travels" to get this working.

I started with the most recent ubuntu distro jaunty, and I command line upgraded to ubuntu studio.
I added gscanbus.

Maybe I messed it all up ahaha and should just start over?

Im going to download the 64 bit of ubuntu studio from the website and just start from scratch, and now that I know what I am looking at a little bit, Im going to follow the directions you guys gave.

One thing about my interface is that, if it talks via firewire to anything a yellow light comes on. I have yet to see that from all I have done heh.

---

### Post by royleith on 2009-09-02
Hi,

You don't say what happens to a 

lspci | grep 1394

Is your current installation recognising the Firewire Card/chipset? The fact that gscanbus found it once suggests that it's in the kernel modules, but has not been loaded properly.

I think a new install of the latest dist. is a good idea. If you have a dual core or an Intel multi-thread processor (one that does virtual multi-core) then you need to add maxcpus=1 to the kernel line in Grub. A new install also ensures the most recent version of FFADO device support is in place.

Regards
Roy Leith

---

### Post by Stochastic on 2009-09-02
Hello,

I couldn't help but notice that your ffado version is 1.999.40 but this version was never included in ANY official Ubuntu repository.  Only 2.0rc versions were included.  I assume in your setup steps you have tried to install ffado from an untrusted source?  This is most likely from an old how-to on getting ffado working - don't read those instructions again, they're unsafe and WAY too much effort.

What I would recommend at this point is a fresh install of Ubuntu Studio 9.04 (Jaunty).  This will come with ffado already installed.  Just a few configuration steps should be needed, which trulan outlines quite well in his above post.

If you get lost in that process, don't go rummaging around in forum archives looking for the hint you're missing (as you've found this can be dangerous to you system), simply post here and I (or someone else equally knowledgeable) will try to answer promptly.

Hope that helps.

---

### Post by halalkebabhut on 2010-01-04
Hi,

I've been finding that jack intermittently shuts down when I'm connected to my Sonar SPS 66 (same as edirol FA-60). I'm on Karmic Studio recently updated from a Jaunty install.

I notice from the message window in Qjack that my version of FFado is also a 1.999.43 (see below)

   *00078640718:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51*
 
I've heard that older versions of ffado cause instability but when I look into my synaptic it shows the latest 2.0rc version as installed. I tried reinstalling all ffado stuff but to no avail. Have you any idea what is going on here ?

---

### Post by AutoStatic on 2010-01-04
Hello halalkebabhut,

1.999.43 is the version that ships with Karmic: [http://packages.ubuntu.com/karmic/i386/libffado1/filelist](http://packages.ubuntu.com/karmic/i386/libffado1/filelist)

But do you get any error messages? Could you post those? And maybe you could open a new thread, first of all you have a different Firewire device and second I think your issue differs from the one described in this thread.

---

### Post by halalkebabhut on 2010-01-04
Thanks 

I posted here with some error messages

[http://ubuntuforums.org/showthread.php?t=1372243](http://ubuntuforums.org/showthread.php?t=1372243)

---

