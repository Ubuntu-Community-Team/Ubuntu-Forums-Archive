---
title: "Firewire alesis multimix worked, but now it doesnt"
date: 2015-09-16
forum: Ubuntu Studio
---

### Post by Mike_Bourgeault on 2015-09-16
I tried to search to find this but didn't see anything, apologies if its already been asked and i missed it. 

Ive been using ubuntu studio with my multimix 16 for over a year. Recently I decided to wipe and reinstall the drive with the latest LTS version. Upon doing so, when i try to set my mixer up in jack in the LADI session handler it doesn't work.

I don't have much experience with Linux, but i can figure things out if i have the time. When I set it up the first time there was a guide at ladish.org that was very helpful. However, the site appears to be down (though not dead? I guess thats comforting). I don't think there is a huge problem, but I cant see what I'm missing. Its probably just a checkbox ore something, but there are too many options to go by trial and error. The jack log is also empty for some reason, so thats not even giving me something to go on. 

Does anybody have access to that setup guide or something like it? My mixer shows up if i set ardour to alsa, so the OS seems to see it and I can get signal recorded into it, but not out however. . I'll settle for alsa if I have to, but I need jack for some signal routing that I have come to depend on, and I am hoping to have it up and running by Saturday night. 

Any help will be greatly appreciated.

---

### Post by jejeman on 2015-09-17
Why are you mention firewire when it works with ALSA? Can ALSA handle firewire deivces now?

---

### Post by tgalati4 on 2015-09-17
Welcome to the forums.  What version of Ubuntu Studio were you running?  What version did you upgrade to?

It's helpful to keep a notebook with configuration settings for a working system.  Otherwise, upgrading means starting from scratch and it can take some time to get everything working.

Here are some Jack troubleshooting links:  [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204)

[https://help.ubuntu.com/community/UbuntuStudio/TroubleShooting](https://help.ubuntu.com/community/UbuntuStudio/TroubleShooting)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

Make a list of things that you have changed and specific settings to get your Alesis Multimix to work.  If nothing else, you can use this thead as your notepad.

---

### Post by vassmarc on 2015-11-04
Do you only have this Firewire hardware connected at your computer?

---

### Post by Mike_Bourgeault on 2015-11-09
I am using Ubuntu Studio 14.04.

I tried a bunch of ffado things, and broke stuff pretty good. So I did another format and reinstall, and haven't changed anything yet.

My instincts tell me that its a firewire issue, but if i run the ffado mixer it does see the multimix, though it doesnt have a mixer panel.

I normally use a firewire hard drive chained of the multimix. Though its disconnected right now, if i plug it back in through the multimix it does show up properly. 

Reading forums, I found this command line: jackd -d firewire

Upon running it I get this:

[FONT=arial]jackdmp 1.9.10[/FONT]
[FONT=arial]Copyright 2001-2005 Paul Davis and others.[/FONT]
[FONT=arial]Copyright 2004-2013 Grame.[/FONT]
[FONT=arial]jackdmp comes with ABSOLUTELY NO WARRANTY[/FONT]
[FONT=arial]This is free software, and you are welcome to redistribute it[/FONT]
[FONT=arial]under certain conditions; see the file COPYING for details[/FONT]
[FONT=arial]no message buffer overruns[/FONT]
[FONT=arial]no message buffer overruns[/FONT]
[FONT=arial]no message buffer overruns[/FONT]
[FONT=arial]JACK server starting in realtime mode with priority 10[/FONT]
[FONT=arial]libffado 2.1.9999- built Oct 19 2013 16:01:09[/FONT]
[FONT=arial]00347571480: Warning (dice_eap.cpp)[ 113] init: no EAP mixer (device does not support EAP)[/FONT]
[FONT=arial] DICE Parameter Space info:[/FONT]
[FONT=arial]  Global  : offset=0x0028 size=0360[/FONT]
[FONT=arial]  TX      : offset=0x0190 size=0568[/FONT]
[FONT=arial]                nb=   2 size=0280[/FONT]
[FONT=arial]  RX      : offset=0x03C8 size=1128[/FONT]
[FONT=arial]                nb=   1 size=0280[/FONT]
[FONT=arial]  UNUSED1 : offset=0x0000 size=0000[/FONT]
[FONT=arial]  UNUSED2 : offset=0x0000 size=0000[/FONT]
[FONT=arial] Global param space:[/FONT]
[FONT=arial]  Owner            : 0x00000000FFC10001[/FONT]
[FONT=arial]  Notification     : 0x00000010[/FONT]
[FONT=arial]  Nick name        : Alesis MultiMix[/FONT]
[FONT=arial]  Clock Select     : 0x01 0x0C[/FONT]
[FONT=arial]  Enable           : false[/FONT]
[FONT=arial]  Clock Status     : locked 0x01[/FONT]
[FONT=arial]  Extended Status  : 0x00000000[/FONT]
[FONT=arial]  Samplerate       : 0x0000AC44 (44100)[/FONT]
[FONT=arial]  Version          : 0x01000400[/FONT]
[FONT=arial]  Version          : 0x01000400 (1.0.4.0)[/FONT]
[FONT=arial]  Clock caps       : 0x11000006[/FONT]
[FONT=arial]  Clock sources    :[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    Firewire[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    unused[/FONT]
[FONT=arial]    Internal[/FONT]
[FONT=arial] TX param space:[/FONT]
[FONT=arial]  Nb of xmit        : 2[/FONT]
[FONT=arial]  Transmitter 0:[/FONT]
[FONT=arial]   ISO channel       :  -1[/FONT]
[FONT=arial]   ISO speed         :   2[/FONT]
[FONT=arial]   Nb audio channels :  16[/FONT]
[FONT=arial]   Nb midi channels  :   0[/FONT]
[FONT=arial]   AC3 caps          : 0x00000000[/FONT]
[FONT=arial]   AC3 enable        : 0x00000000[/FONT]
[FONT=arial]   Channel names     :[/FONT]
[FONT=arial]     MIC_LINE_1[/FONT]
[FONT=arial]     MIC_LINE_2[/FONT]
[FONT=arial]     MIC_LINE_3[/FONT]
[FONT=arial]     MIC_LINE_4[/FONT]
[FONT=arial]     MIC_LINE_5[/FONT]
[FONT=arial]     MIC_LINE_6[/FONT]
[FONT=arial]     MIC_LINE_7[/FONT]
[FONT=arial]     MIC_LINE_8[/FONT]
[FONT=arial]     LINE_9[/FONT]
[FONT=arial]     LINE_10[/FONT]
[FONT=arial]     LINE_11[/FONT]
[FONT=arial]     LINE_12[/FONT]
[FONT=arial]     LINE_13[/FONT]
[FONT=arial]     LINE_14[/FONT]
[FONT=arial]     LINE_15[/FONT]
[FONT=arial]     LINE_16[/FONT]
[FONT=arial]  Transmitter 1:[/FONT]
[FONT=arial]   ISO channel       :  -1[/FONT]
[FONT=arial]   ISO speed         :   2[/FONT]
[FONT=arial]   Nb audio channels :   2[/FONT]
[FONT=arial]   Nb midi channels  :   0[/FONT]
[FONT=arial]   AC3 caps          : 0x00000000[/FONT]
[FONT=arial]   AC3 enable        : 0x00000000[/FONT]
[FONT=arial]   Channel names     :[/FONT]
[FONT=arial]     MAIN_IN L[/FONT]
[FONT=arial]     MAIN_IN R[/FONT]
[FONT=arial] RX param space:[/FONT]
[FONT=arial]  Nb of recv        : 1[/FONT]
[FONT=arial]  Receiver 0:[/FONT]
[FONT=arial]   ISO channel       :  -1[/FONT]
[FONT=arial]   Sequence start    :   0[/FONT]
[FONT=arial]   Nb audio channels :   2[/FONT]
[FONT=arial]   Nb midi channels  :   0[/FONT]
[FONT=arial]   AC3 caps          : 0x00000000[/FONT]
[FONT=arial]   AC3 enable        : 0x00000000[/FONT]
[FONT=arial]   Channel names     :[/FONT]
[FONT=arial]     MAIN_OUT L[/FONT]
[FONT=arial]     MAIN_OUT R[/FONT]
[FONT=arial]firewire ERR: Could not prepare streaming device![/FONT]
[FONT=arial]Cannot attach audio driver[/FONT]
[FONT=arial]JackServer::Open failed with -1[/FONT]
[FONT=arial]no message buffer overruns[/FONT]
[FONT=arial]Failed to open server

If I run ffad-diag I get the following:

[/FONT][FONT=arial]=== CHECK ===[/FONT]
[FONT=arial] Base system...[/FONT]
[FONT=arial]  kernel version............ 3.19.0-25-lowlatency[/FONT]
[FONT=arial]    Preempt (low latency)... True[/FONT]
[FONT=arial]    RT patched.............. False[/FONT]
[FONT=arial]  old 1394 stack present.... False[/FONT]
[FONT=arial]  old 1394 stack loaded..... False[/FONT]
[FONT=arial]  old 1394 stack active..... False[/FONT]
[FONT=arial]  new 1394 stack present.... True[/FONT]
[FONT=arial]  new 1394 stack loaded..... True[/FONT]
[FONT=arial]  new 1394 stack active..... True[/FONT]
[FONT=arial]  /dev/raw1394 node present. False[/FONT]
[FONT=arial]  /dev/fw* permissions:[/FONT]
[FONT=arial]crw-------  1 root root  249, 0 Nov  9 17:52 /dev/fw0[/FONT]
[FONT=arial]crw-rw----+ 1 root audio 249, 1 Nov  9 17:52 /dev/fw1[/FONT]
[FONT=arial]  User IDs:[/FONT]
[FONT=arial]uid=1000(mike) gid=1000(mike) groups=1000(mike),4(adm),24([/FONT][FONT=arial]cdrom),27(sudo),29(audio),30([/FONT][FONT=arial]dip),46(plugdev),108(lpadmin),[/FONT][FONT=arial]123(sambashare)[/FONT]
[FONT=arial] Prerequisites (dynamic at run-time)...[/FONT]
[FONT=arial]   gcc ............... gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4[/FONT]
[FONT=arial]   g++ ............... sh: 1: g++: not found[/FONT]
[FONT=arial]   PyQt4 (by pyuic4) . sh: 1: pyuic4: not found[/FONT]
[FONT=arial]   jackd ............. no message buffer overruns[/FONT]
[FONT=arial]     path ............ /usr/bin/jackd[/FONT]
[FONT=arial]     flags ........... Package jack was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `jack.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'jack' found[/FONT]
[FONT=arial]   libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libraw1394.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libraw1394' found[/FONT]
[FONT=arial]     flags ........... Package libraw1394 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libraw1394.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libraw1394' found[/FONT]
[FONT=arial]   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libavc1394.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libavc1394' found[/FONT]
[FONT=arial]     flags ........... Package libavc1394 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libavc1394.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libavc1394' found[/FONT]
[FONT=arial]   libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libiec61883.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libiec61883' found[/FONT]
[FONT=arial]     flags ........... Package libiec61883 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libiec61883.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libiec61883' found[/FONT]
[FONT=arial]   libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libxml++-2.6.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libxml++-2.6' found[/FONT]
[FONT=arial]     flags ........... Package libxml++-2.6 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `libxml++-2.6.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'libxml++-2.6' found[/FONT]
[FONT=arial]   dbus-1 ............ Package dbus-1 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `dbus-1.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'dbus-1' found[/FONT]
[FONT=arial]     flags ........... Package dbus-1 was not found in the pkg-config search path.[/FONT]
[FONT=arial]Perhaps you should add the directory containing `dbus-1.pc'[/FONT]
[FONT=arial]to the PKG_CONFIG_PATH environment variable[/FONT]
[FONT=arial]No package 'dbus-1' found[/FONT]
[FONT=arial] Prerequisites (static at compile-time)...[/FONT]
[FONT=arial]   gcc ............... gcc (Ubuntu/Linaro 4.8.2-1ubuntu1) 4.8.2[/FONT]
[FONT=arial]   g++ ............... g++ (Ubuntu/Linaro 4.8.2-1ubuntu1) 4.8.2[/FONT]
[FONT=arial]   PyQt4 (by pyuic4) . Python User Interface Compiler 4.10.3 for Qt version 4.8.4[/FONT]
[FONT=arial]   jackd ............. sh: 1: jackd: not found[/FONT]
[FONT=arial]     path ............ [/FONT]
[FONT=arial]     flags ........... Package jack was not found in the pkg-config search path.[/FONT]
[FONT=arial]   libraw1394 ........ 2.1.0[/FONT]
[FONT=arial]     flags ...........  -lraw1394  [/FONT]
[FONT=arial]   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.[/FONT]
[FONT=arial]     flags ........... Package libavc1394 was not found in the pkg-config search path.[/FONT]
[FONT=arial]   libiec61883 ....... 1.2.0[/FONT]
[FONT=arial]     flags ...........  -liec61883 -lraw1394  [/FONT]
[FONT=arial]   libxml++-2.6 ...... 2.36.0[/FONT]
[FONT=arial]     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/[/FONT][FONT=arial]glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/[/FONT][FONT=arial]sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/[/FONT][FONT=arial]glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/[/FONT][FONT=arial]include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  [/FONT]
[FONT=arial]   dbus-1 ............ 1.6.12[/FONT]
[FONT=arial]     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/[/FONT][FONT=arial]dbus-1.0/include  -ldbus-1  [/FONT]
[FONT=arial] uname -a...[/FONT]
[FONT=arial]   Linux Studio 3.19.0-25-lowlatency #26~14.04.1-Ubuntu SMP PREEMPT Fri Jul 24 22:14:45 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
[FONT=arial] Hardware...[/FONT]
[FONT=arial]   Host controllers:[/FONT]
[FONT=arial]07:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023] (prog-if 10 [OHCI])[/FONT]
[FONT=arial]    Subsystem: Intel Corporation Desktop Board DP35DP [8086:5044][/FONT]
[FONT=arial]    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT]
[FONT=arial]    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT]
[FONT=arial]    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes[/FONT]
[FONT=arial]    Interrupt: pin A routed to IRQ 19[/FONT]
[FONT=arial]    Region 0: Memory at d2014000 (32-bit, non-prefetchable) [size=2K][/FONT]
[FONT=arial]    Region 1: Memory at d2010000 (32-bit, non-prefetchable) [size=16K][/FONT]
[FONT=arial]    Capabilities: <access denied>[/FONT]
[FONT=arial]    Kernel driver in use: firewire_ohci[/FONT]

[FONT=arial]   CPU info:[/FONT]
[FONT=arial]Architecture:          x86_64[/FONT]
[FONT=arial]CPU op-mode(s):        32-bit, 64-bit[/FONT]
[FONT=arial]Byte Order:            Little Endian[/FONT]
[FONT=arial]CPU(s):                2[/FONT]
[FONT=arial]On-line CPU(s) list:   0,1[/FONT]
[FONT=arial]Thread(s) per core:    1[/FONT]
[FONT=arial]Core(s) per socket:    2[/FONT]
[FONT=arial]Socket(s):             1[/FONT]
[FONT=arial]NUMA node(s):          1[/FONT]
[FONT=arial]Vendor ID:             GenuineIntel[/FONT]
[FONT=arial]CPU family:            6[/FONT]
[FONT=arial]Model:                 15[/FONT]
[FONT=arial]Stepping:              11[/FONT]
[FONT=arial]CPU MHz:               2664.000[/FONT]
[FONT=arial]BogoMIPS:              5332.70[/FONT]
[FONT=arial]Virtualization:        VT-x[/FONT]
[FONT=arial]L1d cache:             32K[/FONT]
[FONT=arial]L1i cache:             32K[/FONT]
[FONT=arial]L2 cache:              4096K[/FONT]
[FONT=arial]NUMA node0 CPU(s):     0,1[/FONT]
[FONT=arial] Configuration...[/FONT]
[FONT=arial]  IRQ information[/FONT]
[FONT=arial]Hardware Interrupts:[/FONT]
[FONT=arial]--------------------[/FONT]
[FONT=arial] IRQ    0: PID:  None, count:           [134, 0], Sched None (priority None), drivers: ['timer'][/FONT]
[FONT=arial] IRQ    1: PID:  None, count:             [3, 0], Sched None (priority None), drivers: ['i8042'][/FONT]
[FONT=arial] IRQ    8: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['rtc0'][/FONT]
[FONT=arial] IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi'][/FONT]
[FONT=arial] IRQ   12: PID:  None, count:             [1, 3], Sched None (priority None), drivers: ['i8042'][/FONT]
[FONT=arial] IRQ   16: PID:  None, count:     [35046, 28536], Sched None (priority None), drivers: ['16-fasteoi   nvidia'][/FONT]
[FONT=arial] IRQ   17: PID:  None, count:             [1, 2], Sched None (priority None), drivers: ['17-fasteoi   ehci_hcd:usb1', 'uhci_hcd:usb5', 'pata_marvell'][/FONT]
[FONT=arial] IRQ   18: PID:  None, count:       [4765, 4041], Sched None (priority None), drivers: ['18-fasteoi   uhci_hcd:usb3', 'uhci_hcd:usb8'][/FONT]
[FONT=arial] IRQ   19: PID:  None, count:       [2942, 2946], Sched None (priority None), drivers: ['19-fasteoi   uhci_hcd:usb7', 'firewire_ohci'][/FONT]
[FONT=arial] IRQ   21: PID:  None, count:         [188, 200], Sched None (priority None), drivers: ['21-fasteoi   uhci_hcd:usb4'][/FONT]
[FONT=arial] IRQ   22: PID:  None, count:        [71, 54596], Sched None (priority None), drivers: ['22-fasteoi   rt2800pci'][/FONT]
[FONT=arial] IRQ   23: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['23-fasteoi   ehci_hcd:usb2', 'uhci_hcd:usb6'][/FONT]
[FONT=arial] IRQ   30: PID:  None, count:     [14754, 14116], Sched None (priority None), drivers: ['0000:00:1f'][/FONT]
[FONT=arial] IRQ   31: PID:  None, count:           [516, 4], Sched None (priority None), drivers: ['eth0'][/FONT]
[FONT=arial] IRQ   32: PID:  None, count:             [4, 4], Sched None (priority None), drivers: ['mei_me'][/FONT]
[FONT=arial] IRQ   33: PID:  None, count:         [185, 181], Sched None (priority None), drivers: ['snd_hda_intel'][/FONT]

[FONT=arial]Software Interrupts:[/FONT]
[FONT=arial]--------------------[/FONT]


[FONT=arial]=== REPORT ===[/FONT]
[FONT=arial]FireWire kernel drivers:[/FONT]

[FONT=arial]The new FireWire kernel stack is loaded. [/FONT]
[FONT=arial]If running a kernel earlier than 2.6.37 and problems are experienced, either [/FONT]
[FONT=arial]try with the old Firewire kernel stack or upgrade to a newer kernel [/FONT]
[FONT=arial](preferrably 2.6.37 or later).[/FONT]

---

### Post by tgalati4 on 2015-11-09
Your *ffad-diag* output shows new 1394 stack and old 1394 stack, perhaps you can switch between them.  I would set up dual-boot with 12.04 which presumably worked previously, and then 14.04 on another partition.  That way you have a working recording workstation and you can switch back and forth as you check settings to get 14.04 to work.  What was the Ubuntu version that worked?

My instincts tell me that the old style "FreeBob" firewire drivers work, but the newer [FFADO]("http://ffado.org/") do not with your hardware.

The repos show two sets of JACK/firewire connection in 14.04:

> jackd - JACK Audio Connection Kit (default server package)
jackd1 - JACK Audio Connection Kit (server and example clients)
jackd1-firewire - JACK Audio Connection Kit (FFADO backend)
jackd2 - JACK Audio Connection Kit (server and example clients)
jackd2-firewire - JACK Audio Connection Kit (FFADO and FreeBoB backends)


Perhaps install d2.  Check if it is already installed:

```
apt-cache policy jackd2-firewire
sudo apt-get install jackd2 jackd2-firewire
```

So you have 2 sets of firewire modules in the kernel and two sets of firewire connections to JACK.  That's 4 different configurations to test.

---

### Post by Mike_Bourgeault on 2015-11-09
I checked and it looks like d2 is installed. 

I am about an hour and a half away from having the 12.04.4 iso, so we'll see how that goes. I don't mind stepping back as long as it works. Too busy for the next while to troubleshoot the issue to indepth. 

Thanks for the help!

---

### Post by jejeman on 2015-11-09
JACK2 is default install in UbuntuStudio.
As I said in other threads, JACK stopped working with firewire devices since kernel >3.5, regardless from linux distribution, but depending on firewire chipset. For me VIA works, NEC and MSI doesn't.
FFADO tests work.

---

### Post by tgalati4 on 2015-11-09
I think [12.04]("http://http://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version") has 3.2 kernel, so that should work.  You can bump the kernel version up with the Kernel Enablement Stack.

---

### Post by Mike_Bourgeault on 2015-11-09
Just lit up the 12.04.4 and sure enough, jack studio starts without error. Haven't tested actual audio yet, but I can do that tomorrow. 

Thanks again.

---

### Post by Mike_Bourgeault on 2015-11-16
Ok finally had some time, and happy to report much success! 12.04.4 installed, and for kicks I let it do its own update to 14.04.3. After all the other updates, all audio functioning like it should.

Thanks for your help everyone!

---

### Post by jejeman on 2015-11-17
Wich kernel is running?

---

### Post by Mike_Bourgeault on 2015-11-17
How do I check that? ffado-diag? it returns 3.13.0-68 lowlatency

---

### Post by tgalati4 on 2015-11-17
```
uname -a
cat /etc/issue
lsb_release a
```

---

### Post by Mike_Bourgeault on 2015-11-21
As a thanks, if you wanna see what I use the machine for:

[https://www.ustream.tv/broadcaster/17731787#itm_campaign=broadcast_interstitial&itm_source=skip](https://www.ustream.tv/broadcaster/17731787#itm_campaign=broadcast_interstitial&itm_source=skip)

---

