---
title: "tascam 122l wont work"
date: 2009-10-02
forum: Ubuntu Studio
---

### Post by Wild-Storm on 2009-10-02
hi, i'm running ubuntu jaunty x86-64
i recently bought the tascam 122l, which is said to be supported under ubuntu / linux.
so i plugged it in and it gets recognized by alsa (at least by asoundconf)

but it does not show up on aplay -l or on pavucontrol. i searched a lot on google but i could not find any solution


some information:

```
mrnice@root:~$ asoundconf list
Names of available sound cards:
Intel
US122L
mrnice@root:~$ lsusb
Bus 002 Device 003: ID 0644:800e TEAC Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 03f0:0f0c Hewlett-Packard 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 005: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 002: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mrnice@root:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 002/003)
mrnice@root:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l
mrnice@root:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC883 Analog [ALC883 Analog]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC883 Digital [ALC883 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
mrnice@root:~$ arecord -l
**** Liste von CAPTURE Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC883 Analog [ALC883 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC883 Digital [ALC883 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 2: ALC883 Analog [ALC883 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
mrnice@root:~$ sudo jackd -dalsa -dusb_stream:1 -r44100 -p64 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback


**** alsa_pcm: xrun of at least -1254504917893.120 msecs

[repeats for about 7 times]

mrnice@root:~$ cat /etc/asound.conf
pcm.!usb_stream {
	@args [ CARD ]

	@args.CARD {
		type string
		default "1"
	}

	type usb_stream

	card $CARD
}
mrnice@root:~$ cat ~/.asoundrc
pcm.skypeout
{
	type plug
	slave.pcm "dmix"
}
ctl.skypeout
{
	type hw
	card 0
}
pcm.skypein
{
	type plug
	slave.pcm "dsnoop"
}
ctl.skypein
{
	type hw
	card 0
}


```

i hope somebody can help me, since i can't get the interface working with virtualbox as well. (it gets recognized but it does not send any signal. and the virtualbox-guest system crashes, when i unplug it)


edit://
audacity finds the alsa:usb "input" but i get the following error: "Error while opening sound device. Please check the input device settings and the project sample rate."
the souondcard should not be blocked, since my music runs over the intel soundcard..

---

### Post by urlwolf on 2010-03-27
It doesn't work for us either. We tried alsa, pulse, and jack in two computers, pops and cracks. Maybe removing it from the list of supported cards is due?

---

