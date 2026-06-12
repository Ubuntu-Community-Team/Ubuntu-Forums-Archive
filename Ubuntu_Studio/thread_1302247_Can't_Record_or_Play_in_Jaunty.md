---
title: "Can't Record or Play in Jaunty"
date: 2009-10-26
forum: Ubuntu Studio
---

### Post by dberman on 2009-10-26
Hello all. I upgraded Ubuntu Studio from Hardy to Jaunty using a clean install. Now, my system sounds all work, but I can't record or playback with any application. I was using Audacity and Ardour successfully in the previous version. 

I am completely ignorant when it comes to Linux. All I want to do is play and record music. I can follow instructions I find in forums and blogs, but I don't have much idea what I'm doing.

I have read all the posts and followed every link with no luck. I configured PulseAudio correctly, I connected Ardour to Jack, but still no sound going in or out.

I am working on an older Gateway laptop:
Pentium 1.4
1.5GB memory
Intel 8201DB built-in sound card, SigmaTel chipset (don't laugh - it worked great before)
Linux kernel 2.6.28-3-rt
Ubuntu release 9.04

If more information would help, I'd be glad to post it. This has been frustrating, since everything worked great in 2 earlier versions of UbuntuStudio. Thank you in advance for any and all help!!

---

### Post by fancypiper on 2009-10-27
Try running them from a terminal and post the error messages.

---

### Post by dberman on 2009-10-28
Fancypiper, I would run everything from a terminal, except I have no clue how. If you can post the commands, I can certainly follow them, capture the error messages and post the results. Thanks for the suggestion and your willingness to help.

---

### Post by AutoStatic on 2009-10-29
Hello dberman, do you manage to get JACK running? Could you post a screenshot of your settings in Qjackctl? Could you install the package *alsamixergui* and post a screenshot of *alsamixergui*? And do you have no sound at all or is sound dead only with certain applications?

---

### Post by fancypiper on 2009-10-29
To run an application from a terminal, first open the terminal and then type the name of the application and enter. For example, to run audacity, you simply type "audacity" (no quotes), then press enter.

---

### Post by dberman on 2009-10-30
Hello, and thank you for your replies. I installed Alsamixergui as recommended by Autostatic. the Screenshot is below. I also included screenshots of my Audacity preferences and Jack Control audio setup. The following is the result of running these apps from Terminal, as suggested by FancyPiper. The mouse clicks in the application that generated a result are in parens:

**dberman@ClubDave:~$ audacity**
(Stop recording)
HCK OnTimer
(Stop playback)
HCK OnTimer
(Turn on monitoring)
Expression 'err' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2468
Expression 'ContinuePoll( self, StreamDirection_In, &pollTimeout, &pollCapture )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2948
Expression 'PaAlsaStream_WaitForFrames( stream, &framesAvail, &xrun )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3310

**dberman@ClubDave:~$ qjackctl**
Suspending PulseAudio
(Jack message: could not connect to jack server as client...)
(this is the message stream from Jack's message window)
20:11:51.123 Patchbay deactivated.
20:11:51.171 Statistics reset.
20:11:51.307 Startup script...
20:11:51.308 artsshell -q terminate
20:11:51.314 ALSA connection graph change.
sh: artsshell: not found
20:11:51.711 Startup script terminated with exit status=32512.
20:11:51.712 JACK is starting...
20:11:51.712 /usr/bin/jackd -R -t5000 -dalsa -r44100 -p64 -n2 -D -Chw:0 -Phw:0,0
20:11:51.718 JACK was started with PID=5863.
20:11:51.934 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
20:12:02.459 ALSA connection change.
20:12:02.878 Server configuration saved to "/home/dberman/.jackdrc".
20:12:02.884 Statistics reset.
20:12:03.681 Client activated.
20:12:03.683 JACK connection change.
20:12:03.687 JACK connection graph change.

**dberman@ClubDave:~$ ardour2**
Ardour/GTK 2.7.1
   (built using 4296 and GCC version 4.3.3)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
theme_init() called from internal clearlooks engine
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:74: error: unexpected identifier `colorize_scrollbar', expected character `}'
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/dberman/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/dberman/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/dberman/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control protocol Tranzport not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"
JACK COMMAND: /usr/bin/jackd -m -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0 
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
loading bindings from /etc/ardour2/mnemonic-us.bindings
Loading session /home/dberman/newproj using snapshot newproj (2)
Loading history from '/home/dberman/newproj/newproj.history'.
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

After I started Ardour I had to restart Jack, and got the same output.

---

