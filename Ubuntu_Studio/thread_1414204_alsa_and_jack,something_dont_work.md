---
title: "alsa and jack,something dont work?"
date: 2010-02-23
forum: Ubuntu Studio
---

### Post by rixtr66 on 2010-02-23
ive installed the ubuntu studio audio packageson ubuntu karmic,i also installed the rt kernel,however when i start jack i get this:
code:/11:24:31.429 Patchbay deactivated.
11:24:31.435 Statistics reset.
11:24:31.496 Startup script...
11:24:31.497 artsshell -q terminate
11:24:31.519 ALSA connection graph change.
sh: artsshell: not found
11:24:31.933 Startup script terminated with exit status=32512.
11:24:31.933 JACK is starting...
11:24:31.934 /usr/bin/jackd -dalsa -dhw:1,1 -r44100 -p1024 -n3 -i1 -o1 -Xseq
11:24:31.991 JACK was started with PID=4493.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1,1|hw:1,1|1024|3|44100|1|1|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set channel count to 1 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
11:24:32.037 JACK was stopped successfully.
11:24:32.037 Post-shutdown script...
11:24:32.038 killall jackd
11:24:32.141 ALSA connection change.
jackd: no process found
11:24:32.447 Post-shutdown script terminated with exit status=256.
11:24:34.146 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
code:/#
is something wrong with alsa?
ive been following the "jack doesnt work"thread and have set up for realtime.w/permissions etc.im also running an m-audio fast track pro.
any information would be greatly appreciated
Rick  
ps.how do i make the code boxes?

---

### Post by cchhrriiss121212 on 2010-02-23
> **rixtr66 said:**
> 
ALSA: cannot set channel count to 1 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa


Here is your problem. I would set channels to default and try again.
You can make code boxes with a button with # on it on advanced reply.

---

### Post by rixtr66 on 2010-02-23
how do i reset the channels?
Rick
edit;duh i found it!thanks!
Rick

---

### Post by berg3rakger4k on 2011-07-04
> **rixtr66 said:**
> how do i reset the channels?
Rick
edit;duh i found it!thanks!
Rick

how do u reset the channels? 
i dont know how to edit? 
help help help

---

### Post by Pablo_F on 2011-07-05
Please, open a new thread, this is marked as solved. And paste the contents of the Messages window, as the OP did.

---

### Post by berg3rakger4k on 2011-07-05
> **Pablo_F said:**
> Please, open a new thread, this is marked as solved. And paste the contents of the Messages window, as the OP did.

ok... sorry... :)

---

