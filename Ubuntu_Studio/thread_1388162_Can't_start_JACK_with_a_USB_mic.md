---
title: "Can't start JACK with a USB mic"
date: 2010-01-22
forum: Ubuntu Studio
---

### Post by benplaut on 2010-01-22
Trying to connect my Zoom H4n to use with Ardour (in and out).  Laptop mics work with JACK, and the H4n works with Audacity (non-JACK).  The important message is "ALSA: could not start playback (Broken pipe)"

Same results starting JACKd on it's own, qjackctrl, or through Ardour.

Any suggestions?

```
13:45:48.262 Patchbay deactivated.
13:45:48.265 Statistics reset.
13:46:45.970 Startup script...
13:46:45.971 artsshell -q terminate
sh: artsshell: not found
13:46:46.373 Startup script terminated with exit status=32512.
13:46:46.373 JACK is starting...
13:46:46.373 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2
13:46:46.375 JACK was started with PID=14584.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
13:46:46.877 JACK was stopped successfully.
13:46:46.878 Post-shutdown script...
13:46:46.878 killall jackd
jackd: no process found
13:46:47.288 Post-shutdown script terminated with exit status=256.
13:46:48.551 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by AutoStatic on 2010-01-23
Hello benplaut, could you post the outcome of **aplay -l** ? Mine looks like this:
```
jeremy@soushi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA25 [UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So an Intel card (ALSA device name: 'Intel') and an Edirol UA-25 USB sound card (ALSA device name: 'UA25'). For the Edirol the JACK settings look like this:
```
jeremy@soushi:~$ cat .jackdrc 
/usr/bin/jackd -R -m -dalsa -dhw:UA25 -r48000 -p256 -n3 -Xseq
```

So if you know the ALSA device name of the Zoom device you can use that in the Interface field in QjackCtl, see the attachment.

---

