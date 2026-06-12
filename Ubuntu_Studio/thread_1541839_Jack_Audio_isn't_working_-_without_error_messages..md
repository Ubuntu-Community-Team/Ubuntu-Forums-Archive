---
title: "Jack Audio isn't working - without error messages."
date: 2010-07-29
forum: Ubuntu Studio
---

### Post by kooia on 2010-07-29
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]14:28:43.964 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:28:44.006 Statistics reset.[/COLOR]
 [COLOR=#66cc99]14:28:44.018 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]14:28:44.216 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:28:45.504 Startup script...[/COLOR]
 [COLOR=#990099]14:28:45.505 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:28:45.907 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:28:45.907 JACK is starting...[/COLOR]
 [COLOR=#990099]14:28:45.908 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]14:28:45.947 JACK was started with PID=3961.[/COLOR]
 [COLOR=#999999]14:28:45.948 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]14:28:45.948 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:28:45.949 killall jackd[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 jackd: no process found
 [COLOR=#999999]14:28:46.357 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]14:28:48.024 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```That's all I get right now.  First it said to add
```

#@audio          -       rtprio          100
#@audio          -       nice            -10

```to the /etc/security/limits.conf
and then to type
```

sudo -s
usermod -a -G audio (username)

```Now I get that, and I can't see any errors.  Can anyone tell me what to do, or some alternative to JACK?  I really want to try Ardour, but for the last three months, I've been trying to figure out the problem.  Now, I (finally) realize that its a problem with JACK, not that JACK is having a problem with Ardour (and all the other JACK programs).

Thanks anyone!

Yeah, and I use Ubuntu, not Ubuntu Studio.  I set up the MIDI drivers (or whatever you call all that stuff) for my sound card.

---

### Post by cchhrriiss121212 on 2010-07-30
You need to add this to the limits.conf file:
```
@audio          -       rtprio          100
@audio          -       memlock unlimited
```
and not this:
```
#@audio          -       rtprio          100
#@audio          -       nice            -10
```
The # are used for user comments only and any process using the file will ignore whatever is on a line beginning with a #. The nice value is not needed but memlock is.

---

### Post by kooia on 2010-07-30
Hm.  Really?

When I tried
```

@audio            -         rtprio    100
@audio            -         nice       -10

```

Jack still had a problem with it.  But I'll test this out, and thanks for the reply!

---

### Post by kooia on 2010-07-30
So I added the lines you suggested,
```

@audio          -       rtprio          100
@audio          -       memlock         1545999

```

But I get this "XRUNS"  What are they, and here's what its doing (just a little, I think it'll go on forever.  Any more advice?  Thanks in advance!

```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]20:23:57.024 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:23:57.136 Statistics reset.[/COLOR]
 [COLOR=#66CC99]20:23:57.149 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]20:23:57.456 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:23:58.523 Startup script...[/COLOR]
 [COLOR=#990099]20:23:58.524 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]20:23:58.926 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]20:23:58.926 JACK is starting...[/COLOR]
 [COLOR=#990099]20:23:58.927 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 [COLOR=#999999]20:23:58.982 JACK was started with PID=14805.[/COLOR]
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]20:24:01.122 Server configuration saved to "/home/berard/.jackdrc".[/COLOR]
 [COLOR=#999999]20:24:01.124 Statistics reset.[/COLOR]
 [COLOR=#999999]20:24:01.161 Client activated.[/COLOR]
 [COLOR=#9999CC]20:24:01.162 JACK connection change.[/COLOR]
 [COLOR=#CC9966]20:24:01.173 JACK connection graph change.[/COLOR]
 [COLOR=#CC9966]subgraph starting at qjackctl timed out (subgraph_wait_fd=9, status = 0, state = Triggered, pollret = 0 revents = 0x0)[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 1.597 msecs[/COLOR]
 [COLOR=#CC66CC]20:24:35.268 XRUN callback (1).[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 1.476 msecs[/COLOR]
 [COLOR=#CC66CC]20:25:36.083 XRUN callback (2).[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.591 msecs[/COLOR]
 [COLOR=#CC66CC]20:25:38.855 XRUN callback (3).[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.937 msecs[/COLOR]
 [COLOR=#CC99CC]20:25:39.273 XRUN callback (1 skipped).[/COLOR]
 [COLOR=#CC66CC]20:26:56.378 XRUN callback (5).[/COLOR]
 [COLOR=#CC9966]delay of 18300.000 usecs exceeds estimated spare time of 15894.000; restart ...[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 2.023 msecs[/COLOR]
 [COLOR=#CC66CC]20:26:58.039 XRUN callback (6).[/COLOR]
 [COLOR=#999999]20:27:39.927 Client deactivated.[/COLOR]
 [COLOR=#999999]20:27:39.928 JACK is stopping...[/COLOR]
 [COLOR=#CC9966]jack main caught signal 15[/COLOR]
 [COLOR=#999999]20:27:39.980 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]20:27:39.981 Post-shutdown script...[/COLOR]
 [COLOR=#990099]20:27:39.981 killall jackd[/COLOR]
 [COLOR=#CC9966]jackd: no process found[/COLOR]
 [COLOR=#999999]20:27:40.392 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#999999]20:27:41.349 Startup script...[/COLOR]
 [COLOR=#990099]20:27:41.350 artsshell -q terminate[/COLOR]
 [COLOR=#CC9966]sh: artsshell: not found[/COLOR]
 [COLOR=#999999]20:27:41.752 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]20:27:41.752 JACK is starting...[/COLOR]
 [COLOR=#990099]20:27:41.753 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]20:27:41.755 JACK was started with PID=14887.[/COLOR]
 [COLOR=#CC9966]jackd 0.118.0[/COLOR]
 [COLOR=#CC9966]Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.[/COLOR]
 [COLOR=#CC9966]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#CC9966]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#CC9966]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#CC9966]no message buffer overruns[/COLOR]
 [COLOR=#CC9966]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#CC9966]loading driver ..[/COLOR]
 [COLOR=#CC9966]apparent rate = 44100[/COLOR]
 [COLOR=#CC9966]creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#CC9966]control device hw:0[/COLOR]
 [COLOR=#CC9966]configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods[/COLOR]
 [COLOR=#CC9966]ALSA: final selected sample format for capture: 32bit integer little-endian[/COLOR]
 [COLOR=#CC9966]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#CC9966]ALSA: final selected sample format for playback: 32bit integer little-endian[/COLOR]
 [COLOR=#CC9966]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999933]20:27:43.852 Server configuration saved to "/home/berard/.jackdrc".[/COLOR]
 [COLOR=#999999]20:27:43.853 Statistics reset.[/COLOR]
 [COLOR=#999999]20:27:43.854 Client activated.[/COLOR]
 [COLOR=#9999CC]20:27:43.855 JACK connection change.[/COLOR]
 [COLOR=#CC9966]20:27:43.866 JACK connection graph change.[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 3.307 msecs[/COLOR]
 [COLOR=#CC66CC]20:28:35.668 XRUN callback (1).[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 2.124 msecs[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 2.961 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 1.943 msecs[/COLOR]
 [COLOR=#999999]subgraph starting at qjackctl timed out (subgraph_wait_fd=9, status = 0, state = Triggered, pollret = 0 revents = 0x0)[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 1.551 msecs[/COLOR]
 [COLOR=#CC99CC]20:28:37.903 XRUN callback (3 skipped).[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 2.091 msecs[/COLOR]
 [COLOR=#CC66CC]20:30:37.636 XRUN callback (6).[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.045 msecs[/COLOR]
/*This goes on until 25, the I stopped it.*/

```

---

### Post by cchhrriiss121212 on 2010-07-31
XRUNs mean that your system cannot process the audio fast enough for your settings. There are a few things to try to reduce XRUNs:
Try out an rt-kernel
Disable any wireless connections when recording
Increase your latency
Enable soft mode

---

### Post by RaumTrug on 2010-07-31
well, is your cpu maxed out somehow? try adding the system monitor applet to a panel, and watch the cpu graph...normally, on a system with stable audio running in rt-mode xruns should only ocurr when the cpu is running at 100% (but before all other programs not running in rt mode like jack and its clients will become sluggish).

before even trying the -rt kernel:

-use a samplingrate of 48k instead of 44.1. some soundchips don't like 44.1...also play with 3 instead of 2 buffer/period. also try the "force 16bit" option, but all that depends on what kind of sound card you have.

-turn off the fancy "visual desktop effects" (compiz, whatever it's called in english...) while using jack, that will make the system ugly (plain), but stabilizes a lot.

-put the cpu frequency controlling applet to your panel, one for each core of your cpu, and set all of them to "performance" before starting jack (put to "ondemand" when finished with jack to get old, energy-saving standard-behaviour back).

-raising latency at already 1024 frames is probably not really what one wants... ;)

-disabling unneeded devices like usb-stuff attached to the pc, or turning off the wifi (up to unloading its kernel module...) can help, too.

-read through all kinds of linux forums, including this one, to be presented with all of the above tips, and even more. if you care to waste your time this way... :KS

good luck, more you couldn't really do I guess

[edit]
I've almost forgotte one thing to tune yet: watching for shared interrupts. you need to make sure that your soundcard is on its own interrupt, not shared with other devices. use "cat /proc/interrupts" in a shell to see all interrupts in your system. if you managed to find out which device is your sound, and it is on the same line as some other device (graphics, wifi, harddrive...almost everything can cause pain...), you should try to get into your system bios and assign the interrupts so the sound card is alone on it's number. won't work with all bioses/systems, and you better know what you're doing. when I got a pci soundcard, it was on the same interrupt as the graphics card, leading to x-run nightmares and crackling sound. I then disabled all unneeded hardware like onboard sound, serial/parallel ports etc. in bios and assigned different interrupt numbers to the pci slots the sound & gfx were sitting on. since then I can go to real low latencies :)

but as I said, you better read the mainboard manual before & really know what you're changing in bios before trying ;)

---

### Post by kooia on 2010-08-02
I tried what you suggested, and both 2.2GHz CPUs were still running at 1.2GHz the whole time, an System Monitor said that only 10% was being used.  Except for when Jack was opening, it was using 2.2GHz and 60% and 40% of the processors.

---

