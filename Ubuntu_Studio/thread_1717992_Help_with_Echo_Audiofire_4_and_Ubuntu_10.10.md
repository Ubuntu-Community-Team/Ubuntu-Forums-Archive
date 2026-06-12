---
title: "Help with Echo Audiofire 4 and Ubuntu 10.10"
date: 2011-03-30
forum: Ubuntu Studio
---

### Post by KR0GER on 2011-03-30
Hey guys.  My comp crashed a couple of weeks ago and I decided I'd try  Ubuntu. I've never used linux before so please bear with me.  I loaded up a fresh copy and it is working fine.  I can do  almost everything I want to, but I can't get my audio interface to work,  and I'd really like to work on some music.  I have an Echo Audiofire 4.   The ffado website says that it is fully supported.  I switched to the  legacy firewire stack (opposed to the new juju stack).  I changed the  privileges for my user profile so I'm allowed to use both audio and  video devices, and jack still crashes every time I try it.  

I followed the directions here: _[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)_

One thing that I think is kind of weird is that it doesn't seem like the settings are static.  For instance, when i restart and enter,
 ls -al /dev/raw1394
I get "ls: cannot access /dev/raw1394: No such file or directory"

but after I follow the steps in the guide, unload the juju stack, load the legacy stack, black list the juju stack so the legacy should load at boot, and rebuild the initramfs,


when i enter:  ls -al /dev/raw1394
I get "crw------- 1 root root 171, 0 2011-03-21 16:47 /dev/raw1394"

The guide says I should get root video, and I really don't know what to do about that.

when i try to load jack I get a pop up that says "could not load JACK.  sorry"
and this is the error message:

deactivated.
16:50:53.637 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:50:53.754 ALSA connection graph change.
16:50:53.961 ALSA connection change.
16:50:53.962 ALSA connection graph change.
16:51:14.615 Startup script...
16:51:14.615 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:51:15.017 Startup script terminated with exit status=32512.
16:51:15.017 JACK is starting...
16:51:15.017 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n2
16:51:15.059 Could not start JACK. Sorry.
16:51:57.032 JACK was stopped successfully.
16:51:57.033 Post-shutdown script...
16:51:57.033 killall jackd
jackd: no process found
16:51:57.451 Post-shutdown script terminated with exit status=256.

Something else I'm unclear about is the issue of switching kernels.  While trying to get this to work I came across different posts/articles suggesting a switch to a low latency kernel if a user was planning on working with audio.  Is this necessary?  Exactly what Kernel would you recommend? (I'm pretty sure I saw many different versions).  How should I go about this?

Any help is appreciated.  I really want to make some music, and be able to practice through my computer again.  Thanks in advance.

KR0GER

---

### Post by KR0GER on 2011-03-31
so I've been trying to get this running.  I followed the instructions here: [http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu)

when it told me to do the raw1394 thing from the ubuntu studio controls, I just installed the controls from the software center

It still isn't working, and I don't know how to undo what I did.  God damn this is frustrating.

Can I not get this working under regular ubuntu?  Do I need to have studio installed?  

Please help I'm begging you guys.

---

### Post by Pablo_F on 2011-03-31
Hi, you don't strictly need ubuntustudio. ubuntustudio is ubuntu.

At this point you need read and write access to /dev/raw1394 but:
> 
when i enter: ls -al /dev/raw1394
I get "crw------- 1 root root 171, 0 2011-03-21 16:47 /dev/raw1394"

which means that the user is root and the group is root. And only the user has r/w access.

In a terminal:

sudo chown root.audio /dev/raw1394

(user: root; group: audio).

On the other hand, you (user kroger or whatever you chose) need to be a member of the audio group. Check with the *groups* command.

Now, if you type ls -la /dev/raw1394 again you should see:

crw------- 1 root audio

But you need:

crw-rw---- 1 root audio

(the second rw means that the members of the group (audio group in this case) have read & write access to /dev/raw1394).

You can achieve it with this command:

sudo chmod g+rw /dev/raw1394

Cheers, Pablo

EDIT: The last command does the trick for the current session, but you need to write a udev rule, so better use ubuntustudio-controls to enable /dev/raw1394 access consistently. Reboot and check.

---

### Post by AutoStatic on 2011-03-31
Hello KR0GER,

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) **Step 1**
After having enabled raw1394 and related permissions with Ubuntu Studio Controls the */dev/raw1394* device node should get 'audio' as the group ID and these permissions should persists across reboots (contrary to Pablo_F's solution). Make sure you're a member of the 'audio' group and then you should be able to use the device, assuming you're still using the legacy stack.
Also it's better to use a Periods/Buffer setting of 3 instead of 2 with FireWire devices.
And you don't need Ubuntu Studio to get your card running.

Best,

Jeremy

---

### Post by Pablo_F on 2011-03-31
> After having enabled raw1394 and related permissions with Ubuntu Studio Controls the /dev/raw1394 device node should get 'audio' as the group ID and these permissions should persists across reboots (contrary to Pablo_F's solution)

You are right, sorry :). See my EDIT.

---

### Post by KR0GER on 2011-03-31
Thank you guys very much for the help.  It's still not working for me.  I probably screwed something up along the way.  Could one of you write a step by step guide on how to set this up on a fresh install?  I think I'll reinstall just to get everything back to normal and then proceed.  I'm sure the guide would be helpful to a lot of linux/ubuntu noobs such as myself.  I haven't been able to find a good guide, and I think it would save a lot of people a lot of trouble.

---

### Post by KR0GER on 2011-03-31
Alright!  I got a fresh install now.  Hopefully there won't be any surprises.

---

### Post by trulan on 2011-03-31
Hi KROGER,

Well, my attempt at a guide was this:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Which you've already been using, albeit without success.  The problem is, there has been at least one significant configuration change every Ubuntu release for the last several years it seems.  And in an attempt to keep the guide relevant while retaining information for older releases, it got kind of confusing - especially with the change from the old firewire driver stack to the new one.  Maybe I'll redo it for the Natty 11.04 release and split it into two seperate guides, one specifically for Lucid (as that's LTS, some people will be using that for a while) and the other one for Natty which will hopefully apply to Maverick.

Any info I could add to the guide, or any points you find particularly confusing, let me know.  I'm open to suggestions.

Good luck on your re-installation!

---

### Post by KR0GER on 2011-04-07
So I had no clue what I was doing before.  I'm not surprised things didn't work.  I don't think I even had ffado installed correctly.  Anyway.  I'm trying to build it now and am getting this error:

scons: Reading SConscript files ...

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/theo/libffado-2.0.1/SConstruct", line 38, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/theo/libffado-2.0.1/SConstruct", line 43, in <module>

scons: warning: The PathOption() function is deprecated; use the PathVariable() function instead.
File "/home/theo/libffado-2.0.1/SConstruct", line 45, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/home/theo/libffado-2.0.1/SConstruct", line 65, in <module>
Checking for a working C-compiler yes
Checking for a working C++-compiler yes
Checking for pkg-config (at least version 0.0.0)... yes
Checking for C header file expat.h... no
Checking for XML_ExpatVersion() in C library expat... no
/home/theo/libffado-2.0.1/admin/pkgconfig.py:80: DeprecationWarning: os.popen2 is deprecated.  Use the subprocess module.
  out = os.popen2( "pkg-config --cflags --libs %s" % name )[1]
Checking for libraw1394 (1.3.0 or higher)...     yes
Checking for dbus-1 (1.0 or higher)...     yes
Checking for libxml++-2.6 (2.13.0 or higher)...     yes
Checking for libiec61883 (1.1.0 or higher)...     yes

(At least) One of the dependencies is missing. I can't go on without it, please
install the needed packages for each of the lines saying "no".
(Remember to also install the *-devel packages!)

And remember to remove the cache with "rm -Rf .sconsign.dblite cache" so the
results above get rechecked.



I went through the read me and installed all of the dependencies and the dev packages.  

What do I need to do?

---

### Post by AutoStatic on 2011-04-07
Install libffado2 from Synaptic. You don't need to compile FFADO yourself. Did you install all the necessary FFADO packages? What does **dpkg --list | grep ffado** return in a terminal?

Best,

Jeremy

---

### Post by KR0GER on 2011-04-07
it didn't return anything

edit:

I installed the libffado package from synaptic, along with jack1 and now it says this.

ii  ffado-dbus-server                     2.0.1+svn1856-1ubuntu1                            FFADO D-Bus server
ii  ffado-mixer-qt4                       2.0.1+svn1856-1ubuntu1                            FFADO D-Bus mixer applets (QT4)
ii  libffado2                             2.0.1+svn1856-1ubuntu1                            FFADO API

When I try to run jack it fails

when i try to run ffado mixer it says
"somehow the connection to the dbus-service of ffado couldn't be established"

---

### Post by AutoStatic on 2011-04-07
Could you also install the **ffado-tools** package and run **ffado-diag** in a terminal and post the output here? Thanks!

Best,

Jeremy

---

### Post by KR0GER on 2011-04-07
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-28-generic
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
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
   jackd ............. jackd version 0.118.0 tmpdir /dev/shm protocol 24
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
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
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
02:0b.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. P5W DH Deluxe Motherboard [1043:815b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at fdff4000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

04:01.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI])
    Subsystem: Ads Technologies Inc Device [1421:0315]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e3fff000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at e3ff8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping    : 2
cpu MHz        : 2009.125
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 4018.25
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping    : 2
cpu MHz        : 2009.125
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 4018.31
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:           [43, 43], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    6: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['floppy']
 IRQ    7: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['parport0']
 IRQ    8: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:             [9, 9], Sched None (priority None), drivers: ['pata_amd']
 IRQ   15: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['pata_amd']
 IRQ   16: PID:  None, count:   [122097, 122097], Sched None (priority None), drivers: ['firewire_ohci', 'eth2', 'ctxfi', 'nvidia']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['firewire_ohci']
 IRQ   20: PID:  None, count:           [14, 14], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'hda_intel']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['sata_nv']
 IRQ   22: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['sata_nv']
 IRQ   23: PID:  None, count:             [4, 4], Sched None (priority None), drivers: ['ohci_hcd:usb2', 'sata_nv']
 IRQ   46: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   47: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['eth1']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.


************************************************************************


I forgot to mention that I have the new stack loaded, but I thought it said on the ffado website that 2.0.1 now supports the new stack.

I don't know if it makes a difference, but I had my audio interface off when I ran this.

It was on when I was trying to run jack and the mixer before.

---

### Post by AutoStatic on 2011-04-07
Thanks! The new stack should work fine on Maverick despite the warning at the end of the ffado-diag output.

```
IRQ 16: PID: None, count: [122097, 122097], Sched None (priority None), drivers: ['firewire_ohci', 'eth2', 'ctxfi', 'nvidia']
```Ouch, crowded IRQ :( You will need the **rtirq-init** package and add 'firewire_ohci' to */etc/default/rtirq* as described in Step 5 of the [FireWire Help page]("https://help.ubuntu.com/community/FireWire"). So instead of 'ohci1394' you add 'firewire_ohci'. You will need a real-time kernel for this, not sure where you can get one for Maverick though (one of the reasons I don't use Maverick myself).

Best,

Jeremy

---

### Post by KR0GER on 2011-04-07
Thank you so much for the help.  I'm going to screw around with this some more.  I'll let you know how it turns out.

---

### Post by fedexnman on 2011-04-07
ive got a echo audio fire 4 works great in 10.04 with the rt - kernel . just thought id chime in !

---

### Post by KR0GER on 2011-04-08
I said F^*$ it and installed lucid.  So once again I'm really new to this.  What is the difference between the low latency kernel and the real time kernel?  Which one do I want to use?  How do I go about this?  Before I installed lucid I tried using the low latency kernel from some ppa with maverick, and when I tried to boot up I only got a command line, no gui at all., and I needs me a gui!

---

### Post by KR0GER on 2011-04-08
just found this:
    
I suggest following these simple rules:

*) if you don't need a low latency system use -generic kernel
*) If you need a low latency system please use -preempt kernel as a
first choice (this reduces latency but doesn't sacrifice power saving
features) from the Ubuntu archives directly from Ubuntu Kernel Team
*) If you have an i386 system or -preempt isn't enough for your needs
you should try the -lowlatency kernel present in my above-mentioned
PPA.
*) If -lowlatency also isn't enough you should try the -realtime
kernel (like -lowlatency it is available through my PPA)

Which would you guys recommend?


edit:  in windows i would use my audio interface to practice and record.  I really liked playing a video tutorial in vlc while running reaper>guitar rig(vst) at the same time, so I could hear the audio from the video and my guitar with effects at the same time through a pair of headphones.  I read that the rt kernel will put 95% of the processing to the main task and everything else will be sluggish.  Could I still play a video?  What would be the best way to go about this?

---

### Post by AutoStatic on 2011-04-08
You need rtirq-init for your FireWire card to run. So you need a real-time kernel. Get the one from Tango Studios, works best: [http://tangostudio.tuxfamily.org/en/kernel-rt](http://tangostudio.tuxfamily.org/en/kernel-rt)
Don't know where you read that info about real-time kernels but it probably applies to hard real-time [xenomai]("http://www.xenomai.org/index.php/Main_Page") kernels. These kernels are something different than kernels patched with the [real-time patchset]("https://rt.wiki.kernel.org/").

Best,

Jeremy

---

### Post by Pablo_F on 2011-04-08
> Could I still play a video? What would be the best way to go about this?

I chime in :D

You can play a video yes, the good things is that you won't get xruns (buffer overruns / underruns) at relatively low latencies.

As the firewire controller is sharing IRQ number with another hardware devices (double-check it in ffado-diag or directly via "cat /proc/interrupts" command) you need a modified kernel with the PREEMPT_RT patch (normally called "rt kernels"), because generic or just low-latency kernels can't separate IRQ handlers. (In the near future, beginning with 2.6.39 afaik, stock kernels will be able to do it but not just yet). 

Of course, you need to raise the priority of the firewire controller. The rtirq-init script does this automatically when you reboot the computer once that you have tweaked its configuration file. As noted, rtirq-init only works with rt kernels.

So, do as Auto suggests and follow instructions in the tango site to install their rt kernel, then configure rtirq-init.

Cheers, Pablo

---

### Post by KR0GER on 2011-04-08
I can't believe it's still not working.  What the hell?  I reinstalled the OS, installed the -rt kernel, installed libffado, the ffado mixer, ffado dbus, qjacktl, rtirq-init and ubuntu studio control packages.  I edited my user privileges to include audio and video devices.  I used the studio controls to enable raw1394 access. I edited  /etc/security/limits.conf with the values jack gave me, and it's still not running.  I don't mean to be an a-hole but in windows I double clicked one frickin' icon!  And on top of all of that after installing the -rt kernel my wireless card doesn't work.

---

### Post by trulan on 2011-04-08
If I read correctly, firewire_ohci was listed on two IRQ's.  Do you have two firewire controllers in your machine?
> IRQ   16: PID:  None, count:   [122097, 122097], Sched None (priority  None), drivers: ['firewire_ohci', 'eth2', 'ctxfi', 'nvidia']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['firewire_ohci']
I've never run into a situation like this before, so I'm not sure exactly how you would go about doing this, but could you disable the firewire controller on IRQ 16 and use the one on IRQ 19?  Just an idea...

---

### Post by AutoStatic on 2011-04-08
Overlooked that :( You have two TI controllers on your system, try disabling one of them, preferably the one with IRQ 16 of course :)
Out of personal experience I know that FFADO doesn't like multiple FireWire controllers. It should be feasible with some udev rules maybe but disabling one controller is quicker.

Best,

Jeremy

---

### Post by EinZ on 2011-04-17
Hello!
This Thread is really useful, although my audiofire4 is still not working properly...
Pretty much everything is okay, i switched to the old stack, so ffado doesnt give me trouble,
but audiojack still doesnt work properly it makes a click sound and after a short while it tells me that it cant connect to the server as a client.
I'll reread this thread again, I probably have overseen soemthing, but I already did the tutorials mentioned here.
cheers 
E

---

### Post by AutoStatic on 2011-04-17
> **AutoStatic said:**
> It should be feasible with some udev rules maybe but disabling one controller is quicker.Actually it's much simpler, hw:0 is your first FireWire controller, hw:1 your second etc.

Best,

Jeremy

---

### Post by oNNogitaar on 2011-06-27
mine (af12) is still not working either. I like doing things myself but at the moment am willing to pay someone to set it all up for me...

---

