---
title: "Jack jack jack"
date: 2010-05-11
forum: Ubuntu Studio
---

### Post by mineo on 2010-05-11
oh my it sounds like a familiar complication, but any help will help. 
JACK not being normal.
UBUNTU STUDIO the latest version, not much is touched, so likely being problems with hardware. 
/etc/security/limits.conf   is:
@audio - rtprio 99
@audio - memlock 375486  (as suggested by the message below)
@audio - nice -10

me being the member of the group.
here's the message.
 p, li { white-space: pre-wrap; }  > 
[COLOR=#999999]22:10:19.242 Startup script...[/COLOR]
 [COLOR=#990099]22:10:19.243 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:10:19.648 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:10:19.652 JACK is starting...[/COLOR]
 [COLOR=#990099]22:10:19.653 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p64 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    375486
 [COLOR=#999999]22:10:19.699 JACK was started with PID=10126.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 `default' server already active
 [COLOR=#999999]22:10:19.747 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]22:10:19.749 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:10:19.750 killall jackd[/COLOR]
 [COLOR=#999999]22:10:20.164 Post-shutdown script terminated successfully.[/COLOR]
 [COLOR=#FF0000]22:10:21.865 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


it is bypassing some input out put, so i guess it IS working. 
FIRST; I want proper working environment;
SECOND: the biggest problem being ARDOUR not launching.

---

### Post by thorgal on 2010-05-11
you've got the following log msg:

```

`default' server already active

```

so some jackd process is already running. In a terminal, type

```

ps -Leo comm,class,rtprio | grep jackd

```

and see if you get something.

---

### Post by mineo on 2010-05-11
not nice though;
> 
jackd <defunct> TS       -
what does that mean?

---

### Post by hxcobd on 2010-05-11
Top 2 reasons JACK won't start:

1.) You already have some program that's using or WAS using audio open. This includes all media players, web browsers, and so on. CLOSE ALL THAT STUFF BEFORE YOU TRY TO START JACK.

2.) Your JACK settings are incorrect. Buffer, periods/buffer, and samplerate are the most common incorrect settings.

---

### Post by sgx on 2010-05-11
> **mineo said:**
> not nice though;
what does that mean?

On another note, I always use memlock unlimited, instead of some
arbitrary memory amount. Maybe that will help at some point.

In the meantime, start jackd with

jackd -d alsa -r 44100

If that works, and you have a realtime kernel, try

jackd -R -d alsa -r 44100

Cheers

---

### Post by thorgal on 2010-05-12
> **mineo said:**
> not nice though;
what does that mean?

does not look good, you had a jack process that did not die properly and is in the limbo of the unix processes. Kill it first:

```

kill -9 `pgrep jackd`

```

 if it's not working, log out and log in. If it is still around, reboot.

It could well be that jack is automatically started at either boot time or login time. To check, reboot and log in without doing any thing related to jack. Just check if you have a jack process running right after login. If not, then open a terminal and try the most dumb jack command (assuming you want to use your first sound card, so-called hw:0, and the ALSA backend)

```

jackd -dalsa

```

this is almost the dumbest way to start jack (non RT mode, all default options except for the backend).

If you get it running like this, then you can refine the options.

---

