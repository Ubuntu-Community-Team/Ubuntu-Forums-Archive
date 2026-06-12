---
title: "programs opening"
date: 2011-04-03
forum: Ubuntu Studio
---

### Post by JamesBartlett on 2011-04-03
I'm not sure entirely why, but some programs appear to have trouble opening, so far LMMS is only showing the splash screen for a second or two, Ubuntu Software Centre closes after a second, and Hydrogen Drum Machine just does nothing. Can anyone help?

---

### Post by Pablo_F on 2011-04-03
Hi, 

Launch the programs in a terminal to see the error message. Just write down the name and press Enter. 

lmms
software-center
hydrogen
...

---

### Post by JamesBartlett on 2011-04-05
Right, Hydrogen works in Terminal, as does Software Centre, but still no luck with LMMS which is a program I imagine myself using a lot...

---

### Post by Pablo_F on 2011-04-05
Hi, 


Can you give the output of the following informative commands?

free

(info about your RAM)

ls -la /dev/shm

(list the files under /dev/shm)

lmms

(paste the error messages)

Cheers! Pablo

---

### Post by JamesBartlett on 2011-04-05
Cheers mate!

Hygrogen has failed to start in terminal now, the codes are as follows:

Hydrogen:
[FONT=Courier New]james@james-desktop:~$ hydrogen

Hydrogen 0.9.4 [Feb 22 2010]  [[http://www.hydrogen-music.org]](http://www.hydrogen-music.org])
Copyright 2002-2008 Alessandro Cominu

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1448784
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1448784
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
(E) JackOutput    init Unknown status with JACK server. 
Bus error
james@james-desktop:[/FONT]

Free:
[FONT=Courier New]james@james-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1931712    1778564     153148          0      37652    1232272
-/+ buffers/cache:     508640    1423072
Swap:      5654840     151332    5503508
james@james-desktop:~$ [/FONT]

ls -la /dev/shm:
[FONT=Courier New]james@james-desktop:~$ ls -la /dev/shm
total 964676
drwxrwxrwt  3 root        root         620 2011-04-05 20:31 .
drwxr-xr-x 18 root        root        4140 2011-04-05 14:33 ..
drwx------  3 james       james         60 2011-04-05 20:31 jack-1000
-rw-r-----  1 beagleindex nogroup     4096 2011-04-05 15:00 mono.12948
-rw-r-----  1 james       james       4096 2011-04-05 15:17 mono.1630
-rw-r-----  1 james       james       4096 2011-04-05 15:35 mono.1642
-rw-r-----  1 james       james      79880 2011-04-05 14:43 mono-shared-1000-shared_data-james-desktop-Linux-i686-312-12-0
-rw-r-----  1 james       james    3686404 2011-04-05 14:43 mono-shared-1000-shared_fileshare-james-desktop-Linux-i686-36-12-0
-r--------  1 james       james   67108904 2011-04-05 15:19 pulse-shm-1072724168
-r--------  1 james       james   67108904 2011-04-05 14:33 pulse-shm-1610922265
-r--------  1 james       james   67108904 2011-04-05 14:34 pulse-shm-1689683657
-r--------  1 james       james   67108904 2011-04-05 14:33 pulse-shm-1796103556
-r--------  1 james       james   67108904 2011-04-05 14:34 pulse-shm-1844037570
-r--------  1 james       james   67108904 2011-04-05 14:33 pulse-shm-1976996114
-r--------  1 james       james   67108904 2011-04-05 15:18 pulse-shm-2150668129
-r--------  1 james       james   67108904 2011-04-05 15:18 pulse-shm-2504682381
-r--------  1 james       james   67108904 2011-04-05 17:26 pulse-shm-2532220307
-r--------  1 james       james   67108904 2011-04-05 20:31 pulse-shm-2548631173
-r--------  1 james       james   67108904 2011-04-05 15:17 pulse-shm-2689719783
-r--------  1 james       james   67108904 2011-04-05 14:34 pulse-shm-275136215
-r--------  1 james       james   67108904 2011-04-05 20:31 pulse-shm-2833232862
-r--------  1 james       james   67108904 2011-04-05 14:33 pulse-shm-3131904950
-r--------  1 james       james   67108904 2011-04-05 17:23 pulse-shm-341000863
-r--------  1 james       james   67108904 2011-04-05 14:33 pulse-shm-3442616955
-r--------  1 james       james   67108904 2011-04-05 14:51 pulse-shm-3717608246
-r--------  1 james       james   67108904 2011-04-05 14:33 pulse-shm-3980557255
-r--------  1 james       james   67108904 2011-04-05 18:32 pulse-shm-4051790369
-r--------  1 james       james   67108904 2011-04-05 20:31 pulse-shm-4060917791
-r--------  1 james       james   67108904 2011-04-05 20:31 pulse-shm-4244675825
-r--------  1 james       james   67108904 2011-04-05 20:31 pulse-shm-663813791
-r--------  1 james       james   67108904 2011-04-05 20:31 pulse-shm-800376814
james@james-desktop:~$ [/FONT]

And Finally, LMMS:
[FONT=Courier New]james@james-desktop:~$ lmms
Segmentation fault[/FONT]

Thank you very much for your help, I'm very grateful.

---

### Post by JamesBartlett on 2011-04-05
I have scanned through it for anything, but I'm still getting to grips with Terminal. I'm quite familiar with cmd.exe, but that doesn't seem to help at all! :(

---

### Post by Pablo_F on 2011-04-05
Hi James, 

So, with my long post in the other thread and all. You seem to have rtprio and memlock privileges allready :) Good thing.

Note that hydrogen automatically starts the jack server. I recommend you start it before any jack-aware app, by means of Jack Control. At first, it is two or three clicks more. Later you can learn how to automate things.

The problem: /dev/shm is overpopulated with pulse-shm-* files. This is awful and it needs to be solved. 

I strongly recommended that you:

1. Clean /dev/shm
2. Kill pulseaudio and avoid pulseaudio autospawn before running the jack server and start pulseaudio again when you stop the server.

I can teach you how to do this automatically, but for now, do a:

rm -f /dev/shm/pulse-shm*

and things will improve, hopefully. 

Cheers, Pablo

---

### Post by cek on 2011-04-06
It seems to be a problem getting Jack to start.

Find a program in Sound & Video called qjackctl -- this is a visual front end to Jack and allows you to start and stop it manually, as well as changing the many (many) settings.

What the settings need to be for you is dependent upon your hardware, specifically your sound card.

---

