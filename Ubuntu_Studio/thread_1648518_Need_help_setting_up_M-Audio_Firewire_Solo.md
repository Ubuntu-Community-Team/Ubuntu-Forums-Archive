---
title: "Need help setting up M-Audio Firewire Solo"
date: 2010-12-18
forum: Ubuntu Studio
---

### Post by eamner on 2010-12-18
Hello.
I've been trying to set up my recently purchased Firewire Solo for over a week now, and it's got me really frustrated.
I think I managed to make it sound... if I start Hydrogen (it automatically starts jackd) I get sound from the headphone output and also from the rear output. But a few minutes later, I start getting xruns in jack and eventually Hydrogen stops working (even if I do nothing). Hydrogen is configured to use the "Auto" driver. After this, the system gets random "freezes" and gets really unstable. I need to kill the jackd process and reboot to get it working again.
But first of all, I'd like to know if this interface is supposed to appear in the Sound devices list (multimedia section). All I see there is my integrated soundcard and another device appearently from my video card (ati radeon). I don't see anything related to the Solo. Is this normal?
I don't use "ubuntustudio". I have Kubuntu (Maverick), and I have made a few configurations to use the studio features. 
I have a I3 processor, 2gb of ram. If you need more specs let me know.
Please help me, I am new to jack and to music in linux in general. I've worked on windows for many years but I really want to make the transition to linux. Actually I have a dual boot, with windows 7, and this system detects the interface easily (and shows it in the control panel).
I wish to use Rosengarden, but I need to solve this problem first. I purchased this interface because I read it was supported by the system.
 I've read somewhere that to show the device in the list, I need to recompile jack or something like that, but I'm not sure how to do this. I've read so many forums that I'm confused now. Anybody can give me a hand and guide me through the process?

---

### Post by argoson on 2011-01-11
Actually it works very well. using jack i manage to record tracks, with Line6 POD connected, and Ardour as my multi track recorder.

There are a few things you need to make sure you have:

1. On the M-Audio website (forum, actually) they recommend a firewire card/interface with TI (Texas Instruments) chipset. Since i didn't have FW on my PC's motherboard, it was easy for me to install a PCI card, which i bought on-line fairly cheap. It was detected right away and FW Solo works perfectly.

2. Install the latest UbuntuStudio - 10.10. the reason for that is that they changed some crucial settings needed to configure the 1394 interface (Firewire) with memory allocation, permissions and so on.

If you already have an OS installed, you can dual boot. I do that. I have another linux distro as my main os, and Ubuntu Studio as a second boot just for studio recordings.

3. Now check this tutorial:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Make sure you follow for Ubuntu Studio 10.10 Maverick instructions.

---

### Post by eamner on 2011-01-11
Thanks for your answer.
No, I haven't managed it yet. I'm so frustrated that I'm close to giving up. 
The interface works very well in Win7 (I have a dual boot), but in ubuntu, I don't even see the interface in the list of devices.
Actually, I use Kubuntu 10.10. I followed the "Ubuntu Studio Preparation" guide in order to configure it as ubuntustudio. However, at this point, I think I have installed so many things and done so many tweaks, that perhaps I have messed things up.
To answer your questions:
1. I have a VIA FW IEEE1394 card. Actually kubuntu recognizes it pretty well (I can see it in the list of devices).
2. As I said, I have kubuntu 10.10. I'm not using the RT kernel at this point (I could install it if necessary). If possible, I'd prefer not to uninstall/install any OS, as I use these systems for other things besides music.
3. I know that tutorial. Actually I have read so many tutorials that perhaps I have messed things up...

I'm not at home at this moment, but I can tell you a few things from my memory: 
My main concern is that I don't even get the interface recognized by kubuntu. I don't see it in the list of multimedia devices. If I enter:
 "aplay -l"
 ...it only lists the Intel integrated audio card (Actually it also detects the ATI Radeon HDMI audio, but I disabled it via Pulseaudio manager). And if I enter:
 "lspci -v"
 ...it lists the VIA IEEE chipset, but no mention of the FW Solo.
 However, last week I installed some FFADO program (I think it is a FFADO device manager, I can give you details later when I get home). This program doesn't do much, but it DOES detect the card. It lists it as "FW Solo (Dummy)", and in the messages window it says it "has found device M-audio FW Solo" and it gives some hardware address. 
 
There have been a few moments when I could get sound from the interface. If I configure qjackctl with "firewire" driver and start Hydrogen (I've been using it for many of my tests, as I'm not an expert on ardour) actually I get sound from the interface (from the headphone jack and the rear outputs). HOWEVER I was testing a few days ago and I couln't get sound from it (perhaps because of the many tweaks I have done here and there..).
 When I first installed the interface, actually it was detected by kubuntu, not as an audio device, but as some kind of mounted drive (actually I could see it as a hard disk and read its folders with Dolphin). But recently I changed something in the BIOS and now I don't see it anymore, even as a drive). I did this because every time I turned the computer on, it would enter in the "BIOS flash update", and it was very annoying.
 One more thing: what is the "interface" you select in qjackctl? some time ago I managed to make Hydrogen sound through the Solo, by configuring "hw:0" with the "firewire" driver. However I believe the "hw:0" is the Intel audio card. Every time I'd start jack, a few minutes later, it'd start giving xruns, and a few minutes later, the machine would become unstable....
 Please help me if you can. At this point I have followed so many tutorials that I'm pretty confused. I'm not a linux expert. I have worked with audio for many years in Windows. I purchased this card because it seemed to work in kubuntu, and I don't want to go back to Windows. 
P.D. If possible, please don't ask me to reinstall the whole OS... besides from that, I'm willing to do anything.
Thanks in advance.
Eric.

---

### Post by AutoStatic on 2011-01-11
> **eamner said:**
> My main concern is that I don't even get the interface recognized by kubuntu. I don't see it in the list of multimedia devices. If I enter:
 "aplay -l"
 ...it only lists the Intel integrated audio card (Actually it also detects the ATI Radeon HDMI audio, but I disabled it via Pulseaudio manager).That's right, FireWire audio devices don't use the ALSA driver backend, they use the FFADO backend. And only the JACK sound daemon can use the FFADO backend, the PulseAudio sound daemon cannot use it. That's  why your FireWire soundcard doesn't show up as a 'normal' audio device.

> **eamner said:**
> And if I enter:
 "lspci -v"
 ...it lists the VIA IEEE chipset, but no mention of the FW Solo.That's right also, a FireWire device is not a PCI device.

> **eamner said:**
> However, last week I installed some FFADO program (I think it is a FFADO device manager, I can give you details later when I get home). This program doesn't do much, but it DOES detect the card. It lists it as "FW Solo (Dummy)", and in the messages window it says it "has found device M-audio FW Solo" and it gives some hardware address.Probably one of the utilities included in the ffado-tools package, maybe ffado-diag or ffado-test. Try running **ffado-diag** in a terminal when you get home (you might need to install the **ffado-tools** package first) and post the results here.
 
> **eamner said:**
> One more thing: what is the "interface" you select in qjackctl?Your audio interface. All your audio interfaces get an ID. The first device gets ID 0 (hw:0), the second one ID 1 (hw:1) etc.

> **eamner said:**
> some time ago I managed to make Hydrogen sound through the Solo, by configuring "hw:0" with the "firewire" driver. However I believe the "hw:0" is the Intel audio card.hw:0 is the first audio device on your system detected by a driver backend (well, it's a bit more complicated than that), doesn't matter if it's ALSA or FFADO. So hw:0 is the first device detected by FFADO (your FW Solo) or when you use the alsa driver in QjackCtl it is your onboard Intel card. 

> **eamner said:**
> Every time I'd start jack, a few minutes later, it'd start giving xruns, and a few minutes later, the machine would become unstable....This is probably caused by the scaling of your CPU. FFADO doesn't like that. You could try disabling it.

Best,

Jeremy

---

### Post by eamner on 2011-01-11
Thanks for your ideas, I really appreciate it.

> **AutoStatic said:**
> 
Probably one of the utilities included in the ffado-tools package, maybe ffado-diag or ffado-test. Try running **ffado-diag** in a terminal when you get home (you might need to install the **ffado-tools** package first) and post the results here.
I'll do that and post the results here tonight.

> **AutoStatic said:**
> 
hw:0 is the first audio device on your system detected by a driver backend (well, it's a bit more complicated than that), doesn't matter if it's ALSA or FFADO. So hw:0 is the first device detected by FFADO (your FW Solo) or when you use the alsa driver in QjackCtl it is your onboard Intel card. 

 I didn't know that. I guess this explains why I got sound from it when choosing "firewire" driver and "hw:0" in qjackctl... 

> **AutoStatic said:**
> 
This is probably caused by the scaling of your CPU. FFADO doesn't like that. You could try disabling it.

 I will try that.

 Please don't give up on me guys!

---

### Post by trulan on 2011-01-11
Keep hanging in there, you'll get it!  The only other potential problem could be if you have an IRQ conflict (yes, those still exist), especially if you are using a laptop.  On mine, the wireless card and the firewire controller share an IRQ and ffado doesn't like to share, so I have problems if I forget to turn my wireless card off before starting Jack.  The output of ffado-diag contains this information.  But CPU scaling is the more likely culprit.

---

### Post by argoson on 2011-01-11
It does seem you are having problems with the system not detecting the FW solo box. it might come from firewire stack issues (RAW1394), mostly permissions.

Did you check the link to the tutorial i linked ? 
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Here is another tutorial that helped me a lot - especially the comments at the bottom:
[https://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/](https://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/)

There is a utility called 'gscanbus' which will help you figure out if your FW solo box is detected . see if it appears in your software repositories (or look for a download of it).

And last - here is M-Audio's explanation why a Texas Instruments chipset based PCI card is important to use when plugging your FW Solo (it won't ignore your box, but it will affect the quality later on):
[http://www.m-audio.com/index.php?do=support.faq&ID=e3f83a97b5b9ea3d8875e546ab813516](http://www.m-audio.com/index.php?do=support.faq&ID=e3f83a97b5b9ea3d8875e546ab813516)

---

### Post by eamner on 2011-01-11
> **AutoStatic said:**
> Try running **ffado-diag** in a terminal when you get home (you might need to install the **ffado-tools** package first) and post the results here.

Alright, this is the complete output from ffado-diag (I had to install ffado-tools):

```
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-24-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ 2.0.5
     flags ...........  -lraw1394  
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
   dbus-1 ............ 1.4.0
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
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
04:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (8000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fe500000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at d000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
stepping        : 2
cpu MHz         : 2926.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5851.43
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
stepping        : 2
cpu MHz         : 2926.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5851.84
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
stepping        : 2
cpu MHz         : 2926.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 2
apicid          : 4
initial apicid  : 4
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5851.85
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
stepping        : 2
cpu MHz         : 2926.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 2
apicid          : 5
initial apicid  : 5
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5851.86
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [41, 41, 41, 41], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:   [79, 79, 79, 79], Sched None (priority None), drivers: ['i8042']
 IRQ    4: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['']
 IRQ    5: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['parport0']
 IRQ    8: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   16: PID:  None, count: [1724, 1724, 1724, 1724], Sched None (priority None), drivers: ['ehci_hcd:usb1']
 IRQ   19: PID:  None, count: [4927, 4927, 4927, 4927], Sched None (priority None), drivers: ['ata_piix', 'ata_piix']
 IRQ   21: PID:  None, count:   [23, 23, 23, 23], Sched None (priority None), drivers: ['firewire_ohci']
 IRQ   23: PID:  None, count:       [8, 8, 8, 8], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   43: PID:  None, count: [2252, 2252, 2252, 2252], Sched None (priority None), drivers: ['eth0']
 IRQ   44: PID:  None, count: [165, 165, 165, 165], Sched None (priority None), drivers: ['hda_intel']
 IRQ   45: PID:  None, count:       [8, 8, 8, 8], Sched None (priority None), drivers: ['hda_intel']
 IRQ   46: PID:  None, count: [16024, 16024, 16024, 16024], Sched None (priority None), drivers: ['fglrx']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.
```
I'm not an expert on this, but that last message really worries me... Sorry, most of that stuff is chinese to me...

Regarding "CPU Scaling", I looked for that option in my BIOS, but I didn't find it. I did find a "performance" option that mentions something about clock frequency, but it is not enabled.
Also, I tried to do the "killall powernowd" trick, but I don't have that process running, so I guess I'm not using cpu scaling.

FYI: this is my desktop pc: Intel I3 CPU 2.93 ghz, Intel motherboard with integrated audio (enabled), ATI Radeon HD 5700 GPU... if you need more info let me know.

By the way, the ffado program I mentioned before is ffado-mixer. And this is what I see when I run it (via kde menu):
FW Solo (Dummy) / Clock Source: internal (CSP) / Nickname: unsupported / Sample rate: 48000.
...and the log messages:
```

20:54:18 dbus: connecting to: Updated on /org/ffado/Control/DeviceManager (server: org.ffado.Control)
20:54:19 panelmanager: PanelManager::updatePanels()
20:54:19 panelmanager: going to add 000d6c0b00c287ab
20:54:19 panelmanager: Adding device 0: 000d6c0b00c287ab
20:54:19 panelmanager:  Found (000d6c0b00c287ab, D6C, 10062) M-Audio FW Solo
20:54:19 registration: version/GUID combo already registered

```

More info:
This are some of the parameters I have set in qjackctl:
Server path: /usr/bin/jackd / Driver: firewire/
Realtime (ckecked) / Priority: 89 / Frames/Period:512 / Sample rate: 44100 / Periods/Buffer:3 / Port Maximum:256 / Timeout:2000 / Interface: hw:0 / Audio: Duplex / Input channels (and output): default.

Last comments: the xruns start even when I'm not running any audio app. And the DSP load (seen in qjackctl) is usually lower than 1%.

Please let me know if you need more information.

---

### Post by eamner on 2011-01-11
> **trulan said:**
> Keep hanging in there, you'll get it!  The only other potential problem could be if you have an IRQ conflict (yes, those still exist), especially if you are using a laptop.  On mine, the wireless card and the firewire controller share an IRQ and ffado doesn't like to share, so I have problems if I forget to turn my wireless card off before starting Jack.  The output of ffado-diag contains this information.  But CPU scaling is the more likely culprit.

Hello trulan. I don't think it's a IRQ conflict (I assume this from the output I posted in my recent previous post). However perhaps I'm wrong. If there's a test you'd like me to perform, let me know.

[QUOTE=argoson]It does seem you are having problems with the system not detecting the FW solo box. it might come from firewire stack issues (RAW1394), mostly permissions.

Did you check the link to the tutorial i linked ? 
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Here is another tutorial that helped me a lot - especially the comments at the bottom:
[https://westcoastsuccess.wordpress.c...e-solo-ubuntu/](https://westcoastsuccess.wordpress.c...e-solo-ubuntu/)

There is a utility called 'gscanbus' which will help you figure out if your FW solo box is detected . see if it appears in your software repositories (or look for a download of it).[/QUOTE]
Hello argoson. Yes I did check that link. Trust me, if there's a firewire tutorial in internet, I have followed it :P. However as I said before, I have made so many tweaks and changes, that I'm afraid I'd have messed things up. 
Actually, when I run:
```
lsmod | grep 'firewire\|1394'
```
... I get this:
```
firewire_ohci          21042  0 
firewire_core          46643  11 firewire_ohci
crc_itu_t               1383  1 firewire_core
```

...now, that last message from the ffado-diag output (in my previous post) really left me worried... :confused:

Regarding **gscanbus**, I tried to install it, but was impossible. I tried to install it via .deb. It always gives this error: 
```
Error: Dependency is not satisfiable: libglib1.2(>=1.2.0)
```
I also downloaded the .tgz version, but same result... so I gave up.

---

### Post by AutoStatic on 2011-01-12
> **argoson said:**
> It does seem you are having problems with the system not detecting the FW solo box. it might come from firewire stack issues (RAW1394), mostly permissions.This is not the case. The FireWire Solo is being detected and it works.

> **argoson said:**
> There is a utility called 'gscanbus' which will help you figure out if your FW solo box is detected . see if it appears in your software repositories (or look for a download of it).gscanbus is deprecated, obsolete. The ffado-tools package provide all the utilities you need. The gscanbus equivalent is **ffado-test ListDevices**.

Best,

Jeremy

---

### Post by AutoStatic on 2011-01-12
> **eamner said:**
> Alright, this is the complete output from ffado-diag (I had to install ffado-tools):Thanks! Looks good. Your FireWire controller apparently doesn't share an IRQ with another device so the culprit is probably CPU scaling. You have to disable it per CPU core so a little script would be the best option. Have to dig that up though. You can disable it in your BIOS too, wouldn't recommend it though. It's probably called SpeedStep. Don't worry about the "This stack is not supported by FFADO" warning, it should work nonetheless (it does for trulan). I think the ffado-diag tool just does a simple check what version of FFADO you're using and if it's not 2.0.1 it just spits out this message. Since you're using a 2.999.0 version (but with support for the new stack) ffado-diag is just guessing wrong here I think.

Best,

Jeremy

---

### Post by trulan on 2011-01-12
Right.  That last line on ffado-diag is a left over - I guess I should have warned you about that so you didn't have to worry.  In the comments on the ffado 2.0.1 release announcement, one of the developers was asked about it and responded. "Oops, I missed that line in ffado-diag."  Newer versions of ffado-tools will report "The new stack is enabled.  This is still kind of experimental.  If you're having problems, try the old stack."

And you're right, no IRQ conflict, so that's good news.  With a CPU that new, you are using CPU scaling unless you expressly disabled it.  Get that disabled before you try anything else.  Ubuntu by default sets your CPU's to "On Demand" which can wreak havoc with ffado.

And if it still doesn't work, it is possible to revert to the old firewire stack.  It's quite possible that some hardware works better than others on the new stack.  I'm one of the fortunate ones whose hardware works very well indeed.

---

### Post by eamner on 2011-01-12
> **AutoStatic said:**
> You have to disable it per CPU core so a little script would be the best option. Have to dig that up though. You can disable it in your BIOS too, wouldn't recommend it though. It's probably called SpeedStep. 

Ok, I read somewhere in this forum that there's an applet in ubuntu for that, but I don't know if it works in kubuntu (I haven't looked much for it though...)

In this thread..
[http://www.uluga.ubuntuforums.org/showthread.php?t=1428721](http://www.uluga.ubuntuforums.org/showthread.php?t=1428721)
They also mention something about enabling the "no memory lock" option. I haven't tried that. Will do that tonight (I'm not at home at this moment).
If you guys find a better good option to do it, let me know.

Now, what's really got me worried, is that in the last days, I have not been able to get sound from it (with or without xruns!). I've been testing with Hydrogen, and the only way I get sound is starting jack with ALSA (with the onboard sound). A few weeks ago I could hear it through the Solo. I don't know what I broke! :(

[QUOTE=trulan]And if it still doesn't work, it is possible to revert to the old firewire stack. [/QUOTE]
Let's leave that as a last option... :(

Oh! one last thing... now I know definitely that the interface is recognized: when I open Patchage, I see the two windows for "firewire_ohci", with 4 INs in one window and 4 OUTs in the other one (two "line" and two "spdif" each). ...and when Hydrogen starts, it automatically connects to the two line outs in this window. Yet now I hear nothing. I have configured Hydrogen with the Auto option in the driver selection. :confused:

---

### Post by Pablo_F on 2011-01-12
I suggest you try with a jack-aware multimedia player, in case there is something wrong in hydrogen. Aqualung is in the software center and it plays nicely with jack.

Anyway, (I don't think it has something to do with this actual problem but) select jack instead of auto in hydrogen (this way you make hydrogen "jack transport-aware").

Cheers! Pablo

---

### Post by AutoStatic on 2011-01-12
> **eamner said:**
> Ok, I read somewhere in this forum that there's an applet in ubuntu for that, but I don't know if it works in kubuntu (I haven't looked much for it though...)That's the CPU frequency scaling applet for the Gnome panel, no idea what the KDE equivalent would be.

> **eamner said:**
> They also mention something about enabling the "no memory lock" option. I haven't tried that. Will do that tonight (I'm not at home at this moment).
If you guys find a better good option to do it, let me know.That specific user probably didn't configure memory locking properly. When you have the memlock setting in your */etc/security/limits.d/audio.conf* file I don't see why you should use this options, seems contradictory to me.

> **eamner said:**
> I have configured Hydrogen with the Auto option in the driver selection.Try setting it to Jack as Pablo suggests also. Auto doesn't work wel for me either.

Best,

Jeremy

---

### Post by eamner on 2011-01-12
> **AutoStatic said:**
> gscanbus is deprecated, obsolete. The ffado-tools package provide all the utilities you need. The gscanbus equivalent is **ffado-test ListDevices**.


Hello. This is the output from ffado-test ListDevices:
```

-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000d6c0b00c287ab  0x00000D6C  0x00010062   M-Audio - FW Solo
**00263822067: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0**
no message buffer overruns
```
Is this normal? :confused:

Also, in Kinfocenter, I looked for info about IEEE1394 devices. This is what it says (I made a screenshot so you could see it better):
[http://img.photobucket.com/albums/v624/eamner/screen1.jpg](http://img.photobucket.com/albums/v624/eamner/screen1.jpg)

---

### Post by eamner on 2011-01-12
> **Pablo_F said:**
> I suggest you try with a jack-aware multimedia player, in case there is something wrong in hydrogen. Aqualung is in the software center and it plays nicely with jack.

Anyway, (I don't think it has something to do with this actual problem but) select jack instead of auto in hydrogen (this way you make hydrogen "jack transport-aware").


Hola Pablo!
I followed your suggestion. No sound from Aqualung (I ran it with "aqualung -o jack").
Also, I changed "auto" to "jack" in Hydrogen. No change.

---

### Post by eamner on 2011-01-12
> **AutoStatic said:**
> You can disable it in your BIOS too, wouldn't recommend it though. It's probably called SpeedStep. 
Guess what? I found that option in the BIOS. Indeed it is called Intel SpeedStep Technology. I disabled it. What happened is that I didn't get any xrun in the qjackctl main window. HOWEVER I did get lots of xrun messages in the messages window... take a look at the screenshot:
[http://img.photobucket.com/albums/v624/eamner/jack2.jpg](http://img.photobucket.com/albums/v624/eamner/jack2.jpg)

Basically the same thing happens if I start jack in the terminal:
[http://img.photobucket.com/albums/v624/eamner/jack1.jpg](http://img.photobucket.com/albums/v624/eamner/jack1.jpg)

When these xrun messages are running, the pc becomes unstable and no other program will start (hydrogen says it cannot start jack server). 
The messages run for about a minute and then they stop and the system seems to calm down, however a few seconds later they start again. And in order to start jack again I have to reboot the pc.

Could the "node 1" error that I mentioned before be the cause of the problem?

By the way, I forgot to mention: the Auto option in hydrogen used to work for me before (through the Solo). It was when I choosed "jack" option that I couln't make it work. What is really driving me mad is that a couple weeks ago, I could get sound from it...

---

### Post by AutoStatic on 2011-01-13
First thing that comes to mind is that you could try running Jack2 in synchronous mode. I've barely used Jack2, but iirc that's the -S option for the jackd command. Jack2 runs in async mode by default, maybe that is causing issues.

[http://www.grame.fr/~letz/jackdmp.html](http://www.grame.fr/~letz/jackdmp.html)

---

### Post by AutoStatic on 2011-01-13
> **eamner said:**
> Could the "node 1" error that I mentioned before be the cause of the problem?Don't think so, this message is probably firmware related. Did you update the firmware of your Firewire Solo recently? And a newer version of FFADO might help, they did change something in the code recently afaik to prevent this kind of errors from happening.

---

### Post by trulan on 2011-01-13
> **eamner said:**
> ```
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000d6c0b00c287ab  0x00000D6C  0x00010062   M-Audio - FW Solo
**00263822067: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0**
```Is this normal? :confused:
Yes, if you're running the new firewire stack anyway.  I've no idea what it means, but I always get that.

I'll second the vote for running Jack2 in synchronous mode - I'd forgotten about that.  It's been a while since I used Jack2 but that did help a lot as I recall.  Add -S to the jack command line, or add it in the qjackctl window.

---

### Post by eamner on 2011-01-13
> **AutoStatic]Did you update the firmware of your Firewire Solo recently? And a newer version of FFADO might help, they did change something in the code recently afaik to prevent this kind of errors from happening. 
[/QUOTE]
Mmm.. no, I installed the drivers (from the CD) in Win7. I don't know if that did the firmware update. But I remember even after that, I used to get sound from the interface.
I think I installed ffado through "apt-get". Should I download it from ffado.org?

[QUOTE=trulan said:**
> 
I'll second the vote for running Jack2 in synchronous mode - I'd forgotten about that.  It's been a while since I used Jack2 but that did help a lot as I recall.  Add -S to the jack command line, or add it in the qjackctl window.

Ok guys, I will try that tonight. I'll let you know the result.

---

### Post by AutoStatic on 2011-01-13
> **eamner said:**
> Should I download it from ffado.org?No, that's not necessary as trulan already pointed out he has the same error but the device works anyway. Try Jack2 with the -S option first.

---

### Post by eamner on 2011-01-13
Quick question before I do my tests tonight: is it true that I shouldn't plug the Solo while the pc is turned on? (hot plugging).
I read somewhere something about the interface becoming unusable if I do that... is this right or am I confused? I have never tried to do it (even though I don't use the power cable -- I use the 6pin connection).

---

### Post by trulan on 2011-01-13
Hot plugging:  My experience is as follows.  On the old firewire stack (Ubuntu 10.04 and older) it worked best to have the device plugged in and turned on **before** booting the computer.  On the new firewire stack (Ubuntu 10.10 and newer) it is exactly the opposite - I sometimes have problems if the device is plugged in too soon - it seems to work better to only plug in and tun the device on **after** the computer is fully booted up.  YMMV.

---

### Post by AutoStatic on 2011-01-14
Hotplugging works fine for me on the old stack.

---

### Post by eamner on 2011-01-14
Hello. Guess what...
I found out that all this time I've been using jack2. I checked Kpackage and saw the installed packages ("jack1" was not installed). So, I proceeded to install jack1 and "jack1-firewire" (automatically jack2 was uninstalled). The result: although the messages in the message window are a bit different, the behavior is basically the same. Still no sound and still getting xruns from time to time. And after a few xruns, the jack server is shut down. If I'm running hydrogen, a few xruns later it gives the error "jack server is down", or something like that.
BTW, the difference with disabling the SpeedStep technology in the BIOS, is that I get xruns messages in the "message window", but not in the jack main window (the one with the colored buttons). If I enable SpeedStep, I get the xruns both in the message window and in the main window. Anyway, the result is always the same, the machine becomes unstable and the programs won't work.
 Quick question: Is there a way to reinstall the **whole** sound system in linux (without reinstalling linux)?
 As you might understand, I'm beyond frustration.

---

### Post by Pablo_F on 2011-01-14
Hi, 

You have the firewire interface (which btw is just "reported to work"), the firewire controller, the firewire controller modules in the kernel, the ffado drivers, jack and the jack-aware applications. The problem seems to be in a low level, at least at driver level, maybe lower than that, at kernel or hardware level. It is difficult to know. 

In ubuntu 10.04 at least you can try with a rt kernel and the old firewire stack. In Maverick you don't have these options. 

Wait a bit, see what Auto and Trulan comment but I would forget the computer for a day or two and start with a ubuntu lucid based distro from scratch. It is better supported by the community. Maybe tangostudio is a good option.

My 2 cents...

Take it easy. Regards, Pablo

---

### Post by eamner on 2011-01-14
> **Pablo_F said:**
> 
Wait a bit, see what Auto and Trulan comment but I would forget the computer for a day or two and start with a ubuntu lucid based distro from scratch. It is better supported by the community. Maybe tangostudio is a good option.


Thanks for your encouraging words, Pablo. I'm taking one or two days of rest because this thing has got me really stressed. I don't really want to reinstall the whole system... I use the pc for other things besides music... I'll leave that as a very last option...
In the next days I'll try to experiment changing other parameters. 
If that doesn't work I'm thinking the possibility of selling this interface and buying another one with more compatibility... the problem is that it is very hard to find these interfaces in my country (I live in Venezuela).
Hey you are in hispasonic, right?

---

### Post by eamner on 2011-01-14
**OH MY GOD**! I can't believe this.
Right after writing my previous message, as I had nothing to lose, I tried starting Hydrogen (as you know, if jack is not running, it starts the server automatically). And I got sound from the Interface!
Immediately, I also started Aqualung and it also played music!! (it said it was using jack @44100hz). 
I had done that before (starting Hydrogen without starting jack manually). The ONLY difference here, is that this time I waited some time before starting it (I was reading email, navigating the forum...). In the last days, when I was testing, I used to start the programs right after rebooting the machine. 
Could it be that it takes some time before all drivers and daemons are started?
HOWEVER, the bad news is that now it is working as it used to work some weeks ago: after a couple minutes (and shortly after I started Aqualung) it raised a message like "*jack has been shut down because it was not fast enough. You can try starting jack and Aqualung again*". And of course hydrogen stopped playing too.
Of course I guess this is because of the xruns.....
How about that? 
I'll try repeating the experience again tomorrow (I want to sleep happy tonight). ;)

---

### Post by trulan on 2011-01-14
When your break is over and you're all rested up, you can try two more things, if you'd like.  You could disable the new firewire stack and load the old one, and you could install a realtime kernel and get that set up.  This would likely be less painful than reinstalling your entire system, and would allow you to run with pretty much all the relevant pieces that you would have with a 10.04 installation.

Ubuntu 10.10 is pretty much a 'transition' release when it comes to firewire audio.  It uses the new JuJu firewire driver stack, and while that apparently still has some difficulties, it will soon be our only option as the kernel to be used by 11.04 will have the legacy firewire driver stack removed completely (rather than just blacklisted like it is in 10.10.), if I understand correctly.  I've been hesitant to recommend that people using 10.10 revert to the old stack for this reason, but if that's what it takes to get it to work, then that's what you should do.

Edit:  Just saw your last post...I'm not sure what to say except - sleep happy tonight!

---

### Post by eamner on 2011-01-18
Hello, I'm back.
I've been doing some tests. I have disabled the SpeedTest option in the BIOS. I don't really see it makes much difference in the performance, though.
I'm still running jack1, with the "jackd -d firewire -r 44100" command. When I start it via terminal, I start Aqualung and I'm able to listen to some mp3s. However the performance is not flawless. There are some brief silences and glitches (I suppose from the xruns).
For some strange reason, when I start Hydrogen with the Auto parameter, I get sound from it, and I'm able to work with it for some minutes before jack is down. If I start it with the Jack parameter, I can't even get sound from it, and the terminal window shows this error: *"unknown destination port in attempted connection [alsa_pcm: playback_1]"*
Any theory?

---

### Post by eamner on 2011-03-02
Hello. Sorry for not updating in a long time.
Unfortunately I finally gave up with this... I've been thinking about waiting for kubuntu 11 on April, just to see if there's any improvement with Firewire, but...
Anyway, most probably I will sell the Solo and try to buy a new one. Can anybody give me a nice recommendation? preferably on USB or PCI interface? I need a sure thing, an interface that will work out of the box. No more experimenting for me.. :confused: 
I don't need the "ultimate best interface"... just something that allows me to work with a decent latency and good sound, of course in linux. I mostly work in my home studio, with virtual instruments (vst, sfs, etc).
Thanks.

---

### Post by Pablo_F on 2011-03-02
Hi, 

I can recommend M-audio's PCI's like Audiophile 2496, or Delta 44, 1010LT... They work like a charm with alsa-jack. Use envy24control to access the hardware mixer and options (just install "alsa-tools-gui" package).

If you can choose PCI, don't choose USB.

Cheers, Pablo

---

### Post by eamner on 2011-03-14
Hello Pablo, sorry for the late response.
Question: I've read in this site, that Delta 44 and AudioPhile 2496 are not supported in Linux. Can you confirm?
--> [http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

I know that site is not very updated, but just want to be sure, specially having in mind that probably I'll be updating to 11.04 when it comes out.

---

### Post by ailo.at on 2011-03-16
> **eamner said:**
> Hello Pablo, sorry for the late response.
Question: I've read in this site, that Delta 44 and AudioPhile 2496 are not supported in Linux. Can you confirm?
--> [http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

I know that site is not very updated, but just want to be sure, specially having in mind that probably I'll be updating to 11.04 when it comes out.

They are supported and have been for many years, however they won't work with Pulseaudio out of the box, because of how Alsa presents the inputs and outputs to Pulseaudio. But there is a fix.
There are no problems using Jack, however. I use two M-audio cards in sync having 12 ins and outs. Works perfectly.

To check which pci devices are supported, here' the link to Alsa's page [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Here's the fix to get Pulseaudio working with those cards on newer Ubuntu's [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30)

---

### Post by eamner on 2011-03-16
> **ailo.at said:**
> They are supported and have been for many years, however they won't work with Pulseaudio out of the box, because of how Alsa presents the inputs and outputs to Pulseaudio. But there is a fix.

Thanks a lot. By the way, I'm selling my firewire Solo right now.

---

### Post by sgx on 2011-03-16
> **eamner said:**
> Hello Pablo, sorry for the late response.
Question: I've read in this site, that Delta 44 and AudioPhile 2496 are not supported in Linux. Can you confirm?
--> [http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

I know that site is not very updated, but just want to be sure, specially having in mind that probably I'll be updating to 11.04 when it comes out.
Hi, my revision 2 M-Audio 24/96 pci works great, no tweaking needed,
I blacklist the motherboard soundchip. Sound is great, others use
better cards from the same maker, for more complex studio uses.
Cheers.

---

### Post by eamner on 2011-07-28
Hello everyone.
Sorry for bringing this post back again, but, I just wanted to update my status. I just sold my Firewire Solo. Now I'm planing the purchase of my new interface. Some of you have recommended some good alternatives. I'd just like to confirm the best options, having in mind that now I have kubuntu 11.04. I have the following options to buy: M-audio 1010lt, M-audio 2496, and a few others. Could you please help me choose, by taking a look at this link, and letting me know the best option? please have in mind that I'm mostly a home user:
[http://listado.mercadolibre.com.ve/%2Fm%C3%98audio](http://listado.mercadolibre.com.ve/%2Fm%C3%98audio)

The site is in spanish but I just need you to give me your advice about the best options.
Thanks in advance.

---

### Post by Pablo_F on 2011-07-28
In my experience, both m-audio 1010LT and 2496 work like a charm. In 11.04 you just have to install alsa-tools-gui and tweak the levels via envy24control, analog volume tab. 

Anyway, it is up to you to decide if you want a PCI device or a portable one and how many I/O you need. 

Cheers, Pablo

---

### Post by eamner on 2011-07-29
Thank you Pablo, I think I'm going for the Delta 1010lt. It's a little more expensive than the 2496 but I think it's a little better and has more connectivity options. Just one last question: can I use this card in combination with my onboard audio card? (Intel). Or, do I need to disable the onboard card?

---

### Post by Pablo_F on 2011-07-29
Yes you can, but in general it is a good idea to disable the onboard if you are not going to use it.

---

### Post by eamner on 2011-07-29
Thanks for your quick answer Pablo... I was asking because I'm thinking about other possible audio needs (multimedia, web, flash, movies, etc). How does the 1010lt handle 5.1 sound? I have a 5.1 speaker system.

---

### Post by Pablo_F on 2011-07-29
I have only tried the 1010LT in a stereo configuration but I think it will work out of the box (1) in 5.1 with the default audio system (pulseaudio) . 

In any case, imho that card suits better for audio production than for home cinema.

Cheers, Pablo

(1) Or almost, this is, after tweaking analog volumes in envy24control

---

### Post by eamner on 2011-07-29
That's all I need to know! I'm buying this one.
Thanks! ):P

---

