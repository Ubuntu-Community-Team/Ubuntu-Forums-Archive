---
title: "JACK/asla xrun problem in 10.10"
date: 2011-04-05
forum: Ubuntu Studio
---

### Post by mikeymo1741 on 2011-04-05
I've looked for a while to see if this has been answered, but have not seen exactly my problem.  I run a Dell Inspiron B130 with 10.10 Studio.  I've really not had a problem with it, and use Ardour all the time to record, Hydrogen, Jammin, you name it. 

Soon after the 10.10 upgrade, I tried to start JACK, and I keep getting alsa xruns, and JACK will not start.  

I get: 
> 
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
23:16:53.422 ALSA connection change.
23:16:53.425 ALSA connection graph change.
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xdfebc000 irq 42
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery

...and  that goes on and on.   

I thought maybe the new generic kernel was to blame, and found an article about upgrading to the Natty low latency kernel, which I have done, but it makes no difference.  

No hardware has changed, so it's not that. I've tried JACK with and without realtime checked and it makes no difference.  I'm at a loss here.

---

### Post by Pablo_F on 2011-04-06
Hi, 

I suggest you try the synchronous mode, as jackdmp (jackd2) has two modes, sync and async, being the latter the default (while the original jackd is synchronous only).

You should have to append "-S" to the jackd command, in the "server path" field (/usr/bin/jackd -S).

You can also get the original jack by installing the jackd1 package.

Cheers, Pablo

---

### Post by mikeymo1741 on 2011-04-08
Appending -S did nothing.   Exact same situation. 

I un-installed jackd2 and installed jackd1.  Still doesn't run, but I get different error messages: 

> 22:09:54.566 Patchbay deactivated.
22:09:54.786 Statistics reset.
22:09:54.955 Startup script...
22:09:54.956 artsshell -q terminate
22:09:54.983 ALSA connection graph change.
sh: artsshell: not found
22:09:55.881 Startup script terminated with exit status=32512.
22:09:55.883 JACK is starting...
22:09:55.884 /usr/bin/jackd -m -dalsa -dhw:0 -r48000 -p1024 -n2
22:09:55.980 JACK was started with PID=8702.
22:09:55.986 JACK was stopped with exit status=255.
22:09:55.989 Post-shutdown script...
22:09:55.990 killall jackd
Unknown option character 
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
usage: jackd [ --no-realtime OR -r ]
             [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
      (the two previous arguments are mutually exclusive. The default is --realtime)
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --no-sanity-checks OR -N ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             Available backends may include: alsa, dummy, freebob, firewire, net, oss, sun, or portaudio.
       jackd -d backend --help
             to display options for each backend
22:09:56.126 ALSA connection change.
22:09:56.130 ALSA connection graph change.
jackd: no process found
22:09:56.427 Post-shutdown script terminated with exit status=256.
22:09:58.148 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
22:10:06.167 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
22:10:16.747 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

If I run it with the -d alsa switch as the message seems to suggest, I get: 

> 22:13:32.676 Startup script...
22:13:32.677 artsshell -q terminate
sh: artsshell: not found
22:13:33.080 Startup script terminated with exit status=32512.
22:13:33.081 JACK is starting...
22:13:33.082 /usr/bin/jackd -dalsa -m -dalsa -dhw:0 -r48000 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
22:13:33.147 JACK was started with PID=8798.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
22:13:35.503 Server configuration saved to "/home/mmahoney/.jackdrc".
22:13:35.505 Statistics reset.
22:13:40.206 Client activated.
22:13:40.208 JACK connection change.
22:13:40.225 JACK connection graph change.
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
22:13:40.348 XRUN callback (1).
22:13:42.217 XRUN callback (46 skipped).
22:13:44.221 XRUN callback (47 skipped).
jackd watchdog: timeout - killing jackd
22:13:46.388 Shutdown notification.
22:13:46.390 JACK is being forced...
cannot continue execution of the processing graph (Resource temporarily unavailable)
zombified - calling shutdown handler
22:13:46.592 JACK was stopped with exit status=1.
22:13:46.593 Post-shutdown script...
22:13:46.593 killall jackd
jackd: no process found
22:13:47.027 Post-shutdown script terminated with exit status=256.

---

### Post by Pablo_F on 2011-04-09
I don't see where is the unknown parameter in "/usr/bin/jackd -m -dalsa -dhw:0 -r48000 -p1024 -n2". I just tried in a terminal and I don't have errors. I am running jackd jackd 0.120.1 though. 

On the other hand, afaik we should allow jack to lock memory so I don't see the utility of "no memory lock" option.

In general, the server path field should be left alone. Normally, you choose the options graphically. "-S" is a tricky exception. 

Back to the xruns problem, onboard cards are difficult to diagnose. It could be the wireless, it could be that it is sharing IRQ number with other devices (check "cat /proc/interrupts"), it could be the kernel, or the exact parameters (try 44100, 2048...), or the alsa driver, or some weird configuration in alsamixer.

It might help installing the low latency kernel. I doubt that maverick has it in the official repos but you can get it in a less orthodox way.  

Cheers! Pablo

---

### Post by mikeymo1741 on 2011-04-11
I have the Natty low-latency kernal installed now.  Made no difference. 

I'll give flipping some of the other parameters a try.  JACK always ran perfectly on this PC, so it must be one of the recent kernel updates that is messing with it.

---

### Post by zettberlin on 2011-04-11
I run jack on 10.10 sucessfully like this:

/usr/bin/jackd -R -t1000 -u -dalsa -dhw:0 -r48000 -p256 -n2 -S -Xseq

---

### Post by ailo.at on 2011-04-11
I believe the audio card is grabbed by pulseaudio. Try using:

pasuspender -- jackd -d alsa

If that works, you just need to make sure PA is not using any apps whenever you run jack, or just use that command when you start jack.

---

### Post by mikeymo1741 on 2011-05-07
I was hoping the full update to Natty would fix it.  After the update, the xruns were gone, JACK still would not run.  

Turns out that starting JACK with the audio input muted starts all kinds of issues.  It was, I unmuted it, and things are running normally.

---

