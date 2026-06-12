---
title: "Jack audio problems."
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by superzanti on 2009-11-25
I know there have been a lot of topics about this. but I just cant seem to get it working. I'm running ubuntu 9.10 64 bit. 

I just installed rosegarden and I cant get sound to play out of it.
I suspended pulse audio and oppened the jack audio interface, but it just keeps giving me an error saying it cant connect to the Jack server.

```
01:41:25.367 Startup script...
01:41:25.368 artsshell -q terminate
sh: artsshell: not found
01:41:25.771 Startup script terminated with exit status=32512.
01:41:25.771 JACK is starting...
01:41:25.771 /usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p4096 -n3 -i2 -o2
01:41:25.774 JACK was started with PID=3995.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 2080003824, from thread 2080003824] (1: Operation not permitted)
cannot create engine
01:41:25.793 JACK was stopped successfully.
01:41:25.794 Post-shutdown script...
01:41:25.794 killall jackd
jackd: no process found
01:41:26.207 Post-shutdown script terminated with exit status=256.
01:41:27.963 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by AutoStatic on 2009-11-25
Untick Realtime in Qjackctl or set up your system for Realtime audio production: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by superzanti on 2009-11-25
I already have realtime installed. linux-rt. But even if its checked or unchecked it gives me an error. here is the unchecked error:

```
11:02:14.437 Startup script...
11:02:14.438 artsshell -q terminate
sh: artsshell: not found
11:02:14.840 Startup script terminated with exit status=32512.
11:02:14.840 JACK is starting...
11:02:14.840 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p4096 -n3 -i2 -o2
11:02:14.844 JACK was started with PID=2684.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|4096|3|48000|2|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 4096 frames (85.3 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: cannot set period size to 4096 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
11:02:14.890 JACK was stopped successfully.
11:02:14.890 Post-shutdown script...
11:02:14.891 killall jackd
jackd: no process found
11:02:15.302 Post-shutdown script terminated with exit status=256.
11:02:16.888 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
11:11:10.988 Startup script...
11:11:10.989 artsshell -q terminate
sh: artsshell: not found
11:11:11.391 Startup script terminated with exit status=32512.
11:11:11.391 JACK is starting...
11:11:11.391 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p4096 -n3 -i2 -o2
11:11:11.394 JACK was started with PID=2779.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|4096|3|48000|2|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 4096 frames (85.3 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: cannot set period size to 4096 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
11:11:11.419 JACK was stopped successfully.
11:11:11.420 Post-shutdown script...
11:11:11.420 killall jackd
jackd: no process found
11:11:11.832 Post-shutdown script terminated with exit status=256.
11:11:13.437 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
11:11:19.570 Startup script...
11:11:19.571 artsshell -q terminate
sh: artsshell: not found
11:11:19.973 Startup script terminated with exit status=32512.
11:11:19.973 JACK is starting...
11:11:19.973 /usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p4096 -n3 -i2 -o2
11:11:19.976 JACK was started with PID=2790.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 275683056, from thread 275683056] (1: Operation not permitted)
cannot create engine
11:11:19.994 JACK was stopped successfully.
11:11:19.994 Post-shutdown script...
11:11:19.995 killall jackd
jackd: no process found
11:11:20.406 Post-shutdown script terminated with exit status=256.
11:11:22.066 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by trulan on 2009-11-25
In addition to installing linux-rt, you need to enable permissions for your username to access real time scheduling.  You need to be a member of the audio group, and there needs to be a line in /etc/security/limits.conf referring to audio - rtprio.

When RT is unchecked, jack is giving you an error that looks like you have too large of a frames/period size.  Change it from 4096 to something smaller, like 1024 or 512.

---

### Post by superzanti on 2009-11-25
Okay here's the deal. If i run 'sudo qjackctl' everything seems to start okay.

I have the soundblaster live! 24 bit audio card. 

After starting qjackctl, I can run 'sudo rosegarden' and rosegarden starts up with an error 'system timer resolution is too low' and 'Helper programs not found'. Then if I try to play something... There is no sound.

---

### Post by H13N.H3N on 2009-11-25
first than nothing you must have PulseAudio enabled, i know that is not the best sound server,  but is the only that you can work with for now, then go to your audio preferences, if you don't have JACK Control installed then install it from your repositories, perhaps it's qjack but you don't need to run it on terminal as it has it own gui, there you can start jack before initialize Rosegarden, also, Rosegarden has an option to run JACK at running the program itself, i don't know why it says that can't conect with JACK but you'll have MIDI sound enabled, quite weird

---

### Post by superzanti on 2009-11-25
Ya. I just want sound to come out of rosegarden.

---

### Post by trulan on 2009-11-25
> **superzanti said:**
> Okay here's the deal. If i run 'sudo qjackctl' everything seems to start okay.
Exactly. You don't have permissions to use real time scheduling as your username.  If you run as root (ie, sudo), then it works because root has permissions for everything.

If you run Jack as root, you need to run all your sound applications as root and that's not a good or safe idea.  Add your username to the audio group,

If you're running Jaunty, you'll have to create the 'audio' group first:
```
sudo addgroup audio
```This is not necessary in Hardy or Karmic.

Then make yourself a member of the audio group:
```
sudo adduser <username> audio
```putting your username in there, of course.

Then give the audio group real time scheduling permission:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
```
Then log out or reboot.

Once Jack is working without starting it using sudo, then start working on Rosegarden.

---

### Post by superzanti on 2009-11-25
Thanks so much Trulan!

That worked like a charm. Except, now rosegarden doesn't even open...

Though, it does open when i sudo run it. But then it says it failed to connect to the jack server.

---

### Post by trulan on 2009-11-25
Ok! Jack problem solved.  Now on to rosegarden...

I'm not a rosegarden user myself so I won't be much help with that.  But, if you start rosegarden from a terminal, does it give any error messages?

---

### Post by superzanti on 2009-11-25
```
seth@Seth-Linux:~$ rosegarden
Session management error: None of the authentication protocols specified are supported
kbuildsycoca running...
Session management error: None of the authentication protocols specified are supported
SSE2 detected
seth@Seth-Linux:~$ PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/seth/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
Session management error: None of the authentication protocols specified are supported
LADSPAPluginFactory::discoverPlugins - done
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/seth/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
LADSPAPluginFactory::discoverPlugins - done
Rosegarden 1.7.3 - AlsaDriver [ALSA library version 1.0.18, module version 1.0.20, kernel version 2.6.31-15-generic]
SSE2 detected

JackDriver::initialiseAudio - JACK sample rate = 48000Hz, buffer size = 1024
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    16,0 - (CA0106, CA0106 MPU-401 (UART))			(DUPLEX) [ctype 2, ptype 589826, cap 127]

CREATED OUTPUT PORT 3:out 1 - MIDI external device for device 0
Connecting my port 3 to 16:0 on initialisation
done
Creating device 0 in Play mode for connection 16:0 CA0106 MPU-401 (UART) (duplex)
Default device name for this device is MIDI external device
Creating device 1 in Record mode for connection 16:0 CA0106 MPU-401 (UART) (duplex)
Default device name for this device is MIDI hardware input device
CREATED OUTPUT PORT 4:out 2 - MIDI output system device for device 2
done
Creating device 2 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 3 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-15-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 100Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.3/src/base/Composition.cpp:1533
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 129:3 to General MIDI Device
CompositionModelImpl::slotInstrumentParametersChanged()
TrackButtons::slotUpdateTracks
Rosegarden: WARNING: No accurate sequencer timer available
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
Session management error: None of the authentication protocols specified are supported
Comparing current version "1.7.3" with latest version "1.7.3"
RosegardenGUIApp::awaitDialogClearance: entering

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    16,0 - (CA0106, CA0106 MPU-401 (UART))			(DUPLEX) [ctype 2, ptype 589826, cap 127]


```

Thats the output it gives me when i run rosegarden. Then it comes up with 2 errors

"System timer resolution is too low"

"helper programs not found"

and then rosegarden wont make a sound.

---

### Post by trulan on 2009-11-25
I believe the 'System timer resolution' is showing up because you are booting into the generic kernel (your output mentions 2.6.31-15-generic).  You said you installed linux-rt, but does 2.6.31-9-rt show up in your grub menu?  If not, run:
```
sudo update-grub
```And reboot, selecting 2.6.31-9-rt.  That will at least give you a system timer resolution of 1000hz.

---

### Post by superzanti on 2009-11-25
Actually right now im trying to run it without the realtime. I dont even have that checked in JACK

---

### Post by superzanti on 2009-11-25
I think I figured it out. I downloaded zynaddsubfx and routed all of the output of rosegarden to zynaddsubfx.

Now everything seems to work great...

Except, I was wondering if there is a way for me to run JACK and still be able to listen to my normal pulseaudio music.

---

### Post by AutoStatic on 2009-11-26
> **superzanti said:**
> I think I figured it out. I downloaded zynaddsubfx and routed all of the output of rosegarden to zynaddsubfx.

Now everything seems to work great...

Except, I was wondering if there is a way for me to run JACK and still be able to listen to my normal pulseaudio music.That's possible, you can run PulseAudio on top of JACK:
- You need to install pulseaudio-module-jack from here: [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main/+packages](https://launchpad.net/~motin/+archive/until-jack-is-included-in-main/+packages)
- Add the file ~/.pulse/client.conf with the following line: ```
autospawn = no
```
- Add a script to start JACK and to load the PulseAudio modules. The script should contain the following lines:```
#!/bin/bash

/usr/bin/pasuspender -- /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 &
sleep 5
pactl load-module module-jack-source
pactl load-module module-jack-sink
exit
```
- Add this script to your Startup Applications.

Make sure you adapt the jackd settings to your need. Another option is to make a script with just the following lines:```
#!/bin/bash
pactl load-module module-jack-source
pactl load-module module-jack-sink
exit
```
Then open Qjackctl and go to the Setup window, select the Options tab and tick Execute script after Startup, then browse to the script you just made. This should do the trick also. When you start Qjackctl and check the Connect window you will see the PulseAudio sinks in the Audio window.

---

### Post by VertexPusher on 2009-11-26
> **H13N.H3N said:**
> first than nothing you must have PulseAudio enabled, i know that is not the best sound server,  but is the only that you can work with for now
Nonsense.

---

### Post by superzanti on 2009-11-26
Thank You so much!!!

For anyone else having this problem, I used these tutorials, and replaced the script with the one given above - 

```
okay, you'll love this. FIXED! I have jack and pulseaudio running as before, even with flash sound.

You need to use the tweaked versions of pulseaudio in motin's PPA here:

https://launchpad.net/~motin/+archiv...cluded-in-main

Instructions for adding this to the sources list are here:

https://launchpad.net/+help/soyuz/ppa-sources-list.html

Then you just reload synaptic and install the marked updates of pulseaudio etc and install pulseaudio-module-jack from the list. 

That's made my evening!
h.
```

```
http://staghacks.com/?p=319
```

---

### Post by AutoStatic on 2009-11-26
Nice! But did you update using the repository I mentioned? Or did you just install the pulseaudio-module-jack module?

---

### Post by H13N.H3N on 2009-11-26
> **VertexPusher said:**
> Nonsense.

=(, i can't use ALSA, OSS, directly but only using Pulse Audio, what is nonsense? PA installed in every corner of Ubuntu Studio makes nonsense, no audi aplication has the option to work with any other audio option, i.e. Linux Multimedia Studio, that makes no sense

---

### Post by AutoStatic on 2009-11-26
> **H13N.H3N said:**
> =(, i can't use ALSA, OSS, directly but only using Pulse Audio, what is nonsense? PA installed in every corner of Ubuntu Studio makes nonsense, no audi aplication has the option to work with any other audio option, i.e. Linux Multimedia Studio, that makes no senseGnome relies heavily on PulseAudio, not Ubuntu Studio itself. And if you want LMMS to run on top of Alsa, maybe you could try something like **pasuspender -- lmms** in a terminal or use LMMS together with JACK.

---

### Post by H13N.H3N on 2009-11-26
i already sorted those problems, not removing or suspending pulse audio but trying to 'enhancing' it functionality, i still dislike the fact that some applications crashes and close Pulse Audio and Gnome-Volume-Control with it, i have no complains about include pulse audio in Ubuntu Studio, but making Gnome so dependent of PA is what causes my complains (btw, thanks for pointing that, i'll try to be clear with that, is Gnome, not Ubuntu who rely on PA)
STILL... it would be very nice to have an update that can sort that.

---

### Post by VertexPusher on 2009-11-27
> **H13N.H3N said:**
> =(, i can't use ALSA, OSS, directly but only using Pulse Audio, what is nonsense? PA installed in every corner of Ubuntu Studio makes nonsense, no audi aplication has the option to work with any other audio option, i.e. Linux Multimedia Studio, that makes no sense
There is no audio application that needs PulseAudio. All of them work with ALSA, either directly or through Jack. Since PulseAudio is broken in many ways, it makes perfect sense to remove it, especially from multimedia production environments such as Ubuntu Studio.

PulseAudio is not deeply integrated into Gnome either. Gnome is designed to use whatever sound system is available. The PulseAudio mixer and configuration applet in Ubuntu is _not_ part of Gnome. You can replace it with gnome-alsamixer any time. GStreamer applications such as Totem Movie Player can use any sound system for which a plugin is installed. Just replace gstreamer0.10-pulseaudio with gstreamer0.10-alsa, remove pulseaudio and see what happens.

Statements such as "PulseAudio is the only option" or "PulseAudio is here to stay" are just nonsense.

---

### Post by AutoStatic on 2009-11-27
> **VertexPusher said:**
> There is no audio application that needs PulseAudio. All of them work with ALSA, either directly or through Jack. Since PulseAudio is broken in many ways, it makes perfect sense to remove it, especially from multimedia production environments such as Ubuntu Studio.I do remove it too on my production machines since I don't need it there but it runs fine on my desktop machine. So I wonder what's broken about it, a part from the issues that the main dev of PulseAudio pointed out concerning 9.10.

> **VertexPusher said:**
> PulseAudio is not deeply integrated into Gnome either. Gnome is designed to use whatever sound system is available. The PulseAudio mixer and configuration applet in Ubuntu is _not_ part of Gnome. You can replace it with gnome-alsamixer any time. GStreamer applications such as Totem Movie Player can use any sound system for which a plugin is installed. Just replace gstreamer0.10-pulseaudio with gstreamer0.10-alsa, remove pulseaudio and see what happens.Try removing libpulse0 only to find out that a whole lot of Gnome applications are compiled against it. But you're right that even without PulseAudio Gnome will just run fine. Do you know by any chance where I can find more information on this matter?

> **VertexPusher said:**
> Statements such as "PulseAudio is the only option" or "PulseAudio is here to stay" are just nonsense.It is certainly not the only option, I agree. But I do get the idea that in the Land of Linuces a lot of developers are in favor of PulseAudio.

---

### Post by H13N.H3N on 2009-11-27
> **VertexPusher said:**
> You can replace it with gnome-alsamixer any time. GStreamer applications such as Totem Movie Player can use any sound system for which a plugin is installed. Just replace gstreamer0.10-pulseaudio with gstreamer0.10-alsa, remove pulseaudio and see what happens.

oh, now that's nice, but how you suppose that i would know that? also why ubuntustudio-desktop is removed, what this does? the description says:
> 
Ubuntu Studio is a multimedia creation flavor of Ubuntu for the
Linux audio, video, and graphic enthusiast or professional.

A collection of applications that comprises the Ubuntu Studio
Desktop System.

that's not quite descriptive, no matter what Pulse Audio dependency i uninstall i always find that ubuntustudio-desktop is removed also, i don't like how that sounds as that package seems important,anything to add for this?

btw thanks for the short explain and my apologizes for being that negative, i was very annoyed because most of my applications crashed randomly and plus, no 'intuitive' way to disable PA is at sight, i found Pulse Audio Control and it says 'disconnect' which i assumed disabled  PA, but did not work at that way.
-----------------------------------------------------------------------------------------
Edit:

i tried what you said, my only problem is that gnome-volume-control doesn't show in tray anymore, the process is active but i assume that is not working properly, i have the gnome-alsamixer, is there any way in that i can have back the real gnome-volume-control that opens gnome-alsamixer?, out of that all is working fine

---

### Post by VertexPusher on 2009-11-29
> **H13N.H3N said:**
> no matter what Pulse Audio dependency i uninstall i always find that ubuntustudio-desktop is removed also, i don't like how that sounds as that package seems important,anything to add for this?
ubuntustudio-desktop is a metapackage. Metapackages don't contain any software. Their sole purpose is to simplify installing other software packages by listing them as dependencies. Once the other packages are installed, you can remove the metapackage without losing anything.

> is there any way in that i can have back the real gnome-volume-control that opens gnome-alsamixer?, out of that all is working fine
Ubuntu's version of gnome-volume-control is unable to control ALSA volumes, so once PulseAudio is gone, gnome-volume-control becomes useless. Here's how I worked around it:

[img]http://img694.imageshack.us/img694/4810/volume.png[/img]

That's a copy of the gnome-alsamixer launcher from the applications menu. You can put it exactly where the gnome-volume-control icon would have appeared.

---

### Post by H13N.H3N on 2009-11-30
> **VertexPusher said:**
> [img]http://img694.imageshack.us/img694/4810/volume.png[/img]

That's a copy of the gnome-alsamixer launcher from the applications menu. You can put it exactly where the gnome-volume-control icon would have appeared.

That's how i'm working now, it's fine, but i really hope we can have the applet back in a sooner future, thanks for yout time

---

### Post by Arthur_D on 2010-02-22
> **trulan said:**
> Then give the audio group real time scheduling permission:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
```Then log out or reboot.
How do I revert this? Now ALL my sound is gone. :(

---

### Post by AutoStatic on 2010-02-23
Hello Arthur_D, setting rtprio should not disable your sound altogether, but you can remove the line from */etc/security/limits.conf* with **sudo gedit /etc/security/limits.conf**, then go to the line that contains the rtprio setting, remove it and save the file.

---

### Post by pluMmet on 2011-03-04
I'm having an issue too:

> 12:33:25.911 jackdmp -r -dalsa -r32000 -p1024 -n2 -D -Chw:0 -Pplughw:0
12:33:25.914 Could not start JACK. Sorry.
12:33:25.922 JACK was stopped successfully.
12:33:25.922 Post-shutdown script...
12:33:25.923 killall jackd
jackd: no process found
12:33:26.334 Post-shutdown script terminated with exit status=256.

I set up realtime in my /etc/security/limits.conf and I added myself to the audio group. I also did a complete install of pulse audio with this

> sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

I'm not sure what else to do?

---

### Post by Pablo_F on 2011-03-04
> 12:33:25.911 jackdmp -r -dalsa -r32000 -p1024 -n2 -D -Chw:0 -Pplughw:0

The command for both implementations of jack (jack1 and jack2, aka jackmp) is *jackd*, not jackdmp. 

-r option means No realtime mode. You normally want realtime mode.

If you use the same device for capture and playback, fill the interface field, and leave input and output devices as (default).

> I set up realtime in my /etc/security/limits.conf and I added myself to the audio group.

Check that all is right with:

ulimit -r -l

rtprio ninety-something and memlock unlimited or a fair amount of RAM is what you need to run jackd in realtime mode.

> I also did a complete install of pulse audio...
Pulseaudio has nothing to do with jack.

Cheers, Pablo

---

### Post by pluMmet on 2011-03-05
Wow Pablo_F....it was the JackMP option messing me up. I watched a video on youtube that said the JacpMP was just for multiprocessor computers so that is why I had it on.

Everything is working now. Thanks!

---

### Post by Pablo_F on 2011-03-05
In general, everything on the internet about jack and friends which was written or said several years ago, either is deprecated or it can be done in an easier way now. This is not _always_ true but you get the idea. More than two years is very old. Always look at the publication date and discard old stuff if you can choose. 

Another important point is the origin of the info. I recommend taking a look at the official sites of the programs you use.

jackmp, aka jack2, is started with the jackd command, the same as the original jack. Unfortunately, qjackctl in ubuntu still has some deprecated options available.  

Cheers! Pablo

---

### Post by sgx on 2011-03-05
I like to append a google search with
-2009 -2008 -2007 -2008 -2005

Doesn't always work, but thins down much of the outdated info.

I think reversing the long standing -r option was weird,
but the devs are the boss, maybe it was a necessity for all I know,
and in a year, everyone will have figured it out, or be among newcomers to whom it's not an issue. :guitar:
Cheers

---

