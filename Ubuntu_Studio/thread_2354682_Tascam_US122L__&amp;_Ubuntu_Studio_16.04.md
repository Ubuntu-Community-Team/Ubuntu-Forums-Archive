---
title: "Tascam US122L  &amp; Ubuntu Studio 16.04"
date: 2017-03-05
forum: Ubuntu Studio
---

### Post by mnlpnt on 2017-03-05
[FONT=&amp]Hello,[/FONT]

[FONT=&amp]I have a problem with my Tascam US-122L - its in- and outputs won't be recognized. The MIDI ins and outs are, however, recognized. 
It is recognized under ```
lsusb
```[/FONT]```

[FONT=&amp]Bus 002 Device 002: ID 0718:0619 Imation Corp. Bus 002 Device 010: ID 0644:800e TEAC Corp. TASCAM US-122L[/FONT]
[FONT=&amp]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=&amp]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=&amp]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=&amp]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=&amp]Bus 001 Device 002: ID 0ac8:c302 Z-Star Microelectronics Corp. Vega USB 2.0 Camera[/FONT]
[FONT=&amp]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=&amp]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=&amp]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]

```[FONT=&amp] ```
cat /proc/asound/cards
```[/FONT]```

[FONT=&amp] 0 [Intel          ]: HDA-Intel - HDA Intel                      HDA Intel at 0xf0500000 irq 28[/FONT]
[FONT=&amp] 1 [US122L         ]: USB US-122L - TASCAM US-122L[/FONT]
[FONT=&amp]                      TASCAM US-122L (644:800e if 0 at 002/010)[/FONT]
```[FONT=&amp] and also under ```
cat /proc/asound/modules 
```[/FONT]```

[FONT=&amp] 0 snd_hda_intel[/FONT]
[FONT=&amp] 1 snd_usb_us122l[/FONT]

```[FONT=&amp] However, if I run ```
aplay -l**** 
List of PLAYBACK Hardware Devices ****
```[/FONT]```

[FONT=&amp]card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog][/FONT]
[FONT=&amp]  Subdevices: 1/1[/FONT]
[FONT=&amp]  Subdevice #0: subdevice #0[/FONT]
[FONT=&amp]card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital][/FONT]
[FONT=&amp]  Subdevices: 1/1[/FONT]
[FONT=&amp]  Subdevice #0: subdevice #0[/FONT]

```[FONT=&amp] or ```
arecord -l**** List of CAPTURE Hardware Devices ****
```[/FONT]```

[FONT=&amp]card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog][/FONT]
[FONT=&amp]  Subdevices: 1/1[/FONT]
[FONT=&amp]  Subdevice #0: subdevice #0[/FONT]

```[FONT=&amp] it's nowhere to be found.[/FONT]

[FONT=&amp]I have tried the following:[/FONT]
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)
[http://askubuntu.com/questions/95561/how-do-i-get-a-tascam-us-122l-working](http://askubuntu.com/questions/95561/how-do-i-get-a-tascam-us-122l-working)
[http://askubuntu.com/questions/532826/how-do-i-get-the-tascam-us122l-usb-audio-interface-to-work](http://askubuntu.com/questions/532826/how-do-i-get-the-tascam-us122l-usb-audio-interface-to-work)
[https://www.community.ardour.org/node/7044](https://www.community.ardour.org/node/7044)

More information about problems with the kernel
[https://bugzilla.kernel.org/show_bug.cgi?id=53241](https://bugzilla.kernel.org/show_bug.cgi?id=53241)
--> although the fix seems to have been implemented here into a future release of the kernel, it is not working under the current kernel for Ubuntustudio 16.04.

---

