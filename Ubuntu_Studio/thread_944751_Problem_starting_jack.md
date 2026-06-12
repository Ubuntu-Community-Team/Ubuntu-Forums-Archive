---
title: "Problem starting jack"
date: 2008-10-11
forum: Ubuntu Studio
---

### Post by Colci on 2008-10-11
23:05:15.370 Startup script...
23:05:15.371 artsshell -q terminate
23:05:15.790 Startup script terminated with exit status=256.
23:05:15.791 JACK is starting...
23:05:15.791 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -m
23:05:15.794 JACK was started with PID=7518.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
23:05:15.828 JACK was stopped successfully.
23:05:15.829 Post-shutdown script...
23:05:15.829 killall jackd
jackd: no process killed
23:05:16.236 Post-shutdown script terminated with exit status=256.
23:05:17.998 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


23:05:15.370 Startup script...
23:05:15.371 artsshell -q terminate
23:05:15.790 Startup script terminated with exit status=256.
23:05:15.791 JACK is starting...
23:05:15.791 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -m
23:05:15.794 JACK was started with PID=7518.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
23:05:15.828 JACK was stopped successfully.
23:05:15.829 Post-shutdown script...
23:05:15.829 killall jackd
jackd: no process killed
23:05:16.236 Post-shutdown script terminated with exit status=256.
23:05:17.998 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by eye208 on 2008-10-12
Enter these commands in a terminal window to get a list of playback and capture devices:```
aplay -l
arecord -l
```

---

### Post by EndOn9 on 2008-11-06
Hi guys, 

Have a very similar problem to the chap above:

20:42:25.775 Patchbay deactivated.
20:42:25.777 Statistics reset.
20:42:25.787 ALSA connection graph change.
20:42:25.988 ALSA connection change.
20:42:45.734 Startup script...
20:42:45.735 artsshell -q terminate
Creating link /home/endon9/.kde/socket-Shredder.
Created link from "/home/endon9/.kde/socket-Shredder" to "/tmp/ksocket-endon9"
20:42:46.148 Startup script terminated with exit status=256.
20:42:46.148 JACK is starting...
20:42:46.148 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
20:42:46.151 JACK was started with PID=14450.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
20:42:46.267 JACK was stopped successfully.
20:42:46.268 Post-shutdown script...
20:42:46.268 killall jackd
jackd: no process killed
20:42:46.691 Post-shutdown script terminated with exit status=256.
20:42:48.200 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


and:



endon9@Shredder:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
endon9@Shredder:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help would be awesome!

---

### Post by EndOn9 on 2008-11-11
*Bump*

Anyone?

---

### Post by mrhelpman on 2008-11-11
> **Colci said:**
> ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode

This looks like the cause. I think you have a USB sound card but I do not know the manufacturer.

Have a look [here]("http://www.alsa-project.org/main/index.php/Matrix:Main") and see if there are any known issues with your card.

Sorry I cannot be much more help.

JT

---

### Post by EndOn9 on 2008-11-18
Thanks for replying :) Think I might have to go buy a proper sound card

---

### Post by mrhelpman on 2008-11-20
> **EndOn9 said:**
> Thanks for replying :) Think I might have to go buy a proper sound card

Which sound card have you got at the moment? I can see it is a usb device.

John T

---

### Post by mysticofjesus on 2008-11-22
I have the same issue:


17:59:09.706 Patchbay deactivated.
17:59:10.053 Statistics reset.
17:59:10.202 ALSA connection graph change.
17:59:10.311 ALSA connection change.
17:59:11.700 Startup script...
17:59:11.703 artsshell -q terminate
17:59:12.149 Startup script terminated with exit status=256.
17:59:12.152 JACK is starting...
17:59:12.154 /usr/bin/jackd -R -P73 -u -dalsa -dhw:0 -r48000 -p256 -n2 -P -S
17:59:12.169 JACK was started with PID=5716.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|-|256|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
17:59:12.249 JACK was stopped successfully.
17:59:12.250 Post-shutdown script...
17:59:12.251 killall jackd
jackd: no process killed
17:59:12.663 Post-shutdown script terminated with exit status=256.
17:59:14.229 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.




It does the same thing with my integrated sound card and a usb Turtle Beach card, both of which used to work. The problem seemed to come up spontaneously.

---

### Post by raboofje on 2008-11-22
> **EndOn9 said:**
> 
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
**control open "hw:0" (No such file or directory)**
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card


It fails to open alsa card 0

> **EndOn9 said:**
> 
endon9@Shredder:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Indeed, you only have a 'card 1', no 'card 0'. Configure JACK to use hw:1 instead of hw:0.

---

### Post by raboofje on 2008-11-22
> **mysticofjesus said:**
> 
creating alsa driver ... hw:0|-|256|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card


Apparently it fails to open alsa card 0 for output. Does 'aplay -l' list the card?

---

### Post by mysticofjesus on 2008-11-23
Output of aplay -l with both the integrated and the usb sound cards activated:
```
**** List of PLAYBACK Hardware Devices ****
card 1: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Your suggestion worked beautifully. I changed the Interface field in Jack's setup to "hw:1,0", and it worked! Thank you very much, I appreciate it.

---

### Post by Raptor Ramjet on 2009-09-15
Hello,

I just also wanted to say thank you for this post as I too had the same problem so have just switched Jack over to use "hw 1,0" (in "setup" > "interface") and this has got my audio working again.

If it's of use to anyone my motherboard is an ASRock ALiveDual-eSATA2 and the onboard sound is detected as a USB audio device.  For further information the output of a few audio related commands is:

```

me@myhost: cat /proc/asound/cards/

 1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.1-4, full speed

me@myhost: ls -l /dev/snd/

total 0
crw-rw----+ 1 root audio 116, 6 2009-09-15 18:56 controlC1
crw-rw----+ 1 root audio 116, 5 2009-09-15 19:00 pcmC1D0c
crw-rw----+ 1 root audio 116, 4 2009-09-15 19:00 pcmC1D0p
crw-rw----+ 1 root audio 116, 3 2009-09-15 18:56 seq
crw-rw----+ 1 root audio 116, 2 2009-09-15 18:56 timer

me@myhost: aplay -l

**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

me@myhost: arecord - l

**** List of CAPTURE Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  

```

---

