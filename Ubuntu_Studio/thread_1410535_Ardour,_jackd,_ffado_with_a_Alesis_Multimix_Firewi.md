---
title: "Ardour, jackd, ffado with a Alesis Multimix Firewire 16"
date: 2010-02-18
forum: Ubuntu Studio
---

### Post by edfsr777 on 2010-02-18
I currently use Ardour on Ubuntu Studio 9.10 with an M-Audio Delta 1010LT sound card on a quad core workstation.  But I need to use my HP laptop to connect to an Alesis Multimix Firewire 16 mixer for more portable applications ... small, on location sessions.

I've noticed on some postings that the Alesis Multimix Firewire 16 is reported to work with FFADO, but haven't found a clear, concise set of instructions on how to get jackd working with ffado to enable connecting to the Multimix mixer.  The Multimix uses a DICE chip which I've not been able to determine is supported in the ffado release in 9.10.

Has anyone out there successfully connected Ardour, jackd using ffado to a Multimix FIrewire 16 mixer?  If so could you give me some step by step instructions on how to set it up?

---

### Post by trulan on 2010-02-18
Well, have you gone through the basic setup steps?
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
That should work for anything supported by ffado.  If the Alesis is supported by a newer version of ffado than the one in 9.10, maybe we can find a newer build in a ppa.  But try the basic steps first - no need to make things difficult unless there is a problem.

---

### Post by edfsr777 on 2010-02-20
My laptop is not running Ubuntu Studio 9.10, just Ubuntu 9.10.  So I don't have the tools available that show in the thread you suggested.  I have manually implemented the configuration(s) suggested in the thread.

The Alesis runs the Dice chip which I don't think is supported in the 2.0 version of ffado.

---

### Post by robeast on 2010-02-20
[http://ffado.org/?q=node/61](http://ffado.org/?q=node/61) -- Reported to work

You can probably get it going, sounds like you need some more configuration on your laptop. Can you post your JACK settings? Is (default) the selected device? And what error messages do you get when you try to start JACK?

---

### Post by AutoStatic on 2010-02-20
> **edfsr777 said:**
> The Alesis runs the Dice chip which I don't think is supported in the 2.0 version of ffado.Karmic has revision 1569 from the FFADO svn 2.0 branch. And according to the [FFADO wiki]("http://subversion.ffado.org/wiki/Alesis") DICE support is enabled by default since revision 1498. So your device should work in theory.

---

### Post by edfsr777 on 2010-02-20
[COLOR="Red"]When I attempt to run real time, I get:[/COLOR]

18:08:37.565 Patchbay deactivated.
18:08:37.574 Statistics reset.
18:08:37.676 ALSA connection graph change.
18:08:37.971 ALSA connection change.
18:11:15.054 Startup script...
18:11:15.055 artsshell -q terminate
sh: artsshell: not found
18:11:15.459 Startup script terminated with exit status=32512.
18:11:15.459 JACK is starting...
18:11:15.460 /usr/bin/jackd -R -dfirewire -r44100 -p1024 -n3
18:11:15.463 JACK was started with PID=3806.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1587508976, from thread 1587508976] (1: Operation not permitted)
cannot create engine
18:11:15.814 JACK was stopped successfully.
18:11:15.815 Post-shutdown script...
18:11:15.816 killall jackd
jackd: no process found
18:11:16.242 Post-shutdown script terminated with exit status=256.
18:11:17.522 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

[COLOR="Red"]When I run jackd without real time enabled, I get:[/COLOR]

18:12:15.870 Startup script...
18:12:15.872 artsshell -q terminate
sh: artsshell: not found
18:12:16.276 Startup script terminated with exit status=32512.
18:12:16.276 JACK is starting...
18:12:16.277 /usr/bin/jackd -dfirewire -r44100 -p1024 -n3
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
07412036705:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
18:12:16.312 JACK was started with PID=3815.
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
18:12:16.458 JACK was stopped successfully.
18:12:16.460 Post-shutdown script...
18:12:16.461 killall jackd
jackd: no process found
18:12:16.873 Post-shutdown script terminated with exit status=256.
18:12:18.352 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by trulan on 2010-02-20
Can you post the output of:
```
groups
```
and
```
ls -al /dev/raw1394
```
Thanks!

---

### Post by edfsr777 on 2010-03-03
Here is the output as requested above:

~$ groups
myuser adm dialout fax cdrom audio video plugdev lpadmin netdev admin sambashare vboxusers
~$ ls -al /dev/raw1394
crw-rw---- 1 root video 171, 0 2010-03-03 19:02 /dev/raw1394

---

### Post by AutoStatic on 2010-03-04
Looks good, but could you also post the contents of */etc/security/limits.conf* ? Weird though that JACK doesn't start when the Realtime option is disabled.

---

### Post by doogxela on 2010-03-14
I am having exactly the same problems as the original poster. Here is the output of */etc/security/limits.conf* (minus the informational text):
> #<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

---

### Post by rlameiro on 2010-03-14
> **doogxela said:**
> I am having exactly the same problems as the original poster. Here is the output of */etc/security/limits.conf* (minus the informational text):

what problem???

do you have the same hardware as the poster? or just jack is not starting? please be more specific when you ask for something, so people can help you better.

---

### Post by doogxela on 2010-03-14
> **rlameiro said:**
> what problem???

do you have the same hardware as the poster? or just jack is not starting? please be more specific when you ask for something, so people can help you better.

I apologize. I assumed the context of my post made it clear that I had gotten to the same point as the original poster (with the same errors attempting to launch jackd) and I was continuing with the thread. I have an Alesis MultiMix 8 FireWire, and I was getting the exact same errors when attempting to use jackd.

I have since started over. I uninstalled the versions of jackd and ffado that come with Ubuntu 9.10 and installed the latest versions from source. Once I did that, I was able to get qjackcfg to start up and recognize the Alesis. I can now speak into a microphone and get the sound to output from the mixer. The problem now is that I am only getting the right channel. I have not been able to get anything but mono.

Right now I am compiling ardour so I can get that installed to see if I can actually record anything, even if it is mono. The most annoying thing about this saga is that once you start building from source instead of using a package manager, you start having to do that more and more. I couldn't install ardour from Synaptic because ardour is dependent on jackd and ffado. As far as Synaptic could tell, I didn't have those installed, so it wanted to install the versions in the repository, but that would create a problem with concurrent installations, and I can't do that.

Anyway, that's off topic. Now that I have the Alesis partially working, does anyone know why I would only be getting mono, instead of stereo from my microphone?

**EDIT**
I have opened a new thread with the problems I'm having with the Alesis, since this is now way off the the OP topic.

---

### Post by AutoStatic on 2010-03-15
Is it a stereo mic? If not, then try connecting the capture port of the mic in QjackCtl to two playback ports. Easiest way to get 'faux stereo' ;)

---

### Post by rlameiro on 2010-03-15
As autostatic said if you have a stereo mic ou will have stereo. if you have a mono stereo you will just listen to one channel. this is not a problem of ffado or jack. its just how audio works.
About the software install.
you could try to use the software versions in ubuntu again and see if they work. If not you can force install ardour to pass over the dependencies on the package system. i dont recommend tis but sometimes is the only way to go.

---

### Post by edfsr777 on 2010-04-25
Decided to wait for the 10.04 Release Candidate to arrive.  Did a fresh installation of the RC on my laptop, installed ffado and the ffado-dbus-server, installed and loaded Ardour, and connected the laptop to the Multimix Firewire 16.  Using qjackctl, I configured jack to connect using the firewire port.  But jack refuses to start because the ffado-dbus-server will not start.

Any ideas why the ffado-dbus-server will not start?  Is DICE-II support built into the version of ffado that comes with 10.04?

---

### Post by edfsr777 on 2010-04-25
These are the messages from the message window when I attempt to start jack from qjackctl:
16:32:58.960 Patchbay deactivated.
16:32:59.001 Statistics reset.
16:32:59.020 Startup script...
16:32:59.021 artsshell -q terminate
16:32:59.024 ALSA connection graph change.
sh: artsshell: not found
16:32:59.424 Startup script terminated with exit status=32512.
16:32:59.424 JACK is starting...
16:32:59.425 /usr/bin/jackd -r -dfirewire -r48000 -p1024 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
16:32:59.450 JACK was started with PID=7353.
Enhanced3DNow! detected
SSE2 detected
libffado 2.0.0 built Mar 31 2010 16:21:44
16:32:59.628 ALSA connection change.
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
16:32:59.671 JACK was stopped successfully.
16:32:59.672 Post-shutdown script...
16:32:59.673 killall jackd
jackd: no process found
16:33:00.085 Post-shutdown script terminated with exit status=256.
16:33:01.642 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by AutoStatic on 2010-04-26
```
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
```Either the raw1394 module is not loaded or you don't have permission to use the /dev/raw1394 device node. Could you post the output of **cat /etc/modules** and **ls -al /dev/raw1394** ?

---

### Post by edfsr777 on 2010-04-26
Output is below:

$cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc


$ ls -al /dev/raw1394
ls: cannot access /dev/raw1394: No such file or directory

---

### Post by edfsr777 on 2010-04-26
Ran modprobe raw1394

The responses to the commands you requested I run now look like this:

~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
raw1394

~$ ls -al /dev/raw1394
crw-rw---- 1 root root 171, 0 2010-04-26 13:45 /dev/raw1394

The jackd still doesn't start.

---

### Post by edfsr777 on 2010-04-26
Following the my two earlier posts, and changing permissions on /dev/raw1394 as shown below:

~$ ls -al /dev/raw1394
crw-rw-rw- 1 root root 171, 0 2010-04-26 13:45 /dev/raw1394

I now get the following when I attempt to load jackd using qjackctl:

16:59:37.052 Patchbay deactivated.
16:59:37.096 Statistics reset.
16:59:37.116 Startup script...
16:59:37.117 artsshell -q terminate
16:59:37.121 ALSA connection graph change.
sh: artsshell: not found
16:59:37.520 Startup script terminated with exit status=32512.
16:59:37.520 JACK is starting...
16:59:37.521 /usr/bin/jackd -v -r -dfirewire -dhw:0 -r48000 -p1024 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
getting driver descriptor from /usr/lib/jack/jack_firewire.so
16:59:37.530 JACK was started with PID=2299.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
Enhanced3DNow! detected
SSE2 detected
libffado 2.0.0 built Mar 31 2010 16:21:44
16:59:37.724 ALSA connection change.
16:59:39.742 Server configuration saved to "/home/franksed/.jackdrc".
16:59:39.744 Statistics reset.
16:59:39.746 Client activated.
16:59:39.756 JACK connection graph change.
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: firewire_pcm, id = 1 type 1 @ 0x925060 fd = -1
new buffer size 1024
start poll on 3 fd's
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0x7f2b38432000 fd = 13
start poll on 4 fd's
Enhanced3DNow! detected
SSE2 detected
server thread back from poll
new client qjackctl using 14 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 0
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 14 for qjackctl starts at 2865569170
back from client event poll after 228 usecs
client qjackctl: wait_fd=15, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
02868622288: [31mError (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
[0m02873872247: [31mError (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
[0mfirewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
no message buffer overruns
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
... NUMEROUS SIMILAR MESSAGES HERE
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
6:59:48.240 Client deactivated.
cannot continue execution of the processing graph (Broken pipe
16:59:48.243 JACK was stopped successfully.
16:59:48.244 Post-shutdown script...
16:59:48.245 killall jackd
)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
... NUMEROUS SIMILAR MESSAGES HERE
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
16:59:48.710 Post-shutdown script terminated with exit status=256.
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
... NUMEROUS SIMILAR MESSAGES HERE
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
jackd: no process found

---

### Post by AutoStatic on 2010-04-27
```
02868622288: [31mError (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
[0m02873872247: [31mError (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
[0mfirewire ERR: Error creating FFADO streaming device
```
I've seen that one before. Could you please post the output of **lspci** and **cat /proc/interrupts** ?
Also, it's not very common to chmod /dev/raw1394 to 666 (rw for all users), it's better to chgrp (change group) it to 'audio' and add yourself to the audio group.

---

### Post by edfsr777 on 2010-04-27
Changed the group to audio for /dev/raw1394 and added myself to the group.

Below are the results you requested:

~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
~$
~$
~$ cat /proc/interrupts
           CPU0       CPU1       
  0:     722339     491926   IO-APIC-edge      timer
  1:        307        192   IO-APIC-edge      i8042
  5:         81        307   IO-APIC-fasteoi   ohci1394
  7:          3          0   IO-APIC-fasteoi   mmc0
  8:          0          1   IO-APIC-edge      rtc0
  9:       6788       1244   IO-APIC-fasteoi   acpi
 12:        141        238   IO-APIC-edge      i8042
 14:     184886     124650   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 18:      18904     168887   IO-APIC-fasteoi   nvidia
 19:    1869783       2620   IO-APIC-fasteoi   eth1
 20:          0          0   IO-APIC-fasteoi   eth0
 21:        136       1506   IO-APIC-fasteoi   HDA Intel
 22:      33313      13646   IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb2
 23:      50346     535346   IO-APIC-fasteoi   sata_nv
NMI:          0          0   Non-maskable interrupts
LOC:     414458     214041   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:    1368398     723326   Rescheduling interrupts
CAL:       3078       2495   Function call interrupts
TLB:       2642       2534   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         72         72   Machine check polls
ERR:          1
MIS:          2

---

### Post by AutoStatic on 2010-04-27
Thanks!

```
FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
```

From the [FFADO]("http://subversion.ffado.org/wiki/HostControllers") site:

Seems to **not** work for most people (Exceptions - Scott reports 100% success with FFADO-2-RC1 UBS 8.10 on Jan 14th 2009. 100% success with FFADO-2-RC1 in Fedora 10. Pedro reports good performance (128x3) with ffado-svn (as of Nov 2009), kernel 2.6.31.6-rt19/Debian testing on a Lenovo T400 laptop and cpufreq governor set to performance):

```
FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (prog-if 10 [OHCI])
```

So, in a worst case scenario it won't work. But when reading the above, did you disable CPU frequency scaling?

---

### Post by edfsr777 on 2010-04-27
To my knowledge I have not disabled CPU frequency scaling.

And I want to say Thank you for your help.

---

### Post by AutoStatic on 2010-04-28
You can easily disable it by right-clicking on your panel - Add to Panel - CPU Frequency Scaling Monitor. This will add an extra applet to your panel. In this applet you have to set the scaling to Performance. Since you have a dual core CPU you might have to add two applets to your panel, one for each core. Not sure about that though, I tend to disable CPU scaling altogether.

---

### Post by trulan on 2010-04-29
> **AutoStatic said:**
> ```
FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
```From the [FFADO]("http://subversion.ffado.org/wiki/HostControllers") site:

Seems to **not** work for most people
Hmm...That's what I have.  Mine is rev 04 whatever that's worth.  No troubles here.  I know I've read a lot of bad stuff about the Ricoh firewire chips, especially when using Windoze, but I've had two of them, with nothing but success on Linux (admittedly, it was a failure under Windows).  Now I do have to turn off my wireless card to use firewire because they share an IRQ on my laptop.

---

### Post by edfsr777 on 2010-04-29
Trulan ... That's interesting ... because I've always kept my wireless on when I've tried to use the 1394 port.  I'll give that a try this weekend.

---

### Post by JC Cheloven on 2010-06-09
Sorry for bringing this a bit late. Regarding a firewire device similar to the alesis multimix 16, you may find of interest my recent experience:

[http://ubuntuforums.org/showthread.php?p=9437662#post9437662](http://ubuntuforums.org/showthread.php?p=9437662#post9437662)

Greeting
JC
___________________

---

### Post by forgetclosure on 2012-02-14
I have no idea exactly what got it working, but when I changed my regular Ubuntu installation into an Ubuntu *Studio* installation the mixer works when you plug it in and *then* start jack with the following command:

```
jackd -d firewire
```

---

