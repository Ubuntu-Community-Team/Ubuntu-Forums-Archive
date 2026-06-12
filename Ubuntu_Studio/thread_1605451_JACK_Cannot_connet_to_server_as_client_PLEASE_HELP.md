---
title: "JACK Cannot connet to server as client PLEASE HELP!"
date: 2010-10-25
forum: Ubuntu Studio
---

### Post by fumfumfum on 2010-10-25
[COLOR=black]Hi, I know there are numerous other thread around for this same problem but I can't seem to find a workable answer.

Whenever I run Jack I get the following in the message window:

[/COLOR] p, li { white-space: pre-wrap; } [COLOR=black][COLOR=#999999]10:35:06.887 Patchbay deactivated.[/COLOR][/COLOR]
 [COLOR=black][COLOR=#999999]10:35:06.888 Statistics reset.[/COLOR][/COLOR]
 [COLOR=black]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=black]Cannot connect to server socket[/COLOR]
 [COLOR=black]jack server is not running or cannot be started[/COLOR]
 [COLOR=black][COLOR=#66CC99]10:35:07.023 ALSA connection graph change.[/COLOR][/COLOR]
 [COLOR=black][COLOR=#CCCC99]10:35:07.217 ALSA connection change.[/COLOR][/COLOR]
 [COLOR=black][COLOR=#999999]10:35:29.347 Startup script...[/COLOR][/COLOR]
 [COLOR=black][COLOR=#990099]10:35:29.348 artsshell -q terminate[/COLOR][/COLOR]
 [COLOR=black]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=black]Cannot connect to server socket[/COLOR]
 [COLOR=black]jack server is not running or cannot be started[/COLOR]
 [COLOR=black]sh: artsshell: not found[/COLOR]
 [COLOR=black][COLOR=#999999]10:35:29.751 Startup script terminated with exit status=32512.[/COLOR][/COLOR]
 [COLOR=black][COLOR=#999999]10:35:29.751 JACK is starting...[/COLOR][/COLOR]
 [COLOR=black][COLOR=#990099]10:35:29.752 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR][/COLOR]
 [COLOR=black][COLOR=#999999]10:35:29.755 JACK was started with PID=3063.[/COLOR][/COLOR]
 [COLOR=black]no message buffer overruns[/COLOR]
 [COLOR=black]no message buffer overruns[/COLOR]
 [COLOR=black]jackdmp 1.9.6[/COLOR]
 [COLOR=black]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=black]Copyright 2004-2010 Grame.[/COLOR]
 [COLOR=black]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=black]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=black]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=black]JACK server starting in non-realtime mode[/COLOR]
 [COLOR=black]audio_reservation_init[/COLOR]
 [COLOR=black]Acquire audio card Audio0[/COLOR]
 [COLOR=black]creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=black]Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf8600000 irq 47[/COLOR]
 [COLOR=black]the playback device "hw:0" is already in use. Please stop the application using it and run JACK again[/COLOR]
 [COLOR=black]Cannot initialize driver[/COLOR]
 [COLOR=black]JackServer::Open() failed with -1[/COLOR]
 [COLOR=black]Failed to start server[/COLOR]
 [COLOR=black][COLOR=#999999]10:35:30.062 JACK was stopped with exit status=255.[/COLOR][/COLOR]
 [COLOR=black][COLOR=#999999]10:35:30.063 Post-shutdown script...[/COLOR][/COLOR]
 [COLOR=black][COLOR=#990099]10:35:30.063 killall jackd[/COLOR][/COLOR]
 [COLOR=black]jackd: no process found[/COLOR]
 [COLOR=black][COLOR=#999999]10:35:30.475 Post-shutdown script terminated with exit status=256.[/COLOR][/COLOR]
 [COLOR=black][COLOR=#FF0000]10:35:31.932 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR][/COLOR]
 [COLOR=black]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=black]Cannot connect to server socket[/COLOR]
 [COLOR=black]jack server is not running or cannot be started[/COLOR]
[COLOR=black]

I've edited the security/limits.conf file to allow realtime audio and Ive made myself a member of the audio group. I've also played around with the input and output settings in JACK but nothing seems to work.

I only just switched to Ubuntu Studio yesterday so i'm not familiar with what it all means... :confused:

please please somebody help me out, this is driving me crazy!

Thanks,

Josh
[/COLOR]

---

### Post by cchhrriiss121212 on 2010-10-25
> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
This line shows that you have another process running when trying to start jack, eg rhythmbox or anything else that uses sound.

---

### Post by fumfumfum on 2010-10-25
Man I'd swear I did that already. Sorry to waste your time on such a schoolboy error #-o

Thanks anyways though.

---

### Post by jemac001 on 2013-04-15
I got this error please help.

[COLOR=#999999]19:05:21.764 Patchbay deactivated.[/COLOR]
[COLOR=#999999]19:05:21.767 Statistics reset.[/COLOR]
[COLOR=#cccc99]19:05:21.769 ALSA connection change.[/COLOR]
[COLOR=#999999]19:05:21.773 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = Filen eller katalogen finns inte
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]19:05:21.780 ALSA connection graph change.[/COLOR]
[COLOR=#ff0000]19:05:24.045 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = Filen eller katalogen finns inte
Cannot connect to server request channel
jack server is not running or cannot be started
Mon Apr 15 19:05:23 2013: Starting jack server...
Mon Apr 15 19:05:24 2013: JACK server starting in realtime mode with priority 10
Mon Apr 15 19:05:24 2013: [1m[31mERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[0m
Mon Apr 15 19:05:24 2013: control device hw:0
Mon Apr 15 19:05:24 2013: control device hw:0
Mon Apr 15 19:05:24 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Mon Apr 15 19:05:24 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
Mon Apr 15 19:05:24 2013: [1m[31mERROR: Cannot initialize driver[0m
Mon Apr 15 19:05:24 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
Mon Apr 15 19:05:24 2013: [1m[31mERROR: Failed to open server[0m
Mon Apr 15 19:05:25 2013: Saving settings to "/home/jeremiasm/.config/jack/conf.xml" ...
[COLOR=#ff0000]19:05:37.192 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = Filen eller katalogen finns inte
Cannot connect to server request channel
jack server is not running or cannot be started

---

### Post by CraigPid on 2013-04-15
Check the settings in jack before you try to start it.For the input and output devices click the arrow beside them and make sure the right soundcard is selected.If you have an hdmi output it might have chosen that instead of your soundcard.Anyway, that's the first thing I would check for an error like that.
  Craig

---

### Post by overdrank on 2013-04-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

