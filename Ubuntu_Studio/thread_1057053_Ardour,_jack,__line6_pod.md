---
title: "Ardour, jack,  line6 pod"
date: 2009-02-01
forum: Ubuntu Studio
---

### Post by tjodSK on 2009-02-01
Hello there.

I just purchased line6 pod xt, this one features an USB connector. When connected to pc, it should be recognized as sound card.

What i've done so far.

acquired line6 pod xt driver from [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/), built and installed correctly.

I stard ardour, everything works nicely, i can see that i'm recording audio, i see the waveform in ardour's workbench, but, i can't hear anything. If i export ardour's project, it's OK. Just monitoring does not work.

i suspect, that it's problem with JACK, which uses pod xt for input AND output, and, it should use it for input, output should be wired to standard soundcard.

when i tried to select it that way (in qjackctl * setup-> outputdevice:hw0 - this is intel HDA, and inputdevide:hw:1 - line6 pod) my pc freezes.

Thanks for any advices.

btw, i'm running ubuntu 8.10 with installed ubuntu studio afterwards (with apt-get).

thank you!

---

### Post by neu2buntu on 2009-02-01
is qjackctl set for duplex mode in >setup >Audio?

---

### Post by tjodSK on 2009-02-01
thx for reply, yes, it is.

I did quick test, tried output/input, both to HW:1 -> records fine, no sound (only after export from ardour), both to hw:0 -> does not crash.

input to hw:1 and output hw:0, qjackctl freezes.

---

### Post by tjodSK on 2009-02-01
actually, whole PC freezes, so i have to restart.

---

### Post by neu2buntu on 2009-02-01
i think u may have to change the driver from alsa in qjackctl to use the usb soundcard, or maybe its a matter of changing some settings in /etc/modprobe.d/alsa-base file .copy and paste this file in reply

---

### Post by tjodSK on 2009-02-01
here is it:

```
:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

```

thank you very much!

---

### Post by neu2buntu on 2009-02-01
and also output of ```
aplay-l 
``` and ```
arecord-l
``` with your usb soundcard plugged in. and also the make and model of your comp...

---

### Post by tjodSK on 2009-02-01
actually i figured out that i was not running -rt kernel and added those lines to security.conf. Now, qjackctl does not freeze!

But, in messages window:
```
00:35:13.762 Patchbay deactivated.
00:35:13.766 Statistics reset.
00:35:27.930 Startup script...
00:35:27.931 artsshell -q terminate
00:35:28.536 Startup script terminated with exit status=256.
00:35:28.536 JACK is starting...
00:35:28.536 /usr/bin/jackd -dalsa -r44100 -p1024 -n3 -D -Chw:1 -Phw:0 -zr
00:35:28.539 JACK was started with PID=6557.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:1|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: got smaller periods 2 than 3 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
00:35:28.707 JACK was stopped successfully.
00:35:28.707 Post-shutdown script...
00:35:28.708 killall jackd
jackd: no process killed
00:35:29.119 Post-shutdown script terminated with exit status=256.
00:35:30.543 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by tjodSK on 2009-02-01
Disregard my latest post, i forgot to build line6usb module.

here is the output:

```
martinko@PC-Jacalam:~/install/line6usb$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Line6USB [Line6-USB], device 0: PODxt [PODxt]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
martinko@PC-Jacalam:~/install/line6usb$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Line6USB [Line6-USB], device 0: PODxt [PODxt]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
martinko@PC-Jacalam:~/install/line6usb$
```

My comp is custom built,

Intel core2 quad e6600, asus motherboard, 4gig ram. The chipset is intel, i think G965

---

### Post by neu2buntu on 2009-02-01
im no expert here, but it looks like your internal soundcard is grabbing index 0 ,i,e it is the primary soundcard, and i think u will need the external soundcard to be the primary card for this setup to work, make a note of any changes you do here so they can be changed back if it fails.... open the alsa-base file as sudo and change the line 
options snd-usb-audio index=-2 to 
options snd-usb-audio index=0  ,then save and restart and hopefully this will give the usb card top priority

---

### Post by neu2buntu on 2009-02-01
put nmy last post on hold to u build your usbmod

---

### Post by tjodSK on 2009-02-01
I tried it now, no freeze, this is in qjackctl log 

```
00:54:24.983 Startup script...
00:54:24.983 artsshell -q terminate
00:54:25.394 Startup script terminated with exit status=256.
00:54:25.394 JACK is starting...
00:54:25.394 /usr/bin/jackd -dalsa -r44100 -p1024 -n3 -D -Chw:1 -Phw:0,0 -zr
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
00:54:25.410 JACK was started with PID=12141.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:1|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: got smaller periods 2 than 3 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
00:54:25.486 JACK was stopped successfully.
00:54:25.486 Post-shutdown script...
00:54:25.486 killall jackd
jackd: no process killed
00:54:25.892 Post-shutdown script terminated with exit status=256.
00:54:27.450 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

The problem is i need just INPUT from that "soundcard" as long that card has no usable "outputs", it's just box for recording.

---

### Post by neu2buntu on 2009-02-01
i take it u added the @audio rtprio,memlock ,nice values to security/limits.conf and added urself to the audio group from ur earlier post? how r u getting on now with jack?

---

### Post by neu2buntu on 2009-02-01
just noticed u dont have realtime box ticked in qjackctl from your log 
00:54:25.394 /usr/bin/jackd -dalsa -r44100 -p1024 -n3 -D -Chw:1 -Phw:0,0 -zr
check this box in qjackctl stop and restart it to see what happens

heres  1 we may have overlooked open >preferences .sound and see if all sound playback is -alsa and sound recording can be turned to external card, and i think device should be hda intel(alsa mixer)  

im not really sure if this here will make a difference , but try H/W Monitor (enable hardware monitoring of capture ports) in qjackctl

---

### Post by tjodSK on 2009-02-02
to #13, yes, i did exactly this thing. Straight after i reboot, and tried jack, and that is the output you can see.


I saw this in log:
ALSA: got smaller periods 2 than 3 for playback

so i tried to increase the Periods in qjackctl from "2" to "3", and after i clicked connect, my PC froze again.

---

### Post by tjodSK on 2009-02-02
> **neu2buntu said:**
> 
im not really sure if this here will make a difference , but try H/W Monitor (enable hardware monitoring of capture ports) in qjackctl

i tried this, no difference.

i think it's somewhat related to the "period" thing, i guess..


I will try to get a screenshot of the qjackctl settings later today..

---

### Post by tjodSK on 2009-02-02
Nevermind, i figured it out!! 

Actually, i was just a bit stupid:D Tried this today:

Started the JACKD with in and out bound to hw1 (line6 pod), started ardour.
Actually, i plugged in headphones into the phones jack of line6, and i thought i will hear the signal from the effect (the signal being recorded), actually, i heard signal coming from ardour via jack. I double checked this, i bound rosegarden into the loop, and voila, i heard drums right of the lin6 box!!

Thank you for the support!

---

