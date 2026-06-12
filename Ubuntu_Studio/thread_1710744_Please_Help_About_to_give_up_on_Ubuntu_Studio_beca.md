---
title: "Please Help: About to give up on Ubuntu Studio because of JACK"
date: 2011-03-20
forum: Ubuntu Studio
---

### Post by MValhala on 2011-03-20
Okay. I love Ubuntu and have been using it almost exclusively as an OS for about 2 years now. But when I want to do audio recording I boot to Windows and therefore miss out on all the great Ubuntu/linux audio & synth software out there. I really want to start using Ubuntu Studio and other programs like ZynAddSubFX - but I can't seem to get past my JACK problems. I've spent at least 2+ weeks and countless hours searching the forum/web for answers, trying different things, and I'm ready to give up on JACK/Ubuntu Studio all together. So I'm sending out one last cry for **HELP**! One last effort before I revert back to the world of windows. Can anyone of you Ubuntu/JACK gurus - with kindness in your heart - please help me solve my JACK problem? It's probably some simple fix that I can't figure out because I'm a noob. Please help me. I really don't want to give up on Ubuntu Studio/JACK.  

**Here's what I'm using:**
Ubuntu Studio 10.10
Low Latency Kernel from Alessio - ver. 2.6.38-7.35
JACK (jackd, qjackctl, etc.)
M-Audio Fast Track Pro - USB

**Here's the message I'm getting from the JACK Connection Kit:**
21:09:43.147 Patchbay deactivated.
21:09:43.225 Statistics reset.
21:09:43.442 Startup script...
21:09:43.443 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:09:43.503 ALSA connection graph change.
sh: artsshell: not found
21:09:43.868 Startup script terminated with exit status=32512.
21:09:43.869 JACK is starting...
21:09:43.870 /usr/bin/jackd -r -dalsa -r44100 -p32 -n2 -D -Chw:1 -Phw:1
21:09:43.888 JACK was started with PID=1694.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
21:09:44.076 ALSA connection change.
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|32|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 1 - M-Audio FastTrack Pro at usb-0000:00:03.2-1, full speed
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 44100Hz, period = 32 frames (0.7 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: cannot set period size to 32 frames for playback
ALSA: cannot configure playback channel
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
21:09:44.548 JACK was stopped with exit status=255.
21:09:44.549 Post-shutdown script...
21:09:44.549 killall jackd
jackd: no process found
21:09:44.967 Post-shutdown script terminated with exit status=256.
21:09:46.096 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:09:50.558 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:09:59.416 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:10:17.106 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:10:52.549 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:12:03.205 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:14:24.507 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:19:07.061 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:28:32.369 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:47:22.507 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
22:25:02.519 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
23:40:22.547 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
02:11:02.412 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
07:12:22.267 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by AutoStatic on 2011-03-20
Try Periods/Buffer setting of 3 and a higher Frames/Period setting. Afaik USB soundcards cannot go below 64 (limits of USB1.1) so JACK now chokes on that setting of 32.

Best,

Jeremy

---

### Post by MValhala on 2011-03-20
**_Thank you so very much AutoStatic._** Your suggestion seemed to work some magic. I feel like I'm now on the right track to possibly getting this all to work. Can you tell me what the following means? 

[I]Cannot connect to server socket err = No such file or directory
jack server is not running or cannot be started
[/I]
**and**

*ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode*

Here's the new message I'm getting:

15:50:21.527 Patchbay deactivated.
15:50:21.581 Statistics reset.
15:50:21.749 Startup script...
15:50:21.750 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
15:50:21.817 ALSA connection graph change.
sh: artsshell: not found
15:50:22.200 Startup script terminated with exit status=32512.
15:50:22.201 JACK is starting...
15:50:22.202 /usr/bin/jackd -dalsa -r44100 -p64 -n3 -D -Chw:1 -Phw:1
15:50:22.218 JACK was started with PID=1634.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
15:50:22.416 ALSA connection change.
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|64|3|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 1 - M-Audio FastTrack Pro at usb-0000:00:03.2-1, full speed
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 3 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
15:50:24.508 Server configuration saved to "/home/valhala/.jackdrc".
15:50:24.511 Statistics reset.
15:50:24.546 Client activated.
15:50:24.558 JACK connection change.
15:50:24.569 JACK connection graph change.
15:50:45.965 JACK connection graph change.
15:50:46.060 JACK connection change.
15:50:46.087 JACK connection graph change.
15:50:46.132 ALSA connection graph change.
15:50:46.405 ALSA connection change.


I really want to learn how to understand and work/tweak JACK. What do you suggest I read to get a better handle on the setup of JACK. Or is learning about JACK just a matter of continuing to read through the forums.

Thanks

---

### Post by sgx on 2011-03-20
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

check the links at this page, there are Dave Phillips articles
over the years on many linux audio topics. Search youtube for
ardour, hydrogen, rakarrack, and zynaddsubfx, as the videos
sometimes cover jackd connections, and qjackctl.

Cheers

---

### Post by MValhala on 2011-03-20
Thanks SGX for the info.

---

### Post by ailo.at on 2011-03-20
> **MValhala said:**
> Can you tell me what the following means? 

[I]Cannot connect to server socket err = No such file or directory
jack server is not running or cannot be started
[/I]
**and**

*ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode*
Thanks

Could be because of the mentioned limitations of usb 1.1 standard compliancy, that you are only getting access to outputs.
Try using "force 16 bit".

---

### Post by AutoStatic on 2011-03-21
> **MValhala said:**
> **_Thank you so very much AutoStatic._**You're welcome :)

> **MValhala said:**
> Can you tell me what the following means? 

[I]Cannot connect to server socket err = No such file or directory
jack server is not running or cannot be started
[/I]No idea, I don't use Jack2 (JACK 1.9.x) myself, I guess the message is related to that JACK implementation. But JACK starts now so I think it's kind of a bogus image.

> **MValhala said:**
> *ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode*The solution is already given by ailo.at, force the device to capture in 16-bit. If you want to capture in 24-bit you will probably need to build your own kernel with a specific patch, more info here: [http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462)
But I wouldn't advise building your won kernel right now. I have to check the newer version of ALSA, 1.0.24, if that version contains the patch. If so it's better to install the ALSA package from the KXStudio PPA. More on that later ;)

> **MValhala said:**
> I really want to learn how to understand and work/tweak JACK. What do you suggest I read to get a better handle on the setup of JACK.**man jackd** to begin with. Sounds weird but that man page already contains a lot of valuable information.
Some more info: [https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

Best,

Jeremy

---

### Post by MValhala on 2011-03-21
Thanks AutoStatic.  Yea I'll do as ailo.at suggests and force 16-bit.  I'm not doing anything right now that would require 24-bit. Maybe that will solve my input problems.  

Again - thanks to everyone who responded. I feel like I'm making progress and am almost to the point of being able to use some of the software. :)

---

