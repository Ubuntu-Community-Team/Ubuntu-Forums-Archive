---
title: "Presonus Firepod, JACK, xruns - help needed"
date: 2011-02-28
forum: Ubuntu Studio
---

### Post by Brendo613 on 2011-02-28
Taken from[ original post here]("http://ubuntuforums.org/showthread.php?p=10506807#post10506807")


I've been reluctant to start a new forum post because of the amount of information I've learned by searching previous postings; however, I am ready to admit to the online community (as I turn to you for help) that I do not understand how to get a reliable multitrack recording setup set up.

This is how I've been running my system.  I have 8 mic channels coming in from the Presonus Firepod.  The computer is a Pentium dual core 1.46GHz.  Using A. Bogani's 2.6.38-1-lowlatency kernel while running Ubuntu 10.10, I open JACK with "gksudo qjackctl," start the server, then invoke Audacity the same way.  (JACK needs to be run as root, otherwise I can't get realtime to work, I believe because of a cgroups issue; Audacity must be run as root, else it doesn't "see" JACK running.)

**JACK incurs xruns.**  JACK is ignorantly configured:
[LIST]
[*]realtime enabled
[*]memory unlocked
[*]priority: 89
[*]frames/period: 512
[*]44100k
[*]periods/buffer: 8
[*]port maximum: 128
[*]1sec startup delay
[*]timeout: 500ms
[*]default interface; capture only; input channels: default
[/LIST]

[center]**the issue**[/center]
JACK crashes, which crashes Audacity and I lose my work; I also incur xruns [seemingly] unpredictably, if I am lucky enough to not have JACK crash.  I can't start JACK again without powering off/on the board or unplugging/replugging the   data cable.  I haven't caught an error log where JACK has out and out crashed, but I do have a log saved from today.  I was recording 8 inputs when this happened, using only one mic  (can't figure out how to single out one channel out a time).  

```
[...]
Jack: fPollTable i = 1 fd = 51
Jack: fPollTable i = 2 fd = 52
Jack: fPollTable i = 3 fd = 54
Jack: fPollTable i = 1 fd = 51
Jack: fPollTable i = 2 fd = 52
Jack: fPollTable i = 3 fd = 54
Jack: FFADO XRun
JackAudioDriver::ProcessAsync: read error, skip cycle
18:46:08.988 XRUN callback (1).
Jack: fPollTable i = 1 fd = 51
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
JackPosixMutex::Unlock res = 1
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 3
JackPosixMutex::Unlock res = 1
Jack: JackExternalClient::ClientNotify ref = 3 name = PortAudio notify = 3
Jack: fPollTable i = 2 fd = 52
Jack: fPollTable i = 3 fd = 54
[...]
```

Look at this error message - it mentions a FFADO xrun.  When I run ffado-diag, I get:
```
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.38-1-lowlatency
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
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
0a:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:011d]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0400000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME+
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 1467.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 2933.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 2933.26
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [7523629, 7523629], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:     [17397, 17397], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [1489, 1489], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:           [51, 51], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:     [16882, 16882], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count: [1750897, 1750897], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'firewire_ohci']
 IRQ   17: PID:  None, count:   [184463, 184463], Sched None (priority None), drivers: ['mmc0', 'r852', 'ath']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb7']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb6']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   23: PID:  None, count:           [10, 10], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb5']
 IRQ   43: PID:  None, count:     [46437, 46437], Sched None (priority None), drivers: ['ahci']
 IRQ   44: PID:  None, count:         [477, 477], Sched None (priority None), drivers: ['i915']
 IRQ   45: PID:  None, count:             [3, 3], Sched None (priority None), drivers: ['eth0']
 IRQ   46: PID:  None, count:         [179, 179], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

```

How is FFADO being used by JACK, when the stack it requires is not loaded?
Today, while recording vocals only (nothing on playback), I noticed a ~1sec repeated line of what I had just sung being played back through the speakers; I also saw the output meter on Audacity rise in correspondence with the audio played.  If this playback glitch happens while recording, could this be screwing with the "buffer zone" and overloading it?  The xruns and instability can't be caused by other programs' workloads - there have been times when nothing else is open and xruns occur, as well as vice versa.

Please help!  I don't want to give up on Linux, just to record.

---

### Post by AutoStatic on 2011-03-01
Hello Brendo613,

Try this real-time kernel: [http://tangostudio.tuxfamily.org/en/kernel-rt](http://tangostudio.tuxfamily.org/en/kernel-rt)
This will save you from running everything as root. Also set your periods/buffer to 3. Basically one only needs 2 for onboard and PCI(e) cards and 3 for USB/FireWire cards.
And Audacity is not such a good choice for doing multi-track recordings:
- It is actually a wave editor, not a multi-track recording program
- It doesn't talk directly to JACK but uses an extra layer (PortAudio). So you'll run into xruns much faster.

So give Qtractor or Ardour a try, those are specific multi-track recording programs. And don't worry about the FFADO messages about the stack not being loaded, it's a bogus message.

Best,

Jeremy

---

### Post by Brendo613 on 2011-03-03
Thanks for the suggestions.  I am very hesitant to abandon using Audacity at this point, for one due to my familiarity with it, but mainly because becoming familiar with Ardour is not looking to be an easy task, by any means.  With Audacity I can whiz around keyboard shortcuts that don't seem available in Ardour, but I may just be missing something ... I certainly may be missing a lot, because Ardour's interface is majorly tripping me up :x

I read about changing [PulseAudio settings](https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK) if I am to use JACK and Audacity together, but that seems like it may break too many other things.

It's probably most prudent to follow your advice.  The kernel you suggested is the easiest new thing to try (the gksudo thing is a royal pain). but I'm not sure how to apply the kernel patch - can you help me there?.  Qtractor, I have yet to play with.  Any tips for getting comfortable with the seemingly un-intuitive Ardour?  It's unlike me to not be able to figure something out on my own

---

### Post by sgx on 2011-03-04
> **Brendo613 said:**
> Thanks for the suggestions.  I am very hesitant to abandon using Audacity at this point, for one due to my familiarity with it, but mainly because becoming familiar with Ardour is not looking to be an easy task, by any means.  With Audacity I can whiz around keyboard shortcuts that don't seem available in Ardour, but I may just be missing something ... I certainly may be missing a lot, because Ardour's interface is majorly tripping me up :x

I read about changing [PulseAudio settings](https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK) if I am to use JACK and Audacity together, but that seems like it may break too many other things.

It's probably most prudent to follow your advice.  The kernel you suggested is the easiest new thing to try (the gksudo thing is a royal pain). but I'm not sure how to apply the kernel patch - can you help me there?.  Qtractor, I have yet to play with.  Any tips for getting comfortable with the seemingly un-intuitive Ardour?  It's unlike me to not be able to figure something out on my own

Hi, lots of youtube videos for ardour, and also hydrogen, qjackctl, and other apps get coverage. I believe there are four or five mouseclicks needed, to create a project, a track, arm the track, press play, then press record, (or the other way around) so it won't be difficult once you see it in action. I have read that it's audio fidelity is outstanding.
Cheers  (Would it really be so hard for devs to put those steps in a
drop-down list from a main menu item?

---

### Post by AutoStatic on 2011-03-04
> **Brendo613 said:**
> I read about changing [PulseAudio settings](https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK) if I am to use JACK and Audacity together, but that seems like it may break too many other things.You don't need to look at PulseAudio. All that matters now is FFADO/JACK. In Audacity you can select JACK for bot input and output, no need for PulseAudio.

> **Brendo613 said:**
> The kernel you suggested is the easiest new thing to try (the gksudo thing is a royal pain). but I'm not sure how to apply the kernel patch - can you help me there?.It's already patched. So you have to add the lowlatency repository according to the [link]("http://tangostudio.tuxfamily.org/en/kernel-rt") I posted and install the **linux-realtime** package. The info in the link is a bit cryptic (it's translated from French) so if things are unclear don't hesitate to ask.

> **Brendo613 said:**
> Any tips for getting comfortable with the seemingly un-intuitive Ardour?Yes, try Qtractor ;)

Best,

Jeremy

---

### Post by Pablo_F on 2011-03-04
> Any tips for getting comfortable with the seemingly un-intuitive Ardour?

[http://www.ardour.org/node/3322](http://www.ardour.org/node/3322)
[http://en.flossmanuals.net/ardour/](http://en.flossmanuals.net/ardour/)
[http://www.youtube.com/watch?v=43ES7p4ejX0](http://www.youtube.com/watch?v=43ES7p4ejX0)
[http://vimeo.com/2867399](http://vimeo.com/2867399)

---

### Post by Brendo613 on 2011-03-21
All right, Ardour is more familiar to me now.  Too many problems kept popping up with the 10.10 / Natty kernel install - JACK would crash, Ardour would "run out of disk space" (wtf?!), and wireless internet detection disappeared for a week or so then came back ... I can't use a system like that :D  are you kidding me.

I've been researching what other linux audio distro's there are.  It looks like Ubuntu Studio is the only currently supported one.  I'm trying ubuntu 9.10, upgraded into ubuntu studio.  It doesn't work with jack.  It's using jack, not jackd-firewire / jack2 which is what I had success with before.  Should I upgrade to 10.04?  Isn't that where all the stupid cgroups issues and stuff come into play?

I just want to have a stable system.  I promise to never do any more updates or even open a webpage ever again.  My friend needs me to record a non-existent soundtrack for his movie, so my pressure is on!

Oh, here is a list of failed-to-work distros: 64studio, & Puredyne.  I got these to load but they wouldn't work.  Musix, DeMuDi, JAD, and dynebolic wouldn't load.

---

### Post by Pablo_F on 2011-03-22
Hi,

Currently and imho, the "top two" distros for the home studio, with regards to stability, overall configuration and ease of use for the newcomer, are Tango Studio Karmasutra and AV Linux.

Anyway, if you have poblems try to narrow down the sources of them. And, generally speaking, trust the default configurations and do one change at a time. 

Cheers! Pablo

---

### Post by Brendo613 on 2011-03-27
AV Linux has been on my computer since you'd recommended it a few days ago, which has allowed me time to get acquainted with it.  It feels stripped down enough that things are allowed to function without extras clogging things up.  TangoStudio was xrun hell for me, even with the same settings in JACK that are being used in AV Linux :O  Go figure.  I'm not technically sufficient enough to tell you why, but the problem was evident running Tango as a liveCD.  I had vague hope it would work well once installed, because I really liked that distro - but AV Linux is what I have installed now because I need my studio to function :D

It's looking good, guys.  JACK has been running for hours this afternoon and I can even use ol' familiar - Audacity.  As long as I don't press the right arrow to jump ahead while playing back audio, I am fine (doing so crashes the program).  Thank you again for the pointer!  At least my Firepod works and can be used now :)

Do you know if there's any way to select what input of the mixer is being recorded in Audacity?  If I want to record on channel 3, for example, the only way I know of is to record channels one through three simultaneously.  Then I just cancel out the "extras" later.  It's kind of redneck, but it works :D  Oh, and it beats the hell out of Ardour for me because I just can't seem to afford the time to get familiar with it.  Too many "easy" tasks are not only in my knowledge, but also I can't seem to figure them out, even when searching the web and the Ardour manual for help.

---

### Post by ailo.at on 2011-03-27
Don't know how much is covered here: [http://www.flossmanuals.net/audacity/](http://www.flossmanuals.net/audacity/)
There's also: [http://audacity.sourceforge.net/help/](http://audacity.sourceforge.net/help/)

You might find that multi-track recording and effects processing is easier done on another program, like Ardour, Qtractor or Rosegarden.
Audacity can be used for that of course, but is more adapted to editing audio files.

---

### Post by Pablo_F on 2011-03-27
Hi,

Well, I agree with ailo.at but I also understand that you have to stick to what works for you... But note that:

Audacity is a bit tricky with regards to jack connectivity,. At least in the versions I have tried so far. 

If you take a look at the connections window of qjackctl (Jack Control) you will see that Audacity's ports (they probably appear as "portaudio") are not there unless the play button in Audacity is pressed (either recording or playing back) and that new ports are created each time you press the play button.

In that window, you can connect/disconnect Jack clients' ports. On the left column you should see the ones corresponding to the input channels of your audio card, connected to audacity's inputs. Of course, there are some connections that you don't need.

So there is a little problem here: You want to disconnect something but you only can do that once Audacity is already recording.

The workaround is pressing the Pause || button, immediately afterwards the record and play buttons, do/undo connections in qjackctl and press the pause button again.

Cheers, Pablo

---

### Post by trulan on 2011-03-27
To select which channel to record when using Audacity:

Pablo_F pretty much covered it.  As soon as you click 'stop' in Audacity, all JACK connections disappear and are forgotten.  So, to record only channel 3, you'll have to hit record and pause.  Then, you need to make the correct JACK connections.

My favorite program for this is called Patchage.  It's not installed by default on AVLinux, but it's in the repos.  Jack connections make a lot more sense to me when using Patchage. AVLinux includes the LinuxDSP JACK Patchbay which works well too, but I don't like the layout as good.  Also, the 'Connect' tab in Jack Control will do the job.

With Audacity still paused, you'll need to first disconnect the virtual connection from input one to Port Audio in.  Then, connect the desired input (input 3, in this case) to Port Audio in.  Now, you're ready to go back to Audacity and unpause it so you can finally start recording.

It works this way because Audacity has to use that extra layer, Port Audio, to connect to the JACK audio server.  This is precisely why everybody keeps recommending other recording software that will work directly with JACK.  You will probably find these limitations very frustrating (I do!!) and hopefully you can find some spare time to play around with some other recording software.

Good luck!

---

### Post by Brendo613 on 2011-04-03
The port audio thing threw me for a loop before - I came across what Pablo_F mentions when I was fooling around with JACK a while back.  

Maybe one day I'll get over to another recording program.  It certainly makes sense, as far as an ideal recording setup goes.  Thanks for all the input and help :)

---

