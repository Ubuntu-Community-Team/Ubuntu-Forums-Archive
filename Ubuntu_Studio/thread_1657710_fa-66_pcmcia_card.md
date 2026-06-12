---
title: "fa-66 pcmcia card"
date: 2011-01-01
forum: Ubuntu Studio
---

### Post by Big_kev on 2011-01-01
Folks

Could someone guide me through installing and configuring the FA-66 device using a pcmcia card plugged into my laptop. I have gone through many of the posts in this and other forums but i do not have the knowledge to understand what files i should be adjusting and indeed some of the files that are mentioned i cannot find.

I am a complete beginner at Ubuntu as my previous experience lies with Microsoft. If someone could post the commands that i need to obtain the output that you guys require to help me i would be most obliged.

Look forward to your help.

Kevin

---

### Post by cchhrriiss121212 on 2011-01-01
It is a supported card, so I think this guide will cover everything:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Firewire audio is only supported through jack.

---

### Post by Big_kev on 2011-01-02
Thanks for the link.

I have tried many of these links and still i cannot get it to work. I am a member of Audio and Video, i have the correct settings for Realtime as UbuntuStudio 10.10 asked me to set this up during a clean install and i can verify this in the correct file.

When i do an lspci i can see my pcmcia card but i cannot see my FA-66. Is there somewhere i can check to see that the card is recognised. It was working when i was on windows but i don't have a windows machine to check at the moment.

Regards

---

### Post by AutoStatic on 2011-01-02
Install the **ffado-tools** package and post the output of the terminal command **ffado-diag** here.

Best,

Jeremy

---

### Post by Big_kev on 2011-01-02
Jeremy

As requested the output from ffado-diag

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
04:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46) (prog-if 10 [OHCI])
    Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at 48000000 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at 3000 [size=128]
    Region 2: Memory at 48000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 2.00GHz
stepping    : 8
cpu MHz        : 2000.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips    : 3989.69
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:            [23058], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:              [128], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:                [1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:                [2], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:            [16788], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:            [21098], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count:             [1213], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count:              [327], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb2', 'eth0', 'Intel ICH6']
 IRQ   17: PID:  None, count:            [11937], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'ndiswrapper']
 IRQ   18: PID:  None, count:                [0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   19: PID:  None, count:               [84], Sched None (priority None), drivers: ['uhci_hcd:usb5', 'yenta', 'firewire_ohci']
 IRQ   42: PID:  None, count:             [1311], Sched None (priority None), drivers: ['radeon']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.


hope this sheds some light.

---

### Post by Big_kev on 2011-01-02
Jeremy

I have just got it working. I had to unset then reset the enable raw1394 setting in the UbunutStutio controls.

Any advise on my next steps to recording music through my fa-66 would be appreciated.

Kevin

---

### Post by cchhrriiss121212 on 2011-01-02
> Any advise on my next steps to recording music through my fa-66 would be appreciated.
What would you like to record?

---

### Post by Big_kev on 2011-01-02
i would like to record a stereo keyboard output in the first instance. I have selected the jack control interface in audacity but do not seem to get any input.

i am also now getting issues with Jack. I can run Jack once and then if i try to run it again it fails. I have to go to the UbuntuStudio Control uncheck the raw1394 box quit the control and then go back into ubuntustudio control and check the raw1394 box and reboot before it will work again.

Is this normal behaviour?

Kevin

---

### Post by cchhrriiss121212 on 2011-01-02
> 
Is this normal behaviour?
No, this should not happen. In the guide I linked to earlier it states that:
> Most users (Maverick and newer) should be able to use the Juju stack, and **should not enable raw1394**.
Try following the "Driver confusion" paragraph and ask if you get stuck with something.

---

### Post by Big_kev on 2011-01-02
please find attached outputs from the driver confusion process.

kevin@ubuntu:~$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2011-01-02 15:53 /dev/raw1394

kevin@ubuntu:~$ groups
kevin adm dialout cdrom audio video plugdev netdev lpadmin admin sambashare

kevin@ubuntu:~$ lsmod | grep 'firewire\|1394'
raw1394                22462  0 
ieee1394               81069  1 raw1394
kevin@ubuntu:~$ grep 'firewire\|1394' /proc/interrupts
(no output was present)

I was thinking of using the juju stack over the legacy stack because it was newer. What are your thoughts on which stack to use.

Kevin

---

### Post by cchhrriiss121212 on 2011-01-02
I'd recommend using the JuJu stack as it what will be used in the future and seems much easier. See this post [here]("http://ubuntuforums.org/showpost.php?p=10253165&postcount=2"):
> On Maverick - Don't run Ubuntu Studio Controls, and don't start up your  computer with the device plugged in.  You may need to reconfigure jackd  to enable memlocking and rt scheduling, if you did not select allowing  these when jack was installed.  Other than that, it should just work.   Start the computer, plug in the firewire device, start Jack, and have  fun!

On Lucid - exactly the opposite.  Do run Ubuntu Studio Controls and  enable raw1394, do reboot your computer with the device plugged in.
In case you don't know, Ubuntu 10.10 is also called Maverick. I think the problem is that you are following the Lucid method.

---

### Post by Big_kev on 2011-01-03
Jeremy
 
Looks like this is more stable now. Thanks for the advice.
 
Back to the recording. I was planning on using the standard audacity programe that comes with 10.10. I can create a track within the program but i cannot seem to find any place to assign the track to an input from my device.
 
Is there any sort of manual etc that is available for download?
 
Kevin

---

### Post by Big_kev on 2011-01-03
found a good manual for Audacity here [http://audacity.sourceforge.net/manual-1.2/prefs.html#audioio](http://audacity.sourceforge.net/manual-1.2/prefs.html#audioio)
 
If you have any others that would be great.

---

### Post by AutoStatic on 2011-01-03
Hello Kevin,

I'd recommend using a multitrack recording application like Qtractor or Ardour. Audacity is a nice editor but it lacks direct JACK support and is not really good for recording multiple tracks.

Best,

Jeremy

---

