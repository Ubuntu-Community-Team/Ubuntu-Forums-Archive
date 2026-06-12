---
title: "Jack is dead"
date: 2010-05-05
forum: Ubuntu Studio
---

### Post by Funkalicious on 2010-05-05
Helo

I have problems too with Jack and I thought, I post it here rather than opening a new thread. I always get this message:


```
14:33:42.957 Steckfeld deaktiviert.
14:33:42.971 Statistik zurückgesetzt.
14:33:43.008 Schaubild der ALSA-Verbindungen geändert.
14:33:43.184 ALSA-Verbindung geändert.
14:33:46.340 Startup script...
14:33:46.341 artsshell -q terminate
sh: artsshell: not found
14:33:46.746 Startup script terminated mit Rückgabewert = 32512.
14:33:46.746 JACK startet...
14:33:46.747 /usr/bin/jackd -v -p128 -t5000 -dalsa -r44100 -p256 -n3 -D -Chw:0,0 -Phw:0,0
14:33:46.754 JACK wurde mit PID = 2264 gestartet.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    669363
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
JACK compiled with System V SHM support.
server `default' registered
14:33:46.795 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Overall operation failed. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.
loading driver ..
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x632c60 fd = -1
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|256|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
start poll on 3 fd's
14:33:48.552 JACK wurde angehalten erfolgreich.
14:33:48.552 Post-shutdown script...
14:33:48.553 killall jackd
14:33:48.553 JACK ist abgestürzt.
jackd: no process found
14:33:49.157 Post-shutdown script terminated mit Rückgabewert = 256.
```

I don't know how to find out what my soundcard is like...

:guitar:

---

### Post by ibuclaw on 2010-05-05
Moved to own thread. Thanks. :)

---

