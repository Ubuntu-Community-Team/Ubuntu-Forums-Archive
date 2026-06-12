---
title: "Alesis Multimix 16 Firewire with FFADO"
date: 2009-02-16
forum: Ubuntu Studio
---

### Post by cggaret on 2009-02-16
With the help of Adrian Knoth I have gotten my Alesis Multimix 16 Firewire working flawlessly with FFADO and Jack.  The changes have been made upstream to FFADO (once again thanks to Adrian Knoth).  If you want to get yours working, follow the steps at [http://subversion.ffado.org/]("http://subversion.ffado.org/") and remember to set ENABLE_DICE=True when compiling the latest version from svn.  More information can be found here [http://subversion.ffado.org/wiki/Alesis]("http://subversion.ffado.org/wiki/Alesis").  Remember to follow all of the installation instructions, including recompiling jack.  I hope this helps.  Happy recording.

---

### Post by evazan on 2009-04-14
I could use some help with this...with a Multimix 8 but i get the following when i run 
```
jackd -d firewire
```
> [chris@evazan libffado]$ jackd -d firewire
no message buffer overruns
jackd 0.115.6
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with POSIX SHM support.
loading driver ..
04859330214:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.41-1536 built Apr 14 2009 17:22:03
04872111236: Error (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
04872153957: Error (avc_avdevice.cpp)[  88] probe: Subunit info command failed
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns

Here is my ffado-test-streaming...any help would be great...thanks

```

04593486923: Debug (teststreaming3.cpp)[ 265] main: verbose level = 6
04593486970: Debug (teststreaming3.cpp)[ 286] main: FFADO streaming test application (3)
04593486993:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.41-1536 built Apr 14 2009 17:22:03
04593487135: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
04593487152: Debug (StreamProcessorManager.cpp)[1523] setVerboseLevel: Setting verbose level to 6...
04593487169: Debug (devicemanager.cpp)[1084] setVerboseLevel: Setting verbose level to 6...
04593487179: Warning (ffado.cpp)[ 121] ffado_streaming_init: Realtime scheduling is not enabled. This will cause significant reliability issues.
04593487192: Debug (ffado.cpp)[ 148] ffado_streaming_init: setting slave mode to 0
04593487222: Debug (ffado.cpp)[ 154] ffado_streaming_init: setting snoop mode to 0
04593487445: Debug (Configuration.cpp)[  62] openFile: Could not open file: ~/.ffado/configuration
04593488498: Debug (devicemanager.cpp)[ 168] initialize: Found 1 firewire adapters (ports)
04593488548: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
04593488561: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
04593488594: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
04593488607: Debug (IsoHandlerManager.cpp)[ 531] setThreadParameters: (0x22ec730) switch to: (rt=0, prio=1)...
04593488644: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
04593488669: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase
04593488678: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
04593488700: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
04593488719: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_xmit
04593488730: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
04593488748: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
04593488770: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_recv
04593488778: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
04593488787: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
04593488797: Debug (CycleTimerHelper.cpp)[ 231] setThreadParameters: (0x22ec7b0) switch to: (rt=0, prio=1)...
04593488824: Debug (Watchdog.cpp)[ 200] start: (0x22ec9a0) Starting watchdog...
04593488832: Debug (Watchdog.cpp)[ 201] start: Create hartbeat task/thread for 0x22ec9a0...
04593488847: Debug (Watchdog.cpp)[ 215] start:  hartbeat task: 0x22eca00, thread 0x22eca70...
04593488854: Debug (Watchdog.cpp)[ 217] start: Create check task/thread for 0x22ec9a0...
04593488865: Debug (Watchdog.cpp)[ 231] start:  check task: 0x22ecab0, thread 0x22ecb20...
04593489102: Debug (Watchdog.cpp)[ 249] start: (0x22ec9a0) Watchdog running...
04593489178: Debug (ieee1394service.cpp)[ 280] initialize: This system supports the raw1394_read_cycle_timer call, using it.
04593489237: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.min_split_timeout_usecs
04593489266: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.min_split_timeout_usecs
04593489274: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.min_split_timeout_usecs' not found
04593489293: Debug (ieee1394service.cpp)[ 917] getSplitTimeoutUsecs: reading SPLIT_TIMEOUT on node 0x1...
04593489359: Debug (ieee1394service.cpp)[ 924] getSplitTimeoutUsecs:  READ HI: 0x7FFF00000000
04593489400: Debug (ieee1394service.cpp)[ 931] getSplitTimeoutUsecs:  READ LO: 0x7FFF00000019
04593489408: Debug (ieee1394service.cpp)[ 325] initialize: Minimum SPLIT_TIMEOUT: 1000000. Current: 100000
04593489421: Debug (ieee1394service.cpp)[ 889] setSplitTimeoutUsecs: setting SPLIT_TIMEOUT on node 0x1 to 1000124usecs...
04593489492: Debug (ieee1394service.cpp)[ 917] getSplitTimeoutUsecs: reading SPLIT_TIMEOUT on node 0x1...
04593489523: Debug (ieee1394service.cpp)[ 924] getSplitTimeoutUsecs:  READ HI: 0x7FFF01000000
04593489594: Debug (ieee1394service.cpp)[ 931] getSplitTimeoutUsecs:  READ LO: 0x7FFF00000000
04593489608: Debug (CycleTimerHelper.cpp)[ 116] Start: Start 0x22ec7b0...
04593489616: Debug (CycleTimerHelper.cpp)[ 149] initValues: (0x22ec7b0) Init values...
04593489627: Debug (CycleTimerHelper.cpp)[ 156] initValues: Read CTR...
04593489638: Debug (CycleTimerHelper.cpp)[ 167] initValues:  read : CTR:  1564737869, local:  1239755173228321
04593489648: Debug (CycleTimerHelper.cpp)[ 173] initValues:   ctr   : 0x5D44014D  1146421581 (046s 5184cy 0333ticks)
04593489655: Debug (CycleTimerHelper.cpp)[ 179] initValues: requesting DLL re-init...
04593490734: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0x22ec7b0) First run
04593490742: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
04593490765: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 140733198303232, m_dll_e2: 4915200.000000
04593490775: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1239755173229415.000000, next: 1239755173429415.000000
04593490788: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 1146448471.000000, next: 1151363671.000000
04593490798: Debug (CycleTimerHelper.cpp)[ 188] initValues: ready...
04593490813: Debug (Watchdog.cpp)[ 281] registerThread: (0x22ec9a0) Adding thread 0x22ef120
04593490892: Debug (CycleTimerHelper.cpp)[ 195] Init: Initialize 0x22ec7b0...
04593490911: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0x22ef290)
04593490954: Debug (CycleTimerHelper.cpp)[ 393] Execute: (0x22ec7b0) have to retry CTR read, diff unrealistic: diff: 1146453875, max: +/- 140338056399872 (try: 10) 0
04593490972: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
04593490980: Debug (IsoHandlerManager.cpp)[ 572] init: Initializing ISO manager 0x22ec730...
04593491013: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
04593491034: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase
04593491045: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
04593491064: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
04593491086: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_xmit
04593491094: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
04593491118: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
04593491137: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_recv
04593491178: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
04593491200: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
04593491221: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
04593491229: Debug (Configuration.cpp)[ 267] getValueForSetting: path 'ieee1394.isomanager.isotask_activity_timeout_usecs' not found
04593491239: Debug (IsoHandlerManager.cpp)[ 593] init: Create iso thread for 0x22ec730 transmit...
04593491248: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
04593491259: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
04593491265: Debug (IsoHandlerManager.cpp)[ 612] init: Create iso thread for 0x22ec730 receive...
04593491286: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
04593491294: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
04593491303: Debug (Watchdog.cpp)[ 281] registerThread: (0x22ec9a0) Adding thread 0x22ef490
04593491315: Debug (Watchdog.cpp)[ 281] registerThread: (0x22ec9a0) Adding thread 0x22ef670
04593491326: Debug (PosixThread.cpp)[ 150] Start: (ISOXMT) Create non RT thread 0x22ef490
04593491358: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISOXMT) ThreadHandler: start 0x22ef490
04593491154: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0x22ec7b0) First run
04593491387: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
04593491400: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 140338061312000, m_dll_e2: 4915200.000000
04593491409: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1239755173229838.000000, next: 1239755173429838.000000
04593491422: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 1146458837.000000, next: 1151374037.000000
04593491461: Debug (PosixThread.cpp)[ 150] Start: (ISORCV) Create non RT thread 0x22ef670
04593491495: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISORCV) ThreadHandler: start 0x22ef670
04593491539: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
04593491551: Debug (IsoHandlerManager.cpp)[ 531] setThreadParameters: (0x22ec730) switch to: (rt=0, prio=1)...
04593491575: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
04593491597: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase
04593491604: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
04593491625: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
04593491644: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_xmit
04593491654: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
04593491672: Debug (Configuration.cpp)[ 306] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
04593491693: Debug (Configuration.cpp)[ 306] getSetting:   /usr/share/libffado/configuration has no setting ieee1394.isomanager.prio_increase_recv
04593491701: Debug (Configuration.cpp)[ 246] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
04593491711: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISOXMT, 0x22ef490) Drop realtime
04593491728: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISORCV, 0x22ef670) Drop realtime
04593491738: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
04593491745: Debug (CycleTimerHelper.cpp)[ 231] setThreadParameters: (0x22ec7b0) switch to: (rt=0, prio=1)...
04593491755: Debug (PosixThread.cpp)[ 230] DropRealTime: (CTRHLP, 0x22ef120) Drop realtime
04593491768: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0x22efa90)
04593491785: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
04593491805: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
04593491817: Debug (StreamProcessorManager.cpp)[1523] setVerboseLevel: Setting verbose level to 6...
04593491828: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
04593491838: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
04593491844: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
04593491854: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
04593491860: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
04593491870: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
04593491878: Debug (devicemanager.cpp)[1084] setVerboseLevel: Setting verbose level to 6...
04593491896: Debug (devicemanager.cpp)[ 359] discover: Probing node 0...
04593497108: Debug (PosixThread.cpp)[  76] ThreadHandler: (WDGHBT) ThreadHandler: start 0x22eca70
04594596252: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04595646268: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04596697077: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04597746252: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04598796251: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04599846255: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
04599875019: Debug (devicemanager.cpp)[ 359] discover: Probing node 1...
04599875033: Debug (devicemanager.cpp)[ 362] discover: Skipping local node (1)...
04599875085: Debug (DeviceStringParser.cpp)[ 376] show: DeviceStringParser: 0x22eb7d0
04599875120: Debug (devicemanager.cpp)[ 534] discover: Probing node 0...
04600963741: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04602012913: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04603063747: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04604112919: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04605162918: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
04606212917: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
04606241112: Debug (configrom.cpp)[ 560] printConfigRomDebug: Config ROM
04606241125: Debug (configrom.cpp)[ 561] printConfigRomDebug: 	Current Node Id:	0
04606241148: Debug (configrom.cpp)[ 562] printConfigRomDebug: 	GUID:			0x00059504000F5835
04606241157: Debug (configrom.cpp)[ 563] printConfigRomDebug: 	Vendor Name:		Alesis
04606241168: Debug (configrom.cpp)[ 564] printConfigRomDebug: 	Model Name:		MultiMix Firewire
04606241176: Debug (configrom.cpp)[ 565] printConfigRomDebug: 	Node Vendor ID:		0x000595
04606241190: Debug (configrom.cpp)[ 566] printConfigRomDebug: 	Model Id:		0x00000000
04606241198: Debug (configrom.cpp)[ 567] printConfigRomDebug: 	Unit Specifier ID:	0x000595
04606241209: Debug (configrom.cpp)[ 568] printConfigRomDebug: 	Unit version:		0x00000001
04606241217: Debug (configrom.cpp)[ 569] printConfigRomDebug: 	ISO resource manager:	1
04606241227: Debug (configrom.cpp)[ 570] printConfigRomDebug: 	Cycle master capable:	1
04606241234: Debug (configrom.cpp)[ 571] printConfigRomDebug: 	Bus manager capable:	0
04606241245: Debug (configrom.cpp)[ 572] printConfigRomDebug: 	Cycle clock accuracy:	255
04606241253: Debug (configrom.cpp)[ 574] printConfigRomDebug: 	Max rec:		8 (max asy payload: 512 bytes)
04606241266: Debug (devicemanager.cpp)[ 946] getDriverForDevice: Probing for supported device...
04606241274: Debug (devicemanager.cpp)[ 911] getDriverForDeviceDo: Trying BeBoB...
04606241323: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
04606241407: Debug (devicemanager.cpp)[ 918] getDriverForDeviceDo: Trying ECHO Audio FireWorks...
04606241434: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
04606241478: Debug (devicemanager.cpp)[ 926] getDriverForDeviceDo: Trying Generic AV/C...
04606241504: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
04606241547: Debug (devicemanager.cpp)[ 933] getDriverForDeviceDo: Trying Motu...
04606241563: Debug (devicemanager.cpp)[ 954] getDriverForDevice:  no supported device found, trying generic support...
04606241570: Debug (devicemanager.cpp)[ 911] getDriverForDeviceDo: Trying BeBoB...
04606262240: Debug (ieee1394service.cpp)[ 763] doFcpTransactionTry: write of FCP request failed
04606262261: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 0 failed
04606263415: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606263428: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 1 failed
04606264502: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606264512: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 2 failed
04606265590: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606265604: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 3 failed
04606266677: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606266689: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 4 failed
04606267763: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606267774: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 5 failed
04606268846: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606268855: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 6 failed
04606269927: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606269935: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 7 failed
04606271008: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606271017: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 8 failed
04606272089: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606272097: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 9 failed
04606273169: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606273177: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 10 failed
04606274250: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606274258: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 11 failed
04606275330: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606275338: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 12 failed
04606276410: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606276419: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 13 failed
04606277493: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606277504: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 14 failed
04606278577: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606278585: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 15 failed
04606279659: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606279667: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 16 failed
04606280742: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606280751: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 17 failed
04606281823: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606281831: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 18 failed
04606282889: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606282897: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 19 failed
04606283974: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
04606283983: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
04606283993: Debug (avc_generic.cpp)[ 265] fire: no response
04606284009: Error (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
04606284028: Debug (devicemanager.cpp)[ 918] getDriverForDeviceDo: Trying ECHO Audio FireWorks...
04606284063: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606284074: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 0 failed
04606285143: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606285155: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 1 failed
04606286226: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606286239: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 2 failed
04606287309: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606287322: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 3 failed
04606288391: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606288402: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 4 failed
04606289482: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606289494: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 5 failed
04606290562: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606290574: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 6 failed
04606291642: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606291654: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 7 failed
04606292722: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606292736: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 8 failed
04606293805: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606293817: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 9 failed
04606294887: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606294899: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 10 failed
04606295976: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606295990: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 11 failed
04606297063: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606297076: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 12 failed
04606298144: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606298156: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 13 failed
04606299232: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606299246: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 14 failed
04606300315: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606300327: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 15 failed
04606301396: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606301407: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 16 failed
04606302476: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606302488: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 17 failed
04606303560: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606303572: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 18 failed
04606304619: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606304631: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 19 failed
04606305705: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
04606305719: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
04606305726: Debug (avc_generic.cpp)[ 265] fire: no response
04606305744: Debug (devicemanager.cpp)[ 926] getDriverForDeviceDo: Trying Generic AV/C...
04606305768: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606305780: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 0 failed
04606306845: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606306857: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 1 failed
04606307926: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606307938: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 2 failed
04606309007: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606309018: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 3 failed
04606310091: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606310104: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 4 failed
04606311173: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606311185: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 5 failed
04606312253: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606312270: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 6 failed
04606313344: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606313356: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 7 failed
04606314432: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606314445: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 8 failed
04606315519: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606315531: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 9 failed
04606316604: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606316616: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 10 failed
04606317689: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606317702: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 11 failed
04606318776: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606318789: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 12 failed
04606319862: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606319875: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 13 failed
04606320948: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606320961: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 14 failed
04606322035: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606322046: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 15 failed
04606323117: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606323131: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 16 failed
04606324199: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606324211: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 17 failed
04606325280: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606325292: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 18 failed
04606326363: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
04606326375: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 19 failed
04606327447: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
04606327459: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
04606327466: Debug (avc_generic.cpp)[ 265] fire: no response
04606327476: Error (avc_avdevice.cpp)[  88] probe: Subunit info command failed
04606327486: Debug (devicemanager.cpp)[ 933] getDriverForDeviceDo: Trying Motu...
04606327496: Debug (devicemanager.cpp)[ 961] getDriverForDevice:  device not supported...
04606327511: Debug (devicemanager.cpp)[ 534] discover: Probing node 1...
04606327521: Debug (devicemanager.cpp)[ 537] discover: Skipping local node (1)...
04606327530: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
04606327543: Debug (devicemanager.cpp)[1089] showDeviceInfo: ===== Device Manager =====
04606327554: Debug (Element.cpp)[ 121] show: Element DeviceManager
04606327564: Debug (devicemanager.cpp)[1097] showDeviceInfo: --- IEEE1394 Service  0 ---
04606327579: Debug (ieee1394service.cpp)[1380] show: Port:  0
04606327590: Debug (ieee1394service.cpp)[1381] show:  Name: ohci1394
04606327597: Debug (ieee1394service.cpp)[1383] show:  CycleTimerHelper: 0x22ec7b0, IsoManager: 0x22ec730, WatchDog: 0x22ec9a0
04606327607: Debug (ieee1394service.cpp)[1388] show:  Time: 01461901574 (059s 3879cy 1286ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
04606327654: Fatal (ffado.cpp)[ 174] ffado_streaming_init: There are no devices on the bus
04606327668: Debug (Configuration.cpp)[ 137] save: Not saving temporary config file: temporary
04606327678: Debug (Configuration.cpp)[ 134] save: Not saving readonly config file: /usr/share/libffado/configuration
04606327734: Debug (IsoHandlerManager.cpp)[1068] stopHandlers: enter...
04606327746: Debug (IsoHandlerManager.cpp)[ 936] pruneHandlers: enter...
04606327763: Debug (PosixThread.cpp)[ 178] Stop: (ISOXMT) Stop 0x22ef490 (thread: 0x7fa30e8c4950)
04606329692: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISOXMT) ThreadHandler: exit 0x22ef490
04606329727: Debug (PosixThread.cpp)[ 182] Stop: (ISOXMT) Stopped 0x22ef490 (thread: 0x7fa30e8c4950)
04606329744: Debug (PosixThread.cpp)[ 178] Stop: (ISORCV) Stop 0x22ef670 (thread: 0x7fa30e0c3950)
04606329754: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISORCV) ThreadHandler: exit 0x22ef670
04606329772: Debug (PosixThread.cpp)[ 182] Stop: (ISORCV) Stopped 0x22ef670 (thread: 0x7fa30e0c3950)
04606329783: Debug (PosixThread.cpp)[ 178] Stop: (CTRHLP) Stop 0x22ef120 (thread: 0x7fa30f0c5950)
04606491244: Debug (PosixThread.cpp)[  86] ThreadHandler: (CTRHLP) ThreadHandler: exit 0x22ef120
04606491287: Debug (PosixThread.cpp)[ 182] Stop: (CTRHLP) Stopped 0x22ef120 (thread: 0x7fa30f0c5950)
04606491310: Debug (ieee1394service.cpp)[1084] remBusResetHandler: Removing busreset handler (0x22ef290)
04606491320: Debug (ieee1394service.cpp)[1091] remBusResetHandler:  found
04606491468: Debug (PosixThread.cpp)[ 164] Kill: (WDGCHK) Kill 0x22ecb20 (thread: 0x7fa30f8c6950)
04606491535: Debug (PosixThread.cpp)[ 168] Kill: (WDGCHK) Killed 0x22ecb20 (thread: 0x7fa30f8c6950)
04606491549: Debug (PosixThread.cpp)[ 164] Kill: (WDGHBT) Kill 0x22eca70 (thread: 0x7fa3100c7950)
04606491635: Debug (PosixThread.cpp)[ 168] Kill: (WDGHBT) Killed 0x22eca70 (thread: 0x7fa3100c7950)
04606491723: Error (teststreaming3.cpp)[ 315] main: Could not init Ffado Streaming layer
no message buffer overruns

```

---

### Post by cggaret on 2009-04-15
I don't see an error for dice_avdevice.cpp.  Did you set ENABLE_DICE=True when you compiled?  And once again make sure you have the latest version from svn.  The links in my previous post will show you how to do that.  If you've met those requirements, then run ffado-dbus-server -v6 and post that output.  It will be a lot of output, so don't run it for too long.  Ctrl-c  will stop it.

-Chris

---

### Post by evazan on 2009-04-16
Hey! Thanks for the response! I got the latest svn and i used scons ENABLE_DICE=true. So here is the output of the ffado-dbus-server -v6... Also you should i know i am using Archlinux. Here is the PKGBUILD i used.
> # Contributor: Jon Kristian Nilsen <jokr.nilsen@gmail.com>

pkgname=libffado-svn
pkgver=1536
pkgrel=1
pkgdesc="The FFADO project aims to provide a generic, open-source solution for the support \
of FireWire based audio devices for the Linux platform."
arch=('i686' 'x86_64')
url="http://ffado.org"
license=('GPL')
depends=('alsa-lib>=1.0.0' 'glibc' 'libraw1394>=1.3.0' 'libiec61883>=1.1.0' 'libavc1394>=0.5.3' 'libxml++2>=2.14.0' 'pyqt')
makedepends=('subversion' 'scons')
provides=('libffado-svn')
install=

source=()
md5sums=()

_svntrunk=http://subversion.ffado.org/ffado/branches/libffado-2.0
_svnmod=libffado-svn

build() {
  cd $startdir/src

  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi

  msg "SVN checkout done or server timeout"
  msg "Starting make..."

  #rm -r $startdir/src/$_svnmod-build
  cp -r $_svnmod $_svnmod-build
  cd $_svnmod-build

  # Build ffado-svn
  scons ENABLE_DICE=true PREFIX="/usr" \
  DESTDIR="${startdir}/pkg" \
  install || return 1
}
# vim:syntax=sh

```
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 1.999.41-1536
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

35507459345:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
35507462664: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
35507462696: Debug (StreamProcessorManager.cpp)[1523] setVerboseLevel: Setting verbose level to 6...
35507462713: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
35507462723: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
35507462730: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
35507462740: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
35507462747: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
35507462756: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
35507462764: Debug (devicemanager.cpp)[1084] setVerboseLevel: Setting verbose level to 6...
35507462779: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
35507462801: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
35507462811: Debug (StreamProcessorManager.cpp)[1523] setVerboseLevel: Setting verbose level to 6...
35507462818: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
35507462831: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
35507462837: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
35507462847: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
35507462853: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
35507462863: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
35507462869: Debug (devicemanager.cpp)[1084] setVerboseLevel: Setting verbose level to 6...
35507462888: Debug (devicemanager.cpp)[ 359] discover: Probing node 0...
35507462977: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0xe3e6c0) First run
35507463003: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
35507463023: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 1239922703532032, m_dll_e2: 4915200.000000
35507463037: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1239924568254798.000000, next: 1239924568454798.000000
35507463049: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 907594859.000000, next: 912510059.000000
35508509807: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
35509603985: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35510653982: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35511703161: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35512753154: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35513803987: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35514853983: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
35514882059: Debug (devicemanager.cpp)[ 359] discover: Probing node 1...
35514882076: Debug (devicemanager.cpp)[ 362] discover: Skipping local node (1)...
35514882125: Debug (DeviceStringParser.cpp)[ 376] show: DeviceStringParser: 0xe3d6e0
35514882165: Debug (devicemanager.cpp)[ 534] discover: Probing node 0...
35515976489: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35517026487: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35518077324: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35519126488: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35520177332: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
35521227311: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
35521256080: Debug (configrom.cpp)[ 560] printConfigRomDebug: Config ROM
35521256097: Debug (configrom.cpp)[ 561] printConfigRomDebug: 	Current Node Id:	0
35521256106: Debug (configrom.cpp)[ 562] printConfigRomDebug: 	GUID:			0x00059504000F5835
35521256118: Debug (configrom.cpp)[ 563] printConfigRomDebug: 	Vendor Name:		Alesis
35521256126: Debug (configrom.cpp)[ 564] printConfigRomDebug: 	Model Name:		MultiMix Firewire
35521256137: Debug (configrom.cpp)[ 565] printConfigRomDebug: 	Node Vendor ID:		0x000595
35521256145: Debug (configrom.cpp)[ 566] printConfigRomDebug: 	Model Id:		0x00000000
35521256155: Debug (configrom.cpp)[ 567] printConfigRomDebug: 	Unit Specifier ID:	0x000595
35521256163: Debug (configrom.cpp)[ 568] printConfigRomDebug: 	Unit version:		0x00000001
35521256173: Debug (configrom.cpp)[ 569] printConfigRomDebug: 	ISO resource manager:	1
35521256181: Debug (configrom.cpp)[ 570] printConfigRomDebug: 	Cycle master capable:	1
35521256191: Debug (configrom.cpp)[ 571] printConfigRomDebug: 	Bus manager capable:	0
35521256198: Debug (configrom.cpp)[ 572] printConfigRomDebug: 	Cycle clock accuracy:	255
35521256210: Debug (configrom.cpp)[ 574] printConfigRomDebug: 	Max rec:		8 (max asy payload: 512 bytes)
35521256225: Debug (devicemanager.cpp)[ 946] getDriverForDevice: Probing for supported device...
35521256236: Debug (devicemanager.cpp)[ 911] getDriverForDeviceDo: Trying BeBoB...
35521256288: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
35521256375: Debug (devicemanager.cpp)[ 918] getDriverForDeviceDo: Trying ECHO Audio FireWorks...
35521256399: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
35521256447: Debug (devicemanager.cpp)[ 926] getDriverForDeviceDo: Trying Generic AV/C...
35521256480: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
35521256529: Debug (devicemanager.cpp)[ 933] getDriverForDeviceDo: Trying Motu...
35521256542: Debug (devicemanager.cpp)[ 954] getDriverForDevice:  no supported device found, trying generic support...
35521256559: Debug (devicemanager.cpp)[ 911] getDriverForDeviceDo: Trying BeBoB...
35521277210: Debug (ieee1394service.cpp)[ 763] doFcpTransactionTry: write of FCP request failed
35521277240: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 0 failed
35521278315: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521278328: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 1 failed
35521279398: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521279412: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 2 failed
35521280485: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521280497: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 3 failed
35521281568: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521281581: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 4 failed
35521282649: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521282662: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 5 failed
35521283731: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521283741: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 6 failed
35521284811: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521284827: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 7 failed
35521285896: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521285912: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 8 failed
35521286980: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521286993: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 9 failed
35521288062: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521288076: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 10 failed
35521289145: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521289158: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 11 failed
35521290226: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521290241: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 12 failed
35521291309: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521291323: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 13 failed
35521292391: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521292404: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 14 failed
35521293472: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521293485: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 15 failed
35521294558: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521294572: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 16 failed
35521295644: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521295657: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 17 failed
35521296726: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521296738: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 18 failed
35521297807: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521297820: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 19 failed
35521298888: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
35521298901: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
35521298908: Debug (avc_generic.cpp)[ 265] fire: no response
35521298927: Error (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
35521298943: Debug (devicemanager.cpp)[ 918] getDriverForDeviceDo: Trying ECHO Audio FireWorks...
35521298983: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521298990: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 0 failed
35521300066: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521300076: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 1 failed
35521301148: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521301158: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 2 failed
35521302230: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521302240: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 3 failed
35521303312: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521303322: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 4 failed
35521304394: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521304404: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 5 failed
35521305476: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521305486: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 6 failed
35521306563: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521306573: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 7 failed
35521307655: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521307664: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 8 failed
35521308737: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521308746: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 9 failed
35521309799: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521309809: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 10 failed
35521310882: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521310892: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 11 failed
35521311964: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521311973: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 12 failed
35521313044: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521313052: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 13 failed
35521314126: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521314157: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 14 failed
35521315239: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521315259: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 15 failed
35521316340: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521316359: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 16 failed
35521317440: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521317460: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 17 failed
35521318539: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521318560: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 18 failed
35521319638: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521319659: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 19 failed
35521320736: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
35521320757: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
35521320774: Debug (avc_generic.cpp)[ 265] fire: no response
35521320793: Debug (devicemanager.cpp)[ 926] getDriverForDeviceDo: Trying Generic AV/C...
35521320820: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521320840: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 0 failed
35521321920: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521321938: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 1 failed
35521323017: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521323034: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 2 failed
35521324113: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521324133: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 3 failed
35521325216: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521325234: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 4 failed
35521326318: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521326335: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 5 failed
35521327413: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521327433: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 6 failed
35521328511: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521328531: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 7 failed
35521329610: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521329627: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 8 failed
35521330711: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521330728: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 9 failed
35521331808: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521331823: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 10 failed
35521332901: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521332915: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 11 failed
35521334001: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521334015: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 12 failed
35521335098: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521335113: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 13 failed
35521336196: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521336210: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 14 failed
35521337295: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521337309: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 15 failed
35521338392: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521338406: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 16 failed
35521339488: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521339502: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 17 failed
35521340586: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521340600: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 18 failed
35521341682: Debug (ieee1394service.cpp)[ 747] doFcpTransactionTry: could not start FCP listen (err=-1, errno=114)
35521341696: Debug (ieee1394service.cpp)[ 698] doFcpTransaction: FCP transaction try 19 failed
35521342772: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
35521342786: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
35521342802: Debug (avc_generic.cpp)[ 265] fire: no response
35521342814: Error (avc_avdevice.cpp)[  88] probe: Subunit info command failed
35521342832: Debug (devicemanager.cpp)[ 933] getDriverForDeviceDo: Trying Motu...
35521342845: Debug (devicemanager.cpp)[ 961] getDriverForDevice:  device not supported...
35521342868: Debug (devicemanager.cpp)[ 534] discover: Probing node 1...
35521342881: Debug (devicemanager.cpp)[ 537] discover: Skipping local node (1)...
35521342900: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
35521342916: Debug (devicemanager.cpp)[1089] showDeviceInfo: ===== Device Manager =====
35521342936: Debug (Element.cpp)[ 121] show: Element DeviceManager
35521342949: Debug (devicemanager.cpp)[1097] showDeviceInfo: --- IEEE1394 Service  0 ---
35521342973: Debug (ieee1394service.cpp)[1380] show: Port:  0
35521342988: Debug (ieee1394service.cpp)[1381] show:  Name: ohci1394
35521343003: Debug (ieee1394service.cpp)[1383] show:  CycleTimerHelper: 0xe3e6c0, IsoManager: 0xe3e640, WatchDog: 0xe3e8b0
35521343017: Debug (ieee1394service.cpp)[1388] show:  Time: 01248682512 (050s 6472cy 0528ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
35521343087: Debug (devicemanager.cpp)[ 295] registerNotification: register 0xe41a20...
35521343112: Debug (devicemanager.cpp)[ 295] registerNotification: register 0xe41b10...
35521343152:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
35521345174: Debug (Element.cpp)[  80] lockControl: Locking tree...
35521345856: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
35521345896: Debug (StreamProcessorManager.cpp)[1523] setVerboseLevel: Setting verbose level to 6...
35521345917: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
35521345937: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
35521345950: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
35521345970: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
35521345983: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
35521346002: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
35521346016: Debug (devicemanager.cpp)[1084] setVerboseLevel: Setting verbose level to 6...
35521346036: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager'
35521346052: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0xe52390)
35521346096: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
35521346242: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
35521346281: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
35521346381: Debug (Element.cpp)[  89] unlockControl: Unlocking tree...
35521346411:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
35521346426: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
^C35530564638: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
35530564683: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
35530564704:  (ffado-dbus-server.cpp)[ 339] main:  Stopping...
35530564720: Debug (devicemanager.cpp)[ 313] unregisterNotification: unregister 0xe41a20...
35530564747: Debug (devicemanager.cpp)[ 313] unregisterNotification: unregister 0xe41b10...
35530564766: Debug (controlserver.cpp)[ 165] ~Container: Deleting Container on '/org/ffado/Control/DeviceManager'
35530564957: Debug (Element.cpp)[ 143] remSignalHandler: Removing signal handler (0xe52390)
35530564984: Debug (Element.cpp)[ 150] remSignalHandler:  found
35530565594: Debug (Configuration.cpp)[ 137] save: Not saving temporary config file: temporary
35530565619: Debug (Configuration.cpp)[ 134] save: Not saving readonly config file: /usr/share/libffado/configuration
35530565690: Debug (IsoHandlerManager.cpp)[1068] stopHandlers: enter...
35530565710: Debug (IsoHandlerManager.cpp)[ 936] pruneHandlers: enter...
35530565738: Debug (PosixThread.cpp)[ 178] Stop: (ISOXMT) Stop 0xe41420 (thread: 0x7fb818086950)
35530575579: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISOXMT) ThreadHandler: exit 0xe41420
35530575646: Debug (PosixThread.cpp)[ 182] Stop: (ISOXMT) Stopped 0xe41420 (thread: 0x7fb818086950)
35530575663: Debug (PosixThread.cpp)[ 178] Stop: (ISORCV) Stop 0xe41600 (thread: 0x7fb817885950)
35530584267: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISORCV) ThreadHandler: exit 0xe41600
35530584307: Debug (PosixThread.cpp)[ 182] Stop: (ISORCV) Stopped 0xe41600 (thread: 0x7fb817885950)
35530584331: Debug (PosixThread.cpp)[ 178] Stop: (CTRHLP) Stop 0xe41030 (thread: 0x7fb818887950)
35530663065: Debug (PosixThread.cpp)[  86] ThreadHandler: (CTRHLP) ThreadHandler: exit 0xe41030
35530663129: Debug (PosixThread.cpp)[ 182] Stop: (CTRHLP) Stopped 0xe41030 (thread: 0x7fb818887950)
35530663146: Debug (ieee1394service.cpp)[1084] remBusResetHandler: Removing busreset handler (0xe41220)
35530663165: Debug (ieee1394service.cpp)[1091] remBusResetHandler:  found
35530663300: Debug (PosixThread.cpp)[ 164] Kill: (WDGCHK) Kill 0xe3ea30 (thread: 0x7fb819088950)
35530663383: Debug (PosixThread.cpp)[ 168] Kill: (WDGCHK) Killed 0xe3ea30 (thread: 0x7fb819088950)
35530663405: Debug (PosixThread.cpp)[ 164] Kill: (WDGHBT) Kill 0xe3e980 (thread: 0x7fb819889950)
35530663508: Debug (PosixThread.cpp)[ 168] Kill: (WDGHBT) Killed 0xe3e980 (thread: 0x7fb819889950)
35530663587:  (ffado-dbus-server.cpp)[ 353] main:  Bye.
35530663607: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns

```

Thanks for the help.

---

### Post by cggaret on 2009-04-17
I checked out your version of the source and everything that you need is there, and you've obviously compiled with dice support.  Yet, ffado-dbus-server is acting like it does not have dice support.  Could you possibly have two versions of ffado installed?  Try: which ffado-dbus-server.  If it comes back with /usr/local/... then you've got two instances of ffado and you need to get rid of the /usr/local version.  Recompiling with prefix=/usr/local should overwrite any version installed by a package manager.  I can't think of any other reason why this could be happening.  Let me know if you get things worked out or not.  I can enlist others in the fight if we can't figure it out.

---

### Post by cggaret on 2009-04-17
I figured it out.  The ffado-2.0 branch that you are using does not have Dice support.  You need to use the trunk here-  [http://subversion.ffado.org/ffado/trunk](http://subversion.ffado.org/ffado/trunk) to get your source instead of here- [http://subversion.ffado.org/ffado/branches/libffado-2.0](http://subversion.ffado.org/ffado/branches/libffado-2.0). This should fix everything.  Let me know how it goes.

-Chris

---

### Post by evazan on 2009-04-17
Oh dang! Thanks so much man i will let you know how it goes.

---

### Post by evazan on 2009-04-17
Ok i think i am good to go now I uninstalled the old ffado and reinstalled with the source you directed me to and i reinstalled jackd and i think its working?...when i run jackd -d firewire it just says....

```
no message buffer overruns
jackd 0.115.6
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with POSIX SHM support.
loading driver ..
33934099675:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1538 built Apr 17 2009 16:54:58


```

---

### Post by babarosa on 2009-04-18
Hi eavazan,

in our muse group there is at least one very experienced member also on arch linux and ffado. I think to remember taht there were some special issues with some libs.
If you need additional help, post your message at [http://sourceforge.net/mailarchive/forum.php?forum_name=lmuse-user](http://sourceforge.net/mailarchive/forum.php?forum_name=lmuse-user), we are very helpful.

Greetings, Michael

---

### Post by cggaret on 2009-04-21
evazan,  if you check this thread out again would you please upgrade to r1539 or later and try again.  They fixed a bug in the code that makes a former hack unnecessary and would like to confirm that it works for everyone.  Thanks.

---

### Post by evazan on 2009-04-28
Hey! So i updated like you said but it seems that when i use Qjackctl it starts and then after about 30 seconds or so it just crashes. Here is the output...

```
10:05:00.533 /usr/bin/jackd -R -dfirewire -dhw:0 -r48000 -p16 -n3 -i4
10:05:00.536 JACK was started with PID=7235.
no message buffer overruns
jackd 0.115.6
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with POSIX SHM support.
loading driver ..
93078359630:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1538 built Apr 17 2009 16:54:58
10:05:02.607 Server configuration saved to "/home/chris/.jackdrc".
10:05:02.609 Statistics reset.
10:05:03.460 Client activated.
10:05:03.463 JACK connection graph change.
10:05:14.543 JACK connection graph change.
10:05:14.680 JACK connection change.
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
firewire ERR: Could not stop streaming threads
10:05:20.922 JACK connection graph change.
DRIVER NT: error stopping driver
10:05:21.092 JACK connection change.
no message buffer overruns
could not remove SHM ID /jack-3
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
10:05:21.313 Client deactivated.
cannot continue execution of the processing graph (Broken pipe
10:05:21.314 JACK was stopped successfully.
10:05:21.314 Post-shutdown script...
10:05:21.314 killall jackd
)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
jackd: no process killed
10:05:21.754 Post-shutdown script terminated with exit status=256.
```

---

### Post by cggaret on 2009-04-29
Qjackctl is just showing you that FFADO is not working.  Could you post the output of ffado-dbus-server -v6?

---

### Post by evazan on 2009-04-30
Here it is...I dont know why it still says 1538. I even tried uninstalling ffado and did the whole process of the svn install and it still says 1538? =c(

```
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1538
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

288839449261:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
288839452674: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288839452706: Debug (StreamProcessorManager.cpp)[1491] setVerboseLevel: Setting verbose level to 6...
288839452724: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
288839452735: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
288839452742: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
288839452752: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
288839452758: Debug (IsoHandlerManager.cpp)[1135] setVerboseLevel: Setting verbose level to 6...
288839452768: Debug (ieee1394service.cpp)[1522] setVerboseLevel: Setting verbose level to 6...
288839452776: Debug (devicemanager.cpp)[1155] setVerboseLevel: Setting verbose level to 6...
288839452789: Debug (devicemanager.cpp)[ 355] discover: Starting discovery...
288839452812: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288839452823: Debug (StreamProcessorManager.cpp)[1491] setVerboseLevel: Setting verbose level to 6...
288839452831: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
288839452841: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
288839452848: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
288839452858: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
288839452864: Debug (IsoHandlerManager.cpp)[1135] setVerboseLevel: Setting verbose level to 6...
288839452874: Debug (ieee1394service.cpp)[1522] setVerboseLevel: Setting verbose level to 6...
288839452881: Debug (devicemanager.cpp)[1155] setVerboseLevel: Setting verbose level to 6...
288839452901: Debug (devicemanager.cpp)[ 382] discover: Probing node 0...
288839457316: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0x19dac30) First run
288839457404: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
288839457468: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 1241133884309504, m_dll_e2: 4915200.000000
288839457528: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1241134062522055.000000, next: 1241134062722055.000000
288839457583: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 686937002.000000, next: 691852202.000000
288840551166: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288841601198: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288842651164: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288843701164: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288844751160: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288845801163: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
288845829138: Debug (devicemanager.cpp)[ 382] discover: Probing node 1...
288845829154: Debug (devicemanager.cpp)[ 385] discover: Skipping local node (1)...
288845829207: Debug (DeviceStringParser.cpp)[ 376] show: DeviceStringParser: 0x19d9c30
288845829243: Debug (devicemanager.cpp)[ 557] discover: Probing node 0...
288846917830: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288847968653: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288849018658: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288850067828: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288851117829: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
288852167827: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
288852196000: Debug (configrom.cpp)[ 562] printConfigRomDebug: Config ROM
288852196026: Debug (configrom.cpp)[ 563] printConfigRomDebug: 	Current Node Id:	0
288852196042: Debug (configrom.cpp)[ 564] printConfigRomDebug: 	GUID:			0x00059504000F5835
288852196051: Debug (configrom.cpp)[ 565] printConfigRomDebug: 	Vendor Name:		Alesis
288852196063: Debug (configrom.cpp)[ 566] printConfigRomDebug: 	Model Name:		MultiMix Firewire
288852196071: Debug (configrom.cpp)[ 567] printConfigRomDebug: 	Node Vendor ID:		0x000595
288852196083: Debug (configrom.cpp)[ 568] printConfigRomDebug: 	Model Id:		0x00000000
288852196091: Debug (configrom.cpp)[ 569] printConfigRomDebug: 	Unit Specifier ID:	0x000595
288852196106: Debug (configrom.cpp)[ 570] printConfigRomDebug: 	Unit version:		0x00000001
288852196114: Debug (configrom.cpp)[ 571] printConfigRomDebug: 	ISO resource manager:	1
288852196126: Debug (configrom.cpp)[ 572] printConfigRomDebug: 	Cycle master capable:	1
288852196134: Debug (configrom.cpp)[ 573] printConfigRomDebug: 	Bus manager capable:	0
288852196148: Debug (configrom.cpp)[ 574] printConfigRomDebug: 	Cycle clock accuracy:	255
288852196157: Debug (configrom.cpp)[ 576] printConfigRomDebug: 	Max rec:		8 (max asy payload: 512 bytes)
288852196172: Debug (devicemanager.cpp)[1004] getDriverForDevice: Probing for supported device...
288852196181: Debug (devicemanager.cpp)[ 934] getDriverForDeviceDo: Trying BeBoB...
288852196235: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
288852196329: Debug (devicemanager.cpp)[ 941] getDriverForDeviceDo: Trying ECHO Audio FireWorks...
288852196359: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
288852196405: Debug (devicemanager.cpp)[ 948] getDriverForDeviceDo: Trying Oxford FW90x...
288852196429: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
288852196474: Debug (devicemanager.cpp)[ 956] getDriverForDeviceDo: Trying Generic AV/C...
288852196499: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
288852196544: Debug (devicemanager.cpp)[ 963] getDriverForDeviceDo: Trying Motu...
288852196560: Debug (devicemanager.cpp)[ 970] getDriverForDeviceDo: Trying Dice...
288852196667: Debug (Element.cpp)[ 228] addElement: Adding Element ConfigRom to 00059504000f5835
288852196724: Debug (Element.cpp)[ 228] addElement: Adding Element Generic to 00059504000f5835
288852196751: Debug (Element.cpp)[ 228] addElement: Adding Element ClockSelect to Generic
288852196769: Debug (Element.cpp)[ 228] addElement: Adding Element SamplerateSelect to Generic
288852196782: Debug (Element.cpp)[ 228] addElement: Adding Element Nickname to Generic
288852196802: Debug (Element.cpp)[ 228] addElement: Adding Element StreamingStatus to Generic
288852196824: Debug (devicemanager.cpp)[1007] getDriverForDevice:  found supported device...
288852196838: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852196846: Debug (devicemanager.cpp)[ 617] discover: driver found for device 0
288852196856: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
288852196863: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852249905: Debug (dice_avdevice.cpp)[1493] initIoFunctions: DICE Parameter Space info:
288852249928: Debug (dice_avdevice.cpp)[1494] initIoFunctions:  Global  : offset=0028 size=0360
288852249942: Debug (dice_avdevice.cpp)[1495] initIoFunctions:  TX      : offset=0190 size=0568
288852249949: Debug (dice_avdevice.cpp)[1496] initIoFunctions:                nb=   2 size=0280
288852249962: Debug (dice_avdevice.cpp)[1497] initIoFunctions:  RX      : offset=03C8 size=1128
288852249970: Debug (dice_avdevice.cpp)[1498] initIoFunctions:                nb=   1 size=0280
288852249983: Debug (dice_avdevice.cpp)[1499] initIoFunctions:  UNUSED1 : offset=0000 size=0000
288852249990: Debug (dice_avdevice.cpp)[1500] initIoFunctions:  UNUSED2 : offset=0000 size=0000
288852254369: Debug (dice_avdevice.cpp)[ 168] discover: found Alesis Multimix16 Firewire (nick: Alesis MultiMix)
288852254387: Debug (devicemanager.cpp)[ 627] discover: discovery successful
288852254399: Debug (devicemanager.cpp)[ 646] discover: No cached version of AVC model created
288852254443: Debug (Element.cpp)[ 228] addElement: Adding Element 00059504000f5835 to DeviceManager
288852254480: Debug (devicemanager.cpp)[ 654] discover: discovery of node 0 on port 0 done...
288852254489: Debug (devicemanager.cpp)[ 557] discover: Probing node 1...
288852254500: Debug (devicemanager.cpp)[ 560] discover: Skipping local node (1)...
288852254509: Debug (devicemanager.cpp)[ 662] discover: Discovery finished...
288852254558: Debug (ffadodevice.cpp)[ 176] setId: Set id to dev0...
288852254588: Debug (devicemanager.cpp)[1160] showDeviceInfo: ===== Device Manager =====
288852254602: Debug (Element.cpp)[ 121] show: Element DeviceManager
288852254610: Debug (devicemanager.cpp)[1168] showDeviceInfo: --- IEEE1394 Service  0 ---
288852254629: Debug (ieee1394service.cpp)[1537] show: Port:  0
288852254638: Debug (ieee1394service.cpp)[1538] show:  Name: ohci1394
288852254648: Debug (ieee1394service.cpp)[1540] show:  CycleTimerHelper: 0x19dac30, IsoManager: 0x19dabb0, WatchDog: 0x19dae20
288852254655: Debug (ieee1394service.cpp)[1545] show:  Time: 01001418778 (040s 5982cy 2074ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
288852254691: Debug (devicemanager.cpp)[1178] showDeviceInfo: --- Device  0 ---
288852254705: Debug (dice_avdevice.cpp)[ 549] showDevice: Device is a DICE device
288852254714: Debug (ffadodevice.cpp)[ 228] showDevice: Attached to port.......: 0 (ohci1394)
288852254727: Debug (ffadodevice.cpp)[ 229] showDevice: Node...................: 0
288852254736: Debug (ffadodevice.cpp)[ 231] showDevice: Vendor name............: Alesis
288852254748: Debug (ffadodevice.cpp)[ 233] showDevice: Model name.............: MultiMix Firewire
288852254759: Debug (ffadodevice.cpp)[ 235] showDevice: GUID...................: 00059504000f5835
288852254776: Debug (ffadodevice.cpp)[ 240] showDevice: Assigned ID....: dev0
288852254809: Debug (dice_avdevice.cpp)[ 552] showDevice:  DICE Parameter Space info:
288852254820: Debug (dice_avdevice.cpp)[ 553] showDevice:   Global  : offset=0x0028 size=0360
288852254827: Debug (dice_avdevice.cpp)[ 554] showDevice:   TX      : offset=0x0190 size=0568
288852254836: Debug (dice_avdevice.cpp)[ 555] showDevice:                 nb=   2 size=0280
288852254846: Debug (dice_avdevice.cpp)[ 556] showDevice:   RX      : offset=0x03C8 size=1128
288852254856: Debug (dice_avdevice.cpp)[ 557] showDevice:                 nb=   1 size=0280
288852254864: Debug (dice_avdevice.cpp)[ 558] showDevice:   UNUSED1 : offset=0x0000 size=0000
288852254874: Debug (dice_avdevice.cpp)[ 559] showDevice:   UNUSED2 : offset=0x0000 size=0000
288852254881: Debug (dice_avdevice.cpp)[ 561] showDevice:  Global param space:
288852258465: Debug (dice_avdevice.cpp)[ 564] showDevice:   Owner            : 0x00000000FFFF0000
288852262782: Debug (dice_avdevice.cpp)[ 567] showDevice:   Notification     : 0x00000000
288852270666: Debug (dice_avdevice.cpp)[ 570] showDevice:   Nick name        : Alesis MultiMix
288852274328: Debug (dice_avdevice.cpp)[ 574] showDevice:   Clock Select     : 0x02 0x0C
288852278238: Debug (dice_avdevice.cpp)[ 578] showDevice:   Enable           : false
288852283028: Debug (dice_avdevice.cpp)[ 582] showDevice:   Clock Status     : locked 0x01
288852286613: Debug (dice_avdevice.cpp)[ 585] showDevice:   Extended Status  : 0x00000000
288852290346: Debug (dice_avdevice.cpp)[ 588] showDevice:   Samplerate       : 0x0000AC44 (44100)
288852293964: Debug (dice_avdevice.cpp)[ 597] showDevice:   Version          : 0x01000400 (1.0.4.0)
288852297600: Debug (dice_avdevice.cpp)[ 600] showDevice:   Clock caps       : 0x11000006
288852303805: Debug (dice_avdevice.cpp)[ 603] showDevice:   Clock sources    :
288852303822: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303835: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303842: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303852: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303858: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303872: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303878: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303888: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303895: Debug (dice_avdevice.cpp)[ 609] showDevice:     Firewire
288852303905: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303912: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303921: Debug (dice_avdevice.cpp)[ 609] showDevice:     unused
288852303928: Debug (dice_avdevice.cpp)[ 609] showDevice:     Internal
288852303937: Debug (dice_avdevice.cpp)[ 612] showDevice:  TX param space:
288852303944: Debug (dice_avdevice.cpp)[ 613] showDevice:   Nb of xmit        : 2
288852303954: Debug (dice_avdevice.cpp)[ 615] showDevice:   Transmitter 0:
288852307696: Debug (dice_avdevice.cpp)[ 618] showDevice:    ISO channel       :  -1
288852312170: Debug (dice_avdevice.cpp)[ 620] showDevice:    ISO speed         :   2
288852315353: Debug (dice_avdevice.cpp)[ 623] showDevice:    Nb audio channels :   8
288852318981: Debug (dice_avdevice.cpp)[ 625] showDevice:    Nb midi channels  :   0
288852323305: Debug (dice_avdevice.cpp)[ 628] showDevice:    AC3 caps          : 0x00000000
288852326973: Debug (dice_avdevice.cpp)[ 630] showDevice:    AC3 enable        : 0x00000000
288852332516: Debug (dice_avdevice.cpp)[ 633] showDevice:    Channel names     :
288852332535: Debug (dice_avdevice.cpp)[ 638] showDevice:      MIC_LINE_1
288852332542: Debug (dice_avdevice.cpp)[ 638] showDevice:      MIC_LINE_2
288852332552: Debug (dice_avdevice.cpp)[ 638] showDevice:      MIC_LINE_3
288852332558: Debug (dice_avdevice.cpp)[ 638] showDevice:      MIC_LINE_4
288852332568: Debug (dice_avdevice.cpp)[ 638] showDevice:      LINE_5
288852332575: Debug (dice_avdevice.cpp)[ 638] showDevice:      LINE_6
288852332587: Debug (dice_avdevice.cpp)[ 638] showDevice:      LINE_7
288852332594: Debug (dice_avdevice.cpp)[ 638] showDevice:      LINE_8
288852332605: Debug (dice_avdevice.cpp)[ 615] showDevice:   Transmitter 1:
288852336429: Debug (dice_avdevice.cpp)[ 618] showDevice:    ISO channel       :  -1
288852342221: Debug (dice_avdevice.cpp)[ 620] showDevice:    ISO speed         :   2
288852345096: Debug (dice_avdevice.cpp)[ 623] showDevice:    Nb audio channels :   2
288852348704: Debug (dice_avdevice.cpp)[ 625] showDevice:    Nb midi channels  :   0
288852352441: Debug (dice_avdevice.cpp)[ 628] showDevice:    AC3 caps          : 0x00000000
288852356073: Debug (dice_avdevice.cpp)[ 630] showDevice:    AC3 enable        : 0x00000000
288852362068: Debug (dice_avdevice.cpp)[ 633] showDevice:    Channel names     :
288852362090: Debug (dice_avdevice.cpp)[ 638] showDevice:      MAIN_IN L
288852362097: Debug (dice_avdevice.cpp)[ 638] showDevice:      MAIN_IN R
288852362108: Debug (dice_avdevice.cpp)[ 642] showDevice:  RX param space:
288852362114: Debug (dice_avdevice.cpp)[ 643] showDevice:   Nb of recv        : 2
288852362124: Debug (dice_avdevice.cpp)[ 645] showDevice:   Receiver 0:
288852365996: Debug (dice_avdevice.cpp)[ 648] showDevice:    ISO channel       :  -1
288852369723: Debug (dice_avdevice.cpp)[ 650] showDevice:    Sequence start    :   2
288852373356: Debug (dice_avdevice.cpp)[ 653] showDevice:    Nb audio channels :   8
288852376961: Debug (dice_avdevice.cpp)[ 655] showDevice:    Nb midi channels  :   0
288852381407: Debug (dice_avdevice.cpp)[ 658] showDevice:    AC3 caps          : 0x00000000
288852385216: Debug (dice_avdevice.cpp)[ 660] showDevice:    AC3 enable        : 0x00000000
288852390621: Debug (dice_avdevice.cpp)[ 663] showDevice:    Channel names     :
288852390636: Debug (dice_avdevice.cpp)[ 668] showDevice:      MAIN_OUT L
288852390644: Debug (dice_avdevice.cpp)[ 668] showDevice:      MAIN_OUT R
288852390670: Debug (devicemanager.cpp)[1181] showDeviceInfo: Clock sync sources:
288852394552: Debug (dice_avdevice.cpp)[ 331] getSupportedClockSources:  Clock caps: 0x11000006, supported=0x1100
288852398459: Debug (dice_avdevice.cpp)[ 337] getSupportedClockSources:  Clock select: 0x0000020C, selected=0x000C
288852402789: Debug (dice_avdevice.cpp)[ 344] getSupportedClockSources:  Clock status: 0x00000000, status=0x0000, slip=0x0000
288852408271: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 0 not supported by device
288852408283: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 1 not supported by device
288852408293: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 2 not supported by device
288852408300: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 3 not supported by device
288852408313: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 4 not supported by device
288852408320: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 5 not supported by device
288852408333: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 6 not supported by device
288852408339: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 7 not supported by device
288852408394: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 9 not supported by device
288852408401: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 10 not supported by device
288852408412: Debug (dice_avdevice.cpp)[ 365] getSupportedClockSources: Clock source id 11 not supported by device
288852408430: Debug (devicemanager.cpp)[1190] showDeviceInfo:  Type: Compound Syt Match, Id:  8, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Firewire
288852408443: Debug (devicemanager.cpp)[1190] showDeviceInfo:  Type: Internal          , Id: 12, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal
288852408475: Debug (devicemanager.cpp)[ 318] registerNotification: register 0x19ec1a0...
288852408495: Debug (devicemanager.cpp)[ 318] registerNotification: register 0x19eb790...
288852411271: Debug (Element.cpp)[  80] lockControl: Locking tree...
288852411942: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852411960: Debug (StreamProcessorManager.cpp)[1491] setVerboseLevel: Setting verbose level to 6...
288852411976: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
288852411984: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852411999: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
288852412010: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
288852412027: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
288852412034: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
288852412044: Debug (IsoHandlerManager.cpp)[1135] setVerboseLevel: Setting verbose level to 6...
288852412053: Debug (ieee1394service.cpp)[1522] setVerboseLevel: Setting verbose level to 6...
288852412067: Debug (devicemanager.cpp)[1155] setVerboseLevel: Setting verbose level to 6...
288852412075: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager'
288852412087: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0x19ef730)
288852412117: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
288852412158: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
288852412180: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for '00059504000f5835'
288852412204: Debug (controlserver.cpp)[ 361] createHandler: Source is a Control::Container
288852412802: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835'
288852412823: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
288852412831: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852412842: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager/00059504000f5835'
288852412849: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0x19f0a80)
288852412866: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
288852412891: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
288852412905: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'ConfigRom'
288852412914: Debug (controlserver.cpp)[ 412] createHandler: Source is a ConfigRom
288852413499: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/ConfigRom'
288852413514: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852413526: Debug (controlserver.cpp)[ 729] ConfigRomX: Created ConfigRomX on '/org/ffado/Control/DeviceManager/00059504000f5835/ConfigRom'
288852413534: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852413547: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19f0bb0 for Control::Element ConfigRom...
288852413555: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'Generic'
288852413565: Debug (controlserver.cpp)[ 361] createHandler: Source is a Control::Container
288852414091: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic'
288852414112: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852414120: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852414130: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852414137: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852414147: Debug (Element.cpp)[ 325] setVerboseLevel: Setting verbose level to 6...
288852414154: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic'
288852414164: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0x19f2960)
288852414175: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
288852414204: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
288852414214: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'ClockSelect'
288852414225: Debug (controlserver.cpp)[ 398] createHandler: Source is a Control::AttributeEnum
288852414797: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/ClockSelect'
288852414817: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852414824: Debug (controlserver.cpp)[ 664] AttributeEnum: Created Enum on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/ClockSelect'
288852414835: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852414845: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19f2b10 for Control::Element ClockSelect...
288852414856: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'SamplerateSelect'
288852414864: Debug (controlserver.cpp)[ 405] createHandler: Source is a Control::Enum
288852415403: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/SamplerateSelect'
288852415418: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852415430: Debug (controlserver.cpp)[ 624] Enum: Created Enum on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/SamplerateSelect'
288852415438: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852415454: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19f3d20 for Control::Element SamplerateSelect...
288852415465: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'Nickname'
288852415478: Debug (controlserver.cpp)[ 382] createHandler: Source is a Control::Text
288852416011: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/Nickname'
288852416031: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416039: Debug (controlserver.cpp)[ 564] Text: Created Text on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/Nickname'
288852416049: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416061: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19f4c00 for Control::Element Nickname...
288852416075: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'StreamingStatus'
288852416083: Debug (controlserver.cpp)[ 405] createHandler: Source is a Control::Enum
288852416633: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/StreamingStatus'
288852416644: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416655: Debug (controlserver.cpp)[ 624] Enum: Created Enum on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/StreamingStatus'
288852416663: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416673: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19f5940 for Control::Element StreamingStatus...
288852416680: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
288852416691: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19f2b10 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/ClockSelect is present: Control::Element ClockSelect...
288852416698: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19f3d20 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/SamplerateSelect is present: Control::Element SamplerateSelect...
288852416708: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19f4c00 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/Nickname is present: Control::Element Nickname...
288852416715: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19f5940 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/StreamingStatus is present: Control::Element StreamingStatus...
288852416725: Debug (controlserver.cpp)[ 291] updateTree: send dbus signal for path /org/ffado/Control/DeviceManager/00059504000f5835/Generic since something changed
288852416766: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416777: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416783: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416794: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416801: Debug (Element.cpp)[ 325] setVerboseLevel: Setting verbose level to 6...
288852416810: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416817: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416827: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416833: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416844: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19f1cb0 for Control::Element Generic...
288852416851: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
288852416861: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19f0bb0 at /org/ffado/Control/DeviceManager/00059504000f5835/ConfigRom is present: Control::Element ConfigRom...
288852416868: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19f1cb0 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic is present: Control::Element Generic...
288852416878: Debug (controlserver.cpp)[ 291] updateTree: send dbus signal for path /org/ffado/Control/DeviceManager/00059504000f5835 since something changed
288852416913: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
288852416926: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416932: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416942: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416948: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416958: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416964: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416974: Debug (Element.cpp)[ 325] setVerboseLevel: Setting verbose level to 6...
288852416980: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416990: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852416996: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852417006: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
288852417018: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0x19efd90 for Control::Element 00059504000f5835...
288852417029: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
288852417037: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0x19efd90 at /org/ffado/Control/DeviceManager/00059504000f5835 is present: Control::Element 00059504000f5835...
288852417047: Debug (controlserver.cpp)[ 291] updateTree: send dbus signal for path /org/ffado/Control/DeviceManager since something changed
288852417081: Debug (Element.cpp)[  89] unlockControl: Unlocking tree...
288852417096:  (ffado-dbus-server.cpp)[ 328] main: DBUS test service running
288852417102:  (ffado-dbus-server.cpp)[ 329] main: press ctrl-c to stop it & exit
288852417112: Debug (ffado-dbus-server.cpp)[ 332] main: dispatching...


```

---

### Post by cggaret on 2009-05-01
Try redoing the svn in a new folder if you haven't already.  SVN is kinda funny about overwriting anything that it thinks you have edited yourself, and by editing I mean viewing.  So sometimes it's better to just do a new checkout in a new folder.  Also, are you running the ffado-dbus-server or just ffado-test?  Things look a little funny there at the end of your output.  ffado-test could still be the old version number, I'm not sure.  Keep me updated.  If I can't figure it out, I'll find someone who can.

---

### Post by evazan on 2009-05-02
Thanks man I really appreciate this....

Yeah that was the dbus-server output. I will try uninstalling and checking the svn out into a new folder. Thanks!

---

### Post by evazan on 2009-05-02
Ok here is the new dbus-server output...puting in a new folder worked as far as the version i have...but qjackctl still crashes the same. 

```
[chris@evazan libffado-svn-new]$ ffado-dbus-server -v6
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1548
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

01570071787:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
01570077701: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01570077730: Debug (StreamProcessorManager.cpp)[1491] setVerboseLevel: Setting verbose level to 6...
01570077747: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
01570077761: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
01570077768: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
01570077778: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
01570077785: Debug (IsoHandlerManager.cpp)[1135] setVerboseLevel: Setting verbose level to 6...
01570077797: Debug (ieee1394service.cpp)[1522] setVerboseLevel: Setting verbose level to 6...
01570077805: Debug (devicemanager.cpp)[1165] setVerboseLevel: Setting verbose level to 6...
01570077817: Debug (devicemanager.cpp)[ 358] discover: Starting discovery...
01570077840: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01570077850: Debug (StreamProcessorManager.cpp)[1491] setVerboseLevel: Setting verbose level to 6...
01570077860: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
01570077870: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
01570077876: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
01570077886: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
01570077893: Debug (IsoHandlerManager.cpp)[1135] setVerboseLevel: Setting verbose level to 6...
01570077902: Debug (ieee1394service.cpp)[1522] setVerboseLevel: Setting verbose level to 6...
01570077908: Debug (devicemanager.cpp)[1165] setVerboseLevel: Setting verbose level to 6...
01570077929: Debug (devicemanager.cpp)[ 385] discover: Probing node 0...
01571176540: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01572226553: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01573277382: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01574326550: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01575377376: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01576426552: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
01576455386: Debug (devicemanager.cpp)[ 385] discover: Probing node 1...
01576455415: Debug (devicemanager.cpp)[ 388] discover: Skipping local node (1)...
01576455466: Debug (DeviceStringParser.cpp)[ 376] show: DeviceStringParser: 0xe38c30
01576455508: Debug (devicemanager.cpp)[ 560] discover: Probing node 0...
01577543218: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01578593222: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01579643217: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01580694042: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01581743219: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
01582793219: Debug (ieee1394service.cpp)[ 537] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 1
01582821172: Debug (configrom.cpp)[ 562] printConfigRomDebug: Config ROM
01582821194: Debug (configrom.cpp)[ 563] printConfigRomDebug: 	Current Node Id:	0
01582821203: Debug (configrom.cpp)[ 564] printConfigRomDebug: 	GUID:			0x00059504000F5835
01582821215: Debug (configrom.cpp)[ 565] printConfigRomDebug: 	Vendor Name:		Alesis
01582821228: Debug (configrom.cpp)[ 566] printConfigRomDebug: 	Model Name:		MultiMix Firewire
01582821240: Debug (configrom.cpp)[ 567] printConfigRomDebug: 	Node Vendor ID:		0x000595
01582821248: Debug (configrom.cpp)[ 568] printConfigRomDebug: 	Model Id:		0x00000000
01582821263: Debug (configrom.cpp)[ 569] printConfigRomDebug: 	Unit Specifier ID:	0x000595
01582821270: Debug (configrom.cpp)[ 570] printConfigRomDebug: 	Unit version:		0x00000001
01582821282: Debug (configrom.cpp)[ 571] printConfigRomDebug: 	ISO resource manager:	1
01582821289: Debug (configrom.cpp)[ 572] printConfigRomDebug: 	Cycle master capable:	1
01582821300: Debug (configrom.cpp)[ 573] printConfigRomDebug: 	Bus manager capable:	0
01582821308: Debug (configrom.cpp)[ 574] printConfigRomDebug: 	Cycle clock accuracy:	255
01582821322: Debug (configrom.cpp)[ 576] printConfigRomDebug: 	Max rec:		8 (max asy payload: 512 bytes)
01582821332: Debug (devicemanager.cpp)[1014] getDriverForDevice: Probing for supported device...
01582821344: Debug (devicemanager.cpp)[ 937] getDriverForDeviceDo: Trying BeBoB...
01582821392: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
01582821493: Debug (Configuration.cpp)[ 384] getDeviceSetting:   device VME for 595:0 found in /usr/share/libffado/configuration
01582821508: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01582821540: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193389461 (0x7F1800000595)
01582821550: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7F1800000000)
01582821567: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Alesis
01582821577: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Multimix16 Firewire
01582821588: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388052 (0x00000014)
01582821608: Debug (devicemanager.cpp)[ 944] getDriverForDeviceDo: Trying ECHO Audio FireWorks...
01582821634: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
01582821688: Debug (Configuration.cpp)[ 384] getDeviceSetting:   device VME for 595:0 found in /usr/share/libffado/configuration
01582821701: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01582821709: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193389461 (0x7F1800000595)
01582821722: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7F1800000000)
01582821732: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Alesis
01582821742: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Multimix16 Firewire
01582821750: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388052 (0x7F1800000014)
01582821765: Debug (devicemanager.cpp)[ 951] getDriverForDeviceDo: Trying Oxford FW90x...
01582821788: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
01582821842: Debug (Configuration.cpp)[ 384] getDeviceSetting:   device VME for 595:0 found in /usr/share/libffado/configuration
01582821853: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01582821865: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193389461 (0x7F1800000595)
01582821874: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7F1800000000)
01582821885: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Alesis
01582821893: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Multimix16 Firewire
01582821905: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388052 (0x7F1800000014)
01582821918: Debug (devicemanager.cpp)[ 966] getDriverForDeviceDo: Trying Generic AV/C...
01582821944: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
01582821996: Debug (Configuration.cpp)[ 384] getDeviceSetting:   device VME for 595:0 found in /usr/share/libffado/configuration
01582822009: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01582822017: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193389461 (0x7F1800000595)
01582822030: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7F1800000000)
01582822041: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Alesis
01582822054: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Multimix16 Firewire
01582822065: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388052 (0x7F1800000014)
01582822082: Debug (devicemanager.cpp)[ 973] getDriverForDeviceDo: Trying Motu...
01582822096: Debug (devicemanager.cpp)[ 980] getDriverForDeviceDo: Trying Dice...
01582822121: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
01582822174: Debug (Configuration.cpp)[ 384] getDeviceSetting:   device VME for 595:0 found in /usr/share/libffado/configuration
01582822187: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01582822196: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193389461 (0x7F1800000595)
01582822217: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7F1800000000)
01582822228: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Alesis
01582822242: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Multimix16 Firewire
01582822252: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388052 (0x7F1800000014)
01582822355: Debug (Element.cpp)[ 228] addElement: Adding Element ConfigRom to 00059504000f5835
01582822404: Debug (Element.cpp)[ 228] addElement: Adding Element Generic to 00059504000f5835
01582822434: Debug (Element.cpp)[ 228] addElement: Adding Element ClockSelect to Generic
01582822450: Debug (Element.cpp)[ 228] addElement: Adding Element SamplerateSelect to Generic
01582822469: Debug (Element.cpp)[ 228] addElement: Adding Element Nickname to Generic
01582822483: Debug (Element.cpp)[ 228] addElement: Adding Element StreamingStatus to Generic
01582822516: Debug (devicemanager.cpp)[1017] getDriverForDevice:  found supported device...
01582822529: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01582822543: Debug (devicemanager.cpp)[ 620] discover: driver found for device 0
01582822553: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
01582822565: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01582822587: Debug (Configuration.cpp)[ 393] getDeviceSetting:   temporary has no device definitions
01582822644: Debug (Configuration.cpp)[ 384] getDeviceSetting:   device VME for 595:0 found in /usr/share/libffado/configuration
01582822655: Debug (Configuration.cpp)[ 162] showSetting:   Group: (null)
01582822669: Debug (Configuration.cpp)[ 184] showSetting:     vendorid = 140733193389461 (0x7F1800000595)
01582822679: Debug (Configuration.cpp)[ 184] showSetting:     modelid = 140733193388032 (0x7F1800000000)
01582822695: Debug (Configuration.cpp)[ 208] showSetting:     vendorname = Alesis
01582822706: Debug (Configuration.cpp)[ 208] showSetting:     modelname = Multimix16 Firewire
01582822720: Debug (Configuration.cpp)[ 184] showSetting:     driver = 140733193388052 (0x7F1800000014)
01582822735: Debug (dice_avdevice.cpp)[ 128] discover: found Alesis Multimix16 Firewire
01582877028: Debug (dice_avdevice.cpp)[1629] initIoFunctions: DICE Parameter Space info:
01582877042: Debug (dice_avdevice.cpp)[1630] initIoFunctions:  Global  : offset=0028 size=0360
01582877054: Debug (dice_avdevice.cpp)[1631] initIoFunctions:  TX      : offset=0190 size=0568
01582877061: Debug (dice_avdevice.cpp)[1632] initIoFunctions:                nb=   2 size=0280
01582877070: Debug (dice_avdevice.cpp)[1633] initIoFunctions:  RX      : offset=03C8 size=1128
01582877077: Debug (dice_avdevice.cpp)[1634] initIoFunctions:                nb=   1 size=0280
01582877088: Debug (dice_avdevice.cpp)[1635] initIoFunctions:  UNUSED1 : offset=0000 size=0000
01582877098: Debug (dice_avdevice.cpp)[1636] initIoFunctions:  UNUSED2 : offset=0000 size=0000
01582877110: Debug (devicemanager.cpp)[ 630] discover: discovery successful
01582877118: Debug (devicemanager.cpp)[ 649] discover: No cached version of AVC model created
01582877162: Debug (Element.cpp)[ 228] addElement: Adding Element 00059504000f5835 to DeviceManager
01582877176: Debug (devicemanager.cpp)[ 657] discover: discovery of node 0 on port 0 done...
01582877188: Debug (devicemanager.cpp)[ 560] discover: Probing node 1...
01582877196: Debug (devicemanager.cpp)[ 563] discover: Skipping local node (1)...
01582877207: Debug (devicemanager.cpp)[ 665] discover: Discovery finished...
01582877246: Debug (ffadodevice.cpp)[ 176] setId: Set id to dev0...
01582877284: Debug (devicemanager.cpp)[1170] showDeviceInfo: ===== Device Manager =====
01582877293: Debug (Element.cpp)[ 121] show: Element DeviceManager
01582877303: Debug (devicemanager.cpp)[1178] showDeviceInfo: --- IEEE1394 Service  0 ---
01582877317: Debug (ieee1394service.cpp)[1537] show: Port:  0
01582877328: Debug (ieee1394service.cpp)[1538] show:  Name: ohci1394
01582877335: Debug (ieee1394service.cpp)[1540] show:  CycleTimerHelper: 0xe39c30, IsoManager: 0xe39bb0, WatchDog: 0xe39e20
01582877345: Debug (ieee1394service.cpp)[1545] show:  Time: 00493719979 (020s 0716cy 0427ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
01582877373: Debug (devicemanager.cpp)[1188] showDeviceInfo: --- Device  0 ---
01582877383: Debug (dice_avdevice.cpp)[ 532] showDevice: Device is a DICE device
01582877394: Debug (ffadodevice.cpp)[ 228] showDevice: Attached to port.......: 0 (ohci1394)
01582877401: Debug (ffadodevice.cpp)[ 229] showDevice: Node...................: 0
01582877412: Debug (ffadodevice.cpp)[ 231] showDevice: Vendor name............: Alesis
01582877419: Debug (ffadodevice.cpp)[ 233] showDevice: Model name.............: MultiMix Firewire
01582877430: Debug (ffadodevice.cpp)[ 235] showDevice: GUID...................: 00059504000f5835
01582877442: Debug (ffadodevice.cpp)[ 240] showDevice: Assigned ID....: dev0
01582877526: Debug (dice_avdevice.cpp)[ 535] showDevice:  DICE Parameter Space info:
01582877533: Debug (dice_avdevice.cpp)[ 536] showDevice:   Global  : offset=0x0028 size=0360
01582877542: Debug (dice_avdevice.cpp)[ 537] showDevice:   TX      : offset=0x0190 size=0568
01582877549: Debug (dice_avdevice.cpp)[ 538] showDevice:                 nb=   2 size=0280
01582877565: Debug (dice_avdevice.cpp)[ 539] showDevice:   RX      : offset=0x03C8 size=1128
01582877572: Debug (dice_avdevice.cpp)[ 540] showDevice:                 nb=   1 size=0280
01582877582: Debug (dice_avdevice.cpp)[ 541] showDevice:   UNUSED1 : offset=0x0000 size=0000
01582877589: Debug (dice_avdevice.cpp)[ 542] showDevice:   UNUSED2 : offset=0x0000 size=0000
01582877598: Debug (dice_avdevice.cpp)[ 544] showDevice:  Global param space:
01582881233: Debug (dice_avdevice.cpp)[ 547] showDevice:   Owner            : 0x00000000FFFF0000
01582884853: Debug (dice_avdevice.cpp)[ 550] showDevice:   Notification     : 0x00000000
01582893354: Debug (dice_avdevice.cpp)[ 553] showDevice:   Nick name        : Alesis MultiMix
01582897001: Debug (dice_avdevice.cpp)[ 557] showDevice:   Clock Select     : 0x02 0x0C
01582900735: Debug (dice_avdevice.cpp)[ 561] showDevice:   Enable           : false
01582904359: Debug (dice_avdevice.cpp)[ 565] showDevice:   Clock Status     : locked 0x01
01582908628: Debug (dice_avdevice.cpp)[ 568] showDevice:   Extended Status  : 0x00000000
01582912638: Debug (dice_avdevice.cpp)[ 571] showDevice:   Samplerate       : 0x0000AC44 (44100)
01582916541: Debug (dice_avdevice.cpp)[ 580] showDevice:   Version          : 0x01000400 (1.0.4.0)
01582920166: Debug (dice_avdevice.cpp)[ 583] showDevice:   Clock caps       : 0x11000006
01582925460: Debug (dice_avdevice.cpp)[ 586] showDevice:   Clock sources    :
01582925479: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925493: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925502: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925508: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925521: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925527: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925537: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925543: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925553: Debug (dice_avdevice.cpp)[ 592] showDevice:     Firewire
01582925559: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925569: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925576: Debug (dice_avdevice.cpp)[ 592] showDevice:     unused
01582925585: Debug (dice_avdevice.cpp)[ 592] showDevice:     Internal
01582925591: Debug (dice_avdevice.cpp)[ 595] showDevice:  TX param space:
01582925601: Debug (dice_avdevice.cpp)[ 596] showDevice:   Nb of xmit        : 2
01582925607: Debug (dice_avdevice.cpp)[ 598] showDevice:   Transmitter 0:
01582929364: Debug (dice_avdevice.cpp)[ 601] showDevice:    ISO channel       :  -1
01582933786: Debug (dice_avdevice.cpp)[ 603] showDevice:    ISO speed         :   2
01582937610: Debug (dice_avdevice.cpp)[ 606] showDevice:    Nb audio channels :   8
01582941423: Debug (dice_avdevice.cpp)[ 608] showDevice:    Nb midi channels  :   0
01582945209: Debug (dice_avdevice.cpp)[ 611] showDevice:    AC3 caps          : 0x00000000
01582948977: Debug (dice_avdevice.cpp)[ 613] showDevice:    AC3 enable        : 0x00000000
01582954981: Debug (dice_avdevice.cpp)[ 616] showDevice:    Channel names     :
01582954994: Debug (dice_avdevice.cpp)[ 621] showDevice:      MIC_LINE_1
01582955004: Debug (dice_avdevice.cpp)[ 621] showDevice:      MIC_LINE_2
01582955010: Debug (dice_avdevice.cpp)[ 621] showDevice:      MIC_LINE_3
01582955020: Debug (dice_avdevice.cpp)[ 621] showDevice:      MIC_LINE_4
01582955029: Debug (dice_avdevice.cpp)[ 621] showDevice:      LINE_5
01582955038: Debug (dice_avdevice.cpp)[ 621] showDevice:      LINE_6
01582955045: Debug (dice_avdevice.cpp)[ 621] showDevice:      LINE_7
01582955054: Debug (dice_avdevice.cpp)[ 621] showDevice:      LINE_8
01582955062: Debug (dice_avdevice.cpp)[ 598] showDevice:   Transmitter 1:
01582958908: Debug (dice_avdevice.cpp)[ 601] showDevice:    ISO channel       :  -1
01582962632: Debug (dice_avdevice.cpp)[ 603] showDevice:    ISO speed         :   2
01582967444: Debug (dice_avdevice.cpp)[ 606] showDevice:    Nb audio channels :   2
01582970348: Debug (dice_avdevice.cpp)[ 608] showDevice:    Nb midi channels  :   0
01582974700: Debug (dice_avdevice.cpp)[ 611] showDevice:    AC3 caps          : 0x00000000
01582978332: Debug (dice_avdevice.cpp)[ 613] showDevice:    AC3 enable        : 0x00000000
01582983623: Debug (dice_avdevice.cpp)[ 616] showDevice:    Channel names     :
01582983636: Debug (dice_avdevice.cpp)[ 621] showDevice:      MAIN_IN L
01582983646: Debug (dice_avdevice.cpp)[ 621] showDevice:      MAIN_IN R
01582983653: Debug (dice_avdevice.cpp)[ 625] showDevice:  RX param space:
01582983664: Debug (dice_avdevice.cpp)[ 626] showDevice:   Nb of recv        : 2
01582983671: Debug (dice_avdevice.cpp)[ 628] showDevice:   Receiver 0:
01582987536: Debug (dice_avdevice.cpp)[ 631] showDevice:    ISO channel       :  -1
01582991294: Debug (dice_avdevice.cpp)[ 633] showDevice:    Sequence start    :   8
01582996988: Debug (dice_avdevice.cpp)[ 636] showDevice:    Nb audio channels :   0
01582999882: Debug (dice_avdevice.cpp)[ 638] showDevice:    Nb midi channels  :   2
01583003635: Debug (dice_avdevice.cpp)[ 641] showDevice:    AC3 caps          : 0x00000000
01583007246: Debug (dice_avdevice.cpp)[ 643] showDevice:    AC3 enable        : 0x00000000
01583013150: Debug (dice_avdevice.cpp)[ 646] showDevice:    Channel names     :
01583013163: Debug (dice_avdevice.cpp)[ 651] showDevice:      MAIN_OUT L
01583013173: Debug (dice_avdevice.cpp)[ 651] showDevice:      MAIN_OUT R
01583013206: Debug (devicemanager.cpp)[1191] showDeviceInfo: Clock sync sources:
01583017082: Debug (dice_avdevice.cpp)[ 314] getSupportedClockSources:  Clock caps: 0x11000006, supported=0x1100
01583020815: Debug (dice_avdevice.cpp)[ 320] getSupportedClockSources:  Clock select: 0x0000020C, selected=0x000C
01583024431: Debug (dice_avdevice.cpp)[ 327] getSupportedClockSources:  Clock status: 0x00000000, status=0x0000, slip=0x0000
01583029630: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 0 not supported by device
01583029645: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 1 not supported by device
01583029652: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 2 not supported by device
01583029661: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 3 not supported by device
01583029667: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 4 not supported by device
01583029676: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 5 not supported by device
01583029683: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 6 not supported by device
01583029695: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 7 not supported by device
01583029747: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 9 not supported by device
01583029758: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 10 not supported by device
01583029764: Debug (dice_avdevice.cpp)[ 348] getSupportedClockSources: Clock source id 11 not supported by device
01583029785: Debug (devicemanager.cpp)[1200] showDeviceInfo:  Type: Compound Syt Match, Id:  8, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Firewire
01583029795: Debug (devicemanager.cpp)[1200] showDeviceInfo:  Type: Internal          , Id: 12, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: Internal
01583029831: Debug (devicemanager.cpp)[ 321] registerNotification: register 0xe4e770...
01583029858: Debug (devicemanager.cpp)[ 321] registerNotification: register 0xe4dc90...
01583032252: Debug (Element.cpp)[  80] lockControl: Locking tree...
01583032849: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583032870: Debug (StreamProcessorManager.cpp)[1491] setVerboseLevel: Setting verbose level to 6...
01583032880: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
01583032895: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583032907: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
01583032918: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
01583032925: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
01583032935: Debug (IsoHandlerManager.cpp)[ 449] setVerboseLevel: Setting verbose level to 6...
01583032945: Debug (IsoHandlerManager.cpp)[1135] setVerboseLevel: Setting verbose level to 6...
01583032955: Debug (ieee1394service.cpp)[1522] setVerboseLevel: Setting verbose level to 6...
01583032963: Debug (devicemanager.cpp)[1165] setVerboseLevel: Setting verbose level to 6...
01583032974: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager'
01583032983: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0xe51d40)
01583033016: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
01583033054: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
01583033080: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for '00059504000f5835'
01583033093: Debug (controlserver.cpp)[ 361] createHandler: Source is a Control::Container
01583033645: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835'
01583033661: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
01583033678: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583033686: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager/00059504000f5835'
01583033696: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0xe53090)
01583033706: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
01583033733: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
01583033746: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'ConfigRom'
01583033764: Debug (controlserver.cpp)[ 412] createHandler: Source is a ConfigRom
01583034293: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/ConfigRom'
01583034313: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583034320: Debug (controlserver.cpp)[ 729] ConfigRomX: Created ConfigRomX on '/org/ffado/Control/DeviceManager/00059504000f5835/ConfigRom'
01583034331: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583034341: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe531c0 for Control::Element ConfigRom...
01583034352: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'Generic'
01583034359: Debug (controlserver.cpp)[ 361] createHandler: Source is a Control::Container
01583034856: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic'
01583034871: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583034882: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583034893: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583034906: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583034915: Debug (Element.cpp)[ 325] setVerboseLevel: Setting verbose level to 6...
01583034929: Debug (controlserver.cpp)[ 142] Container: Created Container on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic'
01583034939: Debug (Element.cpp)[ 135] addSignalHandler: Adding signal handler (0xe54f70)
01583034955: Debug (controlserver.cpp)[ 221] updateTree: Updating tree...
01583034983: Debug (controlserver.cpp)[ 224] updateTree: Add handlers for elements...
01583035001: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'ClockSelect'
01583035012: Debug (controlserver.cpp)[ 398] createHandler: Source is a Control::AttributeEnum
01583035535: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/ClockSelect'
01583035549: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583035560: Debug (controlserver.cpp)[ 664] AttributeEnum: Created Enum on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/ClockSelect'
01583035568: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583035582: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe55120 for Control::Element ClockSelect...
01583035593: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'SamplerateSelect'
01583035606: Debug (controlserver.cpp)[ 405] createHandler: Source is a Control::Enum
01583036108: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/SamplerateSelect'
01583036126: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583036134: Debug (controlserver.cpp)[ 624] Enum: Created Enum on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/SamplerateSelect'
01583036148: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583036159: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe56330 for Control::Element SamplerateSelect...
01583036173: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'Nickname'
01583036183: Debug (controlserver.cpp)[ 382] createHandler: Source is a Control::Text
01583036702: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/Nickname'
01583036715: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583036726: Debug (controlserver.cpp)[ 564] Text: Created Text on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/Nickname'
01583036737: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583036751: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe570d0 for Control::Element Nickname...
01583036761: Debug (controlserver.cpp)[ 358] createHandler: Creating handler for 'StreamingStatus'
01583036775: Debug (controlserver.cpp)[ 405] createHandler: Source is a Control::Enum
01583037282: Debug (controlserver.cpp)[  43] Element: Created Element on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/StreamingStatus'
01583037297: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037304: Debug (controlserver.cpp)[ 624] Enum: Created Enum on '/org/ffado/Control/DeviceManager/00059504000f5835/Generic/StreamingStatus'
01583037314: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037321: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe57e10 for Control::Element StreamingStatus...
01583037331: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
01583037339: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe55120 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/ClockSelect is present: Control::Element ClockSelect...
01583037355: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe56330 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/SamplerateSelect is present: Control::Element SamplerateSelect...
01583037362: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe570d0 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/Nickname is present: Control::Element Nickname...
01583037372: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe57e10 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic/StreamingStatus is present: Control::Element StreamingStatus...
01583037379: Debug (controlserver.cpp)[ 291] updateTree: send dbus signal for path /org/ffado/Control/DeviceManager/00059504000f5835/Generic since something changed
01583037430: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037437: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037447: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037453: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037462: Debug (Element.cpp)[ 325] setVerboseLevel: Setting verbose level to 6...
01583037469: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037478: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037485: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037494: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037502: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe542c0 for Control::Element Generic...
01583037512: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
01583037519: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe531c0 at /org/ffado/Control/DeviceManager/00059504000f5835/ConfigRom is present: Control::Element ConfigRom...
01583037529: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe542c0 at /org/ffado/Control/DeviceManager/00059504000f5835/Generic is present: Control::Element Generic...
01583037536: Debug (controlserver.cpp)[ 291] updateTree: send dbus signal for path /org/ffado/Control/DeviceManager/00059504000f5835 since something changed
01583037572: Debug (ffadodevice.cpp)[ 216] setVerboseLevel: Setting verbose level to 6...
01583037581: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037592: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037599: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037608: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037615: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037624: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037631: Debug (Element.cpp)[ 325] setVerboseLevel: Setting verbose level to 6...
01583037640: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037646: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037655: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037662: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
01583037676: Debug (controlserver.cpp)[ 238] updateTree: Created handler 0xe523a0 for Control::Element 00059504000f5835...
01583037684: Debug (controlserver.cpp)[ 251] updateTree: Remove handlers without element...
01583037694: Debug (controlserver.cpp)[ 267] updateTree: Slave for handler 0xe523a0 at /org/ffado/Control/DeviceManager/00059504000f5835 is present: Control::Element 00059504000f5835...
01583037701: Debug (controlserver.cpp)[ 291] updateTree: send dbus signal for path /org/ffado/Control/DeviceManager since something changed
01583037737: Debug (Element.cpp)[  89] unlockControl: Unlocking tree...
01583037746:  (ffado-dbus-server.cpp)[ 328] main: DBUS test service running
01583037755:  (ffado-dbus-server.cpp)[ 329] main: press ctrl-c to stop it & exit
01583037762: Debug (ffado-dbus-server.cpp)[ 332] main: dispatching...

```

---

### Post by cggaret on 2009-05-10
Sorry it's taken me so long to get back.  The only thing that I can think for you to do now is to play around with your period and buffers and see if you can get something to work.  I use qjackctl when I'm playing around with things, it makes it a little quicker.  Also,  make sure that you power cycle the multimix between starts of the jack server.  Just turn it off then back on and wait for ffado-dbus-server to show you that it's working again (the Valid:1  Active:1 line) before starting jack again.  This doesn't seem to always be necessary, but sometimes things won't work without it.

---

### Post by evazan on 2009-05-14
That was it! I am recording again! Woooooo!!! Thanks man! You rock!

---

