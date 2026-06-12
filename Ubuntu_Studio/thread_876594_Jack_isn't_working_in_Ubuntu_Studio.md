---
title: "Jack isn't working in Ubuntu Studio"
date: 2008-07-31
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-07-31
Hello all, 

Jack is screwing up big time on my new Ubuntu Studio install.  I installed directly from the DVD.

This is the message window in jack when I start it up:

22:47:22.025 Patchbay deactivated.
22:47:22.155 Statistics reset.
22:47:22.251 ALSA connection graph change.
22:47:22.365 ALSA connection change.
22:47:24.910 Startup script...
22:47:24.912 artsshell -q terminate
22:47:25.340 Startup script terminated with exit status=256.
22:47:25.341 JACK is starting...
22:47:25.341 /usr/bin/jackd -R -P1 -dalsa -dhw:0 -r48000 -p1024 -n2 -P
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
22:47:25.356 JACK was started with PID=16268.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|-|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
22:47:25.387 JACK was stopped successfully.
22:47:25.388 Post-shutdown script...
22:47:25.388 killall jackd
jackd: no process killed
22:47:25.797 Post-shutdown script terminated with exit status=256.
22:47:27.384 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info

It says that hw:0 is in use, but I have NOTHING running.

This problem started happening when I tried to get Qsynth to work.  For some reason with the Sound Blaster Live cards I am stuck with a 48k sample rate and adjusting within Jack has no effect (the display stays on 48k).

Another thing is that Jack had a problem with the device setting set to "duplex" as it turned out I did get Jack to turn on via "playback only"

I have a Dell machine with the OEM Dell Sound Blaster Live on board.  I thought that this card was supposed to be Linux compliant.  But I am finding out that I could do more with Jack with my Sound Blaster X-Fi than this card.

At any rate I am wondering if this is a sound card issue or not.

Thanx,

Geo

---

### Post by eye208 on 2008-07-31
> **jukingeo said:**
> It says that hw:0 is in use, but I have NOTHING running.
I guess hw:0 is occupied by PulseAudio.

Removing PulseAudio is simple:

[LIST=1]
[*]Disable Gnome system sounds. (important)
[*]Remove "pulseaudio" and "pulseaudio-esound-compat". Optionally install "esound" for applications that need it.
[*]Reboot.
[/LIST]

---

### Post by mountain_goat on 2008-08-01
Geo,
looking at your jack file and in particular
> 22:47:25.356 JACK was started with PID=16268.I am guessing you are starting jack via another application, Qsynth I think you mentioned?
If so, check that that application is not wanting to your SB card in it's preferences.
Kill all apps and try just with jack by itself first.

Try setting in jack the input and output device to default instead of hw:0
Mine is set to hw:0

Actually, here is my listing
> 00:07:21.270 JACK is starting...
00:07:21.270 /usr/bin/jackd -R -p128 -t1000 -dalsa -r96000 -p128 -n2 -D -Chw:0 -Phw:0 -S
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
SSE2 detected
apparent rate = 96000
creating alsa driver ... hw:0|hw:0|128|2|96000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 96000Hz, period = 128 frames (1.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit big-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit big-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
00:07:21.297 JACK was started with PID=7334.
**** alsa_pcm: xrun of at least 0.011 msecs
**** alsa_pcm: xrun of at least 0.019 msecs
**** alsa_pcm: xrun of at least 0.005 msecs
**** alsa_pcm: xrun of at least 0.005 msecs
**** alsa_pcm: xrun of at least 0.006 msecs
**** alsa_pcm: xrun of at least 0.014 msecs
00:07:22.117 JACK is stopping...
[IMG]http://ubuntuforums.org/Screenshot-Setup%20-%20JACK%20Audio%20Connection%20Kit.png[/IMG]I'm curious with what eye is saying as I have not disabled my gnome system sounds and all seems fine. Jack starts. The only thing it has trouble with is to lock memory, same as for you too I see.

But yes, something has grabbed your sound card.

May be ok to put your X-Fi card back in, that is if you still have it??

Hope you will have a productive day Geo ;)

mountain goat ~ always walking on the bright side of life

---

### Post by jukingeo on 2008-08-01
> **mountain_goat said:**
> Geo,
looking at your jack file and in particular
I am guessing you are starting jack via another application, Qsynth I think you mentioned?
If so, check that that application is not wanting to your SB card in it's preferences.
Kill all apps and try just with jack by itself first.

Try setting in jack the input and output device to default instead of hw:0
Mine is set to hw:0

Actually, here is my listing
[IMG]http://ubuntuforums.org/Screenshot-Setup%20-%20JACK%20Audio%20Connection%20Kit.png[/IMG]I'm curious with what eye is saying as I have not disabled my gnome system sounds and all seems fine. Jack starts. The only thing it has trouble with is to lock memory, same as for you too I see.

But yes, something has grabbed your sound card.

May be ok to put your X-Fi card back in, that is if you still have it??

Hope you will have a productive day Geo ;)

mountain goat ~ always walking on the bright side of life



Hello M-G,

Nice of you to drop by :).

Anyway, this morning I went into preferences, and shut off the sound mixer and the system sounds.

This is what I got with just Jack started up alone:

13:26:25.238 Patchbay deactivated.
13:26:25.309 Statistics reset.
13:26:25.455 ALSA connection graph change.
13:26:25.572 ALSA connection change.
13:26:27.614 Startup script...
13:26:27.614 artsshell -q terminate
13:26:28.043 Startup script terminated with exit status=256.
13:26:28.044 JACK is starting...
13:26:28.045 /usr/bin/jackd -R -P1 -dalsa -dhw:0 -r48000 -p1024 -n2 -P
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
13:26:28.070 JACK was started with PID=6054.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|-|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
13:26:30.183 Server configuration saved to "/home/geo/.jackdrc".
13:26:30.185 Statistics reset.
13:26:30.187 Client activated.
13:26:30.189 JACK connection change.
13:26:30.212 JACK connection graph change.
cannot lock down memory for RT thread (Cannot allocate memory)
cannot use real-time scheduling (FIFO at priority 0) [for thread -1239995504, from thread -1239995504] (22: Invalid argument


I opened up Ardour and it seems to be holding, but I didn't run anything through it because I am seeing error messages there.

I have a funny feeling that the OEM DELL Soundblaster Live is NOT as fully Linux compliant as I thought.

As to your question about the X-Fi, I can't put that back in because it only works with Ubuntu.  I have other sound applications that I am using as well (outside of Windows).  I have also Puppy Linux on board (and on a USB for portability).  I also have been experimenting with another OS called Dynebolic.  So I need sound in EVERYTHING.

At any rate, I do have the Echo Mona coming in the mail and hopefully I will get it by next week.  Then I can pull the Sound Blaster Live out, put the Mona in and hopefully I don't have to worry about sound again for a VERY long time.

I really don't know what happened between yesterday and today with Jack, but I think it COULD be because I was using YouTube yesterday.  I did shut it down completely, but I think something may have gotten 'stuck'.  This morning I just went in and shut off the system sounds and Jack seems to be acting 'better' but I still don't like all those error messages.

Let me know what you think.

Geo

---

### Post by jukingeo on 2008-08-01
> **eye208 said:**
> I guess hw:0 is occupied by PulseAudio.

Removing PulseAudio is simple:

[LIST=1]
[*]Disable Gnome system sounds. (important)
[*]Remove "pulseaudio" and "pulseaudio-esound-compat". Optionally install "esound" for applications that need it.
[*]Reboot.
[/LIST]


Hello,

I am pretty new to Linux, so you will have to walk me through on doing bullets two and three above (I already know how to disable the system sounds and did that already).

However, before I do anything, I would like to know what it is I am doing here.  I have sound for my internet, mp3 files and games and the sound for those items MUST remain intact.  I can deal without system gui sounds, but all those items I need sound with in addition to having Jack work properly.

Thanx,

Geo

---

### Post by eye208 on 2008-08-02
> **jukingeo said:**
> I am pretty new to Linux, so you will have to walk me through on doing bullets two and three above (I already know how to disable the system sounds and did that already).
[list=1][*]**Disable Gnome system sounds**

Open the sound configuration panel (System > Preferences > Sound). On the "Devices" tab set all entries to "ALSA". On the "Sounds" tab uncheck "Play system sounds". Leave "Enable software sound mixing (ESD)" checked.


[*]**Remove "pulseaudio", install "esound"**

Open a terminal window (Applications > Accessories > Terminal) and enter these commands:
```
sudo apt-get remove pulseaudio
sudo apt-get install esound
```
You can undo these changes later simply by entering:
```
sudo apt-get install ubuntu-desktop
```


[*]**Reboot**

Click the red power button in the upper right corner (or choose System > Quit from the menu), then click "Restart".[/list]
> However, before I do anything, I would like to know what it is I am doing here.  I have sound for my internet, mp3 files and games and the sound for those items MUST remain intact.  I can deal without system gui sounds, but all those items I need sound with in addition to having Jack work properly.
This change will remove the PulseAudio server from the system. Afterwards all applications will either talk to ALSA directly or use ESD or the OSS compatibility layer provided by ALSA. This was Ubuntu's default setup until PulseAudio was introduced. I have successfully tested this configuration in Hardy (8.04.1) with the following applications: Totem, VLC, MPlayer, Audacity, Blender 2.46, Skype, Second Life (including voice chat), the Flash plugin, and Jack.

---

### Post by DMurray on 2008-08-02
Try installing "qjackctl", which is a QT frontend for Jackd.
You can click the options, start and stop jackd and check the message window.
I don't know why it says it can't allocate memory... just for the sake of testing, did you try to start jack as root?

---

### Post by jukingeo on 2008-08-02
> **eye208 said:**
> [list=1][*]**Disable Gnome system sounds**

Open the sound configuration panel (System > Preferences > Sound). On the "Devices" tab set all entries to "ALSA". On the "Sounds" tab uncheck "Play system sounds". Leave "Enable software sound mixing (ESD)" checked.


[*]**Remove "pulseaudio", install "esound"**

Open a terminal window (Applications > Accessories > Terminal) and enter these commands:
```
sudo apt-get remove pulseaudio
sudo apt-get install esound
```
You can undo these changes later simply by entering:
```
sudo apt-get install ubuntu-desktop
```


[*]**Reboot**

Click the red power button in the upper right corner (or choose System > Quit from the menu), then click "Restart".[/list]

This change will remove the PulseAudio server from the system. Afterwards all applications will either talk to ALSA directly or use ESD or the OSS compatibility layer provided by ALSA. This was Ubuntu's default setup until PulseAudio was introduced. I have successfully tested this configuration in Hardy (8.04.1) with the following applications: Totem, VLC, MPlayer, Audacity, Blender 2.46, Skype, Second Life (including voice chat), the Flash plugin, and Jack.




It didn't work...

Jack still is complaining that the audio card is being used.  However, the system sounds are off and I went straight into jack without opening anything else.

These are the results:

13:54:48.911 Patchbay deactivated.
13:54:48.976 Statistics reset.
13:54:49.103 ALSA connection graph change.
13:54:49.211 ALSA connection change.
13:54:50.455 Startup script...
13:54:50.456 artsshell -q terminate
13:54:50.886 Startup script terminated with exit status=256.
13:54:50.887 JACK is starting...
13:54:50.888 /usr/bin/jackd -R -P1 -dalsa -dhw:0 -r48000 -p1024 -n2 -P
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
13:54:50.921 JACK was started with PID=5744.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|-|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
13:54:50.965 JACK was stopped successfully.
13:54:50.965 Post-shutdown script...
13:54:50.966 killall jackd
jackd: no process killed
13:54:51.375 Post-shutdown script terminated with exit status=256.
13:54:53.018 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


Now what I don't get is that in Windows you CAN have more than one thing piping through the sound card at one time.  The signal is mixed.  How come Ubuntu can't do that?

Also, how come everything else is working fine?  I have good quality sound on games (both emulated and Linux native), the internet, my mp3 player and generally most ALSA direct applications do work as well (such as Mixxx).  However, it seems that Jack is the only thing that doesn't want to cooperate.

Supposedly the Sound Blaster Live I have in my machine is supposed to be fully Linux compliant, yet I cannot have it set to capture audio.  Jack gave me a problem with that too (and not just in Ubuntu, but also in other Linus distributions (Puppy, 64Studio).

I am going to try to boot up my Dyne:Bolic disk later on and see if Jack gives me the same headache there.  Supposedly everything is set up already in that operating system, and I have it on a Live Disk. 

Geo

---

### Post by eye208 on 2008-08-02
> **jukingeo said:**
> Now what I don't get is that in Windows you CAN have more than one thing piping through the sound card at one time.  The signal is mixed.  How come Ubuntu can't do that?
Ubuntu can do that unless some application is requesting exclusive control over a specific audio device. For example, any application using the legacy OSS interface is given exclusive control. The same goes for any application that directly accesses one of ALSA's "hw" devices. Only applications using ALSA's generic "default" device and those using ESD will work side by side. This is because "default" is mapped to ALSA's own software audio mixer (which works even if the sound card does not provide mixing of multiple sources in hardware).

This is no different in Windows. There you have DirectSound (used by games and normal multimedia applications) and ASIO (used by professional audio applications). True ASIO drivers usually bypass DirectSound and provide exclusive access to an audio device or provide their own mixer, the same way Jack does on Linux.

There must be some application on your system accessing the sound card so that it's not available to Jack exclusively. I thought it was PulseAudio, but apparently it's something else. You can remove "esound" too and see if that helps. Or configure Jack to use "default" instead of "hw:0".

---

### Post by jukingeo on 2008-08-03
> **eye208 said:**
> 

There must be some application on your system accessing the sound card so that it's not available to Jack exclusively. I thought it was PulseAudio, but apparently it's something else. You can remove "esound" too and see if that helps. Or configure Jack to use "default" instead of "hw:0".

Ok, I just tested Jack again.

Going directly from the login screen I opened up Jack and turned it on (start) and it gives me what I posted above.  Nothing else is turned on or comes up automatically (that I am aware of). (As of yesterday I have set the hardware setting to default within Jack).

Geo

---

### Post by mountain_goat on 2008-08-03
Geo,
Hi, just a thought before I head off, I notice that the error code for jack is 256 in your listing. An di get this code if I don't set the server path correctly.

> 13:54:50.888 /usr/bin/jackd -R -P1 -dalsa -dhw:0 -r48000 -p1024 -n2 -PI think this line tells me that you are using real time control, the -R in that line.
Check under jack | settings | sever path = /usr/bin/jackd.

See how that goes. I am wondering if the error is a red herring and that jack is crashing due to some other issue and not that the card is in use. From what you are saying the card should be free.

Stop the server and try this or some other combinations and see if you get a different error message.

OK, nearly 2 in the morning
I'll catch you in the morning then ;)

mountain goat  ~ off to snuggle in the hay

---

### Post by jukingeo on 2008-08-04
> **mountain_goat said:**
> Geo,
Hi, just a thought before I head off, I notice that the error code for jack is 256 in your listing. An di get this code if I don't set the server path correctly.

I think this line tells me that you are using real time control, the -R in that line.
Check under jack | settings | sever path = /usr/bin/jackd.

See how that goes. I am wondering if the error is a red herring and that jack is crashing due to some other issue and not that the card is in use. From what you are saying the card should be free.

Stop the server and try this or some other combinations and see if you get a different error message.

OK, nearly 2 in the morning
I'll catch you in the morning then ;)

mountain goat  ~ off to snuggle in the hay

Hello MG:

Top O' the mornin' to ya my horned friend!

I can show a listing of when Jack starts and it looks initially to be good, but once started I get the problems.   Initially when I first loaded Ubuntu Studio on I would get Jack to work, but I did have to make some video adjustments and then my troubles really began trying to get Fluidsynth to work and it will not even go in now.

However, my problems with Jack are NOT isolated to Ubuntu, I have problems with it in other OS's as well.  I think something must be wrong with the driver that connects Jack with ALSA to my card.

The funny thing is that I have sound with just about everything else.  Only Jack is giving me the big headache as of now.

Well, as of now I can't do anything because I am at work.

I been thinking too, maybe I should put things on hold with getting Jack to work with my sound card because I have a new sound device on the way and I am more then likely going to pull the Soundblaster. 

I have an Echo Mona coming and I am HOPING I am not going to have trouble with that device.  It should be coming this week.

Have to run!

Geo

---

### Post by mrowth on 2008-08-05
> **eye208 said:**
> Ubuntu can do that unless some application is requesting exclusive control over a specific audio device. For example, any application using the legacy OSS interface is given exclusive control. The same goes for any application that directly accesses one of ALSA's "hw" devices. Only applications using ALSA's generic "default" device and those using ESD will work side by side. This is because "default" is mapped to ALSA's own software audio mixer (which works even if the sound card does not provide mixing of multiple sources in hardware).

JACK attaches to hw:0 here and runs side by side with Xine, Audacity, Flash, games. 

I've told Xine to use OSS, and it still won't bother JACK, or YouTube...

Shouldn't that NOT work?

(This is with VIA 82xx onboard sound that **used** to require an .asoundrc mucking about with dmix until whatever ALSA version came with Feisty (perhaps earlier)...)

---

### Post by eye208 on 2008-08-07
> **mrowth said:**
> JACK attaches to hw:0 here and runs side by side with Xine, Audacity, Flash, games. 

I've told Xine to use OSS, and it still won't bother JACK, or YouTube...

Shouldn't that NOT work?
Well, as you can see, it doesn't work for jukingeo. I remember reading some ALSA docs stating that only "default" is mapped to ALSA's software mixer (unless you remap it using some .asoundrc hack). "hw" devices don't even perform sample format/rate conversion (unlike "plughw"). So if it works for you this way, I'd say it's quite unusual. Consider yourself lucky. ;)

---

### Post by mrowth on 2008-08-07
> **eye208 said:**
> Well, as you can see, it doesn't work for jukingeo. I remember reading some ALSA docs stating that only "default" is mapped to ALSA's software mixer (unless you remap it using some .asoundrc hack). "hw" devices don't even perform sample format/rate conversion (unlike "plughw"). 
I used to **have to** use .asoundrc to make a "default" using dmix and rate conversion - never being too clear on what exactly was working and what wasn't.

From some Ubuntu version on (Edgy or Feisty?), it just worked out of the box (barring strange moments with JACK losing write access to /dev/shm and just not starting at all). Same lousy onboard sound, no .asoundrc.

I'm disheartened to see there're still problems with OSS apps (or anything) hogging the sound hardware...

> So if it works for you this way, I'd say it's quite unusual. Consider yourself lucky. ;)
I can't... this computer's (physically) dying, I don't know what to buy next, and I've not had much luck going by the ALSA sound card matrix before. (I need something that's known to work, recording included, but those whose stuff **just works** don't seem to post...)

---

### Post by jukingeo on 2008-08-07
> **mrowth said:**
> 

I can't... this computer's (physically) dying, I don't know what to buy next, and I've not had much luck going by the ALSA sound card matrix before. (I need something that's known to work, recording included, but those whose stuff **just works** don't seem to post...)


Supposedly the M-Audio Delta line of audio products are automagically detected and installed in Ubuntu.  They do have a full bevy of ins/outs for audio recording enthusiasts.

The Echo line of cards (of one I just purchased) should also work, but it isn't automagically recognized.  You have to configure it manually.

For a REALLY high end card, RME's Hammerfall line supposed to have EXCELLENT Linux support.  But these cards are VERY expensive.   But they are by FAR better quality than M-Audio.

Supposedly in the near future Creative's pro-line, EMU, is to have fully supported cards.

You can also go firewire as well and Edirol, Echo, Focusrite and Presonus is recognized in this department.  Most of these use the Freebob/FFADO system though and you need to run Jack.  The problem with a firewire interface is that you will not have system sounds, game sounds, or any streaming internet sounds...unless you can get it to work with Jack.  There is much more fiddling around to do with firewire.  The point is if you can go with a regular PCI card...then do it.

While the Sound Blaster Live is automagically detected and installed, I find that it does have some issues, of which those I pointed out here.   Everything ALSA worked great with the Live card...except  Jack.   It wouldn't even record in Jack.  Eventually Jack refused to work with the card period.  But I had everything else.  I had sound in; games, internet, mp3 player, movies, system sounds...you name it.  Sound worked great in everything except Jack.

There is another caveat to the SB Live, it can only support ONE sample rate and that is 48k.  When I discovered that, I knew the card was history.  THAT is something I cannot live with for pro work. For me, mastering work will not be done with anything less than 88.2k.

Anyway, I hope that helps you out.  If you have doubts about a potential sound candidate, you can always check out the ALSA website sound card list to see if your devices is supported or not.

This is the web address:

[www.alsa-project.org](www.alsa-project.org)

Just go to the left side and click on soundcards. You will be presented with a list of all the MFG's that are supported under ALSA.

Now remember that supported and automagically detected are two different things.   Depending on the sound device, you could be looking at a minor or major issue with installing it.

All in all if you want the best of all worlds for recording and are 'ok' with a cheaper card then you can't beat the M-Audio Delta line.

[http://www.m-audio.com/index.php?do=products.list&ID=pciinterfaces](http://www.m-audio.com/index.php?do=products.list&ID=pciinterfaces)

The Delta 66 is a good starting point.  It has 4ins 4outs and SPDIF.

Keep in mind though...the Delta line is pretty bare bones.  You only get LINE LEVEL ins/outs.  If you have mics and guitars you want to record, then you have to buy a separate preamp.

This is what I ended up with because I wanted at least 4ins (preamped) and 6 outs

[http://www.echoaudio.com/Products/Discontinued/Mona/index.php](http://www.echoaudio.com/Products/Discontinued/Mona/index.php)

It is discontinued now, but it does show up on Ebay from time to time (that is where I got mine).   I have it set up and working for Windows right now (just to test it), and tonight I am going to set it up in Ubuntu.

Hope that helps in your choice.  Good luck!

Geo

---

### Post by eye208 on 2008-08-08
> **mrowth said:**
> I'm disheartened to see there're still problems with OSS apps (or anything) hogging the sound hardware...
Sometimes that is exactly what you want. Software mixing and sample rate conversion in particular are not bit-transparent. It makes perfect sense to have two audio devices in the system and use one exclusively for Jack and nothing else.

---

### Post by jukingeo on 2008-08-08
> **eye208 said:**
>  It makes perfect sense to have two audio devices in the system and use one exclusively for Jack and nothing else.


I have an Echo Mona as of now that I am trying to configure.  It supposedly is Linux compliant, but the alsa driver has to be compiled into a module.  So I am having a bit of difficulty with that.

If I can't get it to work, I may end up going with two sound devices.  The Sound Blaster Live (Dell OEM variant) works great overall in Ubuntu Studio.  However, Jack hates it.  It will not even accept it for recording.

I did think about going with the Focusrite Saffire firewire device, but I was a bit hesitant to do so because I am waiting for the FFADO project to be complete and the next version installed with Jack instead of FreeBob.

It was around this time when I came across the Echo Mona. 

So far I have set up the Mona in Windows and it is working great there.  So I am hoping that I can get it to work In Linux as well.

Geo

---

### Post by mrowth on 2008-08-09
jukingeo ~ thank you so much. That really helped. 

I think it'll be the Delta 66 or more likely the 1010LT... (any problems with the 1010LT?)

I do want something that'll work for Flash, games, IM, etc. as well as for JACK - and that I can rely on to work with no or little extra configuration. There's enough to check and set up *already* every time before I can be sure a distro is working for me. I'm assuming it's not working under Ubuntu only? (Right now I'm using Mint 4.0 KDE CE, planning to skip 5.0/Hardy Heron. Also kinda have my eyes on either PCLinuxOS or PCLinuxOS Producer Edition when it's ready...).

And then - there's this thread about Deltas not working... [http://ubuntuforums.org/showthread.php?t=805883](http://ubuntuforums.org/showthread.php?t=805883) ...I hope it's really just due to Pulse.

Either way, I would like to make sure the next **mainboard**'s on-board sound will be working as a fallback -- it's unlikely I'll be able to afford all-new equipment right away. So far the ALSA page isn't giving me much hope there...

Thanks again, and good luck with the Mona.

---

### Post by jukingeo on 2008-08-11
> **mrowth said:**
> jukingeo ~ thank you so much. That really helped. 

I think it'll be the Delta 66 or more likely the 1010LT... (any problems with the 1010LT?)

The 1010 should be a good choice as it does have many ins/outs.  I think the LT is the "lite" version, so you don't have balanced connections on that.  If you do "pro" recording work, you may run into a problem with that.

In terms of configuration, there may be the occasional hick-up or two, but for the most part that card should be automagically recognized.


> I do want something that'll work for Flash, games, IM, etc. as well as for JACK - and that I can rely on to work with no or little extra configuration. 

Then you WANT a PCI card and not a firewire system.  As of now firewire audio ONLY works through Jack.  However, it is very much possible that if you have on-board sound, you can use that for the bulk of your audio (mp3, streaming internet, system sounds, games, etc) and just use a firewire audio interface for your 'pro' recording work.   However, if you are going to monitor through your computer speakers (highly inadvisable) then you must make sure your internal patching for the onboard sound card works, so you can feed the output of Jack into the card.  In that manner you can get around the problem with Jack not being able to  play back internal sounds from outside (non Jack) applications.

> There's enough to check and set up *already* every time before I can be sure a distro is working for me. I'm assuming it's not working under Ubuntu only? (Right now I'm using Mint 4.0 KDE CE, planning to skip 5.0/Hardy Heron. Also kinda have my eyes on either PCLinuxOS or PCLinuxOS Producer Edition when it's ready...).

What is not working under Ubuntu only?  Hardy Heron is version 8.04.

I looked at those two applications and they are NOT user friendly.  Neither is 64Studio (it is good for recording, but not intuitive for other tasks).  You should stick with Ubuntu until you have a good grasp on what you are doing within Linux in general.

BUT, just for the record, I am working with a fellow on creating a multi-media package for Puppy Linux.  I was also recommended by this same fellow to check out Dyne:Bolic.  This is an all-in-one multimedia package that is aimed at the "streaming internet radio/tv station" enthusiast.   It comes with many applications you need (however it is not as well endowed as Ubuntu).  It has Ardour, Rosegarden, Muse and some other audio applications, but shockingly, it also comes with Cinelerra for video.  And yes, it connects everything through Jack.  

Best of all, unlike other 'heavyweight' studio applications, Dyne:Bolic doesn't need a DVD.  In fact you don't have to install it either.   It has a Live CD.  If you want the speed of a hard drive you can just copy the contents of the CD-Rom over to a directory and then create a bootable link to the directory (floppy or USB boot).  Or you can stick with using the CD-Rom and just store your system information on the hard drive (so it memorizes your settings...even with a Live CD).

> And then - there's this thread about Deltas not working... [http://ubuntuforums.org/showthread.php?t=805883](http://ubuntuforums.org/showthread.php?t=805883) ...I hope it's really just due to Pulse.

You have to watch out for the pulse/OSS combination.  I don't recommend it because OSS is becoming outdated and you probably will never get EVERYTHING running right.  I first started with OSS in trying to get a Sound Blaster X-Fi to work.  OSS proved to be nothing but headaches.  This probably will be the case with many newer distros out there.  However there are some distros that prefer OSS and work better with it.  But again, it is like taking a step backward and I usually like to "keep moving foward" (gee, where did I hear that before???). 

> Either way, I would like to make sure the next **mainboard**'s on-board sound will be working as a fallback -- it's unlikely I'll be able to afford all-new equipment right away. So far the ALSA page isn't giving me much hope there...

Thanks again, and good luck with the Mona.

Well, even with the Delta series you MAY run into configuration problems with a dual sound setup.  This is very much well documented though and the incident is rectified by a few configuration settings.  Just do a search to find out what scenario fits your particular problem (should it show up).  By far the biggest problem with dual cards is that the HW (hardware) designations switch on reboot (thus what was HW=0 can swap with what is HW=1), and naturally that is going to cause you set up woes.

You CAN "force" a permanent setting within a configuration file though.  Just I don't remember the name of that file.  But a simple search here should tell all.

Good luck!

Geo

---

### Post by mrowth on 2008-09-08
> **jukingeo said:**
> Then you WANT a PCI card and not a firewire system.  As of now firewire audio ONLY works through Jack.  However, it is very much possible that if you have on-board sound, you can use that for the bulk of your audio (mp3, streaming internet, system sounds, games, etc) and just use a firewire audio interface for your 'pro' recording work.   However, if you are going to monitor through your computer speakers (highly inadvisable) then you must make sure your internal patching for the onboard sound card works, so you can feed the output of Jack into the card.  In that manner you can get around the problem with Jack not being able to  play back internal sounds from outside (non Jack) applications.
No monitors... for the time being, everything's sharing the same living room stereo (how's *that* for "'pro' recording work"? :))

> What is not working under Ubuntu only? 
Was just wondering if the Delta cards would work in other distributions, or if their compatibility is Ubuntu-specific. Suppose it's not.
>  Hardy Heron is version 8.04.
Linux Mint 4.0 was based on Gutsy, Linux Mint 5.0 on Hardy. (Anyway, I did end up installing (K)ubuntu 8.04**.1** after accidentally wrecking my Mint 4.0 install.)

> I looked at those two applications and they are NOT user friendly.  Neither is 64Studio (it is good for recording, but not intuitive for other tasks).  You should stick with Ubuntu until you have a good grasp on what you are doing within Linux in general.
User-friendly is good... but the Ubuntu and Jacklab realtime kernels are unstable with my current CPU, whereas the one in PCLinuxOS seemed to run fine - so I was contemplating a switch... except I couldn't get ZynAddSubFX to run. It seemed like a good distro otherwise.

> BUT, just for the record, I am working with a fellow on creating a multi-media package for Puppy Linux.  I was also recommended by this same fellow to check out Dyne:Bolic.  This is an all-in-one multimedia package that is aimed at the "streaming internet radio/tv station" enthusiast.   It comes with many applications you need (however it is not as well endowed as Ubuntu).  It has Ardour, Rosegarden, Muse and some other audio applications, but shockingly, it also comes with Cinelerra for video.  And yes, it connects everything through Jack. 

Best of all, unlike other 'heavyweight' studio applications, Dyne:Bolic doesn't need a DVD.  In fact you don't have to install it either.   It has a Live CD.  If you want the speed of a hard drive you can just copy the contents of the CD-Rom over to a directory and then create a bootable link to the directory (floppy or USB boot).  Or you can stick with using the CD-Rom and just store your system information on the hard drive (so it memorizes your settings...even with a Live CD).
I burnt a Dyne:Bolic CD once but it wouldn't boot. (That was a couple years ago, though.) I've not been so happy with Live discs so far: drive is blocked, everything's slow... just out of curiosity, can you get your "own" persistent fstab, xorg.conf, installed apps (etc.) with a Dyne:Bolic live CD (or others, for that matter)? 

Guess I'm really after the perfect general purpose distro with humongous package repositories that'll let me toy with softsynths and sampling in between the "usual" things (video/GIMP/Google Earth/writing/printing/Java/Flash/AIM/games/blah...)

> You have to watch out for the pulse/OSS combination.  I don't recommend it because OSS is becoming outdated and you probably will never get EVERYTHING running right.  I first started with OSS in trying to get a Sound Blaster X-Fi to work.  OSS proved to be nothing but headaches.  This probably will be the case with many newer distros out there.  However there are some distros that prefer OSS and work better with it.  But again, it is like taking a step backward and I usually like to "keep moving foward" (gee, where did I hear that before???). 
I still don't have Pulse installed; it didn't seem to come with my Kubuntu 8.04.1 install. Not sure it wouldn't simply make things more complicated by adding another layer of abstraction...?

**ALSA** isn't on the way out, is it? It's been so mercifully long that it's given me any (serious) trouble. OSS likewise, actually. Audacity used to be fiddly or even unusable, but recent packages support JACK. I'm starting to wonder if my cheapo onboard sound has hardware mixing after all -- if JACK at hw:0 (usually) cooperates with ALSA and even OSS apps running at the same time.


> Well, even with the Delta series you MAY run into configuration problems with a dual sound setup.  This is very much well documented though and the incident is rectified by a few configuration settings.  Just do a search to find out what scenario fits your particular problem (should it show up).  By far the biggest problem with dual cards is that the HW (hardware) designations switch on reboot (thus what was HW=0 can swap with what is HW=1), and naturally that is going to cause you set up woes.

You CAN "force" a permanent setting within a configuration file though.  Just I don't remember the name of that file.  But a simple search here should tell all.
I've been through it before with the onbord sound"card", PCI soundcard, and TV card all juggling hw:0 to 2 between them. I can disable the onboard sound in the BIOS Setup all I want,  Linux doesn't seem to notice/care. Oh, well.

> Good luck!
And to you too. Thanks again!

---

### Post by jukingeo on 2008-09-09
> **mrowth said:**
> No monitors... for the time being, everything's sharing the same living room stereo (how's *that* for "'pro' recording work"? :))

Ouch![-X  Just remember when you get more 'pro' that you need a good set of monitors.  The KRK stuff is self powered and pretty inexpensive.


> Was just wondering if the Delta cards would work in other distributions, or if their compatibility is Ubuntu-specific. Suppose it's not.

As far as I know the M-Audio Delta series SHOULD be automagically recognized.

> User-friendly is good... but the Ubuntu and Jacklab realtime kernels are unstable with my current CPU, whereas the one in PCLinuxOS seemed to run fine - so I was contemplating a switch... except I couldn't get ZynAddSubFX to run. It seemed like a good distro otherwise.


I burnt a Dyne:Bolic CD once but it wouldn't boot. (That was a couple years ago, though.) I've not been so happy with Live discs so far: drive is blocked, everything's slow...

Ooof!  How old is your system?  If it is too old perhaps you should look into something else.  If not, then maybe you should at least look into a new CDRom drive.

For the most part, I never ran into problems with Live CD's.  Mostly my problems are with sound.  

>  just out of curiosity, can you get your "own" persistent fstab, xorg.conf, installed apps (etc.) with a Dyne:Bolic live CD (or others, for that matter)? 

:confused:  Got me there.  I am new to Linux as well.  I will say that with Dynebolic, you do not need to do a standard install.  You can directly copy the files off the Live CD and then just set up a boot to the Dynebolic directory (using USB or floppy, etc).

> Guess I'm really after the perfect general purpose distro with humongous package repositories that'll let me toy with softsynths and sampling in between the "usual" things (video/GIMP/Google Earth/writing/printing/Java/Flash/AIM/games/blah...)

Same here.


> I still don't have Pulse installed; it didn't seem to come with my Kubuntu 8.04.1 install. Not sure it wouldn't simply make things more complicated by adding another layer of abstraction...?

Naw, you should just go straight ALSA.  I do remember a while back that Pulse did help with getting some of my OSS applications to work.

> **ALSA** isn't on the way out, is it? 

No, opposite in fact.  ALSA is the upcoming standard and Hardy was one of the first Ubuntu distributions to use it in favor of OSS.  OSS is pretty much on it's way out.  It is still very much supported...but more and more programs and operating systems are using ALSA now.

OSS is probably the easiest way to get "some" sound on your machine.  But you will notice that many things will not work.  That is why there is Pulse and other "overlays" you can use.  Many times these "overlays" cause problems with each other.

I ran into this situation when trying to get my Sound Blaster X-Fi to work, but I ended up using the ALSA drivers instead (see my link below).  However the X-Fi really isn't a supported device in Linux and while it worked great in Ubuntu, I couldn't use the sound card with anything else.

I now have an Echo Mona, which is a professional sound device and it is supposedly supported by Linux.  However, it isn't fully recognized by Linux and it doesn't come up automagically.  I am still trying to work on this problem as we speak (see my other posts here in the forums). 


> It's been so mercifully long that it's given me any (serious) trouble. OSS likewise, actually. Audacity used to be fiddly or even unusable, but recent packages support JACK. I'm starting to wonder if my cheapo onboard sound has hardware mixing after all -- if JACK at hw:0 (usually) cooperates with ALSA and even OSS apps running at the same time.

I don't really recommend using both ALSA and OSS together.  That is asking for trouble.  Working with onboard sound is a nightmare in itself.  However, some onboard sound is automagically recognized.  My computer at work for instance.  That machine has something called SoundMAX and it worked great with Puppy and Dynebolic...right off the Live CD (I didn't test it with Ubuntu though).  I didn't have to configure it or anything.

> I've been through it before with the onbord sound"card", PCI soundcard, and TV card all juggling hw:0 to 2 between them. I can disable the onboard sound in the BIOS Setup all I want,  Linux doesn't seem to notice/care. Oh, well.

Your Bios may be just turning off the on-board sound on a software level and that would be something Windows may recognize and comply with.  But as you said, Linux may just not care.   You can see if you have a jumper on your motherboard (see your mobo instructions first) to see if you can manually disable the on board sound.

I think too you can specify multiple sound cards and their priority order within the modprob.conf file.

What is the sound device you are trying to get to work?

Geo

---

### Post by mrowth on 2008-09-09
> **jukingeo said:**
> Ooof!  How old is your system?  If it is too old perhaps you should look into something else.  If not, then maybe you should at least look into a new CDRom drive.
An AMD X2 4800+ with 2GB DDR1 RAM should still be fast *enough* for this in principle... the drive is just a few months old (although it was of course the cheapest dual layer DVD writer I could find). CDs/DVDs in general are a bit of a problem here - recognising a disc ("making its icon appear") takes suspiciously long or fails, discs occasionally stall... (this applies even to freshly unwrapped audio CDs) 

> :confused:  Got me there.  I am new to Linux as well.  I will say that with Dynebolic, you do not need to do a standard install.  You can directly copy the files off the Live CD and then just set up a boot to the Dynebolic directory (using USB or floppy, etc).
That sounds nice, actually, since I don't want to make room for more partitions.

> Naw, you should just go straight ALSA.  I do remember a while back that Pulse did help with getting some of my OSS applications to work.



No, opposite in fact.  ALSA is the upcoming standard and Hardy was one of the first Ubuntu distributions to use it in favor of OSS.  OSS is pretty much on it's way out.  It is still very much supported...but more and more programs and operating systems are using ALSA now.
I don't recall ever *not* using ALSA with Ubuntu (ever since I'm aware of it, anyway); always thought "if an app can't get sound, see if it has an option to use ALSA" - however ALSA itself seems to have improved at some point inasmuch as I'm no longer required to set up rate conversion and software mixing.

> 
OSS is probably the easiest way to get "some" sound on your machine.  But you will notice that many things will not work.  That is why there is Pulse and other "overlays" you can use.  Many times these "overlays" cause problems with each other.
Seems Kubuntu no longer offers aRts as an option for its system sounds... Control Centre still claims "the KDE sound system takes exclusive control over your audio hardware", but Flash, JACK, and everything else prove it wrong...

> I don't really recommend using both ALSA and OSS together.  That is asking for trouble.  Working with onboard sound is a nightmare in itself.  However, some onboard sound is automagically recognized.  My computer at work for instance.  That machine has something called SoundMAX and it worked great with Puppy and Dynebolic...right off the Live CD (I didn't test it with Ubuntu though).  I didn't have to configure it or anything.
The onboard sound here is obviously working great with ALSA's VIA82xx driver... there're like a billion sliders in the mixer, too ;)... it's just that the hardware itself isn't so great. 

> What is the sound device you are trying to get to work?
None right now... those were cheap Terratec and Soundblaster cards.

---

### Post by jukingeo on 2008-09-10
> **mrowth said:**
> An AMD X2 4800+ with 2GB DDR1 RAM should still be fast *enough* for this in principle... the drive is just a few months old (although it was of course the cheapest dual layer DVD writer I could find). CDs/DVDs in general are a bit of a problem here - recognising a disc ("making its icon appear") takes suspiciously long or fails, discs occasionally stall... (this applies even to freshly unwrapped audio CDs)

Well, I am not familiar with AMD machines, but it doesn't sound like your system is too far off from mine.  Perhaps it could be a mobo issue.  I heard Linux doesn't like certain motherboards, but those instances are rare and far between. 


> 

I don't recall ever *not* using ALSA with Ubuntu (ever since I'm aware of it, anyway); always thought "if an app can't get sound, see if it has an option to use ALSA" - however ALSA itself seems to have improved at some point inasmuch as I'm no longer required to set up rate conversion and software mixing. 

I only came on to Linux recently and Ubuntu 8.04.  Supposedly Ubuntu started with OSS and then supported ALSA.  Either version 7.10 or 8.04 made the full commitment to use ALSA as the default.


> Seems Kubuntu no longer offers aRts as an option for its system sounds... Control Centre still claims "the KDE sound system takes exclusive control over your audio hardware", but Flash, JACK, and everything else prove it wrong...

Not familiar with Kubuntu.  I did want to try out Xubuntu, because I wanted a "lightweight" version of Linux, but then I heard about Puppy Linux and used that instead for that application.


> The onboard sound here is obviously working great with ALSA's VIA82xx driver... there're like a billion sliders in the mixer, too ;)... it's just that the hardware itself isn't so great. 

None right now... those were cheap Terratec and Soundblaster cards.

So if the onboard sound is great and you have no other sound device, then what is the issue?

Anyway, I always thought the Terratec stuff was pretty decent.  Not quite on the level of Echo or Emu, but definitely better than M-Audio.

I am in the audio service business and I know the M-Audio stuff is mostly junk.  The Midisport interfaces for Midi are fine and there is still a large ? mark for their audio sound cards.  But I can say that I cannot recommend their keyboards or most other "complex" sound products.  The failure rate is very high.  Just go look for yourself under the clearance section of the Musician's Friend website.  There are loads of M-Audio items listed that are labeled as "B" stock.  B-stock means the item was opened for some reason or another.  So there are two things that would cause that a) returns-people not happy with the product, or b) high failure rate.   Being that I AM in audio service, I found it to be "B".  The one thing that is in your favor with sound cards is that they have no moving parts as keyboards do.  When it comes to a keyboard controller, look into Korg.  They have good stuff and many of the USB keyboard controllers are automagically recognized in Linux.  I tested my Korg Kontrol 49 and it works fine in Linux.

---

### Post by mrowth on 2008-09-10
> **jukingeo said:**
> Not familiar with Kubuntu.
I just like KDE, its apps (K3B, Amarok, Konqueror, Kaffeine, etc.), and its configurability... I can make it lightweight (in appearance) while retaining the full-featuredness.

> So if the onboard sound is great and you have no other sound device, then what is the issue?
It just *works* great - it's very *compatible*. I would still like more than 48 kHz/16 bit, more and more accessible inputs, less flat/muffled recordings, etc.

> Anyway, I always thought the Terratec stuff was pretty decent. 
I couldn't even get it to record, whatever the ALSA site said. There were no capture-related sliders/switches in the mixer, and the hardware device was "blocked".

>  Not quite on the level of Echo or Emu, but definitely better than M-Audio.  I am in the audio service business and I know the M-Audio stuff is mostly junk.  The Midisport interfaces for Midi are fine and there is still a large ? mark for their audio sound cards.  
Oh. Weren't you kinda-sorta recommending the Delta stuff...?

> But I can say that I cannot recommend their keyboards or most other "complex" sound products.  The failure rate is very high.  Just go look for yourself under the clearance section of the Musician's Friend website.  There are loads of M-Audio items listed that are labeled as "B" stock.  B-stock means the item was opened for some reason or another.  So there are two things that would cause that a) returns-people not happy with the product, or b) high failure rate.   Being that I AM in audio service, I found it to be "B".  The one thing that is in your favor with sound cards is that they have no moving parts as keyboards do.  When it comes to a keyboard controller, look into Korg.  They have good stuff and many of the USB keyboard controllers are automagically recognized in Linux.  I tested my Korg Kontrol 49 and it works fine in Linux.
The M-Audio keyboards I saw *looked* bad. Actually the prettiest one in my price range (lowest end) was the Korg K49 (not "Kontrol"). It doesn't have much in the way of pads/knobs/... -- going to put it off until I have a better sense for however many bells & whistles I actually need.

---

### Post by jukingeo on 2008-09-17
> **mrowth said:**
> I just like KDE, its apps (K3B, Amarok, Konqueror, Kaffeine, etc.), and its configurability... I can make it lightweight (in appearance) while retaining the full-featuredness.

I did try other distributions out, but I am not sure if I tried anything that used KDE.  I guess I have to look at a Kubuntu site to see what the interface looks like.


> It just *works* great - it's very *compatible*. I would still like more than 48 kHz/16 bit, more and more accessible inputs, less flat/muffled recordings, etc.

Oh, so you have something that works similar to a Sound Blaster Live.  I had that issue with SB Live myself and I ended up pulling the card.  The SB Live was the only card that I tried that was automagically recognized.

The first card I had was a Sound Blaster X-Fi and that took me about two months to get to work in Ubuntu.  However, it didn't work in any other distribution and I wanted something a bit more "universal", so this way I could use it in other applications.  I have Ubuntu Studio and it is on the buggy size, so I wanted to try other distributions out, so the X-Fi wouldn't work with them.  The Sound Blaster Live worked in all of my Linux distributions, BUT it could only playback (I couldn't get it to record) at 48k/16bit.  Jack didn't like the Sound Blaster Live either.

> I couldn't even get it to record, whatever the ALSA site said. There were no capture-related sliders/switches in the mixer, and the hardware device was "blocked".

I HAD the sliders with my Sound Blaster Live, but putting Jack into record mode (or Dual mode) would induce a crash.  So all in all the Sound Blaster Live had to go and I did quite a bit of research on the Echo devices and supposedly there have been success stories.  So I end up buying an Echo Mona and I have it for over a month now and still no sound in ANY of my Linux distributions.  It works beautiful in Windows XP...but then again...so does my Alesis IO_26 (a far superior device, but isn't supported at all in Linux).  So I am back to square 1.


> Oh. Weren't you kinda-sorta recommending the Delta stuff...?

Yeah, that is a good way of putting it.  I wouldn't choose M-Audio/Delta for the sake of personal choice, but rather by a default.  M-Audio is one of the few companies that actually has active Linux support and makes Linux drivers for their devices.  The drivers are open sourced and are loaded on with most Linux distributions.  So in most cases the M-Audio Delta line will be automagically recognized.  However, the downside is that I don't think that M-Audio has no where near as good digital converters as something by EMU, Echo, Presonus, etc.   So then the other choice for a Linux supported product would be the RME Hammerfall line.  However, these cards are extreme.  I don't need the capabilities of these cards and I certainly cannot afford them.  Most of the cards start at $500.   It is definitely great stuff.  But I am looking for something that is a balance between price and quality.

The bottom line is if I can't get my Echo Mona to work, I am going to sell it and break down and get an M-Audio product.

I am pretty much coming to the conclusion though that Linux is still not ready for a full featured and reliable DAW.  So an M-Audio card may be decent enough for me to try out the programs in Linux, perhaps use Linux for live audio application and learning to do video editing.  However, I doubt that I could ever do professional recording work with it.  After all, 3 out of my 4 sound devices do not work in Linux and it's "automatic" sound support is very limited. In this aspect Linux is extremely behind the times in regards to Windows XP and I am not even going there when it comes to comparing Linux to the Mac.

> The M-Audio keyboards I saw *looked* bad. Actually the prettiest one in my price range (lowest end) was the Korg K49 (not "Kontrol"). It doesn't have much in the way of pads/knobs/... -- going to put it off until I have a better sense for however many bells & whistles I actually need.

Get the Kontrol 49 instead.  It is a WAY better board than the K series.  The Kontrol 49 IS automagically recognized.  I was able to access controls with it directly in Linux programs such as Ardour and Mixxx.  The downside is that the programming feature can only be done in Windows, so you have to make a note of what controls (and control numbers) you want to control in your Linux application and then preset the Kontrol 49 within Windows using it's program.  Once saved in the Kontrol 49, you can call up the settings in Linux and then control your device.

Supposedly any USB device that is CLASS COMPLIANT, should be automagically recognized.

So a huge sigh of relief I had when I realized that I can use my Kontrol 49 in Linux.

BUT I still have the sound issue to deal with...

---

### Post by mrowth on 2008-09-19
> **jukingeo said:**
> I did try other distributions out, but I am not sure if I tried anything that used KDE.  I guess I have to look at a Kubuntu site to see what the interface looks like.
Windowsy, by default... 

Mine looks like [screenshot attached] (that's the Konqueror file manager ready to rip an audio CD, with a complimentary terminal-in-a-panel beneath) 

> Oh, so you have something that works similar to a Sound Blaster Live. I had that issue with SB Live myself and I ended up pulling the card.  The SB Live was the only card that I tried that was automagically recognized.

The first card I had was a Sound Blaster X-Fi and that took me about two months to get to work in Ubuntu.  However, it didn't work in any other distribution and I wanted something a bit more "universal", so this way I could use it in other applications.  I have Ubuntu Studio and it is on the buggy size, so I wanted to try other distributions out, so the X-Fi wouldn't work with them.  The Sound Blaster Live worked in all of my Linux distributions, BUT it could only playback (I couldn't get it to record) at 48k/16bit.  Jack didn't like the Sound Blaster Live either.


I HAD the sliders with my Sound Blaster Live, but putting Jack into record mode (or Dual mode) would induce a crash.  So all in all the Sound Blaster Live had to go and I did quite a bit of research on the Echo devices and supposedly there have been success stories.  So I end up buying an Echo Mona and I have it for over a month now and still no sound in ANY of my Linux distributions.  It works beautiful in Windows XP...but then again...so does my Alesis IO_26 (a far superior device, but isn't supported at all in Linux).  So I am back to square 1.

Augh... that's hard.

Recording does work, here... it's not likely to sound any better in Windows. 

Bit disappointed the Terratec didn't work out, thought it was supported. Disconcerting.

Might start hoarding ancient Soundblaster 16s as fallback options for the Linux future, then... *sigh*


> Yeah, that is a good way of putting it.  I wouldn't choose M-Audio/Delta for the sake of personal choice, but rather by a default.  M-Audio is one of the few companies that actually has active Linux support and makes Linux drivers for their devices.  The drivers are open sourced and are loaded on with most Linux distributions.  So in most cases the M-Audio Delta line will be automagically recognized.  However, the downside is that I don't think that M-Audio has no where near as good digital converters as something by EMU, Echo, Presonus, etc.   So then the other choice for a Linux supported product would be the RME Hammerfall line.  However, these cards are extreme.  I don't need the capabilities of these cards and I certainly cannot afford them.  Most of the cards start at $500.   It is definitely great stuff.  But I am looking for something that is a balance between price and quality.

The bottom line is if I can't get my Echo Mona to work, I am going to sell it and break down and get an M-Audio product.

That they can be expected to work is so reassuring that I may not be able to make myself dislike them just yet...

> I am pretty much coming to the conclusion though that Linux is still not ready for a full featured and reliable DAW.  So an M-Audio card may be decent enough for me to try out the programs in Linux, perhaps use Linux for live audio application and learning to do video editing.  However, I doubt that I could ever do professional recording work with it.  After all, 3 out of my 4 sound devices do not work in Linux and it's "automatic" sound support is very limited. In this aspect Linux is extremely behind the times in regards to Windows XP and I am not even going there when it comes to comparing Linux to the Mac.

I was thinking the apps were the real problem. Whatever I see people falling head over heals in love with lately does not seem to have equally "sexy" Linux counterparts (Pro Tools, Ableton Live...) 

I'm using WINE a lot -- ironically, it's mostly for comparatively "small" stuff that looks like it's just half a year away from a native version.

> Get the Kontrol 49 instead.  It is a WAY better board than the K series.  

I'll keep it in mind. But unless I get a lot more serious about this, I may not need more than a comfortable (non-PC-keyboard) way to find notes/melodies/chords. 

> The Kontrol 49 IS automagically recognized.  I was able to access controls with it directly in Linux programs such as Ardour and Mixxx.  The downside is that the programming feature can only be done in Windows, so you have to make a note of what controls (and control numbers) you want to control in your Linux application and then preset the Kontrol 49 within Windows using it's program.  Once saved in the Kontrol 49, you can call up the settings in Linux and then control your device.

Since I just mentioned WINE... have you tried using that to get around the rebooting? 

> Supposedly any USB device that is CLASS COMPLIANT, should be automagically recognized.

So a huge sigh of relief I had when I realized that I can use my Kontrol 49 in Linux.

Ok, so I'm clueless, but what happened to the MIDI port? 

> BUT I still have the sound issue to deal with...

I wish I had any ideas, but I seem to be stuck as an eternal newbie. (I just realised I've been using Ubuntu since "Warty Warthog", and Mandrake and SUSE before that...)

Good luck.

Oh -- I *seem* to have got the rt kernel to work at last -- for now, that is -- likely through a random combination of BIOS and kernel boot parameters that'll stop working tomorrow. Until then I'm going to be fannish about my decrepit little computer. Hence the screenshot. Ha.

Edit: Some things already stopped working again. Ha!

---

### Post by mrowth on 2008-09-21
> **eye208 said:**
> Well, as you can see, it doesn't work for jukingeo. I remember reading some ALSA docs stating that only "default" is mapped to ALSA's software mixer (unless you remap it using some .asoundrc hack). "hw" devices don't even perform sample format/rate conversion (unlike "plughw"). So if it works for you this way, I'd say it's quite unusual. Consider yourself lucky. ;)
Right now I'm recording something off a Flash object with Audacity through ALSA hw:0,1. It's ALSA "default" that's blocked. Weird?

---

### Post by eye208 on 2008-09-21
> **mrowth said:**
> Right now I'm recording something off a Flash object with Audacity through ALSA hw:0,1. It's ALSA "default" that's blocked. Weird?
Not really. The "default" device gets mapped to hw:0,0 by default (but going through dmix first to provide stream mixing if needed). If an application hogs hw:0,0 then "default" will not be available either. However hw:0,1 will be unaffected because it's a separate device (on the same card).

---

### Post by mrowth on 2008-09-21
Audacity can *play* through "default" while Flash is doing its all singing, all dancing thing -- so I suppose hw:0,0 isn't being hogged... but I guess recording through "default" is nonsensical to begin with. What would I use if I wanted to have multiple apps *recording* at the same time? A self-made ALSA "device" using dsnoop? 

edit: This will all make sense when I'm fully sober. :oops:

---

### Post by eye208 on 2008-09-21
Recording from "default" means capturing from hw:0,0 too. It's not nonsensical; most (well-written) ALSA clients use "default" for everything. It's bad practice to access hw devices directly. Only sound daemons such as Jack, ESD and PulseAudio do that to keep latency down (although it's configurable).

When I use Jack, I connect it to either of "default", "hw:0" or "hw:1" (loopback) depending on what I want to do. "default" won't block the soundcard, while "hw:0" gives me ~10ms latency with my Realtek onboard sound device. "hw:1" lets me route e.g. Flash audio into Jack for recording or further processing in realtime.

Needless to say, I am quite happy with my "pulse-less" setup. ;)

---

### Post by mrowth on 2008-09-21
Hmmmm... so why can't Audacity rec from default although it's available for playback under the exact same (?) conditions (i.e., Flash playing)?

Isn't hw:0,0 playback; hw:0,1 capture?

I set JACK to default because this thread made me think of that as more "polite" ;)... latency 5.33 ms either way at 48 kHz

---

### Post by eye208 on 2008-09-21
> **mrowth said:**
> Isn't hw:0,0 playback; hw:0,1 capture?
No, usually it's both hw:0,0 (if the soundcard is full-duplex). Some soundcards offer additional devices for digital in/out.

> I set JACK to default because this thread made me think of that as more "polite" ;)... latency 5.33 ms either way at 48 kHz
I am getting occasional xruns with the non-RT kernel at 5.33ms. I haven't tried the RT kernel yet.

Anyway, it's much lower than anything I would get on Windows. :)

---

### Post by mrowth on 2008-09-21
> **eye208 said:**
> No, usually it's both hw:0,0 (if the soundcard is full-duplex). Some soundcards offer additional devices for digital in/out.

Hm. I couldn't get Audacity to record from hw:0,0 (nor "default"); hw:0.1 works fine. So I assumed ,0 was playback and ,1 capture. Seems JACK can capture through hw:0,0 and hw:0,1 though, and play through hw:0,1 and hw:0,0...

What's the difference, then? What's hw:0,1 and why is Audacity less flexible?

**aplay -L**

default:CARD=V8237
    VIA 8237, VIA 8237
    Default Audio Device
front:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    Front speakers
surround40:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.0 Surround output to Front and Rear speakers
surround41:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device
default:CARD=Bt878
    Brooktree Bt878, Bt87x Digital
    Default Audio Device

**aplay -l**

card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Mabye ,1 refers to the "IEC958 (S/PDIF) Digital Audio Output". Why, then, can I play through JACK at hw:0,1? There's nothing connected to S/PDIF. 

> I am getting occasional xruns with the non-RT kernel at 5.33ms. I haven't tried the RT kernel yet.
Oh, ok. I suspect you may well be able to reduce latency to 2.66 or even 1.33 msec with the RT kernel. For whatever that's worth.

---

### Post by eye208 on 2008-09-21
"aplay -l" will only show playback devices. To get a list of capture devices enter "arecord -l".

Here's my output:

aplay -L

```
default:CARD=Intel
    HDA Intel, ALC882 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

arecord -l

```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC882 Analog [ALC882 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```

As you can see, I also have a mysterious secondary analog capture device. Maybe it's a loopback device provided by the driver or the card itself. I don't know because I never tested it ... :-k

---

### Post by mrowth on 2008-09-21
> **eye208 said:**
> "aplay -l" will only show playback devices. To get a list of capture devices enter "arecord -l".

Here's my output:

aplay -L

```
default:CARD=Intel
    HDA Intel, ALC882 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

arecord -l

```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC882 Analog [ALC882 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```

As you can see, I also have a mysterious secondary analog capture device. Maybe it's a loopback device provided by the driver or the card itself. I don't know because I never tested it ... :-k
Well, it seems to be quite useful if it makes finicky old Audacity work... 

arecord -l

**** List of CAPTURE Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Bt878 [Brooktree Bt878], device 0: Bt87x Digital [Bt87x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Bt878 [Brooktree Bt878], device 1: Bt87x Analog [Bt87x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Makes card 0 device 0 and card 0 device 1 look identical, though... same with the Bt878 (but I never experimented with that)

:confused:

---

### Post by jukingeo on 2008-09-21
> **mrowth said:**
> Windowsy, by default... 

Mine looks like [screenshot attached] (that's the Konqueror file manager ready to rip an audio CD, with a complimentary terminal-in-a-panel beneath) 

Hmmmm, hate to say it, but I like the look of Gnome better.  BUT I guess if it performs better than it is worth a look see.


> 
Augh... that's hard.

Recording does work, here... it's not likely to sound any better in Windows. 

Bit disappointed the Terratec didn't work out, thought it was supported. Disconcerting.

Might start hoarding ancient Soundblaster 16s as fallback options for the Linux future, then... *sigh*

Yes I am in the same boat.  The Echo Mona is supposed to be supported via a driver written by the ALSA developers.  However, not many people have attempted to get the Echo products to work.  Some have and it was based on those successes as to why I purchased the card.  I do have an above average level of computer usage and to a certain extent programming ability...BUT that is with Windows.  Linux makes me look like I just stepped out of Kindergarten. 

I am both surprised (and yet not so surprised) the Terratec card didn't work out for you.  They are supposed to be decent cards.  Granted they are not as pro as something like from Echo or RME, but still better than the M-Audio stuff.

As for the SB 16, I am not sure how that will work.  Supposedly it is supported like the SoundBlaster Live.   However, I didn't have good results with my SB Live either.  Sure it was automagically recognized in just about all distributions of Linux I tried.  BUT for some reason Jack didn't take to it.  Games, system sounds, and internet streaming audio worked beautifully, but it absolutely refused to record and it refused to work with Jack.   I will say that I DID have the Dell OEM version of the Sound Blaster Live installed in my machine, so THAT could have been an issue (being not a genuine store bought SB Live).  However, according to ALSA the card IS fully supported.

There was another issue I have to warn you about with Sound Blaster.  Many times it is fixed at one frequency.   The Sound Blaster Live WOULD NOT allow settings for recording/playback other than 48k.  So the SB Live is substandard for professional recording work.  I can't imagine the SB 16 to be any better.   I think that card can only do 44.1k.


> 

That they can be expected to work is so reassuring that I may not be able to make myself dislike them just yet...


I was thinking the apps were the real problem. Whatever I see people falling head over heals in love with lately does not seem to have equally "sexy" Linux counterparts (Pro Tools, Ableton Live...) 

It isn't the apps.  It is the sound configuration that causes the most issues.  I really can't vouch for the applications because I been spending most of my time getting the sound to work right.  But I have played around with some applications, and some of them can raise a few eye brows.  For one, the program Mixxx for DJ's is spot on with some of the more expensive programs that are made for Windows XP and I was happy with that program.  I was just starting to do work in Ardour when I found out the limitations of the Soundblaster live and the 48K thing.  So that is why I switched out the SB Live for the Echo Mona.  I thought I would just have to do some minor reconfiguring to get the Echo Mona to work, but alas...almost 2 months later and still no sound with the Echo Mona.


> I'm using WINE a lot -- ironically, it's mostly for comparatively "small" stuff that looks like it's just half a year away from a native version.

I have WINE on my machine, but don't know how to use it yet.  I just "didn't get that far".  Just so many issues with sound to deal with.

> I'll keep it in mind. But unless I get a lot more serious about this, I may not need more than a comfortable (non-PC-keyboard) way to find notes/melodies/chords.

Depends on the need.  I personally just HAVE to have a keyboard to play music on.  

> Since I just mentioned WINE... have you tried using that to get around the rebooting? 

No, not really.  As I said I been trying to get the sound working and didn't get that far yet.


> Ok, so I'm clueless, but what happened to the MIDI port?


The Echo Mona doesn't have a midi port physically.  So naturally I would have to use MIDI via other alternatives.  Perhaps the Midi port on my Kontrol 49 keyboard, or perhaps a MIDIMAN USB interface.

I have a MIDIMAN I borrowed from work and it is automagically recognized. 

> I wish I had any ideas, but I seem to be stuck as an eternal newbie. (I just realised I've been using Ubuntu since "Warty Warthog", and Mandrake and SUSE before that...)

Good luck.

Oh -- I *seem* to have got the rt kernel to work at last -- for now, that is -- likely through a random combination of BIOS and kernel boot parameters that'll stop working tomorrow. Until then I'm going to be fannish about my decrepit little computer. Hence the screenshot. Ha.

Edit: Some things already stopped working again. Ha!

I have found that Ubuntu Studio is like that.  Ubuntu in general isn't the most stable distro in Linux-land.  Sometimes you solve one problem, but then inadvertently cause another one.   I found most of my early problems with Hardy were because of OSS.  Once I dropped OSS and went to ALSA, things were 'better'. 

But the big problem is the sound support in Linux.   As you found out with Terratec, and I with the Echo Mona, not everything on the ALSA list WILL work.  So I am thinking the next go round (and probably my final attempt), will be to go with something that is know to be automatically recognized, such as an M-Audio card.

But I believe I have been long enough of an Ubuntu/Linux user to make the statement that Linux is VERY FAR off from being able to handle a full professional recording studio DAW and most likely I am going to just Linux for experimenting with it's audio programs.   But I still think Linux is a long way off from being seriously considered as a "pro" tool for audio mixing applications.  So in that aspect I am probably going to stick with Windows for pro work.

But the good thing is that I can free up Windows from power robbing programs that I no longer need since I will be doing most of my emails and internet surfing in Linux now.   In that aspect Linux works great.  Most video applications surprisingly work fine too in Linux.

Just sound is the problem.  Not enough sound cards are supported and that needs to change.

Have a good day!

Geo

---

### Post by mrowth on 2008-09-21
> **jukingeo said:**
> Hmmmm, hate to say it, but I like the look of Gnome better.  
That's just "my" KDE... I like simple icons, dark backgrounds, no taskbar, and so on. 

As I said, the default looks rather Windows-like. Lots of bright colours, grey, blue, horizontal taskbar at the bottom.

>  BUT I guess if it performs better than it is worth a look see.

I don't know if it performs better; it's supposed to be "bloated", after all. 

I found the KDE "counterpart apps" to take less CPU, but there may various backgroundy things running that I didn't factor in. 

I just find GNOME dreary and rigid and its applications less versatile and capable... it seems quite a few funny/interesting/useful options have been axed (or never implemented) to not confuse new users.

> I am both surprised (and yet not so surprised) the Terratec card didn't work out for you.  They are supposed to be decent cards.  Granted they are not as pro as something like from Echo or RME, but still better than the M-Audio stuff.

As for the SB 16, I am not sure how that will work.  Supposedly it is supported like the SoundBlaster Live.   However, I didn't have good results with my SB Live either.  Sure it was automagically recognized in just about all distributions of Linux I tried.  BUT for some reason Jack didn't take to it.  Games, system sounds, and internet streaming audio worked beautifully, but it absolutely refused to record and it refused to work with Jack.   I will say that I DID have the Dell OEM version of the Sound Blaster Live installed in my machine, so THAT could have been an issue (being not a genuine store bought SB Live).  However, according to ALSA the card IS fully supported.
And I had picked the Terratec card off the ALSA site for that reason... 

> There was another issue I have to warn you about with Sound Blaster.  Many times it is fixed at one frequency.   The Sound Blaster Live WOULD NOT allow settings for recording/playback other than 48k.  So the SB Live is substandard for professional recording work.  I can't imagine the SB 16 to be any better.   I think that card can only do 44.1k.
I really just meant keeping the old SBs around to have working sound at all... "entertainment sound", so to speak. 

> I have WINE on my machine, but don't know how to use it yet.  I just "didn't get that far".  Just so many issues with sound to deal with.
Whatever file manager you're using might run Windows apps automatically. Basically, you just run Windows .exes with /usr/bin/wine, like you might "run" a JPG with GIMP. Not much to it. (If it works, that is.) 

WINE will create a fake Windows "C:\" drive under ~/.wine that newly installed apps will be installed in -- but if you already have Windows apps installed (through a "real" Windows) they might well work without off your Windows partition. (If they work, that is.)

> Depends on the need.  I personally just HAVE to have a keyboard to play music on.  
Yeah, I don't need to play live. I couldn't, anyway. I'm sort of "constructing" my ...things. Playing around. Having no idea what I'm doing, most of the time.

> The Echo Mona doesn't have a midi port physically.  So naturally I would have to use MIDI via other alternatives.  Perhaps the Midi port on my Kontrol 49 keyboard, or perhaps a MIDIMAN USB interface.
I meant the keyboard... can Linux make sense of it through the MIDI port, not USB?

> But the big problem is the sound support in Linux.   As you found out with Terratec, and I with the Echo Mona, not everything on the ALSA list WILL work.  So I am thinking the next go round (and probably my final attempt), will be to go with something that is know to be automatically recognized, such as an M-Audio card.

But I believe I have been long enough of an Ubuntu/Linux user to make the statement that Linux is VERY FAR off from being able to handle a full professional recording studio DAW and most likely I am going to just Linux for experimenting with it's audio programs.   But I still think Linux is a long way off from being seriously considered as a "pro" tool for audio mixing applications.  So in that aspect I am probably going to stick with Windows for pro work.

I don't know the first thing about audio mixing applications... and perhaps just barely the 0.1-st thing about soft synths and related fields...  

> But the good thing is that I can free up Windows from power robbing programs that I no longer need since I will be doing most of my emails and internet surfing in Linux now.   In that aspect Linux works great.  Most video applications surprisingly work fine too in Linux.

Just sound is the problem.  Not enough sound cards are supported and that needs to change.

Have a good day!

Geo
You too!

---

### Post by mrowth on 2008-09-21
.

---

### Post by jukingeo on 2008-09-22
> **mrowth said:**
> That's just "my" KDE... I like simple icons, dark backgrounds, no taskbar, and so on. 

As I said, the default looks rather Windows-like. Lots of bright colours, grey, blue, horizontal taskbar at the bottom.


I don't know if it performs better; it's supposed to be "bloated", after all. 

KDE is bloated?  Then THAT is what I DON'T want.  For a while I was thinking about Xubuntu for an application I had that needed a "slimmed down" OS, but then I was turned on to Puppy Linux and I like that.  It is VERY lightweight and runs pretty fast, even on old systems.  The funny thing is that Puppy DOES see the Echo Mona card, but it just doesn't work, much like your Terratec situation.

> I found the KDE "counterpart apps" to take less CPU, but there may various backgroundy things running that I didn't factor in. 

I just find GNOME dreary and rigid and its applications less versatile and capable... it seems quite a few funny/interesting/useful options have been axed (or never implemented) to not confuse new users.

Yeah, there are a few things with file navigation that needs a "work around", whereas with Windows you could pretty much do anything anywhere.  I noticed that with Linux in general there are varying degrees to the ease of file navigation, but in terms of a Windows comparison, thusfar I found Ubuntu/Gnome to work out fine.  Getting around in Puppy is just slightly more difficult, but still good.


> And I had picked the Terratec card off the ALSA site for that reason... 


I really just meant keeping the old SBs around to have working sound at all... "entertainment sound", so to speak. 

Yeah, I figured too that (with the Echo Mona), I just had to follow a procedure and perhaps do a little tweak here and a little tweak there, and I was done.  As it stands now, I have had the Mona for over a month and finally I am now speaking with an ALSA driver developer, but the response time is SLOW.

I would say that for most applications for playback only, the SB Live IS the best way to go as I really didn't have to do anything with it.  BUT naturally, that isn't my goal.  Considering that my SB Live wrecked havoc with Jack is one reason why I pulled the SB  Live.


> Whatever file manager you're using might run Windows apps automatically. Basically, you just run Windows .exes with /usr/bin/wine, like you might "run" a JPG with GIMP. Not much to it. (If it works, that is.)

Ahhhh, yes, it always SOUNDS easier than it is.

> WINE will create a fake Windows "C:\" drive under ~/.wine that newly installed apps will be installed in -- but if you already have Windows apps installed (through a "real" Windows) they might well work without off your Windows partition. (If they work, that is.)

Did you notice much difference in performance when comparing running the same application through Windows and then through Linux/Wine?  I heard applications run a bit slower.  But as you pointed out a couple times, not everything works with Wine.  It seems like many older applications (2 to 4 years old or more) will work, but many newer applications and games will not.


> Yeah, I don't need to play live. I couldn't, anyway. I'm sort of "constructing" my ...things. Playing around. Having no idea what I'm doing, most of the time.


I meant the keyboard... can Linux make sense of it through the MIDI port, not USB?

Actually I have not tried to access the Midi through the Kontrol49.  I believe it should work though.  If the MIDI is working through USB, it should recognize the ports on the keyboard.

I was mostly concerned that my MIDIMAN MIDISPORT USB Midi interfaces were working (which they do).  My Puppy Linux project is based around a multi-channel organ and I am using several different modules/controllers for that project.   Some of my older Midi keyboards do not have USB capability and need to go into the computer via the MIDISPORT.   But as I indicated earlier, I am happy to say that both my USB keyboard and the MIDISPORTs ARE automagically recognized.

Granted, some of the advanced features of the unit cannot be accessed in Linux because the programs intended to operate those functions were meant to work with either Windows or a Mac.  But being on a dual boot system, for me that isn't a problem.  I can set up my Kontrol49 within Windows and it will memorize its settings.  Then switching to Linux, the keyboard should be able to access the Linux applications via USB/Midi.  

> I don't know the first thing about audio mixing applications... and perhaps just barely the 0.1-st thing about soft synths and related fields...  



Perhaps that is a good thing that you don't need to.  With my applications, I am always looking for ways to get (audio) information in/out of my machine.  So having a good audio interface is mandatory.

But as of now being that ALSA support on my ECHO MONA is pretty slow going, I have been exploring the option of buying an M-Audio Delta series card.  Supposedly this series doesn't have many issues with Linux and in many cases is automagically recognized.    It is just that M-Audio usually isn't very high end.  They are more or less "project studio" oriented devices.

If M-Audio doesn't work out for me then I am going to go back to the Sound Blaster and just work in Windows until perhaps FFADO is finally seamlessly working with Linux.  Going that route I can use a Firewire device and then I don't have to go crazy and open up my machine all the time.

So there are still a couple of things I can try.  Overall, I AM happy with Linux and Ubuntu (for general housekeeping and running (older) games). But on the DAW or Studio side of things I am very disappointed.  I am a bit put back by that there are only a handful of "basic" sound cards that work with Linux.  Sound support in Linux MUST be greatly improved if the operating system is to be taken seriously for professional work.

Geo

---

### Post by mrowth on 2008-09-22
> **jukingeo said:**
> KDE is bloated?  Then THAT is what I DON'T want.  For a while I was thinking about Xubuntu for an application I had that needed a "slimmed down" OS, but then I was turned on to Puppy Linux and I like that.  It is VERY lightweight and runs pretty fast, even on old systems.  The funny thing is that Puppy DOES see the Echo Mona card, but it just doesn't work, much like your Terratec situation.

Yeah, there are a few things with file navigation that needs a "work around", whereas with Windows you could pretty much do anything anywhere.  I noticed that with Linux in general there are varying degrees to the ease of file navigation, but in terms of a Windows comparison, thusfar I found Ubuntu/Gnome to work out fine.  Getting around in Puppy is just slightly more difficult, but still good.
KDE *is* the "**k**itchen sink desktop environment"... on my old Pentium 3 I booted into Fluxbox to run JACK. Several GHz later, though, the difference is negligible. And it really is ridiculously configurable in places. See what praise [http://insanecoding.blogspot.com/2007/03/file-dialogs.html](http://insanecoding.blogspot.com/2007/03/file-dialogs.html) has for KDE 3.5's file selector -- vs. GNOME's or, sadly, KDE 4's. (KDE 4 is a wholly different beast...)
[COLOR="Gray"]
(Unfortunately, even Kubuntu Hardy's KDE 3.5.9 uses Dolphin by default. Nothing wrong per se with its narrower focus on quick'n'easy "breadcrumb-supported" file management -- but I want my "tree" view, I want to know where links point, and I want to be able to go up from /home/username -- or any bookmarked places whatsoever for that matter. What's up with that, anyway? You drill down to some subdirectory that also happens to have been bookmarked earlier, and the entire path collapses to show just it as though it were a top-level directory. The Dolphin website has this under "features": "The Dolphin places concept allows to hide the physical file hierarchy. For example if a bookmark called 'My Documents' is created which is represented by the URL 'file:///home/peter/Documents' (...)". Does it *help* new users if they're intentionally mislead? Fortunately, it is easily replaced with Konqueror.)[/COLOR]

> Yeah, I figured too that (with the Echo Mona), I just had to follow a procedure and perhaps do a little tweak here and a little tweak there, and I was done.  As it stands now, I have had the Mona for over a month and finally I am now speaking with an ALSA driver developer, but the response time is SLOW.

That's something to put hope in regardless... 

> I would say that for most applications for playback only, the SB Live IS the best way to go as I really didn't have to do anything with it.  BUT naturally, that isn't my goal.  Considering that my SB Live wrecked havoc with Jack is one reason why I pulled the SB  Live.

If I recall correctly -- whatever (ancient!) Soundblaster it was (Ensoniq ES 1370 based), it was unproblematic. I was using JACK at the time, so I suppose I tested it with that. Though there may have been issues with the sampling frequency... I was juggling .asoundrc files a lot... and not entirely clear on what the card "ought to" offer. Anyway, worth keeping aruond, in case everything else spontaneously explodes.

> Did you notice much difference in performance when comparing running the same application through Windows and then through Linux/Wine?  I heard applications run a bit slower.  
It's been years that I "really" used Windows, so I'm not too sure how fast stuff is supposed to run. 

"Plain" apps like Paint Shop Pro 7 seem snappy enough. 8-bit emulators run okay. And apart from crashing the KDE panel, the Windows port of the OpenGL shooter "Nexuiz" also seems to run *perfectly* through WINE with effects set to "high" - no worse than the native Linux version. (One does of course tend to use WINE  to run apps that *don't* have a native Linux version.) 

I suppose if I ran a lot of those things all at the same time, I'd get slowdowns...? Jiggling the mouse over a custom VSTi GUI *real fast* can bring CPU usage up to 50%. Still the track plays without a hitch, and it uses a whole bunch of plugins. At 48 kHz, anyway.


> But as you pointed out a couple times, not everything works with Wine.  It seems like many older applications (2 to 4 years old or more) will work, but many newer applications and games will not.
Yes, pretty much... 

I haven't investigated DirectX 3D game stuffs, though... and there're commercial WINE distributions for MS Office and games, I think.

> 
Actually I have not tried to access the Midi through the Kontrol49.  I believe it should work though.  If the MIDI is working through USB, it should recognize the ports on the keyboard.

I was mostly concerned that my MIDIMAN MIDISPORT USB Midi interfaces were working (which they do).  My Puppy Linux project is based around a multi-channel organ and I am using several different modules/controllers for that project.   Some of my older Midi keyboards do not have USB capability and need to go into the computer via the MIDISPORT.   But as I indicated earlier, I am happy to say that both my USB keyboard and the MIDISPORTs ARE automagically recognized.

Go, Linux, go! :)

> Granted, some of the advanced features of the unit cannot be accessed in Linux because the programs intended to operate those functions were meant to work with either Windows or a Mac.  But being on a dual boot system, for me that isn't a problem.  I can set up my Kontrol49 within Windows and it will memorize its settings.  Then switching to Linux, the keyboard should be able to access the Linux applications via USB/Midi.  



Perhaps that is a good thing that you don't need to.  With my applications, I am always looking for ways to get (audio) information in/out of my machine.  So having a good audio interface is mandatory.

I'm relatively okay with things not being that great -- I don't have to meet professional demands (or any demands, really). Though I do want stuff to work, of course, and sound half-way decent. But I suspect it's largely my lack of expertise that's in the way of that. I mean... people have been and are making great music with just about anything that makes noises.

> But as of now being that ALSA support on my ECHO MONA is pretty slow going, I have been exploring the option of buying an M-Audio Delta series card.  Supposedly this series doesn't have many issues with Linux and in many cases is automagically recognized.    It is just that M-Audio usually isn't very high end.  They are more or less "project studio" oriented devices.

If M-Audio doesn't work out for me then I am going to go back to the Sound Blaster and just work in Windows until perhaps FFADO is finally seamlessly working with Linux.  Going that route I can use a Firewire device and then I don't have to go crazy and open up my machine all the time.
Would that magically make every Firewire audio thing work, though? 

> So there are still a couple of things I can try.  Overall, I AM happy with Linux and Ubuntu (for general housekeeping and running (older) games). But on the DAW or Studio side of things I am very disappointed.  I am a bit put back by that there are only a handful of "basic" sound cards that work with Linux.  Sound support in Linux MUST be greatly improved if the operating system is to be taken seriously for professional work.

Geo
I'm wondering... would it really kill manufacturers to support Linux instead of letting Linux developers poke around in the dark?

---

### Post by thorgal on 2008-09-22
go RME HDSP (PCI or cardbus), pricy but works a treat out of the box and quality is great! :)
I had an MAudio Delta1010LT, worked also good but when I got serious about my studio, I had to replace it and the difference was really noticeable with RME.

---

### Post by jukingeo on 2008-09-24
> **thorgal said:**
> go RME HDSP (PCI or cardbus), pricy but works a treat out of the box and quality is great! :)
I had an MAudio Delta1010LT, worked also good but when I got serious about my studio, I had to replace it and the difference was really noticeable with RME.

Yes, I am very well aware of the RME line of products and supposedly they are just as easy to set up as M-Audio.  The trouble is with a wife out of work, 2 children to feed, and my job not doing so great...lets just say I can't afford an RME card right now.  But it is well noted and I will keep it in mind in the future.

Right now I just need something that I can try out the Linux based audio applications with.  Something that has more than 2in/out something that has BALANCED connections.

So far it would seem my pick would be either the M-Audio Delta 44 or 66.  Why not the 1010?  Well, unless you get a good deal on it used, it is also pretty expensive for something that doesn't have mic pre-amps.   So I know I need a good mic pre-amp as well with the M-Audio line.

---

### Post by thorgal on 2008-09-24
> **jukingeo said:**
> it is also pretty expensive for something that doesn't have mic pre-amps.   So I know I need a good mic pre-amp as well with the M-Audio line.

not quite, the 1010 has 2 mic preamps associated to its 2 XLR inputs (IIRC, there were 2 XLR inputs - mic level).

---

### Post by jukingeo on 2008-09-24
> **thorgal said:**
> not quite, the 1010 has 2 mic preamps associated to its 2 XLR inputs (IIRC, there were 2 XLR inputs - mic level).

Which 1010 are you referring to?

This is the one I am referencing:

[http://www.midiman.com/products/en_us/Delta1010.html](http://www.midiman.com/products/en_us/Delta1010.html)

There aren't any XLR jacks on this unit.

---

### Post by thorgal on 2008-09-25
I am talking about the 1010LT, should have been more precise :p

[http://www.midiman.com/images/global/media_hqpics/delta1010lt.jpg](http://www.midiman.com/images/global/media_hqpics/delta1010lt.jpg)

But the PCI card chips are the same. The 1010 IO box seems dull, you would probably need adaptors XLR -> RCA, which is not the best ... XLR is balanced but not RCA. That's the drawback of the 1010 serie, no balanced IOs.

---

### Post by jukingeo on 2008-09-25
> **thorgal said:**
> I am talking about the 1010LT, should have been more precise :p

[http://www.midiman.com/images/global/media_hqpics/delta1010lt.jpg](http://www.midiman.com/images/global/media_hqpics/delta1010lt.jpg)

But the PCI card chips are the same. The 1010 IO box seems dull, you would probably need adaptors XLR -> RCA, which is not the best ... XLR is balanced but not RCA. That's the drawback of the 1010 serie, no balanced IOs.


Ahh, yes, I see it now.  I never really considered the 1010LT version because of the unbalanced line in/outs, I also "assumed" that if the entire Delta series didn't have mic pre's why would the LT version?  So, I really like the idea that I don't have to connect another mixer with the 1010LT and can connect two mics directly to it.

With the 1010 (standard version), the balanced ins/outs do allow a bit more flexibility in regards to connections.  I do have a Mackie 1402 mixer and as such could borrow preamps from that, if need be.  But, with the 1010 I HAVE to do that if I want to hook up just one mic.  

The Echo Mona device I have now is all XLR balanced (not TRS).  And it has it has FOUR pre-amps (with gains and meters).  It is 4 in and 6 out, which is really what I need.  It sounds beautiful in Windows, but I just can't get the darn thing to run in Linux.

I can squeeze by on the Delta 44 or 66, it is just going to be a pain to hook up the mixer/pre-amp every time I want to use mics. (That is until I get a separate pre-amp later down the road).

In the home, I only occasionally use a mic or maybe two.  But on the road I would average 4 or more...but then that isn't a biggie because I WILL have the mixer with me for live work.

---

### Post by mrowth on 2008-10-19
> **jukingeo said:**
> Ahh, yes, I see it now.  I never really considered the 1010LT version because of the unbalanced line in/outs, I also "assumed" that if the entire Delta series didn't have mic pre's why would the LT version?  So, I really like the idea that I don't have to connect another mixer with the 1010LT and can connect two mics directly to it.

That's why I picked it out instead of the 66. Not that I can afford either at the moment. 

I still suppose I'm in for the shock of my Linux lifetime when I upgrade (?) to a "real" sound interface. 

I'm used to running JACK on hw:0 without it blocking any other applications. 

The dawn of PulsaAudio was making me nervous so I installed it on my Kubuntu 8.04.1 system. It ran without a hitch alongside ALSA-using JACK, last.fm (Flash), and Pidgin. I don't think ALSA funneled anything into Pulse, either; at least, I did not create an .asoundrc to that effect. 

Then I uninstalled it again because I saw and see no need for it (in my case). ALSA or ALSA+JACK already do everything I need without adding another layer of complexity. 

Will an M-Audio card be the end of this "mixing freedom"? I don't want to go back to 2004 or whenever stuff last blocked each other all the time...

---

### Post by jukingeo on 2008-10-19
> **mrowth said:**
> 
I still suppose I'm in for the shock of my Linux lifetime when I upgrade (?) to a "real" sound interface. 

I'm used to running JACK on hw:0 without it blocking any other applications. 

The dawn of PulsaAudio was making me nervous so I installed it on my Kubuntu 8.04.1 system. It ran without a hitch alongside ALSA-using JACK, last.fm (Flash), and Pidgin. I don't think ALSA funneled anything into Pulse, either; at least, I did not create an .asoundrc to that effect. 

Then I uninstalled it again because I saw and see no need for it (in my case). ALSA or ALSA+JACK already do everything I need without adding another layer of complexity. 

Will an M-Audio card be the end of this "mixing freedom"? I don't want to go back to 2004 or whenever stuff last blocked each other all the time...

As of now I do not have PulseAudio or any other layered sound drivers on my system.  I had to do that with OSS and it caused MAJOR problems.  Right now I ONLY have ALSA.  Now as far as the interaction goes between running programs...such as playing a game while listening to music off of YouTube (streaming audio mixed with a game).  I can say that is asking for trouble.  Linux isn't Windows and mixing applications is something that really hasn't been fully ironed out.

Last night I found I was able to mix two streams at once and there were no problems with it.

I know that Jack usually doesn't like anything taking sound from it.  I have not tested mixing with Jack yet, but I know that when I had OSS on my X-Fi card, Jack didn't want to cooperate with other audio applications. OSS with Pulse did work for a short time with games and YouTube together, but then OSS had an upgrade, which did away with the need for Pulse, but it also knocked out streaming audio and I had no sound on the internet.

EDIT:

I just tested Jack with streaming audio on You Tube with my Delta 44.  It WILL NOT work together.  I repeat:  Jack and streaming internet audio WILL NOT work together.

It will go without saying that Jack will probably not work with games either.

For me that isn't a big deal.  Jack can be set up to work with most of the "pro" applications within a Linux distribution.  So once it is running, you can patch your audio devices into it.  The best thing is that if you need to record something from a streaming source is to do it live and save the source on your system.  Then play back the audio file in something like Audacity or Ardour which uses Jack.

I don't know if this was what you were referring to in regards to mixing.  I know if this was Windows, it WOULD work.  But it isn't.

During my ordeals with getting sound applications to run properly in Linux I found out a few things and many I learned the hard way.

1) For housekeeping Linux is pretty much on par with most internet browsers and MS Office type data processing programs.
2) Sound support is WAY behind the times.  Only much older devices or those that have excellent support work well.
3) Very High end DAW work or high end gaming simply will not happen in this OS.

Simply put, I think Linux is still a WAYS off from a good reliable pro-audio DAW.  For a project studio and for tinkering around with the cool programs, yes, that you can do.  Would I say you can use a Linux based DAW for a commercial application?  No, absolutely not.

Now I may change my tune on what I said above based on any new found discoveries based on my new sound card.  For the most part the Delta 44 is working with just about everything in ALL of my Linux distributions (I am running 4 now).  So I can't complain too much.

Prior to my getting the Delta 44 I had nothing but problems configuring audio.  I actually almost gave up on Linux entirely for audio work.  I was just going to use it for housekeeping and playing older emulated console games.  But the Delta 44 was my last attempt to get DAW based programs to work, and I am happy to say that it DOES work with Jack beautifully AND with the RT kernel no less.  I couldn't do that with the Soundblaster X-Fi or Live.  The Soundblaster Live was pathetic...it couldn't even record/play outside of 48k sample rate.

My experiences with the so called "Alsa Supported" Echo Mona device was even more disasterous.  I couldn't get it to work AT ALL in ANY Linux Distribution.  Support from the Alsa developer that created the driver was poor at best.

That was when I threw in the towel and wanted to get a card that was PROVEN to work.   Thusfar the only two companies that make cards that work automatically were M-Audio and RME.  But RME was too expensive for me.

The future does look bright for Linux though and it is improving in leaps and bounds.  I am hoping one day audio device support will increase dramatically.  But for now I believe your best low cost option is limited to the M-Audio Delta Line.

I do still have many more tests to run and really have not done any serious recording yet, but thusfar for general playback using both sound for regular system functions (games, internet, etc) and Jack.  I am good.  For the most part I can finally test out all those nice Linux audio applications.

Before I do some serious recording though, I am going to see if I can get some video editing applications to work as well. 

But all in all, so far so good.  It isn't a "perfect" system, but it is MUCH better than trying to get the mediocre results I had the past four months.  If hindsight was 20/20, I would have listened more closely to those that kept saying to go with the M-Audio cards and I would have saved quite a bit of time and troubles.

Hope you have good results with your M-Audio card when you get one.

Geo

---

### Post by mrowth on 2008-10-19
> As of now I do not have PulseAudio or any other layered sound drivers on my system. I had to do that with OSS and it caused MAJOR problems. Right now I ONLY have ALSA. Now as far as the interaction goes between running programs...such as playing a game while listening to music off of YouTube (streaming audio mixed with a game). I can say that is asking for trouble. Linux isn't Windows and mixing applications is something that really hasn't been fully ironed out.

I know I had to run the ALSA "default" device through an ALSA dmix plugin a couple versions ago so apps wouldn't block each other's audio.
 
JACK, of course, was one of those apps: so without dmix no JACK + Flash or JACK + game or JACK + mediaplayer. 

No biggie -- the "dmix" trick worked, after all... usually. 

Then even that little workaround became obsolete when the default device provided dmix without further prompting. What I still don't understand is why even hw:0 provides mixing now, in several scenarios. I can have Audacity play or record Flash or whatever other sound sources there may be through ALSA: VIA 8237: VIA 8237 (hw:0,0/1) and at the same time run JACK on hw:0 without one bothering the other.
 
I suppose non-"productive" users (no JACK required) could compensate with Pulse. It looks like unnecessary complexification/overhead to me, as appealing as being forced to run several different webservers, but wouldn't it provide reliable audio mixing (among other things)? Since ALSA can be configured to send ALSA-using apps' audio to Pulse, you should (or: might) be able to run a pure Pulse setup... right? 

Unless, I suppose, you're planning to use JACK, by which I mean "completely dependent on it". JACK and Pulse getting along would either tax ALSA's software mixing, or Pulse's, or whatever... at any rate, it doesn't sound like low latencies.

> I know that Jack usually doesn't like anything taking sound from it. I have not tested mixing with Jack yet, but I know that when I had OSS on my X-Fi card, Jack didn't want to cooperate with other audio applications. OSS with Pulse did work for a short time with games and YouTube together, but then OSS had an upgrade, which did away with the need for Pulse, but it also knocked out streaming audio and I had no sound on the internet.

OSS still has upgrades?... I thought it was part of ALSA these days, i.e. emulated by ALSA for the sake of those legacy apps that insist on talking to OSS...

> EDIT:

I just tested Jack with streaming audio on You Tube with my Delta 44. It WILL NOT work together. I repeat: Jack and streaming internet audio WILL NOT work together.

What if you put JACK on ALSA "default"? Not ideal, I suppose (I didn't notice a difference myself, though), but would it work?

> For me that isn't a big deal. Jack can be set up to work with most of the "pro" applications within a Linux distribution. So once it is running, you can patch your audio devices into it. The best thing is that if you need to record something from a streaming source is to do it live and save the source on your system. Then play back the audio file in something like Audacity or Ardour which uses Jack.

I don't know if this was what you were referring to in regards to mixing. I know if this was Windows, it WOULD work. But it isn't.

I'm not sure what you mean by "do it live"...
 
What I'd do now is fire up Rezound or Audacity (because it doesn't need to have JACK running for it -- though if JACK *is* running, it'll use it, too) and hit the record button to capture whatever's playing. 

But apparently that's going to stop working when I upgrade from 48kHz/16 bit onboard ALC850 sound to a real soundcard (:confused:, :mad:, and :rolleyes:)? (Though by then PCs will probably have just 1 PCI slot left underneath a square yard of fans, heatsinks and video cards... I'm already wondering how to connect my existing - and mostly *working*! - peripherals/cards to a new motherboard - none that I've found have enough PCI, PATA or parallel slots/ports.)

I'm still half hoping I can get the Delta set up in a similarly fashion, though I'm sure there'll be a year of frustration until I've figured out what's what and what just won't work. (Hm, care to take a snapshot of the full (playback + capture) alsamixer window for your Delta? Mine looks intimidating enough already. At least half of those things I don't know what they're for, to be honest.)

---

### Post by markbuntu on 2008-10-22
You can use pulseaudio with jack through the pulse-audio-module-jack which is in the debian repos. Why this is not in the ubuntu repos I do not know because it works fine in ubunutu hardy.

Any application playing through pulseaudio is available to be switched to the pulse-jack sink which makes it available to any jack application. I use it myself occaisionally to record flash audio and internet radio streams from amarok or xmms in ardour, or just to add some jack-rack effects for more pleasing sound.

According to the pulse devs pulseaudio provides lower latency and is more reliable than dmix for mixing the audio from multiple applications. Also according to the pulse devs, pulseaudio introduces no latency except when resampling where some latency is unavoidable no matter what does it. Anyway if you are just capturing audio streams for recording, latency is not really an issue for that.

With two sound cards a usb headest and usb webcam, pulseaudio makes my life a lot easier and now that I have it working with jack....

---

### Post by mrowth on 2008-10-22
> **markbuntu said:**
> You can use pulseaudio with jack through the pulse-audio-module-jack which is in the debian repos. Why this is not in the ubuntu repos I do not know because it works fine in ubunutu hardy.

Any application playing through pulseaudio is available to be switched to the pulse-jack sink which makes it available to any jack application. I use it myself occaisionally to record flash audio and internet radio streams from amarok or xmms in ardour, or just to add some jack-rack effects for more pleasing sound.

According to the pulse devs pulseaudio provides lower latency and is more reliable than dmix for mixing the audio from multiple applications. Also according to the pulse devs, pulseaudio introduces no latency except when resampling where some latency is unavoidable no matter what does it. Anyway if you are just capturing audio streams for recording, latency is not really an issue for that.

With two sound cards a usb headest and usb webcam, pulseaudio makes my life a lot easier and now that I have it working with jack....

You mean let Pulse plug Pulse-using apps into JACK which is plugged into Pulse which is plugged into ALSA...?

Sorry, I'm not sure I still see how all this links together, still hoping against hope it'll never become necessary

---

### Post by jukingeo on 2008-10-22
> **mrowth said:**
> I know I had to run the ALSA "default" device through an ALSA dmix plugin a couple versions ago so apps wouldn't block each other's audio.
 
JACK, of course, was one of those apps: so without dmix no JACK + Flash or JACK + game or JACK + mediaplayer. 

It is weird that some applications DO mix, and some don't.  For instance, if I decide to play TWO instances of You Tube with different videos, songs, etc...the sound WILL mix.  But if I go to another website that streams it's audio differently..it may or may not work.

Last night I was listening to a song on You Tube and I started up Gens (A Sega Genesis game console emulator) and the audio mixed as well.

But Jack...well, Jack is picky.  It wants the audio for itself.  


> No biggie -- the "dmix" trick worked, after all... usually. 

Then even that little workaround became obsolete when the default device provided dmix without further prompting. What I still don't understand is why even hw:0 provides mixing now, in several scenarios. I can have Audacity play or record Flash or whatever other sound sources there may be through ALSA: VIA 8237: VIA 8237 (hw:0,0/1) and at the same time run JACK on hw:0 without one bothering the other.
 
I suppose non-"productive" users (no JACK required) could compensate with Pulse. It looks like unnecessary complexification/overhead to me, as appealing as being forced to run several different webservers, but wouldn't it provide reliable audio mixing (among other things)? Since ALSA can be configured to send ALSA-using apps' audio to Pulse, you should (or: might) be able to run a pure Pulse setup... right? 

Uhhhh, you lost me a bit back there.  I know when I had OSS on my system I had to deal with the Pulse Audio layering.  I abandoned it because only half of my applications worked with the OSS/Pulse combo. Then as you mentioned above, if you change something with your sound configuration, then you knock something else out.  In my case, I did an OSS upgrade in which I no longer needed Pulse for my game sound...however, that knocked out my streaming internet.  Jack never worked with OSS (or OSS/Pulse).  I got fed up with OSS because of this.  So I went ALSA.  Initially that wasn't roses either.  I had the SB X-Fi and I needed a special kernel build to get it to work with ALSA.  I DID get it to work...and with Jack too, but there were shortcomings. 1) It ONLY worked in Ubuntu 2) It didn't work in real-time.

> Unless, I suppose, you're planning to use JACK, by which I mean "completely dependent on it". JACK and Pulse getting along would either tax ALSA's software mixing, or Pulse's, or whatever... at any rate, it doesn't sound like low latencies.

Yes, when it comes to my DAW based applications, I make sure that they can be routed through Jack.  I just shut everything down (including system sounds) and start Jack up.  After that I ONLY start Jack based applications and pipe everything through Jack.  I know it may sound restricting at first, but it isn't.   Think of Jack as you would a Digital to Analog converter (in the real world).   Now think of all of your audio pieces coming together in one place.  Everything is configured by the Digital to Analog converter and then finally the resultant output is converted to Analog and sent to your Amp.  That is kind of what Jack does in the virtual realm.  It gathers all of your audio applications in one place and then configures them as you need.  Then it pipes the result through the ALSA driver and to your sound card.

If you have one application that has it's ALSA driver, then another that has it's driver, and so on and so on...something is bound to trip up.

I guess one reason why Jack is very picky about sound is because sound processing does take up computer power.  So as you pointed out...latency is a big factor to take into consideration.

So the more I am playing with Linux/Ubuntu/Jack in a DAW based scenario, the more I am liking Jack.

But outside of using the STUDIO aspect of Ubuntu Studio I am using straight ALSA.   

> OSS still has upgrades?... I thought it was part of ALSA these days, i.e. emulated by ALSA for the sake of those legacy apps that insist on talking to OSS...

I think you mean OSS is a part of Ubuntu, not ALSA.  Up until Hardy, I believe OSS WAS the favored application, but now because of the switch over to primarily ALSA is perhaps the reason why there are so many issues with sound here in Ubuntu.   Ubuntu now favors ALSA.   Sure there overlays in which you can technically convert from OSS to ALSA and vice versa.  Jack has something like that, but it rarely works.


> What if you put JACK on ALSA "default"? Not ideal, I suppose (I didn't notice a difference myself, though), but would it work?

Not sure what you mean by that.  If you mean setting Jack to the ALSA driver?  Yes, that is where I have mine set.  As I said in a prior post, I am not running ANY kind of audio overlays, patches or what not.  I am just strictly ALSA.  General system applications (Games, streaming internet, etc) are straight ALSA.  Audio/Video editing and processing applications I set to go through Jack.

> I'm not sure what you mean by "do it live"...

On the Fly....right there and then.  Recording off of streaming internet with straight ALSA while attempting to record using a Jack based application.  THAT will not work.  I know that for sure.  If you recorded what you wanted outside of Jack (an audio/video capture) and THEN put that resultant file into a Jack based program...then you can edit it.
 
> What I'd do now is fire up Rezound or Audacity (because it doesn't need to have JACK running for it -- though if JACK *is* running, it'll use it, too) and hit the record button to capture whatever's playing.

Audacity can run with or without Jack.  That would add to your advantage because if Audacity works with streaming internet at the same time, you can record what you want and then set Audacity to Jack when you want to use Jack based applications.  I tried to do this with my X-Fi card and I had a bit of a latency stuttering problem with Audacity outside of Jack.  It worked...but not very well.  However, within Jack Audacity recorded beautifully.

I ended up using another program for my "outside Jack" recording and that program was called Sweep.  I believe it is in the repos.

> But apparently that's going to stop working when I upgrade from 48kHz/16 bit onboard ALC850 sound to a real soundcard (:confused:, :mad:, and :rolleyes:)? (Though by then PCs will probably have just 1 PCI slot left underneath a square yard of fans, heatsinks and video cards... I'm already wondering how to connect my existing - and mostly *working*! - peripherals/cards to a new motherboard - none that I've found have enough PCI, PATA or parallel slots/ports.)

Oh!  I have to warn you about something with Jack being that you mentioned sample frequency. You MUST have your sample rates in your applications all synced up.  If you don't either Jack will crash, or you get weird results like the audio playing slow or too fast.  So be very careful about recording now if you have a fixed recording frequency.

> I'm still half hoping I can get the Delta set up in a similarly fashion, though I'm sure there'll be a year of frustration until I've figured out what's what and what just won't work. (Hm, care to take a snapshot of the full (playback + capture) alsamixer window for your Delta? Mine looks intimidating enough already. At least half of those things I don't know what they're for, to be honest.)

Setting up the Delta was a dream.  There WAS no setup, no frustration.  The card was automatically recognized in Ubuntu...not only that, but ALL my Linux distributions.  Setting up the Envy24 gui was a bit tricky, but I did get it going.  So I am using that as my 'general' volume application right now.  As for taking a picture of Alsamixer, I have still yet to master any audio recording apps in Linux let alone anything that has to do with pictures and video.  In simpler terms, I don't know how to post a picture here.

What you do have to do though is MAKE SURE you disable your on-board audio device before plugging in an M-Audio Delta card.  I hear many people having problems getting multiple sound devices to work in Linux.  So you can reduce your headache by 10 fold if you make sure you disable your on board sound.

I only have the Delta 44 in my system right now.  I was going to put it side by side with a SB Live, but I decided against it and I am glad I did.  I was totally amazed at how seamless the Delta 44 was when everything else before gave me so much grief.  If I didn't know any better it would seem like they designed Linux around the Delta series cards.

Sure the Delta 44 doesn't have anywhere near the features and in/out options I would like, but the bottom line is that it is working.  I am running right now a triple boot computer in which I have Windows XP, Ubuntu Studio, and Puppy Linux.   I also have outside my system a bootup to Dynebolic (which didn't require a hard drive partition) and I am also experimenting with OpenSuSE 11.0.   ALL...meaning everything, have sound with the Delta 44.

Considering I was struggling for four months with sound...well, this was a huge burden off my shoulders and now I can enjoy all those Linux applications.

 

Geo

---

### Post by mrowth on 2008-10-22
> **jukingeo said:**
> It is weird that some applications DO mix, and some don't.  For instance, if I decide to play TWO instances of You Tube with different videos, songs, etc...the sound WILL mix.  But if I go to another website that streams it's audio differently..it may or may not work.
That IS weird...
> Last night I was listening to a song on You Tube and I started up Gens (A Sega Genesis game console emulator) and the audio mixed as well.
Knowing OSS doesn't mix audio at all I used to think ALSA (if set up to run everything through a dmix plugin) was the rescue. Now my sound"card" seems to have magically acquired hardware mixing. JACK (using ALSA, hw:0) + Audacity playback (using OSS for a change) + Amarok (using OSS likewise) + Pidgin (using ALSA) + Flash plugin (I don't know what it's using, not JACK) + = mixing fine. From all that I read that shouldn't even be impossible: several apps using OSS? 

(At least Audacity is having problems *recording* additional tracks while playing back existing tracks; starting a Commodore emulator running through WINE (ALSA) gives it playback problems also: strangely enough, it doesn't even work with ALSA's allegedly soft-mixing devices... which it *should*, no? But then, there's always JACK. It's just that so little of this makes any sense to me.)


> But Jack...well, Jack is picky.  It wants the audio for itself.  
> [quote]What if you put JACK on ALSA "default"? Not ideal, I suppose (I didn't notice a difference myself, though), but would it work?
Not sure what you mean by that. If you mean setting Jack to the ALSA driver? Yes, that is where I have mine set. [/quote]
Yes, I mean the ALSA driver... but additionally a specific ALSA interface: "default" or "dmix" or "plughw:" or whatever else provides software mixing, whereas the "hw:" interfaces bypass this and provide the direct-most access to the hardware. Shouldn't that allow you to use JACK & JACK apps along with other applications - as long as those can be configured to likewise use an ALSA software mixing interface instead of "hw:"? Hypothetically, at least? I can't test it because I see no rhyme or reason to whatever works here.



> I think you mean OSS is a part of Ubuntu, not ALSA. Up until Hardy, I believe OSS WAS the favored application, but now because of the switch over to primarily ALSA is perhaps the reason why there are so many issues with sound here in Ubuntu. Ubuntu now favors ALSA. Sure there overlays in which you can technically convert from OSS to ALSA and vice versa. Jack has something like that, but it rarely works.

I did mean part of ALSA, actually, although I suppose something like "emulation/compatibility layer" would be more correct. I'm not too clear on the internals here, nor am I a programmer. From Wikipedia: *"Advanced Linux Sound Architecture (known by the acronym ALSA) is a Linux kernel component intended to **replace** the original Open Sound System (OSS) for providing device drivers for sound cards. ... In the 2.6 version [of the Linux kernel] it **replaces** OSS by default, although a backwards-compatibility layer exists."* (Emphases mine!) 

However, I've never tried the "real", new, software-mixing-capable OSS (4) -- that is, I've never installed or upgraded OSS, and only ever seen whatever OSS interfaces ALSA provides for the sake of compatibility. And that's the only OSS I've been talking about here. Sorry about the confusion. I had pretty much forgotten/ignored that OSS was still being developed "elsewhere".


> Oh!  I have to warn you about something with Jack being that you mentioned sample frequency. You MUST have your sample rates in your applications all synced up.  If you don't either Jack will crash, or you get weird results like the audio playing slow or too fast.  So be very careful about recording now if you have a fixed recording frequency.I've been using both lower sample rates (old 8 bit samples included) and higher sample rates, partly out of convenience, partly out of necessity, partly in much the same way editing images at high resolutions yields better results even when you end up printing them at very small sizes... didn't notice speed/pitch problems or crashes. Isn't JACK resampling everything to whatever you set it up to, within the limits imposed by the hardware? (Maybe I should read the manual.)



> What you do have to do though is MAKE SURE you disable your on-board audio device before plugging in an M-Audio Delta card. That would be a problem, because Linux never cared if it was disabled. But I've been running two cards before; it was more of a nuisance than a showstopper...

---

### Post by thorgal on 2008-10-23
ALSA has an OSS emulation layer. This is how it conceptually works :

at boot time, the kernel loads the ALSA driver. That one is the only thing that really matters. If the ALSA driver is not loaded or does not work properly, you're screwed. Of course, it could be that you are using a custom kernel where you disabled ALSA and instead chose the deprecated OSS. In this case, the OSS driver will be loaded. But nowadays, this is quite unlikely as ALSA is far more superior and is the default low level sound architecture. Anyway, let's stick to ALSA for now.


Then, if ALSA was configured with OSS emulation and your /etc/modprobe.d/alsa-base is set up so this emulation is to be loaded at boot time, the kernel will load these emulation modules (snd-pcm-oss, snd-mixer-oss, snd-seq-oss IIRC). The only thing these modules provide is a fake OSS environment : creation of /dev/dsp's, and emulation of OSS io calls for applications that want to use OSS. All this is fake. It is just a layer to fool apps that still want to use OSS (/dev/dsp). This OSS emul. layer will talk to the real ALSA driver, it's some sort of translator : OSS io calls to ALSA io calls.

About jack : some ppl have hacked an jack OSS emulation called oss2jack. It is, from the user standpoint, the same concept : a layer that creates some /dev/dsp and translates OSS io calls from apps to the jack "language". oss2jack is in fact a jack client with jack input and output ports. For an app that's using OSS (for example the firefox flash plugin by default), jack does not exist, it's invisible, oss2jack will look like an OSS environment. But in fact, it is just a bridge to the jack graph. This is very convenient for users like me who use jack ALL the time as you sometimes need oss2jack because of some apps that were not updated to more modern audio layers.

---

### Post by mrowth on 2008-10-23
oss2jack does sound like it could ease the transition to a Delta card (if it has the issues jukingeo describes), although the installation instructions sound quite ...invasive. Thanks for the hint...

---

### Post by markbuntu on 2008-10-23
> **mrowth said:**
> You mean let Pulse plug Pulse-using apps into JACK which is plugged into Pulse which is plugged into ALSA...?

Sorry, I'm not sure I still see how all this links together, still hoping against hope it'll never become necessary

A lot of people seem to be misunderstanding what pulseaudio is and what alsa is. Alsa is actually two parts, low level drivers and a sound server for application interface that has things like dmix and esd grafted onto it. Jack bypasses the alsa sound server and uses the low level drivers directly.

Pulseaudio replaces the alsa sound server and dmix and esd and also directly addresses the low level alsa drivers. But pulseaudio does not always need to do this the way jack does. Pulseaudio can also use virtual sinks to direct audio to. Like ones for jack and network broadcasting and for multiple sound cards.

When the pulse-jack sink is used, pulseaudio just hands the application audio to jack in a way that jack can understand. It does not use alsa or dmix or esd, it does this directly with zero latency.

---

### Post by markbuntu on 2008-10-23
> **thorgal said:**
> ALSA has an OSS emulation layer. This is how it conceptually works :

at boot time, the kernel loads the ALSA driver. That one is the only thing that really matters. If the ALSA driver is not loaded or does not work properly, you're screwed. Of course, it could be that you are using a custom kernel where you disabled ALSA and instead chose the deprecated OSS. In this case, the OSS driver will be loaded. But nowadays, this is quite unlikely as ALSA is far more superior and is the default low level sound architecture. Anyway, let's stick to ALSA for now.


Then, if ALSA was configured with OSS emulation and your /etc/modprobe.d/alsa-base is set up so this emulation is to be loaded at boot time, the kernel will load these emulation modules (snd-pcm-oss, snd-mixer-oss, snd-seq-oss IIRC). The only thing these modules provide is a fake OSS environment : creation of /dev/dsp's, and emulation of OSS io calls for applications that want to use OSS. All this is fake. It is just a layer to fool apps that still want to use OSS (/dev/dsp). This OSS emul. layer will talk to the real ALSA driver, it's some sort of translator : OSS io calls to ALSA io calls.

About jack : some ppl have hacked an jack OSS emulation called oss2jack. It is, from the user standpoint, the same concept : a layer that creates some /dev/dsp and translates OSS io calls from apps to the jack "language". oss2jack is in fact a jack client with jack input and output ports. For an app that's using OSS (for example the firefox flash plugin by default), jack does not exist, it's invisible, oss2jack will look like an OSS environment. But in fact, it is just a bridge to the jack graph. This is very convenient for users like me who use jack ALL the time as you sometimes need oss2jack because of some apps that were not updated to more modern audio layers.

You can also get

libjackasyn0

from the repos and launch an OSS application with the command:

jacklaunch application

To get your OSS application to use jack.

---

### Post by mrowth on 2008-10-23
"jacklaunch firefox" just seems to hang... I tried jacklaunch "in the past" when Audacity didn't know how to use JACK, without it ever working...

> **markbuntu said:**
> A lot of people seem to be misunderstanding what pulseaudio is and what alsa is. Alsa is actually two parts, low level drivers and a sound server for application interface that has things like dmix and esd grafted onto it. Jack bypasses the alsa sound server and uses the low level drivers directly.

Pulseaudio replaces the alsa sound server and dmix and esd and also directly addresses the low level alsa drivers. But pulseaudio does not always need to do this the way jack does. Pulseaudio can also use virtual sinks to direct audio to. Like ones for jack and network broadcasting and for multiple sound cards.

When the pulse-jack sink is used, pulseaudio just hands the application audio to jack in a way that jack can understand. It does not use alsa or dmix or esd, it does this directly with zero latency.


But JACK can also use: dummy, oss, alsa, portaudio, coreaudio, freebob, firewire

So which would I make JACK use in this scenario? ALSA? And should *only* JACK be using it? Pulse doesn't talk to the ALSA driver in any way; it scoops up audio streams (from applications using Pulse) and hands them to JACK, which hands them to the ALSA driver...? 

Figuring out three or four (or more) sound servers, each with their own means of "faking" some of the others, is confusing indeed. At least I never touched ESD or aRts.

---

### Post by jukingeo on 2008-10-23
> **mrowth said:**
> 
Knowing OSS doesn't mix audio at all I used to think ALSA (if set up to run everything through a dmix plugin) was the rescue. Now my sound"card" seems to have magically acquired hardware mixing. JACK (using ALSA, hw:0) + Audacity playback (using OSS for a change) + Amarok (using OSS likewise) + Pidgin (using ALSA) + Flash plugin (I don't know what it's using, not JACK) + = mixing fine. From all that I read that shouldn't even be impossible: several apps using OSS?

ALSA isn't a cure all for everything...at least not yet, but it does get pretty close.  However, as my experience with the Echo Mona shows, there are quite a few independent people making ALSA drivers.  So what happens when someone looses interest in updating their driver? 

As for "magical" hardware mixing...if you noticed, I DO tend to use the word "Automagically" instead of automatically.  While I cannot claim credit for that term, it does aptly describe quite a few scenarios I have experienced in my dealings with Linux.

I had problems with the X-Fi, but that wasn't a supported card.  That is a given.  However, I did get it to work rather well in Ubuntu.  The big shortcoming was the fact I couldn't use it with just any Linux distribution AND it wouldn't work in real time.  The next card I had in my system was the Soundblaster Live.  While this did work in all distributions...it only worked PARTIALLY.  It wouldn't record in most situations.  Jack hated it.  It was fixed at 48k.  The Echo product line came with much promise that it would work under ALSA, but in fact it didn't work at all with ANY Linux distribution.   Naturally to my utter amazement, the M-Audio Delta 44 I bought seemed to magically cure all the ailments I had in EVERY Linux distribution I have.  In fact I even tried to stump it by using the Live CD version of OpenSuSE 11.0 (not installed) and believe it or not it was still "automagically" recognized.

Now wait...it gets better.  I own two Midi only interfaces.  Midiman (M-Audio) Midisport interfaces.  One is a 2x2 and the other is a 4x4.  The 2x2 is automagically recognized in Linux, but the 4x4 isn't.  But here is the kicker.  If I "kick start" the 4x4 in Windows XP, then reboot into Linux, it IS automagically recognized.  Is THAT weird or what?

BUT it gets better.  I was told that my Korg Kontrol49 keyboard wouldn't be recognized in Linux.  Guess what?  it is!  Granted, I can't use the sophisticated patch editing features as that requires a Windows program.  But once a program is set in the unit's memory, I can go into a Linux distribution and use it.

Overall, it seem there is more mystical stuff going on with Linux than Science!  LOL, I know that isn't true, but it sure seems that way.

I guess I am still very much used to Windows XP where just about everything works just about all of the time.

> (At least Audacity is having problems *recording* additional tracks while playing back existing tracks; starting a Commodore emulator running through WINE (ALSA) gives it playback problems also: strangely enough, it doesn't even work with ALSA's allegedly soft-mixing devices... which it *should*, no? But then, there's always JACK. It's just that so little of this makes any sense to me.)

Welcome to the club.  I always considered myself an "advanced" computer user when it came to Windows 98 and Windows XP.  However, Linux makes me look like a Neanderthal. 

> Yes, I mean the ALSA driver... but additionally a specific ALSA interface: "default" or "dmix" or "plughw:" or whatever else provides software mixing, whereas the "hw:" interfaces bypass this and provide the direct-most access to the hardware. Shouldn't that allow you to use JACK & JACK apps along with other applications - as long as those can be configured to likewise use an ALSA software mixing interface instead of "hw:"? Hypothetically, at least? I can't test it because I see no rhyme or reason to whatever works here.

I didn't play around with this too much.  I always told to set Jack at the highest priority level and the HW to 0.  This setting could be the reason why Jack is so picky, but I don't know too much about messing around with these settings.

I do know how to juggle the frame rates, sample rates (etc) to lower the latency.  But outside of that, I don't mess around too much inside the Jack set up screen.  But as I said earlier, be careful about messing with the sample rate too much and the sample rates must match in your application and in Jack.


>  In the 2.6 version [of the Linux kernel] it **replaces** OSS by default, although a backwards-compatibility layer exists."[/i] (Emphases mine!) 

Yup, that is what I mentioned above.  ALSA is favored over OSS in Hardy.

And therein lies the problem.  I think they are trying to make Hardy do too much and hence that why it has so many problems.  I personally deleted EVERYTHING OSS in Ubuntu Studio and it seems to be that the system is working better because of it.  

> However, I've never tried the "real", new, software-mixing-capable OSS (4) -- that is, I've never installed or upgraded OSS, and only ever seen whatever OSS interfaces ALSA provides for the sake of compatibility. And that's the only OSS I've been talking about here. Sorry about the confusion. I had pretty much forgotten/ignored that OSS was still being developed "elsewhere".

I guess if you had prior versions of Ubuntu, I can see that you probably were used to OSS.  I came into the picture with Hardy.  I DID start with OSS and initially it was pretty easy to get sound going on my system...but I never had COMPLETE sound.  Always something had a problem.  At one point I did almost have everything working with Pulse Audio layered with OSS.  But Jack never worked.  I updated OSS in the hopes that I can get it to work with Jack and everything went downhill from there to the point were I couldn't recover.  I ended up wiping Ubuntu Studio, and I started over with ALSA only.


> I've been using both lower sample rates (old 8 bit samples included) and higher sample rates, partly out of convenience, partly out of necessity, partly in much the same way editing images at high resolutions yields better results even when you end up printing them at very small sizes... didn't notice speed/pitch problems or crashes. Isn't JACK resampling everything to whatever you set it up to, within the limits imposed by the hardware? (Maybe I should read the manual.)

Because my uses are different I am pretty much going to stick with 24 bit samples for recording.

I mostly intend on using 3 frequencies:

44.1 for your average everyday listening and sound for videos, etc.
88.2 for regular mastering and "studio" recording work.
96 for high end projects and record archival purposes.  (I was going to go to 192k for this, but the Delta 44 cannot go this high and I heard that 192k has some issues in Linux).

I would say perhaps I would go 16bit for video games and such...that is fine enough for that.

>  But I've been running two cards before; it was more of a nuisance than a showstopper...

LOL, yes, I been hearing the same thing.

However, I have heard that if you have two similar cards (such as two Audigy cards or two M-Audio cards)...the ordeal isn't as bad.  But considering all my troubles I had in the past, I am just going to stick with the one card.

Have a good one!

Geo

---

### Post by mrowth on 2008-10-25
Ubuntu 8.10 release notes:

"No real-time kernel variant is available for the Linux 2.6.27 kernel included with Ubuntu 8.10. Users of UbuntuStudio 8.04 who need real-time kernel support are advised not to upgrade to UbuntuStudio 8.10."

...wha? 

*Will* there be such a kernel later?

If not, does this:  [http://sourceforge.net/projects/realtime-lsm/](http://sourceforge.net/projects/realtime-lsm/) help in any way? Can it be explained in non-kernel-hacker-yet-not-a-wholly-disinterested-moron-either language? There's no documentation.

Or is realtime overrated? I do get noticeably better performance (xruns and DSP load) out of JACK with it. Even in the generic kernel for some reason.

---

### Post by markbuntu on 2008-10-26
Probably some more widespread testing of the patch is in order before it will be packaged into a kernel image and included in the repo but I am sure it will be since demand is high.

---

### Post by luctor on 2008-10-27
[http://packages.ubuntu.com/intrepid/linux-rt](http://packages.ubuntu.com/intrepid/linux-rt)

i have installed myself, though not thorougly tested

---

### Post by jukingeo on 2008-10-27
> **mrowth said:**
> Ubuntu 8.10 release notes:

"No real-time kernel variant is available for the Linux 2.6.27 kernel included with Ubuntu 8.10. Users of UbuntuStudio 8.04 who need real-time kernel support are advised not to upgrade to UbuntuStudio 8.10."

...wha? 

*Will* there be such a kernel later?

If not, does this:  [http://sourceforge.net/projects/realtime-lsm/](http://sourceforge.net/projects/realtime-lsm/) help in any way? Can it be explained in non-kernel-hacker-yet-not-a-wholly-disinterested-moron-either language? There's no documentation.

Or is realtime overrated? I do get noticeably better performance (xruns and DSP load) out of JACK with it. Even in the generic kernel for some reason.

Ok, there needs to be a bit of clarification here.  I DO have Ubuntu Studio and it IS a realtime kernel.  However, it will not work out of the box with Jack.

Let me explain:

I am using Grub bootloader because I am on a multi-boot system.  Upon start up on my machine, I am presented with a list of OS's to choose from.  The Ubuntu Studio version number link DOES specifically end in RT, which is the real time Kernel.

Now there are some that are saying the RT Kernel doesn't work in Ubuntu Studio.  This is both true and false.  The trouble with Ubuntu Studio is that the PERMISSIONS prevent you from accessing the real time portion of Ubuntu Studio.  Thus the average person that has Ubuntu Studio will start up Jack and realized that when you tick the RT box in setup, Jack will crash.  Hence...The RT kernel doesn't work.

Once the permissions are set, the RT light WILL come on and Jack is stable.

Hope that sheds some light on the scene :).

> **luctor said:**
> [http://packages.ubuntu.com/intrepid/linux-rt](http://packages.ubuntu.com/intrepid/linux-rt)

i have installed myself, though not thorougly tested

Intrepid is out????  Uuuuuggggh!  Now after I JUST got everything working in Hardy.

---

