---
title: "FL Studio in Wine - Latency?"
date: 2008-05-27
forum: Ubuntu Studio
---

### Post by Yonderknight on 2008-05-27
Hi,

I've recently been messing around with ubuntu more and more and I'm finding less and less reasons to stay with Windows =). One program I haven't really found a suitable alternative for is FL Studio though. That's why I was pretty excited when I got FL7 working just fine in Wine!

However, one issue I've noticed was latency with my M-audio oxygen 61 keyboard. I'm wondering if this is coming mostly from FL, or from wine? And more importantly, what can I do to minimize it? I've read a little about Jack, but I haven't tried installing or setting it up. Can that help my latency issues?

---

### Post by robeast on 2008-05-27
Check out wineASIO: [http://sourceforge.net/projects/wineasio](http://sourceforge.net/projects/wineasio)
I don't know if it's in the repos or not. It will send your wine apps with ASIO audio through jack which should improve performance and make fruityloops able to interact with linux audio apps. I'm not sure if this will solve your latency issues, but it's worth trying.

---

### Post by Yonderknight on 2008-05-27
Hrm thanks.
The only thign is I don't have Jack installed and it looks kind of complicated to set up. I'll try looking into it though, thanks!

---

### Post by SynthesizersFTW on 2008-05-28
Jack isn't as bad as everyone makes it out to be.  Just make sure you also install QjackCtl, so you can trial-and-error your way to minimizing your latency - settings either work or they don't, and the output log will let you know what is going on.  Once it's working, the routing is fairly straightforward.  If you're coming from Windows, it's a lot more intuitive than some of the setup horrors I've seen.

As far as M-Audio controllers go, I've noticed my Axiom isn't as responsive as my Roland synths over MIDI (in **any** environment).  They've taken a lot of heat for it from a lot of folks on their forums, but it was still disappointing considering USB was supposed to outperform MIDI.

---

### Post by thorgal on 2008-05-28
jackd rocks, man!
sure, it's not your average sound server. It's meant for pro work and as such, requires a bit of sweat to have it tuned as you want, which means you need to know what you really want ;)

---

### Post by Yonderknight on 2008-05-30
Okay well,

I installed the ASIO4ALL drivers on my Vista setup and that pretty much eliminated the latency issues I was having, so at least now I know what to aim for on ubuntu =p.

I installed Jack and the WineASIO drivers according to this guide:
[http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio)

Except in the wine config I only had the ALSA drivers selected like some people suggested.

Everything seemed to be going just fine, but when I run FL studio and select the wineasio drivers, nothing plays =(. The "CPU Load" bar is at 100%, and even if the step sequencer is completely empty and I hit play, it goes to the first beat and just stops there.

If I select the regular drivers in FL Studio, everything works like it used to.
O.o

Does anybody know what the problem is?

Thanks in advance

EDIT:

If I change Jack server's driver to "dummy" instead of "alsa", things seem to work fine (but of course I can't hear any sound). Does this mean it's a problem with Jack connecting to ALSA?

---

### Post by Yonderknight on 2008-06-01
Okay well...
I think I'm a little closer to getting Jack working.

I followed some instructions from this thread:
[http://ubuntuforums.org/showthread.php?p=5038203](http://ubuntuforums.org/showthread.php?p=5038203)

(created a group named audio and added some lines to /etc/security/limits.conf)

Now, jack starts up in Realtime mode (it wasn't doing that before). I also stopped getting a constant flow of Xruns when I'm not even listening to anything. But...when I start up FL studio...I get a whole bunch of error messages in Jack, and my CPU usage goes up to about 70% when I'm not even doing anything.

Here's some of the Jack log

```

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|512|6|44100|0|0|nomon|swmeter|soft-mode|32bit
control device hw:0
configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 6 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 6 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 6 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
00:54:33.257 Server configuration saved to "/home/henry/.jackdrc".
00:54:33.258 Statistics reset.
00:54:33.259 Client activated.
00:54:33.261 JACK connection change.
00:54:33.263 JACK connection graph change.
cannot lock down memory for RT thread (Cannot allocate memory)
00:54:46.711 ALSA connection graph change.
00:54:48.145 JACK connection graph change.
00:54:48.280 JACK connection change.
ALSA: poll time out, polled for 17413074 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
cannot complete execution of the processing graph (Success)
cannot complete execution of the processing graph (Success)
cannot complete execution of the processing graph (Success)
...
cannot complete execution of the processing graph (Success)
cannot complete execution of the processing graph (Success)
00:54:48.622 Client deactivated.
cannot compl
00:54:48.624 JACK was stopped successfully.
00:54:48.625 Post-shutdown script...
00:54:48.626 killall jackd
ete execution of the processing graph (Success)
cannot complete execution of the processing graph (Success)
cannot complete execution of the processing graph (Success)
...
jackd: no process killed

```

Also, in FL studio when I take a look at the number of underruns it's just continually going up very fast.

It feels like I'm so close to getting this to work!!! >:(
Anybody know what's up with jack?

---

### Post by thorgal on 2008-06-01
you probably need a realtime kernel.

---

### Post by Yonderknight on 2008-06-01
I have one installed. It was in that first guide I posted.

EDIT:

Well i finally got it working! I didn't have my sound card selected in one of the dropdown boxes (I had it set to "default"). The quality is really bad though...and I can't seem to get rid of the XRuns even with the buffer settings to the highest they'll go (which kind of defeats the point of having a low-latency setup anyways).

I guess I will try messing around with some Linux DAW's then, either that or stick with FL studio on windows =\.

---

