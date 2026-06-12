---
title: "jack2d will not start"
date: 2010-10-25
forum: Ubuntu Studio
---

### Post by Jsdey on 2010-10-25
Earlier today qjackctl was running at a latency of 5.33 ms without creating any xruns.  I am using the current stock 10.10 kernel--x64.  I downloaded rosegarden and vlc and some ancillary plugins.  Now jackd will not run.  I have purged associated programs and reloaded qjackctl and jack2d but jackd still does not start.  Any suggestions would be greatly appreciated.  Thanks.  The error messages from jackd are:

robo12@robo12:~$ jackd -dalsa -dhw:0 -r48000 -p128 -n2 -P -o2
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|128|2|48000|0|2|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xee400000 irq 48
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle

---

### Post by AutoStatic on 2010-10-26
> **Jsdey said:**
> Earlier today qjackctl was running at a latency of 5.33 ms without creating any xruns.Hello Jsdey, we're you only running it or were you also connecting programs to it and routing sound or MIDI through JACK?

> **Jsdey said:**
> I am using the current stock 10.10 kernel--x64.  I downloaded rosegarden and vlc and some ancillary plugins.  Now jackd will not run.  I have purged associated programs and reloaded qjackctl and jack2d but jackd still does not start.JACK does start but is producing xruns. When do you get those xruns? When you start JACK or when you start up other apps like VLC and try to connect them with JACK?

You could try disabling CPU frequency scaling, what kind of CPU do you have?

---

### Post by Jsdey on 2010-10-26
AutoStaic--Thanks for your response. 

 I was running qjackctl and aeolus and driving with aplaymidi all connected through qjackctl.  The xruns occur when jackd starts.  I have purged vlc and rosegarden.  My Thinkpad t60p is using an Intel Core Duo T7200/2ghz.  Again qjackctl was work without a hitch before downloading vlc and rosegarden.  Something has changed the state of my machine that does not get repaired by purging the programs.  

In preparing this response I did make a discovery that gives me hope.  I set my enviroment to root (sudo su) and qjackctl/aeolus/aplaymide work and produce sound without xruns.  So it looks like  the user space environment was changed.  Do you recall a link that provides the steps for manually setting the user environment for sound/jackd.  I would like to go through the installation procedure to see if I can repair.  Any other suggestions would be greatly appreciated.

Jsdey

---

### Post by Jsdey on 2010-10-26
Well!  It appears that jackd is working and my problems had nothing to do with the downloads.  What had occurred was the I changed jackd by changing the setup page in qjackctl.  The setting windows showed a latency of 5.33 ms.  I then returned to the main window in qjackctl and was warned that the changes would not take effect until I restarted jackd--I ignored (didn't read) this warning and went about testing with aeolus.  It worked like a charm--I thought I was running with a latency of 5.33ms but I was not.  After running several hours without any xruns, I was convinced that the generic kernel is now doing a good job of running realtime applications.  When I stopped qjackctl, it saved the .jackdrc file with the low latency setting.  I then downloaded other applications and qjackctl would not start after that. (Or as pointed out to me, it did start but was throwing pages and pages of xruns at me.)  It appears that the generic kernel on a lenovo t60p laptop cannot deliver real low latency.  I did go back to the setup and now am running reliably with a latency of 16ms.

I would sure like to see the -rt project resurrected.  I would be available to test and assist in any way possible with my non-existing knowledge of the intricacies of the linux kernel.

---

