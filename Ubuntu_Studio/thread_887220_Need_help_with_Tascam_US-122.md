---
title: "Need help with Tascam US-122"
date: 2008-08-11
forum: Ubuntu Studio
---

### Post by Miesco on 2008-08-11
I downloaded alsa-firmware and fxload from medibuntu, it loads the firmware fine, the lights go on and alsa recognizes it.  I get errors in dmesg and jackd doesn't work.


shawn@ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 19
 1 [K88            ]: USB-Audio - Keystation Pro 88
                      Evolution Electronics Ltd. Keystation Pro 88 at usb-0000:00:1d.7-2.4, full spee
 2 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 007/006)


I get this in dmesg:
[   95.442460] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/usb/usx2y/usbusx2yaudio.c:313: Sequence Error!(hcd_frame=345 ep=10out;wait=345,frame=342).
[   95.442488] Most propably some urb of usb-frame 345 is still missing.
[   95.442491] Cause could be too long delays in usb-hcd interrupt handling.
[   95.479404] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/usb/usx2y/usbusx2yaudio.c:313: Sequence Error!(hcd_frame=382 ep=10out;wait=382,frame=379).
[   95.479429] Most propably some urb of usb-frame 382 is still missing.
[   95.479431] Cause could be too long delays in usb-hcd interrupt handling.
[   96.012293] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/usb/usx2y/usbusx2yaudio.c:313: Sequence Error!(hcd_frame=5 ep=8in;wait=1026,frame=2).
[   96.012311] Most propably some urb of usb-frame 1026 is still missing.
[   96.012314] Cause could be too long delays in usb-hcd interrupt handling.


I get this with jackd:
23:01:43.405 JACK is starting...
23:01:43.406 /usr/bin/jackd -R -dalsa -dhw:2 -r96000 -p1024 -n3
23:01:43.434 JACK was started with PID=22944.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 96000
creating alsa driver ... hw:2|hw:2|1024|3|96000|0|0|nomon|swmeter|-|32bit
control device hw:2
configuring for 96000Hz, period = 1024 frames (10.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
ALSA: cannot set hardware parameters for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
23:01:44.454 JACK was stopped successfully.
23:01:44.455 Post-shutdown script...
23:01:44.455 killall jackd
jackd: no process killed
23:01:45.053 Post-shutdown script terminated with exit status=256.
23:01:46.681 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Help please!

---

### Post by Stochastic on 2008-08-11
It's been a while since I've had my US-122 running, but I'll try to help out.

First, what is the output of the following command:
```
uname -r
```
Second, what options are listed in the drop down menu for devices in qjackctl's settings window?

Third, do any of the errors you've found, change if you run jack from command line:
```
jackd -R -dalsa -dhw:2
```

Fourth, after a full reboot, before you've attempted to start jack, do you see any errors in dmesg?

---

### Post by Miesco on 2008-08-11
shawn@ubuntu:~$ uname -r
2.6.24-20-rt

shawn@ubuntu:~$ jackd -R -dalsa -dhw:2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
creating alsa driver ... hw:2|hw:2|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:2
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
ALSA: cannot set hardware parameters for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns


I see the errors when I boot before I run jackd.

I get the error when I run modprobe snd_usb_usx2y

---

### Post by Miesco on 2008-08-12
Got it to work, just the usx2yloader wasn't loading the hex file, that was all.  But there is noise coming from my speakers...  Like dee dee,
and buh buh buh.  The buh buh is random, the dee dee is constant and
goes every second.

---

### Post by Stochastic on 2008-08-12
> **Miesco said:**
> Got it to work, just the usx2yloader wasn't loading the hex file, that was all.  But there is noise coming from my speakers...  Like dee dee,
and buh buh buh.  The buh buh is random, the dee dee is constant and
goes every second.


Good to hear you've fixed your issue.  The noise thing was a major issue for me too - back in Edgy and Feisty - so I ended up getting a bigger and better soundcard.  I've heard of many people using the US-122 on linux though, so there may be another model that doesn't have the noise issue, or a way of making it stop, but I've never heard of a solution.  Here's hoping you do.

---

