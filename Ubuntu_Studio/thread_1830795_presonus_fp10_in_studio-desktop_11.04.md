---
title: "presonus fp10 in studio-desktop 11.04"
date: 2011-08-22
forum: Ubuntu Studio
---

### Post by mccuisinart on 2011-08-22
EDIT- My core specs:

Intel Core i5 2405S
BIOSTAR TP67XE motherboard
G.SKILL F3-10666CL8D-4GBECO DR1333 Memory x4 7.9GB

I just built a new pc rig but I haven't bought windows for it. I'm working out of ubuntu studio natty/11.04 right now and I like it a lot. I've been fiddling around with this OS for a few days now and I've found that my [presonus fp10 interface is supported (?)]("http://ffado.org/?q=node/317") with the ffado drivers, which is neat because I would love not having to buy an OS if I can get this thing up and running with this OS, but I could use some help.

I originally installed ubuntu 11.04 as a temporary solution, but then I learned about studio/jack/ffado, and installed the packages using sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-desktop
    During installation of the plugins, I recall seeing a prompt for installing a new realtime kernel. I don't know if that part was successful or not. My system monitor says my kernel is linux 2.6.38-11-generic-pae

I'm having trouble getting my fp10 device to sync with my system. I've learned a little bit about jack and its gui controller qjackctl. From what I've gathered from reading about other people's experiences, I am supposed to use jack to sync my fp10, right? Qjackctl displays this on start-up:

```
08:29:47.186 Patchbay deactivated.
08:29:47.187 Statistics reset.
08:29:47.191 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
08:29:47.196 ALSA connection graph change.
```The driver is set to firewire in setup. How do I get j.a.c.k. started? How can I know if my kernel is a realtime kernel, and ultimately how can I get my fp10 synched to my system? Should I do a fresh install of jack/jackd ?

edit - I can start JACK when the ALSA driver is selected in Setup, and RT blinks. This means realtime is working correct?

---

### Post by fedexnman on 2011-08-22
im using ubuntustudio 10.04 with a rt kernel and an echo audiofire4 firewire interface at the moment , but ill try to help . ubuntustudio  11.04 does'nt have a rt kernel, when installing 11.04 it asks you about rt scheduling , but its not the rt kernel .  kernel versions 2.39 and newer can use rt scheduling without a rt kernel ,  You can still get your firewire interface up and running though,  just google ubuntustudio preparation   and you ll see how to get firewire working and learn about jackd and qjackqrtl .  its a little bit of a learning curve and ive had my moments where i went back to windows , because of xruns .  im hoping some more experienced/smarter users will answer this thread and help you out soon,  but 1st  google ubuntustudio preparation and go thru those pages im sure youll have some success soon  .

---

### Post by AnWe on 2011-08-22
I think you may have permission/access problems, check here for enabling access to the firewire node:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by mccuisinart on 2011-08-22
> **AnWe said:**
> I think you may have permission/access problems, check here for enabling access to the firewire node:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Thanks! This page looks very helpful. I will follow the steps when I get home and report any issues or successes.

---

### Post by fedexnman on 2011-08-22
Tried out ubuntu/studio 11.04 and abogani lowlatency  kernel ppa . what a total disaster again !!
   YOUR BEST OPTIONS ARE TOO  try A/V linux 5.0 or  Ubuntustudio 10.04 LTS and add the rt kernel and software packages  PPA s over at the tangostudio website  or you could  also try falktx   kxstudio ppa added to 10.04  lucid as well .

---

### Post by mccuisinart on 2011-08-23
Mmkay. I'll avoid some hassle. How do I "downgrade" without doing a clean install?

---

### Post by jejeman on 2011-08-24
You can't.

---

### Post by fedexnman on 2011-08-24
How bigs your hardrive ?  you could keep 11.04, and dualboot it with avlinux5.0 or 10.04.   Just trying to save you some fustration . Avlinux 5.0 works pretty much out of the box with firewire its unbelievable.:popcorn:

---

### Post by mccuisinart on 2011-08-27
Spent 3 hours downloading the studio10.04 ISO, burned it, and then then checked the disc for defects only to have it crap out on me on the final percentage-of-progress made point. AV Linux looks even scarier to install. The support forums are full of people with problems.

---

### Post by fedexnman on 2011-08-27
1. I would  download ( plain old ) ubuntu 10.04 Lts release from the ubuntu site and install
 2.  add the ppa 's from the tango studio site .  one for rt  kernel and   the one for apps . 
 3.  go to synaptic package manager and add all the _ ubuntu studio stuff too your system + _rt kernel an rt headers .
 Now on too  av linux 5.0 .  the  installer isnt as straight forward as ubuntu , because you have to do the g- parted stuff yourself and decide where your home, grub , and swap go , but it is a  good linux learning experience for anyone and is not hard to do once you learn it . the instuction manual for av linux 5.0  on the avlinux live dvd helps out with this too , a little.  I've learned alot over the years and i dual-boot with windows7  , too .  Ive had to learn how to re-install the bootloader with windows7 too .   I dont know how new you are to ubuntu or linux , but if you follow the steps 1-3 and google ubuntu studio prep and follow those steps for firewire , jack , etc youll be up and running.

---

### Post by mccuisinart on 2011-08-28
Thanks fedexnman you are a true friend. I am completely new to ubuntu/linux altogether. School just started and this is going to be hell to take care of in the time I want to get it done, so it's nice to have a guide.

---

### Post by mccuisinart on 2011-08-28
downloaded/installed Lucid 10.04, and followed the directions found in  the ubuntustudioprep and firewire ubuntu docs. Still no success but Jack  doesn't have that cannot connect to server socket err anymore. Instead this is what happens in jack control, (basically the same thing whether the interface is set to hw1, hw0 or just default. here it is set to default)

[

p, li { white-space: pre-wrap; } [COLOR=#999999]06:57:56.729 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]06:57:56.733 Statistics reset.[/COLOR]
 [COLOR=#66cc99]06:57:56.769 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]06:57:56.967 ALSA connection change.[/COLOR]
 [COLOR=#999999]06:58:19.602 Startup script...[/COLOR]
 [COLOR=#990099]06:58:19.603 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]06:58:20.004 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]06:58:20.004 JACK is starting...[/COLOR]
 [COLOR=#990099]06:58:20.004 /usr/bin/jackd -dfirewire -r44100 -p128 -n3[/COLOR]
 [COLOR=#999999]06:58:20.006 JACK was started with PID=9850.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    6180513
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 libffado 2.999.0- built Jan 15 2011 16:38:42
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 [COLOR=#999999]06:58:20.284 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]06:58:20.284 Post-shutdown script...[/COLOR]
 [COLOR=#990099]06:58:20.284 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]06:58:20.689 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]06:58:22.087 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

]

Where to go from here? the firewire ERR line is disappointing. Is my fp10 going to be able to sync, ever?

EDIT - ffado-test ListDevices returns this:

```
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0030670000b47e13  0x00003067  0x00000000   Linux - ohci1394  -
no message buffer overruns
```Node id 0 is supposed to *look like* this according to another thread...
```
0       0x000a9200c8100982  0x00000A92  0x00010066   Presonus  - PreSonus FP10
```ffado-test is supposed to see my device. It's on, plugged into the correct firewire port, but absolutely no detection. :(

I'm not sure what firewire 'stack' I'm using or what that really means, but apparently it's important and this should mean something to me, mmhmm?

```
xxxx@xxxx:~$ lsmod | grep 'firewire\|1394'
raw1394                22271  0 
ohci1394               27238  0 
ieee1394               81213  2 raw1394,ohci1394
```

---

### Post by jejeman on 2011-08-28
Ubuntu 10.04 uses old stack. Did you set permissions for firewire?
```
ls -l /dev/raw1394
```

---

### Post by fedexnman on 2011-08-28
1 . have you added yourself to the audio group ? and checked all the blocks off for audio devices camera , tape machines  etc. etc. ?  i usually just check all the blocks .
2.   do have the rt kernel and rt headers downloaded and running,    make sure you  x the rt block on qjackctrl . 
3.   did you launch ubuntu studio controls and x the firewire block (raw1394) , before starting jack  ?  

we can get this working !  I know its frustrating , but  you'll  get it .

---

### Post by fedexnman on 2011-08-28
Now you got your rt-kernel  , rt image and headers download , reboot into the rt kernel  on the grub2 screen, upon reboot of your computer .
 1.  1st  launch ubuntustudiocontrols do this   just click  x  enable  raw1394 block ,  i dont think you need to check the other  2 blocks any more  this page is kinda old .  
[https://help.ubuntu.com/community/UbuntuStudioControls](https://help.ubuntu.com/community/UbuntuStudioControls)
 2.  2nd  follow the older ubuntu column ,  dont do step 5 yet , we'll worry bout that later .  a. in qjackcrt  put frame/periods put 64 instead  of 128  and  b.  in timeout(msec) put 2000 instead of 500   .      [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by trulan on 2011-08-30
@mccuisinart:  For whatever reason, your computer is completely failing to see your FP10.  The firewire driver stack is properly loaded, and ffado-test ListDevices shows your controller card but no devices.  So it's not a permissions problem (at least not yet), a kernel problem, a realtime problem, or anything like that; it looks to me like either 1. a connection problem (as in, a bad firewire cable or no power to the FP10) or, 2. a problem with the firewire host controller card in your computer.  So, here's a few things to check:

1. Is your FP10 plugged into AC power, the switch turned on, and the light red?  FP10's cannot be powered from the firewire cable, they need their own power supply.
2. Is your firewire cable plugged in properly at both ends?  (Try another firewire cable if you have one.)
3. Finally, can you post the output of:
```
ffado-diag
```

ps. Don't be scared by all the "people with problems" on this forum, the AVLinux forum, or anywhere else - forums are intended for people with problems to ask for (and hopefully get) help.  Saying "It works! Yay!" takes up a lot less space than "I have a problem with..."

---

### Post by fedexnman on 2011-08-30
Im gonna bet thats it ! !  You got plug the fp10  into the ac electrical outlet as well as the firewire port .

---

### Post by mccuisinart on 2011-09-02
> **trulan said:**
> @mccuisinart: For whatever reason, your computer is completely failing to see your FP10. The firewire driver stack is properly loaded, and ffado-test ListDevices shows your controller card but no devices. So it's not a permissions problem (at least not yet), a kernel problem, a realtime problem, or anything like that; it looks to me like either 1. a connection problem (as in, a bad firewire cable or no power to the FP10) or, 2. a problem with the firewire host controller card in your computer. So, here's a few things to check:
 
1. Is your FP10 plugged into AC power, the switch turned on, and the light red? FP10's cannot be powered from the firewire cable, they need their own power supply.
2. Is your firewire cable plugged in properly at both ends? (Try another firewire cable if you have one.)
3. Finally, can you post the output of:
```
ffado-diag
```
 
ps. Don't be scared by all the "people with problems" on this forum, the AVLinux forum, or anywhere else - forums are intended for people with problems to ask for (and hopefully get) help. Saying "It works! Yay!" takes up a lot less space than "I have a problem with..."
I'll bump this now and post the ffado-diag later. I'm posting from another computer, because my wireless networking USB controller won't work in 10.04, like it did in 11.04, where it was just plug and play. Kind of frustrating.
 
The fp10 has power. The light is blue upon being turned on, turns red after a few seconds, which I know is normal, and is meaning that it isn't syncing. It is however, plugged into a surge protector (a nice one), and not directly into the wall. That shouldn't make a difference, right? I can't test the firewire cable with another device or computer because I have no other device, and no other computer with IEEE1394 ports. Thanks all for helping me out. I'll post another update this weekend because school is boggin' me down.
 
More information: This is my motherboard, it has the one and only firewire port that I can and am plugging into. Do you think it is this thing that is giving me trouble? Would a seperate firewire controller do my situation wonders?
[http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=510](http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=510)

---

### Post by sgx on 2011-09-02
The difference between having power, and having enough power, is critical, especially with external audio hardware, designed to use
more power than a typical motherboard connector supplies. If you can,
try the device in a $Mac$ perhaps from the school music department. Motherboard quality varies wildly.
Cheers

---

### Post by mccuisinart on 2011-09-04
What is grub2? How do I use it to boot into the realtime kernel?

---

### Post by fedexnman on 2011-09-04
Still hanging in there I see !!    run this in a terminal    sudo update-grub     .  Reboot your computer , while rebooting the computer hold the shift key down . the grub menu should appear , here you can pick your kernel to boot into . I believe you got the rt kernel installed , but have not booted it yet . Pick the one with rt at the end of some numbers  it is your real-time kernel for more info on grub2   check this page out .    [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by mccuisinart on 2011-09-05
ffado-diag

with fp10 turned off...
 

```
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers

=== CHECK ===
Base system...
kernel version............ 2.6.32-33-generic-pae
FIXME: implement test for RT kernel
RT patched............... False
old 1394 stack present.... True
old 1394 stack loaded..... True
old 1394 stack active..... True
new 1394 stack present.... True
new 1394 stack loaded..... False
new 1394 stack active..... False
/dev/raw1394 node present. True
/dev/raw1394 permissions.. True
Prerequisites (dynamic at run-time)...
gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
g++ ............... sh: g++: not found
PyQt4 (by pyuic4) . sh: pyuic4: not found
jackd ............. jackd version 0.118.0 tmpdir /dev/shm protocol 24
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
gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
g++ ............... g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
jackd ............. sh: jackd: not found
path ............ 
flags ........... Package jack was not found in the pkg-config search path.
libraw1394 ........ 2.0.5
flags ........... -lraw1394 
libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
flags ........... Package libavc1394 was not found in the pkg-config search path.
libiec61883 ....... 1.2.0
flags ........... -liec61883 -lraw1394 
libxml++-2.6 ...... 2.30.0
flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0 
dbus-1 ............ 1.2.16
flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -L/lib -ldbus-1 -lpthread -lrt 
Hardware...
Host controllers:
06:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403] (rev 01) (prog-if 10)
Subsystem: Biostar Microtech Int'l Corp Device [1565:4203]
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 19
Region 0: Memory at fb100000 (64-bit, non-prefetchable) [size=2K]
Region 2: I/O ports at c000 [size=256]
Capabilities: <access denied>
Kernel driver in use: ohci1394
Kernel modules: firewire-ohci, ohci1394
CPU info:
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 2501.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 0
cpu cores : 4
apicid : 0
initial apicid : 0
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4997.71
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 1600.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 1
cpu cores : 4
apicid : 2
initial apicid : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4998.24
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
processor : 2
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 1600.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 2
cpu cores : 4
apicid : 4
initial apicid : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4998.25
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
processor : 3
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 1600.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 3
cpu cores : 4
apicid : 6
initial apicid : 6
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4998.25
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
Configuration...
IRQ information
Hardware Interrupts:
--------------------
IRQ 0: PID: None, count: [69, 69, 69, 69], Sched None (priority None), drivers: ['timer']
IRQ 1: PID: None, count: [2, 2, 2, 2], Sched None (priority None), drivers: ['i8042']
IRQ 4: PID: None, count: [2, 2, 2, 2], Sched None (priority None), drivers: ['']
IRQ 8: PID: None, count: [1, 1, 1, 1], Sched None (priority None), drivers: ['rtc0']
IRQ 9: PID: None, count: [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
IRQ 12: PID: None, count: [4, 4, 4, 4], Sched None (priority None), drivers: ['i8042']
IRQ 14: PID: None, count: [10314, 10314, 10314, 10314], Sched None (priority None), drivers: ['ata_piix']
IRQ 15: PID: None, count: [0, 0, 0, 0], Sched None (priority None), drivers: ['ata_piix']
IRQ 16: PID: None, count: [435, 435, 435, 435], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'nouveau', 'HDA Intel']
IRQ 17: PID: None, count: [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd:usb3']
IRQ 19: PID: None, count: [1068, 1068, 1068, 1068], Sched None (priority None), drivers: ['ata_piix', 'ohci1394']
IRQ 22: PID: None, count: [605, 605, 605, 605], Sched None (priority None), drivers: ['HDA Intel']
IRQ 23: PID: None, count: [58, 58, 58, 58], Sched None (priority None), drivers: ['ehci_hcd:usb2']
IRQ 29: PID: None, count: [404, 404, 404, 404], Sched None (priority None), drivers: ['eth0']
Software Interrupts:
--------------------

=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

```

...with fp10 turned on, (appears to be no different):

```
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers

=== CHECK ===
Base system...
kernel version............ 2.6.32-33-generic-pae
FIXME: implement test for RT kernel
RT patched............... False
old 1394 stack present.... True
old 1394 stack loaded..... True
old 1394 stack active..... True
new 1394 stack present.... True
new 1394 stack loaded..... False
new 1394 stack active..... False
/dev/raw1394 node present. True
/dev/raw1394 permissions.. True
Prerequisites (dynamic at run-time)...
gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
g++ ............... sh: g++: not found
PyQt4 (by pyuic4) . sh: pyuic4: not found
jackd ............. jackd version 0.118.0 tmpdir /dev/shm protocol 24
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
gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
g++ ............... g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
jackd ............. sh: jackd: not found
path ............ 
flags ........... Package jack was not found in the pkg-config search path.
libraw1394 ........ 2.0.5
flags ........... -lraw1394 
libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
flags ........... Package libavc1394 was not found in the pkg-config search path.
libiec61883 ....... 1.2.0
flags ........... -liec61883 -lraw1394 
libxml++-2.6 ...... 2.30.0
flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0 
dbus-1 ............ 1.2.16
flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -L/lib -ldbus-1 -lpthread -lrt 
Hardware...
Host controllers:
06:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403] (rev 01) (prog-if 10)
Subsystem: Biostar Microtech Int'l Corp Device [1565:4203]
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 19
Region 0: Memory at fb100000 (64-bit, non-prefetchable) [size=2K]
Region 2: I/O ports at c000 [size=256]
Capabilities: <access denied>
Kernel driver in use: ohci1394
Kernel modules: firewire-ohci, ohci1394
CPU info:
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 2501.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 0
cpu cores : 4
apicid : 0
initial apicid : 0
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4997.71
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 1600.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 1
cpu cores : 4
apicid : 2
initial apicid : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4998.24
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
processor : 2
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 1600.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 2
cpu cores : 4
apicid : 4
initial apicid : 4
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4998.25
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
processor : 3
vendor_id : GenuineIntel
cpu family : 6
model : 42
model name : Intel(R) Core(TM) i5-2405S CPU @ 2.50GHz
stepping : 7
cpu MHz : 1600.000
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 3
cpu cores : 4
apicid : 6
initial apicid : 6
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips : 4998.25
clflush size : 64
cache_alignment : 64
address sizes : 36 bits physical, 48 bits virtual
power management:
Configuration...
IRQ information
Hardware Interrupts:
--------------------
IRQ 0: PID: None, count: [73, 73, 73, 73], Sched None (priority None), drivers: ['timer']
IRQ 1: PID: None, count: [2, 2, 2, 2], Sched None (priority None), drivers: ['i8042']
IRQ 4: PID: None, count: [2, 2, 2, 2], Sched None (priority None), drivers: ['']
IRQ 8: PID: None, count: [1, 1, 1, 1], Sched None (priority None), drivers: ['rtc0']
IRQ 9: PID: None, count: [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
IRQ 12: PID: None, count: [4, 4, 4, 4], Sched None (priority None), drivers: ['i8042']
IRQ 14: PID: None, count: [11580, 11580, 11580, 11580], Sched None (priority None), drivers: ['ata_piix']
IRQ 15: PID: None, count: [0, 0, 0, 0], Sched None (priority None), drivers: ['ata_piix']
IRQ 16: PID: None, count: [435, 435, 435, 435], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'nouveau', 'HDA Intel']
IRQ 17: PID: None, count: [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd:usb3']
IRQ 19: PID: None, count: [1069, 1069, 1069, 1069], Sched None (priority None), drivers: ['ata_piix', 'ohci1394']
IRQ 22: PID: None, count: [617, 617, 617, 617], Sched None (priority None), drivers: ['HDA Intel']
IRQ 23: PID: None, count: [58, 58, 58, 58], Sched None (priority None), drivers: ['ehci_hcd:usb2']
IRQ 29: PID: None, count: [412, 412, 412, 412], Sched None (priority None), drivers: ['eth0']
Software Interrupts:
--------------------

=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.
```

---

### Post by trulan on 2011-09-06
Is this still the computer you built?  The firewire controller is sharing an IRQ with a hard driver controller:
> IRQ 19: PID: None, count: [1068, 1068, 1068, 1068], Sched None (priority None), drivers: ['ata_piix', 'ohci1394']
...and that is certainly asking for trouble.  I can't say for sure if that's the problem, but if there's any way you can get the firewire controller on its own irq, that would greatly increase your chances of getting this working, in my opinion.

---

### Post by mikeh789 on 2011-09-06
i use a presonus firepod in 10.04, and have tested it in 10.10, 11.04 and 11.10. im holstein in the #ubuntustudio irc channel if you would like some help setting jack up with the fp10. i would suggest (temporarily) running in a terminal

gksudo qjackctl

try getting jack running stable using the firewire driver with the fp10. then, if it doesnt run as normal user, you have some permissions error that we can troubleshoot.

i use a -reatime kernel from the kxstudio ppa's in 10.04.

---

### Post by mccuisinart on 2011-09-06
> **trulan said:**
> Is this still the computer you built? The firewire controller is sharing an IRQ with a hard driver controller:
 
...and that is certainly asking for trouble. I can't say for sure if that's the problem, but if there's any way you can get the firewire controller on its own irq, that would greatly increase your chances of getting this working, in my opinion.
Yes it is still the computer I just put together, and I did not buy a separate controller card. I'm plugging directly into a firewire port on my [motherboard]("http://4.bp.blogspot.com/_VppLa7dcUG0/TOzHlRQz8PI/AAAAAAAAAIQ/O2_zCDFJRr8/s1600/BIOSTAR+TP67XE.jpg"). Should I have bought one?

---

### Post by trulan on 2011-09-07
> **mccuisinart said:**
> Yes it is still the computer I just put together, and I did not buy a separate controller card. I'm plugging directly into a firewire port on my [motherboard]("http://4.bp.blogspot.com/_VppLa7dcUG0/TOzHlRQz8PI/AAAAAAAAAIQ/O2_zCDFJRr8/s1600/BIOSTAR+TP67XE.jpg"). Should I have bought one?
There isn't anything intrinsically wrong with onboard firewire controllers, but in my experience, ffado does not play well with something else that is trying to share its irq.  Both my machines use onboard firewire controllers; on my desktop it has its own irq, and on my laptop it shares an irq with the wireless card.  I have to shut wireless off to be able to use my firepods reliably.

I would think a hard drive controller is going to be a fairly aggressive irq user.  And it looks like you should have an open slot or two on that board, so if you can, I would buy a firewire card.  Conventional wisdom says you should get a 6-wire firewire card (firewire 400) with a Texas Instruments (TI) chip.  It also says that VIA chips can be hit-or-miss (and I did happen to notice that your firewire chip is a VIA.)

Anyway, sorry you're having so much trouble with this, and I wish you good luck!

PS. There is something to be said for using an RT kernel to help overcome the problems presented by an irq conflict.  2.6.33-rt, with a properly configured rtirq script, may just do the trick here (I know forum member Autostatic says this enables him to share an IRQ between firewire and wireless on his system).  In your case, though, I don't think this is going to be enough.  But trying this would be free, trying a firewire card will likely cost you at least $30.

---

### Post by mccuisinart on 2011-09-07
Excellent. So is changing my firewire IRQ something I can just learn how to do in terminal myself? Or, is it something to do with how all of my hardware is wired? I am not against getting a separate controller. I still have some shopping to do for my rig anyway.

---

### Post by sgx on 2011-09-07
In the old days, you could add, remove, or rearrange pci cards,
and their new slot assignments would modify the irq assignments.
Might be worth a try if you have an old pci modem, video card,
usb hub pci card just gathering dust. There are new $50 pci 256 meg nvidia video cards, that could be a strength for your system, and might
rearrange the works in your favor. You could do a usb stick install, and disable the hard-disk controller in the bios temporarily, to see if
things improve. Do take notesof bios changes so you can reverse them later :) 

You can also try turning off power management, bluetooth wireless motherboard sound, networking etc in the bios, and make sure cpu scaling is off, or set to productivity, not energy savings.

Do you have a pae kernel, to properly access your memory?

Cheers

---

### Post by trulan on 2011-09-09
It's pretty much about how the motherboard is wired, definitely not something you can do from a terminal.  There may be ways to do this in the bios, and sgx gave some good suggestions.  But the easiest way to change an IRQ is to put the card in a different slot, and, well, you know...

---

### Post by mccuisinart on 2011-09-11
Okay, I found/bought a firewire 400 controller (TI!) that is on its way and should arrive on Tuesday. In the meantime my problem is getting grub2 in working order. I can't for the life of me access the menu to boot into my realtime kernel even though i've installed grub-pc / grub2, and followed the directions on the page that fedex'nman hooked me up with. [ [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) ] What am I missing here?

---

### Post by jejeman on 2011-09-11
Don't know what is youre trouble with grub. But if you can't access it with shift key, you can set it up to show it self.
In file /etc/default/grub
comment out the line 
GRUB_HIDDEN_TIMEOUT=0
just put (#) in front, to look like this
#GRUB_HIDDEN_TIMEOUT=0

after that update the grub
```
sudo update-gub
```

---

### Post by mccuisinart on 2011-09-11
> **jejeman said:**
> Don't know what is youre trouble with grub. But if you can't access it with shift key, you can set it up to show it self.
In file /etc/default/grub
comment out the line 
GRUB_HIDDEN_TIMEOUT=0
just put (#) in front, to look like this
#GRUB_HIDDEN_TIMEOUT=0

after that update the grub
```
sudo update-gub
```
This worked, and the menu shows up now, but when I select the RT kernel to boot into, it fails and returns this message:

```
mount: mounting none   on /dev failed: no such device
```

Then there is about a ten second pause...

```
Gave up waiting for root device. Common problems:
   -Boot args (cat proc/cmdline)
     -check root delay= (did the system wait long enough?)
     -check root= (did the system wait for the right device?)
   -missing modules (cat /proc/modules; ls dev)
ALERT! /dw/disk/by-uuid/9566c49ad0c64cc8a0d4+cbc4d5c14dc7 does not exist. Opening to a shell!
```

And then my system runs a poor man's terminal Busybox v1.13.3

Can anyone make sense of this?

---

### Post by jejeman on 2011-09-11
Check the fstab entry for / partition, is it properly mapped. (/etc/fstab)
And check the grub entry for rt kernel, for same thing. (/boot/grub/grub.cfg)
Check UUID.

---

### Post by sgx on 2011-09-11
I would do a fresh install, with separate /home partition, when your firewire card arrives. Too much weirdness in the current setup, to be lucky! :popcorn: You might want to go with 10.04 instead of 11.xxx
as it seems to be the choice for quite a few good ubuntu based distro variants. 
Opinion based solely on 'vibes' ;)

---

