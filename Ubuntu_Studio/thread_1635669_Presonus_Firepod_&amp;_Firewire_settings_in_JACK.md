---
title: "Presonus Firepod &amp; Firewire settings in JACK"
date: 2010-12-02
forum: Ubuntu Studio
---

### Post by woolyg on 2010-12-02
Hi all,
I've been knocking my head off this for days now - reading various tutorials and forum posts, etc, but I simply can't get JACK to recognise my Presonus FP10 Firewire device.

Are there any step by step tuts out there, going through what to expect? (i'm getting half way through the tut at [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) but when i run "ls -al /dev/raw1394" the output is not what is expected).. and am lost.

I've gone through every possible setting in JACK for firewire, but no dice.

Can any FP10/Firepod owners out there tell me how they got it to be recognised!?!?!

I'm quite new to Linux, so please be gentle with terminology..!

Woolyg

---

### Post by trulan on 2010-12-02
I'll start by saying that I'm the proud owner of not one but two firepods, and I've used them under Hardy, Jaunty, Karmic, Lucid, Maverick, and even a bit in Natty - which brings up the first important question:

Which version of Ubuntu are you using?

(Lucid and older uses a different firewire driver stack than is used by Maverick and newer, so Lucid (10.04) or older needs different configuration settings than Maverick (10.10) or newer.  That's why the how-to you've been reading is so confusing.  Once Natty (11.04) is out the door and everything is straightened out, this firewire configuration mess will be a lot less messy.)

---

### Post by woolyg on 2010-12-02
Hey Trulan,

It's Ubuntu standard 32-bit 10.04 - Lucid. Can you help out with which drivers/settings I should be using?

As an aside, what DAW are you using? I do love my Firepod, but am making the conscious decision to move away from costly Windows DAW's!

Thanks,
WoolyG

---

### Post by trulan on 2010-12-03
On Lucid, you'll need to use the legacy firewire driver stack, or raw1394.  Follow the steps in the guide related to this, for instance, using Ubuntu Studio controls and checking the 'enable raw1394' or 'use firewire devices' box or whatever it is called.  If it still doesn't work, post the output of:
```
ffado-diag
```

And as an aside - Ardour is my DAW.  I keep telling myself that someday I'm going to really learn to use QTractor but it hasn't happened yet.

---

### Post by woolyg on 2010-12-08
Hey Trulan

Thanks so much for your help - I ended up uninstalling standard Ubuntu and put Ubuntu Studio (10.10) in its place. (Ubuntu Studio's GUI is *cool*). Upon inputting the firewire settings, the Firepod came up and online, and I can immediately begin tracking audio.

Awesome!!!!

I have other questions about digital pops and pauses, but they are for another thread. Thanks again - VERY invaluable help!

WoolyG

---

### Post by trulan on 2010-12-09
Probably the first place to look when hunting down those pops and pauses (or xruns as they are commonly called) is CPU frequency scaling.  There are a number of ways to deal with this, but the general idea is this:  If you're running JACK and firewire audio, you really want your CPU at its max frequency, or have the scaling governor set to performance mode.

---

### Post by woolyg on 2010-12-09
Hey Trulan
Thanks for that, I'll look into it.

Going back to the first issue, the JACK manager has gone back to not connecting. I tried to select 96000 as a sample rate,but it's returned to displaying "Could not connect to JACK server as a client", even when I try to revert to 44100 hz. Hmmmm.


Here's the output of ffado-diag (does this command apply to this distro?):
------------------------------------------------





FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-23-generic
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
05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. IEEE 1394a Firewire Controller [1043:8294]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 3003.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 5998.84
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2003.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 5999.22
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:           [44, 44], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['i8042']
 IRQ    6: PID:  None, count:             [2, 2], Sched None (priority None), drivers: ['floppy']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:             [3, 3], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count:           [39, 39], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'pata_marvell', 'nouveau']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb5', 'uhci_hcd:usb8']
 IRQ   19: PID:  None, count:     [35142, 35142], Sched None (priority None), drivers: ['ata_piix', 'ata_piix', 'uhci_hcd:usb7', 'firewire_ohci']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   23: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb6']
 IRQ   44: PID:  None, count:         [686, 686], Sched None (priority None), drivers: ['hda_intel']
 IRQ   45: PID:  None, count:           [37, 37], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

---

### Post by woolyg on 2010-12-09
I think I've managed to put in the right settings for it to be stable and come online every time:

Priority:70
Frames/period:512
Sample Rate 96000
Periods/buffer: 3
Port Max: 256
Timeout: 500
Interface: hw:0
Audio: Duplex
INput CHannels: 8
Output Channels: 8


.. its starting up pretty well for me now. Can you foresee any issues with these settings?

Thanks
WoolyG

---

### Post by trulan on 2010-12-09
...But now you're using Ubuntu Studio Maverick 10.10, not Lucid 10.04 as you were at the beginning of this thread, right?

Anyway, those settings look okay.  You really should be able to take the Frames/period setting lower than that, ideally down to 128 which should get your round trip latency down to just under 10ms (the 'perfect' number).  But that might cause more xruns .

On thing I've noticed is that while the old firewire stack likes to have devices plugged in and powered on before the computer is turned on, the new stack seems to prefer waiting until the computer is fully booted up before plugging in.  Just an observation, it might explain why it works sometimes and doesn't work other times..

---

### Post by woolyg on 2010-12-09
Hey Trulan,

Yeah, using Maverick 10.10 at this stage. It seems to be stable, but I'm getting Xruns (which I've taken up in another thread.

The process I'm using is:

1. Boot up OS
2. Turn firepod on
3. Start JACK
.. and it's working fine.

Simple enough, and it's working fine.

It's a pretty good hardware setup:
Intel Core 2 3GHz
4GB paged ram, 8GB installed (utilised in other OS on machine)
Asus P5Q Mobo, S775, 1600Mhz FSB
Asus EN9600GT Black Pearl 512M Graphics

..and I'm utilising the in-built firewire port on the motherboard to port out to the firepod. 

I get loads more Xruns the lower frames/period I use. Is this normal?

---

### Post by orbesnet on 2011-01-06
not to derail but I'm going round and round and [trulan]("http://ubuntuforums.org/member.php?u=849412") you seem to know what you're talking about.

i'm a noob, but I've been searching around for a couple of days, looking for a way to get my presonus firebox to work with my new ubuntu install Natty... no love.

I've seen a lot about of this and that, but I think most of it is for older versions of ubuntu, any guidance would be appreciated.

---

### Post by AutoStatic on 2011-01-06
> **orbesnet said:**
> i'm a noob, but I've been searching around for a couple of days, looking for a way to get my presonus firebox to work with my new ubuntu install Natty... no love.Why natty? Really, do yourself a favor and install 10.04 Lucid Lynx or 10.10 Maverick Meerkat.

> **orbesnet said:**
> I've seen a lot about of this and that, but I think most of it is for older versions of ubuntu, any guidance would be appreciated.Guidance with a Ubuntu release that hasn't even reached beta yet? Then it might be better to check here: [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Best,

Jeremy

---

### Post by orbesnet on 2011-01-06
> **AutoStatic said:**
> Why natty? Really, do yourself a favor and install 10.04 Lucid Lynx or 10.10 Maverick Meerkat.


Truthfully I thought I installed 10.10 as that's what it said on the site when I d/l'd but once I was up and running I checked my status and it was Natty.  Is there a preference between 10.04 and 10.10 for running a firewire soundcard?

---

### Post by AutoStatic on 2011-01-06
> **orbesnet said:**
> Is there a preference between 10.04 and 10.10 for running a firewire soundcard?I'd go for 10.04, no hassle with different FireWire stacks and different JACK implementations. And there are no equivalent multimedia PPA's like there are for 10.04.

---

### Post by orbesnet on 2011-01-06
Working on it, we'll see how she goes.

---

### Post by trulan on 2011-01-06
What Autostatic said - your best odds are to use 10.04 at this point.  10.10 uses the new firewire stack and configuration settings are completely different.

Last I checked, Natty has got an issue with the kernel that breaks real time scheduling, making it pretty much impossible to use a firewire device, or any serious audio work really.  For reference, here are my experinces with that:
[http://ubuntuforums.org/showthread.php?t=1641877&highlight=ffado](http://ubuntuforums.org/showthread.php?t=1641877&highlight=ffado)

---

### Post by orbesnet on 2011-01-07
Ok. running 10.04.

I've gotten as far as getting the blue light to come on on my firbox once i get jack running, so it's being recognized but no sound as of yet.

I'm not really trying to set up a DAW here, I'm just trying to use the firebox as my sound card so I can enjoy some music and movies off my studio monitors.

I followed the instructions given by [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514"):
[http://ubuntuforums.org/showthread.php?t=1488678&highlight=firebox](http://ubuntuforums.org/showthread.php?t=1488678&highlight=firebox)

If there is a better way for me to go about setting this up please advise.

Thanks.

---

