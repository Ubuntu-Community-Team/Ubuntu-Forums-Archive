---
title: "Could not connect to JACK server as client"
date: 2009-11-24
forum: Ubuntu Studio
---

### Post by hakimoerton on 2009-11-24
Hello from a musical and command line noob running karmic with rt kernal on a PC with an ASUS P5KPL-CM mother board and Intel Pentium Dual-Core CPU     E5200 @ 2.50GHz and 2Gig of RAM. Sound is onboard HDA Intel.

I have been playing around for ages trying to get sound working and read days worth of advice. Sound is working for audio and video (Rhythbox and Mplayer).

Now I am trying to edit an audio file recorded on a Sony voice recorder which uses a proprietary format. Got this to save via line-in and Sound Recorder. Then tried Jokosher but it will not save the edited material. Looking at Jokosher's forum, there seems to be no current support.

After much reading, decided Ardour and Jack were the way to go but I can't get Jack to work properly, hence the above message title.
Message window shows:

19:35:50.621 Patchbay deactivated.
19:35:50.649 Statistics reset.
19:35:50.682 Startup script...
19:35:50.682 artsshell -q terminate
19:35:50.686 ALSA connection graph change.
sh: artsshell: not found
19:35:51.084 Startup script terminated with exit status=32512.
19:35:51.084 JACK is starting...
19:35:51.084 /usr/bin/jackd -R -dalsa -r44100 -p1024 -n2 -D -Chw:0 -Phw:1 -i1 -o1 -H -M
19:35:51.088 JACK was started with PID=2883.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:0|1024|2|44100|1|1|hwmon|hwmeter|-|32bit
control device hw:1
19:35:51.287 ALSA connection change.
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: cannot set channel count to 1 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
19:35:51.612 JACK was stopped successfully.
19:35:51.612 Post-shutdown script...
19:35:51.613 killall jackd
jackd: no process found
19:35:52.022 Post-shutdown script terminated with exit status=256.
19:35:53.294 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Aplay -l yeilds:

hakim@hakim-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x47f0xc001 [USB Device 0x47f:0xc001], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
hakim@hakim-desktop:~$ 

I had a look at the Jack site and have changed /etc/security/limits.conf as advised.

Any help would be appreciated.
Hakim

---

### Post by trulan on 2009-11-24
> **hakimoerton said:**
> 
19:35:51.084 JACK is starting...
19:35:51.084 /usr/bin/jackd -R -dalsa -r44100 -p1024 -n2 -D -Chw:0 -Phw:1 -i1 -o1 -H -M
...
ALSA: cannot set channel count to 1 for capture
ALSA: cannot configure capture channel
...

You have hw:0 selected for capture and hw:1 selected for playback (you are trying to record from one sound card and play back on another).  Since capture is throwing the error I would set it to hw:1 as well.

---

### Post by hakimoerton on 2009-11-24
Thanks Trulan,

Your suggestion didn't work but showed me where to look. hw1 wasn't an option for input in setup so I set them both to hw0 which did not work either. Next choice made was to set both to 'default' which gave a different error message, referring to number of input and output channels. I set these to 2 each instead of the existing 1 each and Jack now loads.

Hooray and thank you for assisting.

Output is now:

22:57:56.584 Patchbay deactivated.
22:57:56.591 Statistics reset.
22:57:56.674 Startup script...
22:57:56.675 artsshell -q terminate
22:57:56.677 ALSA connection graph change.
sh: artsshell: not found
22:57:57.076 Startup script terminated with exit status=32512.
22:57:57.076 JACK is starting...
22:57:57.076 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -i2 -o2 -H -M
22:57:57.080 JACK was started with PID=3497.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|2|2|hwmon|hwmeter|-|32bit
control device hw:0
22:57:57.278 ALSA connection change.
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
22:57:59.289 Server configuration saved to "/home/hakim/.jackdrc".
22:57:59.304 Statistics reset.
22:57:59.648 Client activated.
22:57:59.650 JACK connection change.
22:57:59.655 JACK connection graph change.

I am not quite sure what it all means. Yet ... :)
Again, thank you.:popcorn:
Hakim

---

