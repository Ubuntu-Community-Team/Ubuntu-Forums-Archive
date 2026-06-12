---
title: "Cannot start Jack - It just quits"
date: 2010-07-02
forum: Ubuntu Studio
---

### Post by etienne@Rofti on 2010-07-02
Hi there friendly Ubuntu-ers!

I have a clean install of Ubuntu Studio 10.04, and I have attempted to start the JACK server using the QJackCTL - the GUI for Jack.

However, whenever I press the "Start" button, it just stops as soon as I have started it, and I get the following message in the messages window:

```
17:32:06.633 Startup script...
17:32:06.634 artsshell -q terminate
sh: artsshell: not found
17:32:07.037 Startup script terminated with exit status=32512.
17:32:07.038 JACK is starting...
17:32:07.039 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    551451
17:32:07.063 JACK was started with PID=1481.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
17:32:07.877 JACK was stopped successfully.
17:32:07.878 Post-shutdown script...
17:32:07.879 killall jackd
17:32:07.880 JACK has crashed.
jackd: no process found
17:32:08.305 Post-shutdown script terminated with exit status=256.
17:32:09.174 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```

Does anyone know why I cannot start the Jack server? I have been Googling but I have no results as of yet...

Thanks!

Etienne

---

### Post by mango42 on 2010-07-02
Hi,

I had the same problem a while back but being somewhat 'synaptically challenged' I don't remember the details; however, I do remember a very useful starting point [here]("https://help.ubuntu.com/community/HowToJACKConfiguration").

Jumping into [this thread]("http://ubuntuforums.org/showthread.php?t=806730&highlight=Jack+AutoStatic&page=3") should help you also.

Bon chance - the end result is *way more* than worth the effort, IMO ;-)

---

### Post by baekgaard on 2010-07-02
I've had a similar problem. Jackd stopped with a bus error (which is visible if you try to run it manually).

What I did was to go to System / Preferences / Startup Applications and disable Pulseaudio.

It might also be a good idea to edit /etc/pulse/client.conf and add the 2nd line below, to prevent any "accidental" starts of pulseaudio:

; autospawn = yes
autospawn = no

I then did a killall pulseaudio, but you can probably also just reboot.

At least jack started to work on my Lucid Lynx Ubuntu Studio installation when I did the above.

Depending on what you want to do afterwards, you may have to select ALSA out devices for your "standard" programs otherwise.


-- Per.

---

