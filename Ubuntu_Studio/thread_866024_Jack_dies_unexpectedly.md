---
title: "Jack dies unexpectedly"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by angelsguitar on 2008-07-21
Hi all.

While I'm using Jack with Hydrogen or any other app, it dies unexpectedly and won't let me restart it unless I reboot :mad:.  Here's the output on the messages window , just after it died and I tried to restart it(I left out some of the repeating messages because otherwise it would be too long for this post):

09:54:49.468 Patchbay deactivated.
09:54:49.528 Statistics reset.
09:54:49.541 ALSA connection graph change.
09:54:49.739 ALSA connection change.
09:54:56.621 Startup script...
09:54:56.621 artsshell -q terminate
09:54:57.048 Startup script terminated with exit status=256.
09:54:57.049 JACK is starting...
09:54:57.049 /usr/bin/jackd -R -dalsa -r48000 -p128 -n2 -D -Chw:0 -Phw:0
09:54:57.056 JACK was started with PID=6814.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
09:54:59.150 Server configuration saved to "/home/angelsguitar/.jackdrc".
09:54:59.151 Statistics reset.
09:54:59.185 Client activated.
09:54:59.189 JACK connection change.
09:54:59.191 JACK connection graph change.
ALSA: poll time out, polled for 3998627 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
cannot read server event (Success)
cannot complete execution of the processing graph (Resource temporarily unavailable)
cannot complete execution of the processing graph (Resource temporarily unavailable)

*(continues with the same message, then...)*

cannot continue execution of the processing graph (Broken pipe)

*(continues with the same message...)*

cannot continue execution of the processing graph (Broken pipe)
jackd: no process killed


I'm using a Pentium D with 2 GB RAM and an MAudio Delta 1010LT (the older ones), and Ubuntu Studio 8.04-1. I'm including a screenshot of my Jack settings in qjackctl.

Any ideas? Thanks in advance.

---

### Post by angelsguitar on 2008-07-22
On my first post I posted the contents of the message window after I tried to restart jack.  Well, in case it helps, this is the output of the messages window *just after* it dies the first time. I noticed it is slightly different:

08:05:54.123 Patchbay deactivated.
08:05:54.228 Statistics reset.
08:05:54.253 Startup script...
08:05:54.253 artsshell -q terminate
08:05:54.269 ALSA connection graph change.
08:05:54.964 Startup script terminated with exit status=256.
08:05:54.965 JACK is starting...
08:05:54.965 /usr/bin/jackd -R -dalsa -r48000 -p128 -n2 -D -Chw:0 -Phw:0
08:05:54.967 JACK was started with PID=6479.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
08:05:55.169 ALSA connection change.
08:05:56.177 Server configuration saved to "/home/angelsguitar/.jackdrc".
08:05:56.178 Statistics reset.
08:05:56.471 Client activated.
08:05:56.474 JACK connection change.
08:05:56.478 JACK connection graph change.
08:06:07.859 JACK connection graph change.
08:06:07.883 JACK connection change.
08:06:08.103 ALSA connection graph change.
08:06:08.104 JACK connection graph change.
08:06:08.287 ALSA connection change.
08:06:14.492 Transport start.
08:06:34.706 Transport stop.
08:06:58.922 Transport start.
08:07:01.124 Transport stop.
08:07:29.341 Transport start.
08:07:43.552 Transport stop.
ALSA: poll time out, polled for 3998524 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
08:07:58.903 Shutdown notification.
08:07:58.907 JACK is stopping...
08:07:58.909 JACK is being forced...
cannot complete execution of the processing graph (Success)
zombified - calling shutdown handler
08:07:59.110 JACK was stopped successfully.
08:07:59.110 Post-shutdown script...
08:07:59.110 killall jackd
jackd: no process killed
08:07:59.545 Post-shutdown script terminated with exit status=256.
08:10:13.303 ALSA connection graph change.
08:10:13.402 ALSA connection change.

After this, if I try to restart it will give the output I published on the previous post.

Any ideas on what's happening? I even reinstalled UbuntuStudio but the problem reappeared.

---

### Post by doomsday101 on 2008-07-23
I had a very similar problem a day or two ago from tooling around with the computer I figured out that in my case the on board sound card was screwing jack up when I was plugged into the additional sound card so you can take out and extra sound cards and run on the on board or disable the on board and try to run through the plug in sound card.

---

### Post by angelsguitar on 2008-07-23
> **doomsday101 said:**
> I had a very similar problem a day or two ago from tooling around with the computer I figured out that in my case the on board sound card was screwing jack up when I was plugged into the additional sound card so you can take out and extra sound cards and run on the on board or disable the on board and try to run through the plug in sound card.

Actually, my board does not have an integrated sound card; I just have the PCI M Audio Delta 1010LT.

---

### Post by angelsguitar on 2008-07-29
Well, I finally decided to install Ubuntu Studio 8.04-1 64 bit (I was running the 32 bit version) just to see how different it behaves.

At least I know the problem is not hardware related; I'm running 64 Studio too on this machine, and it works perfectly (by the way, nice audio distro...but that's another topic)

---

### Post by silentb on 2008-08-08
I experience this problem, too. jackdmp behaves the same.

What sound cards do you use? ICExxxx based ones?

Increasing the latency to > 20 ms helps, but that is inacceptable for me.

---

### Post by angelsguitar on 2008-08-09
> **silentb said:**
> I experience this problem, too. jackdmp behaves the same.

What sound cards do you use? ICExxxx based ones?

Increasing the latency to > 20 ms helps, but that is inacceptable for me.

Yes, indeed, the Delta 1010LT card I have has an ICE1712 chip inside.  And the > 20ms is unacceptable to record audio and/or play the synths, I agree.

Right now I'm testing 64 Studio (another debian-based distro for audio) and, so far, had not had any problems. So maybe I'll switch to 64 Studio for the serious audio work.

---

### Post by vivichrist on 2008-09-05
oops

---

### Post by pazuzuzu on 2009-10-25
I started having this problem a few days ago, though in my case the failure occurs reliably after about a minute of jackd starting.

I am also using a 1010lt, on-board audio disabled, but I also have a Delta 66 synched with the 1010lt.  The Delta 66 can start up normally.

I also note that if I attempt to use any output PCMs on the 1010lt, the writing program hangs indefinitely.

I'm currently attempting to install Studio 64; if this works, then I'll file this as an Ubuntu bug.

---

### Post by nzuri on 2010-01-20
i know, this is an old thread, but i have exactly the same problem (with a sound blaster live!) and installing 64 bit version didn't change anything.
any new ideas?
thank u

System:
Studio 9.04
kernel: 2.6.28-3-rt

---

