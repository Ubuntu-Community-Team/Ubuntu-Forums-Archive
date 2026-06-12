---
title: "Tried Jack and some audio aps, now I dont have sound..."
date: 2009-11-06
forum: Ubuntu Studio
---

### Post by pc999 on 2009-11-06
Hi,

First time linux user here and I tried to play with some audio programes, like Ardour, Audacity, Rosengarden...

But it cant get JackControl to work, it does say this in the mensages:

>   p, li { white-space: pre-wrap; }  [COLOR=#999999]12:21:48.172 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:21:48.174 Statistics reset.[/COLOR]
 [COLOR=#999999]12:21:48.263 Startup script...[/COLOR]
 [COLOR=#990099]12:21:48.265 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]12:21:48.281 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:21:48.791 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:21:48.793 JACK is starting...[/COLOR]
 [COLOR=#990099]12:21:48.794 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]12:21:48.800 JACK was started with PID=2061.[/COLOR]
 [COLOR=#CCCC99]12:21:49.000 ALSA connection change.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1216596288, from thread -1216596288] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]12:21:49.422 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:21:49.424 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:21:49.425 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]12:21:49.886 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]12:21:51.035 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


Now I dont even have sound in internet movies ou Rhythmbox.

Anyone knows what hapened?

Thanks in advance.

---

### Post by aeh on 2009-11-06
Try first turning on Ardour then JACK
Hope this helps

---

### Post by Bunnybugs on 2009-11-06
Try to remove the 'Software Modem' driver...

this is probably the home of your problem, just like everyone should do...

I removed it, and problems were solved...

System>Applications>Hardware Drivers>>select 'Software Modem'> De-activate or some like that

---

### Post by AutoStatic on 2009-11-06
Hello pc999,

You need to either disable the Realtime option in QJackctl or make sure you are a member of the 'audio' group on your system and add a few lines to your */etc/security/limits.conf* file to enable realtime permissions for the 'audio' group.

---

