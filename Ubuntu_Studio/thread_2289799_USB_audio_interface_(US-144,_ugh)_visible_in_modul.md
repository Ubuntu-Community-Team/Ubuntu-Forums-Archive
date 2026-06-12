---
title: "USB audio interface (US-144, ugh) visible in modules but not aplay"
date: 2015-08-07
forum: Ubuntu Studio
---

### Post by rpickle on 2015-08-07
Hi- been some years since I posted here but I am completely stumped on this one. 

Made the minor mistake of buying a tascam US-144 to use for linux. Finally figured out that it needs to be ran on a USB 1.1 port, which I managed by running an old 1.1 hub between my laptop and the device. Pretty frustrating. 

But now it's visible at least.  

$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l

However, the second check, not so much

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD93BXX Analog [92HD93BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I do not have a .asoundrc file. I've tried goofing with that file (usually with info from posts dating back to 2009) with no results and at this point think it's probably best it doesn't exist? The device is not visible in the pulseaudio sound preferences speaker icon nor in pavucontrol. it is visible via alsamixer but not alsamixergui. 

The device is there in qjackctl but I can't get it to start. D-bus error. 

 Fri Aug  7 18:58:10 2015: Starting jack server...
 Fri Aug  7 18:58:10 2015: JACK server starting in realtime mode with priority 10
 Fri Aug  7 18:58:10 2015: self-connect-mode is "Don't restrict self connect requests"
 Fri Aug  7 18:58:10 2015: Acquired audio card Audio1
 Fri Aug  7 18:58:10 2015: creating alsa driver ... hw:US122L|hw:US122L|256|3|44100|2|2|nomon|swmeter|-|32bit
 Fri Aug  7 18:58:10 2015: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Fri Aug  7 18:58:10 2015: ERROR: Cannot initialize driver
 Fri Aug  7 18:58:10 2015: ERROR: JackServer::Open failed with -1
 Fri Aug  7 18:58:10 2015: ERROR: Failed to open server

That looks like a big clue but I'm way too dumb. Where is "alsa_pcm" being referenced?

by the way I'm using ubuntu MATE 1.8.2 with updated everything on a dell latitude E6530

finally, here's my alsa-info.sh output:

[http://www.alsa-project.org/db/?f=7dae0f5d8776f9f697d455972dd1b92814283ad4](http://www.alsa-project.org/db/?f=7dae0f5d8776f9f697d455972dd1b92814283ad4)


Thanks in advance!

---

### Post by rpickle on 2015-08-10
update- i sold this piece of crap and bought another interface from a company who respects its linux users (native instruments). 

will not be purchasing any further tascam products.

---

