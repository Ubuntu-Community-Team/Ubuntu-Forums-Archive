---
title: "Jack Version"
date: 2009-12-03
forum: Ubuntu Studio
---

### Post by lavadisco on 2009-12-03
I am running Karmic 64. I installed the realtime kernel, Jack, edited my limits.conf, added myself to the audio group, etc. When running Reaper in WINE with wineasio, it would play fine for a minute or so then crash the audio and give me this error, even at really high latencies (70 ms!):

> subgraph starting at qjackctl timed out (subgraph_wait_fd=16, status = 0, state = Running, pollret = 0 revents = 0x0) 

I figured maybe I wasn't running the latest Jack as the repos are often behind in these things, so I went to jackaudio.org and downloaded "Jack2" Jack-1.9.4. It appeared to install in the terminal without a hitch. However, when I go into synaptic and look for it, I see nothing. I still see the old jackd & qjackctl in the list (not installed, of course), but nothing new. Got a sinking feeling that I am missing something really dumb and obvious here. Anybody know the answer?

---

### Post by trulan on 2009-12-03
First off:  Jack2 isn't exactly newer, it's just different.

Secondly:  I have had zero success building Jack on my own.  I am currently using Jack2 from here:
[https://launchpad.net/~frasten/+archive/ppa](https://launchpad.net/~frasten/+archive/ppa)

Add the ppa to synaptic's sources, then tell synaptic to update Jack.  Then, if you ever want to roll back to the version of Jack in the repository, remove the ppa from your sources and reinstall.

---

### Post by lavadisco on 2009-12-03
Thanks! I was able to install Jack 1.9.4 using your suggested PPA. However, it did not ask me to install qjackctl like a Jack install usually does, so I used Synaptic to do so. Should I have done that? Now, when I run qjackctl, it appears there is some trouble communicating with the new Jack:

> 13:28:44.540 Patchbay deactivated.
13:28:44.567 Statistics reset.
13:28:44.610 Startup script...
13:28:44.610 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
13:28:44.614 ALSA connection graph change.
sh: artsshell: not found
13:28:45.011 Startup script terminated with exit status=32512.
13:28:45.011 JACK is starting...
13:28:45.011 /usr/bin/jackd -R -m -dalsa -dhw:UA25 -r44100 -p256 -n3
13:28:45.020 JACK was started with PID=2781.
Unkown driver "alsa"
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
13:28:45.111 JACK was stopped with exit status=255.
13:28:45.113 Post-shutdown script...
13:28:45.113 killall jackd
13:28:45.213 ALSA connection change.
jackd: no process found
13:28:45.527 Post-shutdown script terminated with exit status=256.
13:28:47.215 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

I checked the path /usr/bin/jackd and it appears to be in there, so I don't know why it's not being used.

---

### Post by trulan on 2009-12-03
Oh sorry.  I think you need to update qjackctl from that ppa too for things to work.  I know I am using qjackctl from that ppa.

---

### Post by lavadisco on 2009-12-03
Wouldn't adding the PPA give me both the latest Jack and qjackctl in Synaptic? There was only one qjackctl in there after I added the PPA, and that's the one I installed.

---

### Post by trulan on 2009-12-04
[LEFT]OK, then qjackctl isn't the problem.  I thought from the way it sounded you were still on the Ubuntu version and that may not be compatible with jack2 from the ppa.

Looking at your jack log, it's throwing an error about alsa being an unknown driver.  Obviously alsa isn't an unknown driver but you might want to fiddle with the driver selection in qjackctl and see what happens.  Maybe the two versions use different names/selection items for the driver.
[/LEFT]

---

### Post by lavadisco on 2009-12-05
I have qjackctl 0.3.5.3+cvs20090929-1~frasten0+karmic0. Is that what you have?

I tried everything in the server jack control server path list, no dice. Looking at the file /usr/bin/jackd, permissions are set to root. Is that how it should be?

---

### Post by trulan on 2009-12-05
That's exactly what I am using.  /usr/bin/jackd is owned by root and modifiable only by root, yes.

The problem isn't in qjackctl talking to jack but in jack talking to alsa.  I would experiment with different drivers and see if you get different results.  Also, I know you just learned how to specify your USB device in the hardware setting box, but that may have change for this version of Jack, so I'd experiment with that as well.

---

### Post by lavadisco on 2009-12-06
I found this thread on the Ardour message board:

[http://ardour.org/node/2322](http://ardour.org/node/2322)

The OP fixed this issue by installing "alsa-devel" package. I don't have that in Synaptic. Is it called something else now or is there a repository I have to go and get that contains it?

---

### Post by trulan on 2009-12-06
The dev packages are used in building other packages.  If that assessment of the problem is correct, it would mean that the version of jackdmp we got from the ppa is compiled without support for alsa.  But that version of jackdmp does indeed work with alsa for me (albeit in playback only mode, but that's my laptop's crappy soundcard, not jack or alsa's problem.)  So that makes no sense to me.

Plus, if that is indeed the problem, then to fix it you would need to build jack yourself anyway and you're back where you started at the beginning of this thread.

What alsa-related packages are installed on your system?

---

### Post by lavadisco on 2009-12-07
Here's what I get in Synaptic when I search for Alsa:

[IMG]http://mohodisco.com/synaptic.jpg[/IMG]

---

### Post by lavadisco on 2009-12-12
The guys in this thread don't think it's possible for me to make my setup work right:

[http://ardour.org/node/2322](http://ardour.org/node/2322)

They don't think that the version of Jack in the PPA you gave, Trulan, has Alsa support. I'm not entirely sure I believe that because you got yours working.

---

### Post by trulan on 2009-12-12
Here are two other ppa's that have jack-audio-connection-kit for Karmic:
[https://launchpad.net/~michael-gruz/+archive/sound?field.series_filter=karmic]("https://launchpad.net/%7Emichael-gruz/+archive/sound?field.series_filter=karmic")
[https://launchpad.net/~marienz/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/%7Emarienz/+archive/ppa?field.series_filter=karmic")

I have not tested those.  Be careful especially with the first one as it has Ardour 3.0 which is completely dead for me.

And, for reference, here's the one I've been using, once again:
[https://launchpad.net/~frasten/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/%7Efrasten/+archive/ppa?field.series_filter=karmic")

It is possible to compile jack for yourself, I just don't know how to do it.

---

