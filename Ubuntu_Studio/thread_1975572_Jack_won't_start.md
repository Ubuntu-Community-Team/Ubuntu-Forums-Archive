---
title: "Jack won't start"
date: 2012-05-07
forum: Ubuntu Studio
---

### Post by aparaatti on 2012-05-07
Hi,

I have a m-audio transit. I just installed ubuntu studio 12.04. I installed madfu-load, ran lsusb, saw that

```
Bus 001 Device 008: ID 0763:2006 Midiman M-Audio Transit
```Launched qjackctl, selected the soundcard, set up my settings and pressed play:

Error dialog 1: 
D-BUS: JACK server could not be started.
 
Sorry

Error dialog 2:
Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.

]...and had a message waiting for me:
 ```
Mon May  7 22:16:51 2012: Starting jack server...
 Mon May  7 22:16:51 2012: JACK server starting in realtime mode with priority 10
 Mon May  7 22:16:51 2012: control device hw:1
 Mon May  7 22:16:51 2012: control device hw:1
 Mon May  7 22:16:51 2012: Acquired audio card Audio1
 Mon May  7 22:16:51 2012: creating alsa driver ... hw:1|hw:1|512|3|96000|0|0|nomon|swmeter|-|32bit
 Mon May  7 22:16:51 2012: control device hw:1
 Mon May  7 22:16:51 2012: configuring for 96000Hz, period = 512 frames (5.3 ms), buffer = 3 periods
 Mon May  7 22:16:51 2012: ALSA: final selected sample format for capture: 24bit little-endian
 Mon May  7 22:16:51 2012: ALSA: use 3 periods for capture
 Mon May  7 22:16:51 2012: ALSA: final selected sample format for playback: 24bit little-endian
 Mon May  7 22:16:51 2012: ALSA: use 3 periods for playback
 Mon May  7 22:16:51 2012: port created: Midi-Through:midi/playback_1
 Mon May  7 22:16:51 2012: port created: Midi-Through:midi/capture_1
 Mon May  7 22:16:51 2012: [1m[31mERROR: ALSA: could not start playback (Broken pipe)[0m
 Mon May  7 22:16:51 2012: [1m[31mERROR: Cannot start driver[0m
 Mon May  7 22:16:51 2012: [1m[31mERROR: JackServer::Start() failed with -1[0m
 Mon May  7 22:16:51 2012: [1m[31mERROR: Failed to start server[0m
 Mon May  7 22:16:51 2012: port deleted: Midi-Through:midi/playback_1
 Mon May  7 22:16:51 2012: port deleted: Midi-Through:midi/capture_1
 Mon May  7 22:16:51 2012: control device hw:1
 Mon May  7 22:16:51 2012: Released audio card Audio1
 Mon May  7 22:16:51 2012: control device hw:1
 Mon May  7 22:16:52 2012: Saving settings to "/home/aparaatti/.config/jack/conf.xml" ...
 22:17:20.371 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```What is it? I don't want to go through the internet....

I'm on 64bit...

---

### Post by aparaatti on 2012-05-08
so.... it's not something trivial? anyone?

---

### Post by aparaatti on 2012-05-08
Ok, I just now realized to test the laptops own sound card, and for it jack works fine... I also have the transient running fine on arch linux with same settings, so it should work. To be blunt I'm quite disappointed on the welcome the distro gave me, it's the same kind of things I bumped to few years before when I was using ubuntu studio. I was thinking that by now everything should just work, but it's still the same route to take. No working jack out of the box in an audio distro?

On arch it's ok to pumb into these kind of problems, since you always have a great information resource (eg. the wiki), so I would say that this is harder to troubleshoot than arch. 

On the other hand the new menu organization is nice and I really like the blue theme plus xfce is a nice choice.

I also tried to get to the #ubuntustudio irc on freenode, but that failed on xchat not havin SASL (??) support out of the box. I googled and I should install some perl script to the .xchat2 folder and to do other things for it (which I'll spent time on next).. Irssi complains on the same thing.... phew... Really ubuntu, I can't get to freenode out of the box? But anyway this seems a nice set up anyway, just wanted to have my say...

peace :arrow: goes to check if there is a web service for freenode

---

### Post by Sylos on 2012-05-08
Hello there.

Just a thought - but your jack output seems to suggest that your running 24 bit with the alsa driver. If I understand it correctly this device is USB 1.1 so probably doesnt support 24 bit. Try using the force 16 bit option in jack settings and see if that has any effect.

Also maybe try dropping down to 48khz sample rate as well.

Cheers

---

### Post by shimoda on 2012-05-09
In my case I always had problems with multiple sound cards configuration... I don't remember well, but I think that my solution was to set default Alsa Card 0 the one I want to use...

---

### Post by aparaatti on 2012-05-21
Dropping the sample rate and forcing 16bit made it run :confused:, though the audio-card is 32bit and 96000kHz. I haven't checked the udev-load rules ([http://linuxaudiolive.wordpress.com/2012/05/04/m-audio-transit-on-ubuntu-12-04/](http://linuxaudiolive.wordpress.com/2012/05/04/m-audio-transit-on-ubuntu-12-04/)), which I'll check at some point.. thanks for your answers.

By the way, should it run better if I force 16bit although it is capable of 24bit?

---

### Post by Stuz719 on 2012-05-21
Not sure it's solved for me... upgraded to 12.04 and trying to use din (din is noise) and my A3850 machine resolutely refuses to start jack.

very frustrating!

---

### Post by Sylos on 2012-05-22
> **aparaatti said:**
> Dropping the sample rate and forcing 16bit made it run :confused:, though the audio-card is 32bit and 96000kHz. I haven't checked the udev-load rules ([http://linuxaudiolive.wordpress.com/2012/05/04/m-audio-transit-on-ubuntu-12-04/](http://linuxaudiolive.wordpress.com/2012/05/04/m-audio-transit-on-ubuntu-12-04/)), which I'll check at some point.. thanks for your answers.

By the way, should it run better if I force 16bit although it is capable of 24bit?

Hello again.

Glad you had some success.

When I replied to you I googled around your issue and found something that said the windows driver for the cards does some clever trickery to get the 24 bit performance out of it. If what I read is correct the alsa driver doesnt know what to do with it in 24 bit mode so it doesnt work. Forcing 16 bit then allows the alsa driver to work.

Thats just what I read elsewhere so I cant verify its accuracy.

Maybe check the alsa compatability list and the latest driver to see if support has emerged yet for the 24bit.

Cheers


EDIT: Heres the excerpt I read:
 "I've also discovered why you are unable to play 24-bit with the device. The limitation is not in ALSA but is with the Transit itself. Since it's a USB 1.1 device it does not have enough bandwidth to reliably send a 96/24 stream in and out at the same time. M-Audio has worked around this by having several operating modes selectable in the Windows Drivers. When the firmware first loads, it defaults to the 16-bit 8000-48000hz mode, which gives you recording and playback. ALSA does not know (or probably care) how to change this, however, as a result you cannot support more than 48khz 16-bit on this under Linux."

From

[http://www.howtoforge.com/how-to-get-the-m-audio-transit-usb-audio-device-working-in-ubuntu-9.04-amd64](http://www.howtoforge.com/how-to-get-the-m-audio-transit-usb-audio-device-working-in-ubuntu-9.04-amd64)

---

### Post by Sylos on 2012-05-22
> **Stuz719 said:**
> Not sure it's solved for me... upgraded to 12.04 and trying to use din (din is noise) and my A3850 machine resolutely refuses to start jack.

very frustrating!

Hello there.

Can you give us the output from your jack message window when trying to start it?

Cheers

---

### Post by Stuz719 on 2012-05-22
> **Sylos said:**
> Hello there.

Can you give us the output from your jack message window when trying to start it?

Cheers

Yep...

> <<< using data files in /home/stuart/.din/ >>>
<<< loading globals, done >>>
<< loading audio prefs from: /home/stuart/.din/jack_prefs, done. >>>
*** connecting to JACK server ***
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
JACK server starting in realtime mode with priority 10
Cannot lock down 82241434 byte memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
JackTemporaryException : now quits...
Cannot initialize driver
JackServer::Open() failed with -1
Failed to open server
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
!!! couldnt connect to JACK server. !!!
!!! din shutdown !!!


Even tried a sudo-apt get jack, and that didn't solve it.

Qjackctl says:

[QUOTE]  p, li { white-space: pre-wrap; }  [COLOR=#999999]18:00:32.417 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:00:32.444 Statistics reset.[/COLOR]
 [COLOR=#cccc99]18:00:32.497 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:00:32.704 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#ff0000]18:00:32.794 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]18:00:32.899 ALSA connection graph change.[/COLOR]
 Tue May 22 18:00:32 2012: Starting jack server...
 Tue May 22 18:00:32 2012: JACK server starting in realtime mode with priority 10
 Tue May 22 18:00:32 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
 Tue May 22 18:00:32 2012: control device hw:0
 Tue May 22 18:00:32 2012: control device hw:0
 Tue May 22 18:00:32 2012: Acquired audio card Audio0
 Tue May 22 18:00:32 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Tue May 22 18:00:32 2012: control device hw:0
 Tue May 22 18:00:32 2012: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
 Tue May 22 18:00:32 2012: [1m[31mERROR: Cannot initialize driver[0m
 Tue May 22 18:00:32 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Tue May 22 18:00:32 2012: [1m[31mERROR: Failed to open server[0m
 Tue May 22 18:00:34 2012: Saving settings to "/home/stuart/.config/jack/conf.xml" ...
 [COLOR=#ff0000]18:00:44.563 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#ff0000]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#ff0000]Cannot connect to server socket[/COLOR]
 [COLOR=#FF0000]jack server is not running or cannot be started[/COLOR]
[COLOR=#ff0000][/QUOTE}
[/COLOR]

---

### Post by Sylos on 2012-05-22
Could you also give the output of:


cat /proc/asound/cards
aplay-l
arecord -l

Cheers

---

### Post by Stuz719 on 2012-05-25
> **Sylos said:**
> Could you also give the output of:


cat /proc/asound/cards
aplay-l
arecord -l

Cheers

>  0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 53
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb40000 irq 16

AND

> **** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

AND

> **** List of CAPTURE Hardware Devices ****
card 1: Generic_1 [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 2: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Hope this helps!

---

### Post by Sylos on 2012-05-26
Hello again.

I may be barking up the wrong tree here but at first glance I am wondering if the issue could be that alsa is trying to use your HDMI output as the primary card (it shows as card:0 in aplay -l but doesnt show in cat/proc/asound/cards).

I'll do some research when I get a little more time and then come back here.

Cheers

EDIT: just re-reading your errors and had a thought: Have you added your user to the audio group? Might be why you get the message "Cannot create thread 1 Operation not permitted".

---

### Post by Stuz719 on 2012-05-27
Yep... added to audio group. BTW I am showing as "Custom" user type?

Maybe I will just have to save up and join the 21st Century with an HDMI monitor.

Curiously pavucontrol only offers me the HDMI output option but when using the Sound setting the test works fine. Seriously toying with reversion to 11.04 now :-/

---

### Post by Sylos on 2012-05-29
This seems far too simple to be a solution - but its worth a shot.

It seems jack is trying to open hw:0 - which is not the card we want. What you want (if I understand correctly) should be labled as hw:1,0 (the first device of the second card). See if you can change this is in qjackctl. Failing that you could issue a custom command to launch jack in the terminal. Possibly the best way would be to check you .jackrc file in your home folder. I think that holds the command that it uses. Copy it them modify it with the correct card identifier.


Cheers

---

### Post by Stuz719 on 2012-06-05
Hi, tried selecting hw1,0 in qjackctl and it's still not playing ball.  It's a pain, but the workaround I'm going to try is via some BIOS settings (if there are any) to force a sound option, and failing that I've ordered a PCI soundcard to use that instead.

We'll see - I don't get to go on my desktop machine too much at the mo', so can live with it for a while, hoping that some updates will fix it idc...

Cheers for all the help!

---

### Post by Stuz719 on 2012-06-09
> **Sylos said:**
> This seems far too simple to be a solution - but its worth a shot.

It seems jack is trying to open hw:0 - which is not the card we want. What you want (if I understand correctly) should be labled as hw:1,0 (the first device of the second card). See if you can change this is in qjackctl. Failing that you could issue a custom command to launch jack in the terminal. Possibly the best way would be to check you .jackrc file in your home folder. I think that holds the command that it uses. Copy it them modify it with the correct card identifier.


Cheers
Success!

Respect is most assuredly due and given to Sylos.

Bizarrely selecting hw:1,0 in qjackctl now appears to do the job and din starts with nary an error message in sight.  I'm happy to take a solution that works over something more elegant that doesn't, tbh, so I'm not going to delve into the whys and wherefores.

I'm just pleased I can now make electronic noise and record it in Audacity to my heart's content!

Cheers again Sylos!

---

### Post by Sylos on 2012-06-10
> **Stuz719 said:**
> Success!

Respect is most assuredly due and given to Sylos.

Bizarrely selecting hw:1,0 in qjackctl now appears to do the job and din starts with nary an error message in sight.  I'm happy to take a solution that works over something more elegant that doesn't, tbh, so I'm not going to delve into the whys and wherefores.

I'm just pleased I can now make electronic noise and record it in Audacity to my heart's content!

Cheers again Sylos!


Glad to be of assistance. Happy music making my friend.

:guitar::guitar:

---

