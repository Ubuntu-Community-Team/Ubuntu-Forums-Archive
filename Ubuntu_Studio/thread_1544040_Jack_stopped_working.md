---
title: "Jack stopped working"
date: 2010-08-02
forum: Ubuntu Studio
---

### Post by Peter7K on 2010-08-02
```
22:24:36.398 Patchbay deactivated.
22:24:36.422 Statistics reset.
22:24:36.536 JACK is starting...
22:24:36.537 /usr/bin/jackd -u -dalsa -dhw:0 -r44100 -p2048 -n4 -m
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
22:24:36.565 ALSA connection graph change.
22:24:36.611 JACK was started with PID=2469.
could not open driver .so '/usr/lib/jack/jack_freebob.so': libfreebob.so.0: cannot open shared object file: No such file or directory
22:24:36.759 ALSA connection change.
no message buffer overruns
could not open component .so '/usr/lib/jack/jack_freebob.so': libfreebob.so.0: cannot open shared object file: No such file or directory
no message buffer overruns
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|2048|4|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf6fdc000 irq 21
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
22:24:36.974 JACK was stopped with exit status=255.
22:24:36.974 Post-shutdown script...
22:24:36.974 killall jackd
jackd: no process found
22:24:37.412 Post-shutdown script terminated with exit status=256.
22:24:38.764 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
22:24:43.230 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
22:24:52.066 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

That occurs when I run QjackCtl.  Any tips?  Thank you for your time.

---

### Post by cchhrriiss121212 on 2010-08-02
> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
This is likely the reason, so just shut down anything that is using audio before trying to run jack.

---

### Post by AutoStatic on 2010-08-02
You're running Jack2 (jackdmp 1.9.5) which is not the version that comes with Lucid Lynx. Did you update JACK from a PPA or are you running the Meerkat Alpha 1? Also, it's best to run onboard cards with a Periods setting of 2 instead of 4.

---

### Post by Peter7K on 2010-08-02
Ah, earlier I did not have to close *everything* to start jack, I guess I do now with this different version.

The version of jack is from this ppa:
[http://ppa.launchpad.net/falk-t-j/lucid/ubuntu](http://ppa.launchpad.net/falk-t-j/lucid/ubuntu)

(taken from these forums!)

And it started just fine if I closed everything, thanks!  Marking solved.

---

