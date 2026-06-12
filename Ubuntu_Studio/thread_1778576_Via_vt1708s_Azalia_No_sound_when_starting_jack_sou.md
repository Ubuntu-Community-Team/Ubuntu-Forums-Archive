---
title: "Via vt1708s Azalia No sound when starting jack sound server."
date: 2011-06-09
forum: Ubuntu Studio
---

### Post by tt50 on 2011-06-09
Hi, I am very new to ubuntu, and have only just installed it for the very first time (ubuntu studio 11.04). After installing I was not able to get many of the audio programmes to work. After some reading, I realised that this was probably due to jack not starting. 

I was unable to get jack to start normally but have been able to get it started with the playback only option selected. Programmes that use jack now work, however there is no sound once jack has been started. The sound does work in other programs when jack is not started. Strangely, I only have to open qjackctl for the sound to stop, and jack is not even started. Initially I thought these problems were due to my sound card not being supported, but I believe that alsa support was added for the via 1708 codec at some point. I found that support had been added in a document showing the changes between alsa versions; however I cannot find the exact model listed as a supported sound card on the alsa site. 

I believe that altering jack settings could fix the problem, as i have been able to get audio to work in hydrogen by selecting plughw:0 but there is still no sound in other programs. I have tried altering many other settings but to no avail, however I do not really understand the meaning of the settings that i am adjusting. 

Does anyone know what settings to adjust or know something else that might fix this problem so that sound works once jack has been started? 

Also, would programmes that use jack such as audacity, hydrogen, and ardour work with pulseaudio as the main sound server if I were to install normal ubuntu - it might be worth seeing if my soundcard works with the puleaudio sound server 

if this helps, here is the error message received when jack does not start when the normal duplex option is selected.

21:24:04.867 Patchbay deactivated.
21:24:04.868 Statistics reset.
21:24:04.886 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:24:04.900 ALSA connection graph change.
21:24:06.469 JACK is starting...
21:24:06.470 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -S
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
21:24:06.517 JACK was started with PID=1552.
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe8f4000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
21:24:13.534 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
21:24:35.589 JACK is stopping...
jack main caught signal 15

_Here is the message with playback only when jack can be started_

21:26:35.540 Patchbay deactivated.
21:26:35.540 Statistics reset.
21:26:35.571 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:26:35.580 ALSA connection graph change.
21:26:36.366 JACK is starting...
21:26:36.367 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -S -P
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:26:36.402 JACK was started with PID=1576.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|1024|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe8f4000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
**** alsa_pcm: xrun of at least 0.040 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.071 msecs
**** alsa_pcm: xrun of at least 0.058 msecs
**** alsa_pcm: xrun of at least 0.061 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.059 msecs
**** alsa_pcm: xrun of at least 0.045 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.055 msecs
**** alsa_pcm: xrun of at least 0.056 msecs
**** alsa_pcm: xrun of at least 0.054 msecs
**** alsa_pcm: xrun of at least 0.052 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
21:26:38.457 JACK connection change.
21:26:38.458 Server configuration saved to "/home/fox/.jackdrc".
21:26:38.458 Statistics reset.
21:26:38.511 Client activated.
21:26:38.517 XRUN callback (1).
21:26:38.518 JACK connection graph change.
**** alsa_pcm: xrun of at least 0.074 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.063 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.060 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.052 msecs

_here is a list of my capture and playback devices_

fox@ubuntu:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
Subdevices: 1/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
fox@ubuntu:~$

and my alsa information is here
[[COLOR=#444444]http://www.alsa-project.org/db/?f=e7...5e43437980cf4f[/COLOR]]("http://www.alsa-project.org/db/?f=e7461ef8eb264da5cf3686abd95e43437980cf4f")


also, when i open alsamixer in the terminal for some reason the headphone part is greyed out, even when the sound is working before qjackctl is opened. 

Thanks

---

### Post by Pablo_F on 2011-06-09
> would programmes that use jack such as audacity, hydrogen, and ardour work with pulseaudio as the main sound server if I were to install normal ubuntu

No. Hydrogen and ardour depend on jack. Audacity can work with or without jack. This is so by upstream design, nothing to do with ubuntu or ubuntustudio (apart from the fact that ubuntustudio includes these programs in its DVD installer or ubuntustudio metapackages).

As you have noted, there are some programs that are jack clients by default while others are pulseaudio clientes by default. Some are smart enough to know what audio server is up and running and they just work. Some others are "jack only" (ardour for example). Some others are pulseaudio only ("system sounds"). Others can be "jackified" in a more or less easy way depending on the case... 

You can solve the problem by using the pulseaudio-module-jack. When you start jack via qjackctl a script is executed and pulseaudio redirects the audio streams to the jack sink.  You can follow the  instructions [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio%20and%20Jack"). Anyway, jack is not designed as a "desktop audio" server.


On the other hand, you should run jack in realtime mode. You need realtime and memlock privileges and you can gain them with these commands:

sudo dpkg-reconfigure -p high jackd2

Choose YES (TAB key). And then:

sudo adduser your_user_name audio

And then, reboot. 

Next time, enable the realtime option and put "pacmd load-module module-jack-sink channels=2" (I realy don't see the point of the pulseaudio jack-source) as the post-start script in Jack Control set up and options, respectively. 

HTH, Pablo

---

### Post by tt50 on 2011-06-09
Thanks for the reply. I think I understand now - pulseaudio sounds are suspended when jack is running.
The instructions you gave will be useful to me.  If I understand correctly it would allow me to use programmes that use either jack or pulseaudio at the same time. is this correct? 
 
The main problem though is that when jack is started, sounds don't work in any jack programmes like hydrogen and ardour. I have managed to get sound working in hydrogen alone by selecting plughw:0 but not any other.
 
I gave realtime privlages when i installed ubuntu studio, but just unchecked it in the jack setup options when I was adjusting settings trying to get things to work.
 
I believe that maybe adjusting the settings in a certain way could get the sound to work in jack programmes, although I dont understand what the settings mean. I have tried changing the interface settings to several different ones such as hw:0, hw:0,0 etc, but still couldn't get sound working in jack programmes.

---

### Post by tt50 on 2011-06-10
I now believe the problem is solved. With plughw:0 selected, I have found that other jack programmes do work with sound. The reason for me not realising this before was that I didn't understand how to use ardour properly, and the other programmes I tried used pulseaudio (such as sound recorder), which is suspended once jack has started. 
 
Thanks for all your help.

---

### Post by Pablo_F on 2011-06-10
You are welcome. 

There are a couple of apps that work fine as proofs of concept:

To test **jack playback**, **aqualung** is a nice audio player.

To test **jack capture**, jack **timemachine** is cool. It even captures the past.

Both are in the software center, so really, two clicks away, don't forget to check jack connections and you are almost there.

Cheers, Pablo

---

