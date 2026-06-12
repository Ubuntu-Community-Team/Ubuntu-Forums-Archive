---
title: "Finally! all set up! But Jack hates me"
date: 2011-02-20
forum: Ubuntu Studio
---

### Post by m3x1c0 on 2011-02-20
Well after 3 days of trying to get my wireless card to work I finally have a basic functioning laptop with studio! I absolutely love this os even though roughly 25% of it isnt currently working! The issue seems to be that JACK isn't working. When I click on a few things in the audio production tab it simply does nothing. I'm going to guess JACK isnt helping out with this problem so I deal with it first. when I open jack up I get an error message that says:

"Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info"

It pulls up a message window with all of this in it: 

```
20:23:12.960 Patchbay deactivated.
20:23:13.040 Statistics reset.
20:23:13.055 Startup script...
20:23:13.056 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:23:13.063 ALSA connection graph change.
sh: artsshell: not found
20:23:13.466 Startup script terminated with exit status=32512.
20:23:13.467 JACK is starting...
20:23:13.468 /usr/bin/jackd -p128 -dalsa -dhw:0 -r44100 -p512 -n2
20:23:13.485 JACK was started with PID=22962.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|512|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf8500000 irq 47
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
20:23:13.636 JACK was stopped with exit status=255.
20:23:13.637 Post-shutdown script...
20:23:13.638 killall jackd
20:23:13.672 ALSA connection change.
jackd: no process found
20:23:14.048 Post-shutdown script terminated with exit status=256.
20:23:15.677 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:23:23.593 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:23:34.896 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:29:36.003 ALSA connection graph change.
```

here are my settings:

[[img]http://farm6.static.flickr.com/5140/5463033543_3b04f45d9a.jpg[/img]](http://www.flickr.com/photos/53112027@N05/5463033543/)
[Screenshot-2](http://www.flickr.com/photos/53112027@N05/5463033543/) by [v8carsandguitars](http://www.flickr.com/people/53112027@N05/), on Flickr

This may only be step one on my path audio production nirvana but i gotta start somewhere. Additionally, LMMS is having issues when I use instrument plugins. If I play with the keyboard to fast or repeatedly, LMMS will just disappear and I lose all of my work (2 hours worth of music went away when I first discovered this:() Thanks in advance for the help!

---

### Post by AutoStatic on 2011-02-21
> **m3x1c0 said:**
> ```
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
```You might try closing all audio related applications and try again, something is locking your soundcard (probably your browser).

Best,

Jeremy

---

### Post by RaumTrug on 2011-02-21
that something can usually be found well with the command "lsof | grep pcm"

---

### Post by m3x1c0 on 2011-02-21
> **RaumTrug said:**
> that something can usually be found well with the command "lsof | grep pcm"

when I had chromium open the command showed that but with everything closed the command runs nothing, Yet i still get the same error messages from Jack

---

### Post by m3x1c0 on 2011-02-21
what exactly does it mean by could not connect not connect? is it trying to connect to the audio card?

---

### Post by sgx on 2011-02-21
Try starting jackd like this, after a fresh boot:

jackd -d alsa -r 44100

the resulting terminal output should have this near the bottom:


ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback


Then start qjackctl and in the connections tabs, you highlight one desired item on each side, and press the connect button. Keeping sound playing into your soundcard line-in will help as you experiment with connections.
Cheers

---

