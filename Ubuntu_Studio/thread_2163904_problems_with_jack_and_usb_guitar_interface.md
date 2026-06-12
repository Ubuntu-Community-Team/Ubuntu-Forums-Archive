---
title: "problems with jack and usb guitar interface"
date: 2013-07-20
forum: Ubuntu Studio
---

### Post by hagai_sela on 2013-07-20
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]I am trying to connect my guitar to my ubuntu 12.04 PC. I have a chinese USB guitar interface, which I know people used successfully in ubuntu.[/COLOR]
[COLOR=#000000]I tried connecting it to my speakers using the embedded jack build and couldn't get any sound, so I downloaded compiled and installed jack 1.9.9.5. This is the output I get when I try running it:[/COLOR]

[COLOR=#999999]23:15:58.257 Patchbay deactivated.[/COLOR]
[COLOR=#999999]23:15:58.284 Statistics reset.[/COLOR]
[COLOR=#cccc99]23:15:58.660 ALSA connection change.[/COLOR]
[COLOR=#999999]23:15:58.669 JACK is starting...[/COLOR]
[COLOR=#990099]23:15:58.670 /usr/local/bin/jackd -p128 -t5000 -dalsa -r48000 -p64 -n2 -S -D -Chw:CODEC,0 -Phw:0[/COLOR]
[COLOR=#000000]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#000000]Cannot connect to server request channel[/COLOR]
[COLOR=#000000]jack server is not running or cannot be started[/COLOR]
[COLOR=#000000]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#000000]Cannot connect to server request channel[/COLOR]
[COLOR=#000000]jack server is not running or cannot be started[/COLOR]
[COLOR=#000000]jackdmp 1.9.9.5[/COLOR]
[COLOR=#000000]Copyright 2001-2005 Paul Davis and others.[/COLOR]
[COLOR=#000000]Copyright 2004-2012 Grame.[/COLOR]
[COLOR=#000000]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
[COLOR=#000000]This is free software, and you are welcome to redistribute it[/COLOR]
[COLOR=#000000]under certain conditions; see the file COPYING for details[/COLOR]
[COLOR=#000000]JACK server starting in realtime mode with priority 10[/COLOR]
[COLOR=#000000]creating alsa driver ... hw:0|hw:CODEC,0|64|2|48000|0|0|nomon|swmeter|-|16bit[/COLOR]
[COLOR=#000000]configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods[/COLOR]
[COLOR=#000000]ALSA: final selected sample format for capture: 16bit little-endian[/COLOR]
[COLOR=#000000]ALSA: use 2 periods for capture[/COLOR]
[COLOR=#000000]ALSA: final selected sample format for playback: 16bit little-endian[/COLOR]
[COLOR=#000000]ALSA: use 2 periods for playback[/COLOR]
[COLOR=#66cc99]23:15:59.428 ALSA connection graph change.[/COLOR]
[COLOR=#999999]23:15:59.664 JACK was started with PID=3916.[/COLOR]
[COLOR=#ff0000]23:16:04.670 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
[COLOR=#000000]JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[/COLOR]
[COLOR=#000000]Driver is not running[/COLOR]
[COLOR=#000000]Cannot create new client[/COLOR]
[COLOR=#000000]Cannot read socket fd = 25 err = Success[/COLOR]
[COLOR=#000000]CheckRes error[/COLOR]
[COLOR=#000000]JackSocketClientChannel read fail[/COLOR]
[COLOR=#000000]Cannot open qjackctl client[/COLOR]
[COLOR=#000000]CheckSize error size = -1 Size() = 4[/COLOR]
[COLOR=#000000]CheckRead error[/COLOR]
[COLOR=#000000]CheckSize error size = 0 Size() = 12[/COLOR]
[COLOR=#000000]CheckRead error[/COLOR]
[COLOR=#999999]23:16:07.533 JACK is stopping...[/COLOR]
[COLOR=#000000]Jack main caught signal 15[/COLOR]

---

### Post by marianoa on 2013-07-20
What was the problem with the version of jack that you can install from the repositories? Did it start but it didn't work with the usb interface you're trying to use? If it starts,
can you see if you get any sound using some jack compatible application, you can try to install zynaddsubfx, it's a synthesizer with a built-in keyboard.

---

