---
title: "Support for Behringer FCA202; can it be fixed?"
date: 2011-02-13
forum: Ubuntu Studio
---

### Post by Royke on 2011-02-13
Last year i bought this device because it was affordable and within reach. Before i bought it i did a check on the Ffado-supportlist and by reading the info there, i was pretty convinced that i could make this device work. I still am.
It should be possible - as far as i know - to use jackd's firewire or freebob driver for it. That means it will only work with Jack started, but that is why i bought this thing anyway.(With the pulse-jack-module it would even be possible to hear systemsounds and stuff) 
So far i tried to recompile Jack on ubuntustudio 10.04, but i think that something went wrong in the process. Freebob was still an "unknown driver" and the firewire-option made the thing go crazy(and me too):D.I also tried it on 10.10 but not thoroughly.
If some of you great compilers and developers can fix this little issue, than a whole bunch of ubuntustudiousers can take this thing out of their box again(just kidding)..
My plan was to have it up and running before the end of 2010 and even write some sort of manual, but i don't have the mental power to dig in that deep into this piece of equipment. You linux audio can be so inscrutable sometimes, but i want to learn.

Please, can someone help with this!

---

### Post by Royke on 2011-02-14
Please, anyone. 
To mu opinion this device is still worth getting to work and not because it's cheap. This week i will give it another go with trying to set it up, but i don't want to mess up my 10.10.

If someone could just tell me if i understand well what i described in my thread, or maybe give some directions than i could possably fix it myself and describe what i did in a manual.

It also is possible that the device is working now under ubuntustudio 10.10, although i tested it. I still have the impression that the proper driver is not installed in Jack. 

Please tell me at least if i'm goïng in the right direction here. 

btw, since i couldn't get the fca202 to work i also bought the uca202 and it solved my soundIRQ problem and i have now a decent productionmachine! UbuntuStudio, thanks for your existence and i hope to become more part of it in the near future.

Sorry to dwell off, please help!

---

### Post by AutoStatic on 2011-02-14
Hello Royke,

Could you post the output of **ffado-diag** with the FCA202 attached? ffado-diag is part of the ffado-tools package.

Best,

Jeremy

---

### Post by Royke on 2011-02-15
Hello Autostatic and beautiful Ubuntu community!

It is done!:popcorn:

After i typed ffado-diag in a terminal i saw it was saying that IE1394 was disabled. So i visited Autostatic's dutch site for firewire and followed the steps.
After that i rebooted and checked with the UbuntuStudio Controls if IE1394 was enabled. Hmm was my thought..
I opened up the terminal again and typed ffado-diag again and felled that good feeling in the stomach that i can trust with my life.
I had before some signs of device-recognition, even with 10.04, but this had to be it.
Now it was a matter of using qjackctl for setting up the thing. I started with an as light as reasonable setting, because i didn't want to be punched out by jack at this point: 44,100kHz,frames/period=128 and periods/buffer=3. 
Than i just hit the playbutton on qjackctl and plugged in a headphones..:popcorn:
To be honest: i ran downstairs to my mother and lifted her up in the air. 
Now i am still listening through the headphones to some relaxed music, but i want to use this device for high quality recordings.
I also have the berhinger uca202, since i couldn't get this device to work in time and i am proberbly going to use this as main-soundboard(works without Jack). Also now i know how to safely re-enable the onboardsound without having IRQ-trouble.

This was all possible with a few wise words from AutoStatic, thank you for it!

For fun&studying here is my correct output of ffado-diag:

roy@RoyComputy:~$ ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.36-1-lowlatency
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... sh: g++: not found
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
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.5
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.2.24
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
04:06.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7293]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at dfaff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at 9c00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: ohci1394, firewire-ohci

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping	: 2
cpu MHz		: 1800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 3591.01
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:              [128], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:                [2], Sched None (priority None), drivers: ['i8042']
 IRQ    2: PID:  None, count:                [0], Sched None (priority None), drivers: ['cascade']
 IRQ    4: PID:  None, count:             [2098], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb4']
 IRQ    7: PID:  None, count:                [2], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count:                [0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:                [0], Sched None (priority None), drivers: ['acpi']
 IRQ   10: PID:  None, count:              [518], Sched None (priority None), drivers: ['uhci_hcd:usb2', 'eth0']
 IRQ   11: PID:  None, count:            [21722], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'uhci_hcd:usb5', 'sata_via', 'firewire_ohci', 'nvidia']
 IRQ   12: PID:  None, count:                [4], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:                [0], Sched None (priority None), drivers: ['pata_via']
 IRQ   15: PID:  None, count:              [441], Sched None (priority None), drivers: ['pata_via']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

roy@RoyComputy:~$ Yippy!

---

### Post by Pablo_F on 2011-02-16
> To be honest: i ran downstairs to my mother and lifted her up in the air. 

:lol:


By the way, ffado-diag seems outdated. Is this true anymore?

> The new FireWire kernel stack is loaded.
This stack is not supported by FFADO. Please use the old stack.

---

### Post by AutoStatic on 2011-02-16
Hello Royke, glad I could help out! I just updated my tutorial on how to configure your system properly for 10.04 but I'll also update the FireWire tutorial if necessary one of these days. If you got any further questions don't hesitate to ask!
@Pablo_F, that's a minor bug from the FFADO svn check-out Ubuntu 10.10 uses. The message is harmless, it works nonetheless with the new JuJu stack (except for DICE based devices like the newer Focusrites). This has been fixed.

Best,

Jeremy

---

### Post by Royke on 2011-02-16
@AutoStatic (especially)

Oops!

Today when i turned on my machine again ffado-diag says that there is no stack loaded. I reviewed the steps, all in order. It doesn't seem to want to start. I'm trying out some things but don't know really what to do, at least i'm still happy it worked for one good evening. 
Maybe i stay up this night to learn all about ffado and fix this thing forever. In worst case i am ready to repeat all steps, including fresh studio-install and run all related stuff in a terminal to learn what's wrong. But AutoStatic proberbly has another golden answer to this.:D

Yeah, i'm gonna connect this thing to my 100% in shape 12mm tapedeck, my mothers organ and even to the world(w pulse;))

---

### Post by AutoStatic on 2011-02-16
Hello Royke, that's weird and very unfortunate :(
But no need to reinstall anything, if it worked before it should work again. Are you sure your FCA202 is turned on and that it is properly connected? Anything that changed between yesterday evening and today on your system?

Best,

Jeremy

---

### Post by Royke on 2011-02-17
Hello AutoStatic,
When i reboot my system it works and when i reboot again it doesn't. I wander if it may have something to do with the added udev rule and a change in Ubuntu??

---

### Post by AutoStatic on 2011-02-17
> **Royke said:**
> When i reboot my system it works and when i reboot again it doesn't. I wander if it may have something to do with the added udev rule and a change in Ubuntu??No, it shouldn't, and in fact you don't need the udev rule and the raw1394 module in */etc/modules* because you're using the new FireWire stack. I think it is best to remove the udev rule and to delete the raw1394 module from the */etc/modules* file.

Best,

Jeremy

---

### Post by Royke on 2011-02-22
@AutoStatic, O.K., i will do that. What i did discovered is that IE1394 isn't even loaded in BIOS, only after reboot. When i reboot again it's gone again. 
Conclusion: good enough for me:lolflag: I do have mainboard-manual somewhere.
Today i've connected the thing with an older pc, connected through a creative audigy(1)-card with firewire and tested it in winxp. Let's just say: the sound works. Maybe i'll manage to fix another UbuntuStudio on this machine.
Reading the ffado-forum it sould also be possible to run this device with the old stack and i could try out many "new" things on this old machine. 
If i learn something more about this device i will let it know here. I also hope that everyone with this device knows now how to get it running.
Thanks again for all the help..

---

### Post by AutoStatic on 2011-02-23
> **Royke said:**
> Today i've connected the thing with an older pc, connected through a creative audigy(1)-card with firewire and tested it in winxp. Let's just say: the sound works.I've tried a similar card for like a few minutes and tossed it in the dustbin. Really, don't waste your time on getting your FireWire card to work with the controller on the Audigy card, it won't work in a stable and reliable manner. You can always try of course, maybe I didn't take enough time for it.

Best,

Jeremy

---

### Post by Royke on 2011-02-28
Looking back now at this tread makes me smile now, especially AutoStatic's last reaction. Totally right as ever!:)
I successfully installed Ubuntu 11.04 on my old pc but accidentily erased my last running windows and 2x Puppy when i used the second option in the partition manager with install(!!), listened to music with jack and firewire, but how..
Also i noticed that ubuntu has become VERY HEAVY for an older pc, even with Xfce.
Before all was gone i did tested it in XP because i wanted to try out the software included. Don't bother, you might as well trow the cd away when you have ubuntustudio!:guitar: Well, the device was working ok with sound output. The latency seemed more like 10 seconds, but there was no stuttering. This small test makes me wander: isn't USB2.0 just about as fast as not the newest firewire?  This i can conlude now on my Core2duo US-system, where i get a reasonable 8msec latency with shared IRQ with video. That's the same value as my onboard sound, both @ 96KHz.(2,67msec@48KHz with UCA and i feel it can be improved!) The funny thing (and mindbreaking too) is that FINALLY, the onboard ALC888 is on its own IRQ16, when all three devices are running!:confused: Still i do get xruns, no matter what setting but they happen without Jack too and mostly only on the output, not on the recording. There are some things left that could be improved in my hardware-setup, but all=working ok now.
Not to forget: Ffado-mixer registered my Behringer on-line. Although it has no controls this seems to be a good sign:) 
Also i'm wandering if fixing all the issues reported by ffado-diag could make the thing work without jack(?)

---

### Post by Royke on 2012-02-10
Too keep an old thread going; the card works like a charm now!:popcorn: After a few years of playing with IRQ/hardwaresetup it is even now working on every boot, although i thought i had read somewhere in my mainboardmanual, good that i can't find it anymore.

I can only use its sound with jack set to firewire but this time the latency is well setup at 2,67msec with US10.04 and 12.04 too with the generic kernel.:D I also can without further trouble use my UCA202 card at the same time. 

Really i'm hoping to figure out how to merge these 2 devices in jack so i have a dedicated 4-track recording system when i start jack. It may be a bit hard to merge firewire and usb but somewhere there must be a way..

:KSIf someone really wants firewire and is satisfied with just 2 inputs than you won't be disappointed to buy this cheap-*** bastard.(The cd you may just as well trow away because what you can do in a standard UbuntuStudio just goes way beyond.

Now i'm not even afraid anymore when buying new hardware about linux-support, i am gonna fix it all and let you know about it. There is Big Love for you from me, Ubuntu and GNU/Linux. You are changing the world for the better with your ideal system and i will help translate it into dayly life. No promises needed, it is happening now..

P.S. This thread is still not closed now. When there are 2 beautiful firewire/pulse mixer-controls it will be, okay?:guitar:

---

