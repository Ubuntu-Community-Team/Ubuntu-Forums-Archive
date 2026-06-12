---
title: "JACK audio connection wont work"
date: 2009-09-01
forum: Ubuntu Studio
---

### Post by MatthewWaterman on 2009-09-01
When I run it all I get is this

 p, li { white-space: pre-wrap; }  [COLOR=#999999]10:51:56.350 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:51:56.408 Statistics reset.[/COLOR]
 [COLOR=#66CC99]10:51:56.419 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]10:51:56.627 ALSA connection change.[/COLOR]
 [COLOR=#999999]10:52:04.292 Startup script...[/COLOR]
 [COLOR=#990099]10:52:04.293 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]10:52:04.695 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]10:52:04.695 JACK is starting...[/COLOR]
 [COLOR=#990099]10:52:04.696 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]10:52:04.701 JACK was started with PID=5280.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1212119360, from thread -1212119360] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]10:52:04.761 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]10:52:04.762 Post-shutdown script...[/COLOR]
 [COLOR=#990099]10:52:04.762 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]10:52:05.172 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]10:52:06.848 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000][COLOR=Black]Can anyone help?[/COLOR][/COLOR]
[COLOR=#FF0000][COLOR=Black]What can I do?[/COLOR][/COLOR]
Cheers 



[COLOR=#FF0000]
[/COLOR]

---

### Post by dawiba on 2009-09-01
What are you using?

UbuntuStudio? Which version?

Ubuntu? Which version?

What soundcard?

It looks as if you need to disable the realtime option in Jack settings.

---

### Post by MatthewWaterman on 2009-09-01
What are you using?
[COLOR=Lime]Rosegarden 1.7.2[/COLOR]

Ubuntu? Which version?
[COLOR=Lime]Ubuntu 9.04[/COLOR]

What soundcard?
[COLOR=Lime]SigmaTel STAC9872AK[/COLOR]

[COLOR=Black]Cheers! I have a look at the settings in JACK as well[/COLOR]

---

### Post by dawiba on 2009-09-01
Rosegarden is a great program, but does work better if you are running a realtime kernel. If you're running ordinary Ubuntu, you won't have a realtime kernel installed by default. You would need to download this and install it separately. If you're new to Ubuntu and music making on Ubuntu, you might want to do a good bit of reading first before you try this!

To try and get Rosegarden running just now without that, open Jack Control, click setup, uncheck the realtime option and make sure that on the right hand side where it says driver, that you've selected alsa from the drop down menu. It's probably best to leave all the other stuff under that - interface, dither, audio, input device, output device etc etc - set to default. Once you've done all that, click start and hopefully you'll be under way. Then try launching Rosegarden. You'll probably get some error message about system timer resolution, but you'll just have to ok that for just now.

I'd suggest LMMS for your needs, based on your other post looking for an Ableton-like program. I don't use it myself, but I think you can use it without Jack, ideal for your situation. Someone will correct me if I'm wrong

---

