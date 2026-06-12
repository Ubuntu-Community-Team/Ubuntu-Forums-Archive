---
title: "Cakewalk (edirol) UA-25 EX and jack"
date: 2010-01-24
forum: Ubuntu Studio
---

### Post by delaossa on 2010-01-24
Hello,
I just got the usb audio/midi interface Cakewalk (edirol) UA-25 EX and trying to make it work properly in ubuntu studio 9.10 (karmic).
The device is recognised and fully functional out-of-the-box: great!
I can also configure jack server and everything to start playing with it: great!
Multimedia production programs like ardour, hydrogen, rosegarden, etc. work as expected: great!
My troubles start when trying to operate with jack at a low latency, let's say below 10ms.
My system runs with the current RT kernel in repositories: ***2.6.31-9-rt*** .
I have also setup /etc/security/limits.conf for a proper RT access, just like I read here ([ubuntustudio preparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")).
Finally, I configured jack server with the following features:

[I]Realtime: Y
Everything else: N

Priority: (default)
Frames/Period: 128
Sample Rate: 48000
Periods/Buffer: 2

Port maximum: 128
Timeout: 500

--> Latency: 5.33 ms.[/I]   

As I read in this other [thread]("http://ubuntuforums.org/showthread.php?t=1225076"):
*"I've tried with various frames/period settings and it is a bit more reliable with higher settings, but I'm really trying to keep the latency below 10ms."*
However, I get frequent xruns which cause glitches in my recordings: not great!
I post here some jack output:
```

 [COLOR=#990099]17:31:29.950 /usr/bin/jackd -R -p128 -dalsa -dhw:1 -r48000 -p128 -n2[/COLOR]
 [COLOR=#999999]17:31:29.952 JACK was started with PID=4552.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
...
 loading driver ..
 SSE2 detected
 apparent rate = 48000
 creating alsa driver ... hw:1|hw:1|128|2|48000|0|0|nomon|swmeter|-|32bit
 control device hw:1
 configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 24bit little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999999]17:31:32.040 Client activated.[/COLOR]
**** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.032 msecs[/COLOR] [COLOR=#cc66cc]
17:32:43.829 XRUN callback (1).[/COLOR]
**** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.159 msecs[/COLOR] 
[COLOR=#cc66cc]17:34:50.103 XRUN callback (4).[/COLOR] 
**** alsa_pcm: [COLOR=#cc0000]xrun of at least 0.017 msecs[/COLOR] 
[COLOR=#cc66cc]17:35:23.452 XRUN callback (5).[/COLOR] 
```Yes, I can avoid the problem increasing Frames/Period, for instance, up to 512, which normally gives back no xruns (or very few). However, this consequently increase the latency to 21.3 ms, that seems to me a rather high value.
Ok.. My question is the following:
Is this a normal behaviour or am I doing something wrong?

Please, if anybody has some experience with jack and cakewalk (edirol) usb interfaces, I would appreciate your comments or advices for an optimal configuration.
Cheers!

---

### Post by AutoStatic on 2010-01-24
Hello delaossa, try Periods/Buffer of 3.
I have an Edirol UA-25 (its predecessor) and I can achieve latencies below 5ms with the same kernel. Also make sure the sample rate knob on the back of the Edirol matches the sample rate in QjackCtl.

---

### Post by delaossa on 2010-01-24
Hello!
Well.. the knob at back of the device was already set to 48 kHz.
On the other hand, changing the Periods/Buffer to 3 as you suggest, implies to change Frames/Period to 128 in order to get a latency below 10 ms.
And that causes even more xruns than the configuration I was using.
I don't know, perhaps I have something wrong in my system setup...
Could you please post here your jack setup with which you get latencies below 10 ms. and no xruns?
Thank you very much for your suggestions!

---

### Post by AutoStatic on 2010-01-25
I've attached my settings. I now see I've set Priority to (default) while in my case it should be 73 (I use [rtirq]("http://ubuntuforums.org/showthread.php?t=1328175")).
Could you post the outcome of the terminal commands **uname -a** , **lsusb** and **cat /proc/interrupts** ?
And some things you could already take a look at:
[LIST]
[*]You could try disabling the Ondemand service and make sure Ubuntu is scaling your CPU to the max
[*] System - Preferences - Startup Applications and disable everything you don't need in a music production environment. At the moment I only have GNOME Settings Daemon and Indicator applet ticked, I don't need the rest
[*] Does the UA-25EX also have an 'Advanced' switch? If so, turn it on
[*] Disable desktop effects
[*] In my case I've also disabled wireless and bluetooth
[/LIST]

---

### Post by delaossa on 2010-01-25
Wow, I didn't know one had to save so much resources in order to avoid the xruns..
I have checked the thread in relation with the [rtirq]("http://ubuntuforums.org/showthread.php?t=1328175"). I guess I am also using it, since I have that package installed and the configuration script in /etc/default/rtirq. I don't have a firewire card, so I guess I don't need to give the extra priorities they suggest there.
But, should I somehow give some extra priorities to my usb sound card? If so, how?
Besides, I have followed the instructions there to set cpu frequency scaling to high performance using these[ two scripts]("http://ubuntuforums.org/showthread.php?t=1328175#10") at jack daemon startup and shutdown. 
It should play the role you suggest in your first point. Do you use them?
It seems to be very important as well, and I found it there as a bonus, thanks!
Finally I have copied your configuration and set jack priority to 78.
On the other hand, the 'Advanced' switch was already set to ON.

Here some output:

[LIST]
[*]**uname -a:** ```
[Ziz]:/~/Programs>uname -a
Linux Ziz 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux
```
[*]**lsusb: **```
[Ziz]:/~/Programs>lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 005 Device 004: ID 0582:00e6 Roland Corp.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
[*]**cat /proc/interrupts :**```
[Ziz]:/~/Programs>cat /proc/interrupts
            CPU0       CPU1
   0:        146         25   IO-APIC-edge      timer
   1:      13167      12930   IO-APIC-edge      i8042
   8:          0          1   IO-APIC-edge      rtc0
   9:          1          2   IO-APIC-fasteoi   acpi
  12:       7384       7404   IO-APIC-edge      i8042
  14:     100647     100704   IO-APIC-edge      ata_piix
  15:          0          0   IO-APIC-edge      ata_piix
  16:       7510       7449   IO-APIC-fasteoi   nvidia
  18:          7          5   IO-APIC-fasteoi   mmc0
  19:          2          1   IO-APIC-fasteoi   ohci1394
  20:     148407     148235   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb5
  21:       2816       2844   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb6, HDA Intel
  22:        771        822   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
  29:      33425      33630   PCI-MSI-edge      ahci
  30:     121869     121971   PCI-MSI-edge      iwlagn
  31:          2          2   PCI-MSI-edge      eth0
 NMI:          0          0   Non-maskable interrupts
 LOC:   13687691   13576143   Local timer interrupts
 SPU:          0          0   Spurious interrupts
 CNT:          0          0   Performance counter interrupts
 PND:          0          0   Performance pending work
 RES:      36341      36573   Rescheduling interrupts
 CAL:     696520     814601   Function call interrupts
 TLB:       8041       7430   TLB shootdowns
 TRM:          0          0   Thermal event interrupts
 THR:          0          0   Threshold APIC interrupts
 MCE:          0          0   Machine check exceptions
 MCP:         44         44   Machine check polls
 ERR:          0
 MIS:          0
```
[/LIST]
Let me check a bit the new configuration and I will let you know later.
Thanks again for your suggestions and feedback!

---

### Post by AutoStatic on 2010-01-25
> **delaossa said:**
> Wow, I didn't know one had to save so much resources in order to avoid the xruns..Well, this is the config of my netbook with a 1,2 GHz CPU so I need all resources I can get. I still have to ditch Gnome, I'd like to use IceWM instead, it runs, but with some minor but annoying issues. And if I can tweak my system to the max, I tweak it to the max ;)

> **delaossa said:**
> I don't have a firewire card, so I guess I don't need to give the extra priorities they suggest there.
But, should I somehow give some extra priorities to my usb sound card? If so, how?You can prioritize your USB soundcard too with rtirq, it's not specifically written for Firewire devices. I should check at home on my main PC, I've reserved an USB bus specifically for the UA-25 and defined that in the /etc/default/rtirq file.

> **delaossa said:**
> It should play the role you suggest in your first point. Do you use them?Yes, realtime processing and the Ondemand service don't get along together very well.

```
[Ziz]:/~/Programs>lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 005 Device 004: ID 0582:00e6 Roland Corp.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The UA-25EX and your mouse are on the same USB bus, if possible use another USB bus for your Edirol. The bus numbers correspond with the usb numbers of the interrupt output, so Bus 005 = usb5, Bus 001 = usb1 etc. With a bit of puzzling you might be able to put your Edirol on a free USB bus so that nothing could interfere with the data streams of the Edirol. Normally it shouldn't be a problem but you just never know. And maybe you could try disabling your webcam and fingerprint reader but I don't think that's necessary.

And I've understood that there are motherboards that assign USB buses dynamically, can't help you with that though if that might be the case for you.

---

### Post by delaossa on 2010-01-25
Hello AutoStatic,
I can not get rid of those xruns with the configuration that you proposed. The minimal stable (with no xruns) configuration I can achieve, following all the advices you gave me is Frames/Period: 128 <--> Latency: 16 msec. 
Below this value, xruns quickly appear.
Now, my processors automatically change to 100% frequency scaling when connecting jack server, and I have even tried with IceWM to minimize system resources.
On the other hand, the usb bus issue: My laptop only have 2 usb ports. One on the left and one on the right. Maybe, physical ports have nothing to do with buses, but I don't know.
> You can prioritize your USB soundcard too with rtirq, it's not specifically written for Firewire devices. I should check at home on my main PC, I've reserved an USB bus specifically for the UA-25 and defined that in the /etc/default/rtirq file.Oh! This could help, isn't? I still have the default configuration:

[LIST]
[*]/etc/default/rtirq:```
# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc ohci1394 snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

# On kernel configurations that support it,
# which services should be NOT threaded
# (space separated list).
RTIRQ_NON_THREADED="rtc snd ohci1394"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
# RTIRQ_HIGH_LIST="timer"
```
[/LIST]
Once again, thanks!

---

### Post by Hanine on 2010-10-03
> **AutoStatic said:**
> Hello delaossa, try Periods/Buffer of 3.
I have an Edirol UA-25 (its predecessor) and I can achieve latencies below 5ms with the same kernel. Also make sure the sample rate knob on the back of the Edirol matches the sample rate in QjackCtl.

Plz Help! I am frustrated again!
I have an Edirol UA-25 USB. But I cannot make it work on Ubuntu.
I installed Ubuntu Studio but that doesn't help!

Here is my : **lsusb**

```
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0582:00b4 Roland Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

my **uname -a**
```
2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
```

my **cat /proc/interrupts**

```
CPU0       CPU1       
  0:    1955341          0   IO-APIC-edge      timer
  1:         10          0   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          1          0   IO-APIC-fasteoi   acpi
 12:        135          0   IO-APIC-edge      i8042
 14:      78758          0   IO-APIC-edge      ata_piix
 15:      19908          0   IO-APIC-edge      ata_piix
 16:       7208          0   IO-APIC-fasteoi   i915
 17:     170712          0   IO-APIC-fasteoi   eth0
 18:          0          0   IO-APIC-fasteoi   mmc0, r852
 19:          1          0   IO-APIC-fasteoi   firewire_ohci
 20:         56          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 21:         27          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:       1217          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:      37997          0   IO-APIC-fasteoi   uhci_hcd:usb5
 43:       6465          0   PCI-MSI-edge      iwl3945
 44:      10063          0   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:     442735    1171721   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:    1401724    1457559   Rescheduling interrupts
CAL:         77         53   Function call interrupts
TLB:       8134       7591   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         14         14   Machine check polls
ERR:          1
MIS:          0
```

The device is working properly under Windows XP. :(

---

