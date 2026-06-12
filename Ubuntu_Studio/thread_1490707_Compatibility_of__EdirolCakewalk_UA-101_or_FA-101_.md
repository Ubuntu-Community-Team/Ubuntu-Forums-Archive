---
title: "Compatibility of  Edirol/Cakewalk UA-101 or FA-101 with Ubuntu Studio  10.04"
date: 2010-05-22
forum: Ubuntu Studio
---

### Post by fritzm on 2010-05-22
I'm considering buying either a UA-101 or FA-101 audio interface (formerly branded as Edirol, now Cakewalk), the FA model being Firewire and the UA USB. There's been some discussion on the LAU mailing list which indicates that drivers for both of these exist, but it is not clear if they are included in Ubuntu Studio 10.04 and how much tweaking would be required to get the interfaces working.

Is anyone here using either of these, and how well does it work ? If so, what did you have to do to get it to work, or did it work with the default installation ?

Fritz

---

### Post by tipii on 2010-09-16
Hello, did you ever have any success with the FA101?
I've recently switched back to ubuntu which makes me a rusty noob... I have the FA101 and would welcome any tips on getting it running.
Cheers

---

### Post by AutoStatic on 2010-09-16
The FA-101 is fully supported by the FFADO drivers so it should work with 10.04.

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by tipii on 2010-09-16
Awesome, thanks AutoStatic!

---

### Post by tipii on 2010-10-16
Hello, me again!

No luck unfortunately...

I followed the instructions in the link given but I'm not getting any audio through.


My jack messages are as follows:

```
18:02:38.364 Patchbay deactivated.
18:02:38.397 Statistics reset.
18:02:38.411 Startup script...
18:02:38.412 artsshell -q terminate
18:02:38.415 ALSA connection graph change.
sh: artsshell: not found
18:02:38.813 Startup script terminated with exit status=32512.
18:02:38.813 JACK is starting...
18:02:38.813 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n3 -i8 -o8
18:02:38.816 JACK was started with PID=4062.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2321799
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
18:02:39.015 ALSA connection change.
18:02:41.020 Server configuration saved to "/home/tom/.jackdrc".
18:02:41.021 Statistics reset.
18:02:41.053 Client activated.
18:02:41.054 JACK connection change.
18:02:41.057 JACK connection graph change.
subgraph starting at qjackctl timed out (subgraph_wait_fd=13, status = 0, state = Triggered, pollret = 0 revents = 0x0)
```


When running ffado-dbus-server, after launching ffado-mixer I get the following stdout in the terminal running ffado-dbus-server:

```
03024525016: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024574156: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024622293: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024751089: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024797633: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024846338: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024897255: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug
03024945924: Error (avc_avdevice.cpp)[ 289] supportsSamplingFrequency: sample rate not supported by input plug

```

My firewire card is set to sample rate 44100 and jack setting match the example [here]("https://help.ubuntu.com/community/FireWire") exaclty (sample rate 44100).

Can you see anything in these messages that I'm failing to understand properly?

---

### Post by AutoStatic on 2010-10-16
Hello tipii,

The error message is related to ffado-dbus-server, not to the driver I think. Maybe you could provide the outcome of:
[LIST]
[*]**lspci | grep 1394**
[*]**cat /proc/interrupts**
[*]**uname -a**
[*]**ffado-diag**
[/LIST]

And check your FireWire cables and if you're not using the FA-101 with the external powers adapter do so.

Best,

Jeremy

---

### Post by tipii on 2010-11-07
Hi Jeremy,

I've attached the external power adapter as you suggested but there's no change.

Here's the outputs of the commands as requested:

**lspci | grep 1394**
```
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```

**cat /proc/interrupts**
```
           CPU0       CPU1       
  0:         48          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  6:          5          0   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge    
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 16:          7          0   IO-APIC-fasteoi   nouveau
 19:     128746          0   IO-APIC-fasteoi   ohci1394
 20:       7709      40868   IO-APIC-fasteoi   ehci_hcd:usb1, HDA Intel
 21:        398       1216   IO-APIC-fasteoi   sata_nv
 22:      28583          0   IO-APIC-fasteoi   sata_nv
 23:        715       3207   IO-APIC-fasteoi   ohci_hcd:usb2, sata_nv
 26:         45       1848   PCI-MSI-edge      eth0
 27:          0          0   PCI-MSI-edge      eth1
NMI:          0          0   Non-maskable interrupts
LOC:      92950      47204   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      11908       7843   Rescheduling interrupts
CAL:         71      13227   Function call interrupts
TLB:        481        354   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          2          2   Machine check polls
ERR:          2
MIS:          0
```

**uname -a**
```
Linux monster 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux
```

**ffado-diag**
*attached*

---

### Post by AutoStatic on 2010-11-08
Looks good so your card should work. What is it that doesn't work yet? The ffado-mixer?

---

### Post by tipii on 2010-11-18
I'm not sure if it's the mixer or the ffado-dbus-server...
When I start the mixer I get the supportsSamplingFrequency error in the dbus-server shell. The sound card has a physical dial from which I presume the mixer is reading the sampling frequency. I have tried changing this and rebooting... no joy though.
What would the 'input plug' plug be in this case (from my previous post with the mixer errors)

Tom

---

### Post by bluesscream on 2010-11-19
> The sound card has a physical dial 
That's indeed a little tricky. You'll have to make sure that FA101's and jackd's sr are identical. When you change FA101's sr you'll have to power it off and on physically before restarting jackd

---

