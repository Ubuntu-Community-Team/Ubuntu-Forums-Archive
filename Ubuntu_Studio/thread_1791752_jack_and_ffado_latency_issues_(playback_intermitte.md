---
title: "jack and ffado latency issues (playback intermittently stops while moving the mouse)"
date: 2011-06-27
forum: Ubuntu Studio
---

### Post by jeremija on 2011-06-27
Hello, I have a firewire sound card (Terratec Phase X24). I have managed to get it to actually work by using jack and ffado. 

i start the server by using this command:
```
jackd -dfirewire
```

and by selecting the JACK output plugin in Audacious (or by using jackaudiosink output pipeline in Quod Libet).

I can hear the sound, but as soon as I move the mouse the sound intermittenly starts and stops. As soon as I stop doing that everything is OK.

I have tried to mess around with the --period and --nperiods and --output-latency values in jack server and by starting jack in both realtime and non-realtime mode, but I wasn't able to get any decent results.

Is there something else to try?

---

### Post by jeremija on 2011-06-27
Also, the same thing is in Ardour, but every time the skip happens, i get this in the jackd console:
```
JackPosixMutex::Unlock res = 1
```

Increasing the -p to 4096 seems to help, I got only one skip in the last five minutes. But still, isn't that too much compensation?

---

### Post by jeremija on 2011-06-27
I have managed to get a quite decent sound for playback by using this config:

jackd -dfirewire -r 44100 -p 512 -n 5 -O 8192

I guess that for low-latency recording I must use lower values, but for playback this is more than enough - I only got 8 xruns in the last 30 minutes.

Also, if anybody needs this - I have managed to link PulseAudio to Jack:> sudo apt-get install pulseaudio-module-jack pulseaudio-utils

and then execute this command when jackd is running:
> pactl load-module module-jack-sink
pactl load-module module-jack-source


---

### Post by trulan on 2011-06-29
That does seem like unusually large buffering, something must be conflicting.  Can you post the output of:
```
ffado-diag
```

---

### Post by jeremija on 2011-06-30
Here is the output:

```
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 2.6.38-8-generic
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
   g++ ............... g++ (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
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
   gcc ............... gcc (Ubuntu/Linaro 4.5.2-7ubuntu1) 4.5.2
   g++ ............... g++ (Ubuntu/Linaro 4.5.2-7ubuntu1) 4.5.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.8.3 for Qt version 4.7.2
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.6
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.33.1
     flags ........... -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include  -pthread -L/usr/lib/x86_64-linux-gnu -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.4.6
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -L/usr/lib/x86_64-linux-gnu -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
03:07.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80) (prog-if 10 [OHCI])
	Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 64 (8000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at e800 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

   CPU info:
Architecture:          x86_64
CPU op-mode(s):        64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 107
Stepping:              2
CPU MHz:               1000.000
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:           [25, 25], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    7: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pata_atiixp']
 IRQ   15: PID:  None, count:           [26, 26], Sched None (priority None), drivers: ['pata_atiixp']
 IRQ   16: PID:  None, count:     [11072, 11072], Sched None (priority None), drivers: ['ohci_hcd:usb3', 'ohci_hcd:usb4']
 IRQ   17: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1']
 IRQ   18: PID:  None, count:     [19284, 19284], Sched None (priority None), drivers: ['ohci_hcd:usb5', 'ohci_hcd:usb6', 'ohci_hcd:usb7', 'nvidia']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   22: PID:  None, count:       [9151, 9151], Sched None (priority None), drivers: ['ahci']
 IRQ   23: PID:  None, count:   [136747, 136747], Sched None (priority None), drivers: ['firewire_ohci']
 IRQ   42: PID:  None, count:     [11451, 11451], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This is still kind of experimental. If you encounter problems, please also check
with the old stack.

```

I have also had problems with random hangs in jack server after which I had to restart the server. The messages were:
```
JackFFADODriver::ffado_driver_wait - unhandled xrun
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, stopping...
```

After reading the recommendations yesterday I changed the priority in qjackctl from the default in 10 to 70 and it seems that that problem is gone, I just have to test it more to be sure.

However, I still get about 20 xruns in an hour with:
```
jackd -P70 -dfirewire -r44100 -p512 -n5 -O8192
```

---

### Post by jeremija on 2011-07-01
i have done the following tests: mprime (prime95 for linux), gtkperf and glxgears.

the first two do not yield an xrun, but everytime i close the glxgears window, an xrun happens. also, I downloaded the Unigine Heaven 2.5 benchmark tool for GPU and xruns happen all the time when I run this program, especially when I use the "3D GUI". 

Could it be that this is all due to my graphics card (nVidia 9800gt)?

---

### Post by Sylos on 2011-07-01
Hello there.

I wouldnt expect the xruns to be the fault of the graphics card. I would suggest it is more likely that the graphical tests are straining the CPU a little - hence the xruns.

Make sure that you have the nvidia proprietary drivers installed though..

---

### Post by jeremija on 2011-07-01
Yes the nVidia drivers are installed, although the **System->Administration->Hardware Drivers** lists them as activated, but not in use. I can, however run compiz and opengl applications with no problems. 

But how come the xruns don't appear when I use mprine to stress test the CPU, at least not on the latest settings that I'm using (jackd -P70 -dfirewire -r44100 -p512 -n5 -O8192) ?

---

### Post by trulan on 2011-07-01
Well, your ffado-diag output looks good, firewire is on its own irq (which is a very good thing).  Setting your JACK realtime priority was also a good thing to do.

Another system tweak that may be helpful for you is to set your cpu governor to 'performance', it looks like your cpu is clocked at 1000MHz and I'm guessing it can go a bit faster than that.  ;)  CPU scaling is often a culprit for xruns.

---

### Post by jeremija on 2011-07-01
yes, i have an amd athlon x2 6000+, which can go up to 3000 MHz on both cores. Could you please explain how to disable CPU scaling?

Will this command do it?
```
sudo killall powernowd
```

---

### Post by trulan on 2011-07-01
I'm not sure about killing powernowd; the easiest way in my opinion is to use the gnome panel cpu scaling applets, you'd need to use two, one set up to control each cpu.  There are other options though, a quick search yielded this thread which has some relevant info, especially post #8: [http://ubuntuforums.org/showthread.php?t=1027165](http://ubuntuforums.org/showthread.php?t=1027165)

However, depending on your Ubuntu version, it may automatically set your cpu to 'ondemand' one minute after boot-up, I'm not sure how to make the system boot up and stay on the 'performance' governor.  I just use the cpu scaling applets, then I can set the cpu speed to whatever I need.

---

### Post by jeremija on 2011-07-02
Thank you, the CPU scaling widget works as you say, but it doesn't seem to affect the xruns. For example, I always get an xrun when I close the glxgears app, no matter if I set the CPU scaling to performance or to the maximum value (3.10 GHz).

---

### Post by jeremija on 2011-07-05
UPDATE: after a few days of testing, it looks like that using the CPU scaling widget helps a lot with the occasional xruns. I had zero xruns all this time. Except in one case: when I run a GPU intensive application like glxgears or gta san andreas in wine (didn't have anything else to try :D) - I get this really often and need to restart jackd:

```
00:46:59.792 XRUN callback (1).
00:46:59.836 XRUN callback (1 skipped).
JackFFADODriver::ffado_driver_wait - unhandled xrun
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, stopping...
```

---

