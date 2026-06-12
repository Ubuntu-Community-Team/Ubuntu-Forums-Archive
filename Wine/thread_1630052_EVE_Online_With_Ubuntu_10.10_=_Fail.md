---
title: "EVE Online With Ubuntu 10.10 = Fail?"
date: 2010-11-24
forum: Wine
---

### Post by pacman43 on 2010-11-24
So first off, Im running Ubuntu 10.10, Wine 1.2 and I have an ATI video card.

I installed EVE online the other day and here are the problems I'm having:

1. If I enable sound the game crashes.(Not just the ingame jukebox or EVE voice. Enabling sound in general crashes the game).

2. I cant run the game via wine's virtual desktop mode. (The splash screen loads and then it just freezes.)

3. I cant ALT-TAB. (the screen just flickers when I do this)

4. I cant run the game in windowed mode. (I did this and the screen went black and every time i tried logging in after it was just a black screen until I edited the .ini file and set fullscreen back to =true.)

Has anyone been able to get any of the above working in Ubuntu 10.10?

---

### Post by bobwyajnr on 2010-11-24
Hi **pacman**,

Don't use Eve myself - however the standard troubleshooting rules apply as always.

What ATI GPU model do you have? Are you using the proprietary ATI driver and if so which version of Catalyst? [I notice from the AppDB page that all the Wine reports are positive except for this AMD/ATI one!!]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20275&iTestingId=58238&bShowAll=true") Unfortunately AMD cards still don't play nice under Linux/Ubuntu...

Have you tried launching the game from a console yet? If so perhaps you could post the output here... If not I can talk you through this - thought it is (usually!!) relatively straightforward task...

Bob

---

### Post by pacman43 on 2010-11-24
I was able to get audio working by renaming the Jukebox folder.

I have an ATI Radeon HD4650, Catalyst Version=2.13, Driver version 8.783

My only Issue now is that the game wont work in Wine virtual desktop mode (Which I'd like to use since I'm unable to alt-tab. 
Heres what I get when I launch the game in virtual desktop mode:

$ wine '/home/matt/.wine/dosdevices/c:/Program Files/CCP/EVE/eve.exe' 
fixme:ntoskrnl:KeInitializeEvent stub: 0x542690 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x5426b0 1 0
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x542684
fixme:ntoskrnl:ObReferenceObjectByHandle stub: 0x40 1f03ff (nil) 0 0x54267c (nil)
fixme:ntoskrnl:KeSetEvent (0x542690, 0, 0): stub
fixme:ntoskrnl:KeGetCurrentThread () stub
fixme:ntoskrnl:KeSetPriorityThread ((nil) 16)
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x542690, 0, 0, 0, 0x64ea18
wine: Call from 0x7b835102 to unimplemented function ntoskrnl.exe.ExfInterlockedRemoveHeadList, aborting
wine: Unimplemented function ntoskrnl.exe.ExfInterlockedRemoveHeadList  called at address 0x7b835102 (thread 0017), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExfInterlockedRemoveHeadList called in 32-bit code (0x7b835102).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b835102 ESP:0064e980 EBP:0064e9e4 EFLAGS:00200203(   - --  I   - - -C)
 EAX:7b825039 EBX:7b881ff4 ECX:683c96a0 EDX:0064e9a0
 ESI:80000100 EDI:00541540
Stack dump:
0x0064e980:  0064ea04 00000008 0000003c 80000100
0x0064e990:  00000001 00000000 7b835102 00000002
0x0064e9a0:  683c96a0 683c9942 683d1dc2 00542690
0x0064e9b0:  00000000 00000000 00000000 0064ea18
0x0064e9c0:  00541724 0064ea50 c0000000 683c6829
0x0064e9d0:  7bc9aff4 0064ea30 7b8350ba 7bc9aff4
Backtrace:
=>0 0x7b835102 in kernel32 (+0x25102) (0x0064e9e4)
  1 0x683c9628 in ntoskrnl (+0x19627) (0x0064ea14)
  2 0x683bab19 in ntoskrnl (+0xab1 (0x0064ea34)
  3 0x00541647 in bios.sys (+0x1646) (0x0064ea6
  4 0x7bc6e6f0 call_thread_func+0xb() in ntdll (0x0064ea7
  5 0x7bc6e8c0 call_thread_entry_point+0x6f() in ntdll (0x0064eb4
  6 0x7bc76e95 in ntdll (+0x66e94) (0x0064f39
  7 0x68163cc9 start_thread+0xd8() in libpthread.so.0 (0x0064f49
0x7b835102: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (24 modules)
PE      540000-  543580    Export          bios.sys
ELF    68000000-6801e000    Deferred        ld-linux.so.2
ELF    6801e000-6815e000    Deferred        libwine.so.1
ELF    6815e000-68178000    Export          libpthread.so.0
ELF    68178000-682d6000    Export          libc.so.6
ELF    682d6000-682da000    Deferred        libdl.so.2
ELF    682da000-68300000    Deferred        libm.so.6
ELF    68300000-68308000    Deferred        libnss_compat.so.2
ELF    68308000-6831f000    Deferred        libnsl.so.1
ELF    6831f000-6832a000    Deferred        libnss_nis.so.2
ELF    6832a000-68336000    Deferred        libnss_files.so.2
ELF    68336000-6834b000    Deferred        winedevice<elf>
  \-PE    68340000-6834b000    \               winedevice
ELF    6834b000-683a5000    Deferred        advapi32<elf>
  \-PE    68360000-683a5000    \               advapi32
ELF    683a5000-683ea000    Export          ntoskrnl<elf>
  \-PE    683b0000-683ea000    \               ntoskrnl
ELF    6b9ec000-6ba5f000    Deferred        rpcrt4<elf>
  \-PE    6ba00000-6ba5f000    \               rpcrt4
ELF    7b800000-7b971000    Export          kernel32<elf>
  \-PE    7b810000-7b971000    \               kernel32
ELF    7bc00000-7bcb7000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 ntdll.dll
    00000009    0
0000000a wineboot.exe
    0000000b    0
0000000c winemenubuilder.exe
    0000000d    0
0000000e services.exe
    00000023    0
    0000001e    0
    00000018    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 (D) C:\windows\system32\winedevice.exe
    00000017    0 <==
    00000016    0
    00000013    0
    00000012    0
00000019 winedevice.exe
    0000001f    0
    0000001d    0
    0000001a    0
00000020 winedevice.exe
    00000024    0
    00000022    0
    00000021    0
Backtrace:
=>0 0x7b835102 in kernel32 (+0x25102) (0x0064e9e4)
  1 0x683c9628 in ntoskrnl (+0x19627) (0x0064ea14)
  2 0x683bab19 in ntoskrnl (+0xab1(0x0064ea34)
  3 0x00541647 in bios.sys (+0x1646) (0x0064ea6
  4 0x7bc6e6f0 call_thread_func+0xb() in ntdll (0x0064ea7
  5 0x7bc6e8c0 call_thread_entry_point+0x6f() in ntdll (0x0064eb4
  6 0x7bc76e95 in ntdll (+0x66e94) (0x0064f39
  7 0x68163cc9 start_thread+0xd8() in libpthread.so.0 (0x0064f49
wine: Call from 0x7b835102 to unimplemented function ntoskrnl.exe.ExfInterlockedRemoveHeadList, aborting
err:eek:le:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:eek:le:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x480000 0 0x33fc40 4
EVE Client version 6.32 build 197121 starting  18:30:51
Multi-Language System: Client using language [EN]
fixme:win:EnumDisplayDevicesW ((null),0,0x338cfc,0x00000000), stub!
EVE Client version 6.32 build 197121 started  18:30:55
Starting services
Replacing service 'machoNet' with 'eveMachoNet'
Service machoNet: 0.001s
Replacing service 'dataconfig' with 'eveDataconfig'
Service dataconfig: 0.009s
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
Starting services - Done
Service moonScan: 0.000s
Service gameui: 0.000s
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
Replacing service 'device' with 'eveDevice'
Service device: 0.001s
Service make: 0.000s
Service event: 0.000s
Replacing service 'font' with 'eveFont'
Service font: 0.003s
Service registry: 0.000s
Replacing service 'audio' with 'eveAudio'
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20070 0x00000000
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xdaea308,0xdaea89: stub
Service audio: 0.372s
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x20070, 0x1684c: stub
Service log: 0.000s
Replacing service 'cmd' with 'eveCmd'
Service ime: 0.001s
Service cmd: 0.007s
Service loading: 0.000s
Replacing service 'connection' with 'eveConnection'
Replacing service 'vivox' with 'evevivox'
Service connection: 0.000s
Service damage: 0.000s
Service logger: 0.001s
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
matt@matt-G31M:~$ Replacing service 'jukebox' with 'eveJukebox'
Service jukebox: 0.001s

Then it just hangs there. 
To me it looks like it's an issue with the 'jukebox' but I essentially  removed this file so i dont see why its still not working...

---

### Post by bobwyajnr on 2010-11-24
> **pacman43 said:**
> I was able to get audio working by renaming the Jukebox folder.

I have an ATI Radeon HD4650, Catalyst Version=2.13, Driver version 8.783


Uhhmmm. That won't be your Catalyst driver version (AMD do some funny tricks with their numbering system). Given the current driver series is 10.x... Anyway...

The game crashes at:
```
wine: Unimplemented function ntoskrnl.exe.ExfInterlockedRemoveHeadList called at address 0x7b835102 (thread 0017), starting debugger...

```
clearly some obscure part of the Windows kernel API that has yet to be implemented in Wine...

If I was you I would file a bug against this problem on WineHQ. Attach all of that console output as **debug.txt** or similar (they're fussy about their file extensions at WineHQ ;) ).

You said the game works fullscreen without any problems - yeh? That's unusual (usually Virtual Desktop works and fullscreen doesn't).

Bob

---

### Post by Gunman1982 on 2010-11-25
Mhh though I would guess that the problem is related to ATI you could try to run eve in a virtual screen with explorer, meaning:
'WINEPREFIX="/home/yourhome/.wine" wine explorer /desktop=0,1680x1050 "C:\Programs\CCP\EVE\eve.exe"  /end /LUA:OFF'
change the resolution so that it fits your needs of course.
If your computer can handle the load you can even start multiple instances of eve (if you gonna be a miner or for a scout account) by changing 'the desktop=0,' to 'desktop=1,' for the next client.

---

### Post by nlsthzn on 2010-11-25
What I would suggest is installing Playonlinux (in SC but an updated version can be had directly from the site).  If Eve is supported it will get the best version of Wine and also pre-configure everything so it can work optimally...

Hope it helps...


Neil

---

