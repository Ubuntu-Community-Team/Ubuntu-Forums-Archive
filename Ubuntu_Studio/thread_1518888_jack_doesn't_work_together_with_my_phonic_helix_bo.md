---
title: "jack doesn't work together with my phonic helix board 24 firewire mk 2"
date: 2010-06-27
forum: Ubuntu Studio
---

### Post by justlifeable on 2010-06-27
Hello,
no i have been reading threads and wikis for over 5 hours. 
I hope you can help me ...

I want to connect my phonic helixboard 24 firewire with my computer!
[http://www.thomann.de/de/phonic_phhb24u.htm](http://www.thomann.de/de/phonic_phhb24u.htm) &lt;- (i'm using this board, just without usb)

my computer (thinkpad r60) has not firewire, so i solved this problem over a pcmcia firewire card. It worked fine and i'm short before to install windows again ... 

I installed ffado and jack, the QT Jack Control Interface to).
before i'm starting jack im doing this:

```
sudo chmod a+rw /dev/raw1394
```

When i'm starting jack:
```

17:04:50.278 Steckfeld deaktiviert.
17:04:50.446 Statistik zurückgesetzt.
17:04:50.466 Startup script...
17:04:50.467 artsshell -q terminate
17:04:50.472 Schaubild der ALSA-Verbindungen geändert.
sh: artsshell: not found
17:04:50.882 Startup script terminated mit Rückgabewert = 32512.
17:04:50.882 JACK startet...
17:04:50.883 /usr/bin/jackd -r -dfirewire -r44100 -p128 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    762900
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
17:04:50.914 JACK wurde mit PID = 1999 gestartet.
libffado 2.0.0 built Jun 27 2010 14:13:07
17:04:51.085 ALSA-Verbindung geändert.
17:04:53.098 Serverkonfiguration nach "/home/jonassiewertsen/.jackdrc" gespeichert.
17:04:53.100 Statistik zurückgesetzt.
17:04:53.102 Client aktiviert
17:04:53.106 JACK-Verbindung geändert.
17:04:53.110 Schaubild der JACK-Verbindungen geändert.
17:04:53.968 XRUN callback (1).
17:05:03.987 XRUN callback (2).
17:05:13.982 XRUN callback (3).
17:05:23.828 XRUN callback (4).
17:05:28.366 XRUN callback (5).
17:05:33.978 XRUN callback (6).
17:05:42.066 Schaubild der ALSA-Verbindungen geändert.
17:05:42.223 ALSA-Verbindung geändert.
17:05:44.600 Schaubild der JACK-Verbindungen geändert.
firewire ERR: wait status &lt; 0! (= -1)
DRIVER NT: could not run driver cycle
17:05:45.719 Schaubild der JACK-Verbindungen geändert.
17:05:45.873 JACK-Verbindung geändert.
jack main caught signal 12
no message buffer overruns
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler
17:05:45.918 Benachrichtigung zum Herunterfahren.
17:05:45.920 JACK fährt herunter...
17:05:45.921 JACK wird gezwungen...
17:05:46.122 JACK wurde angehalten erfolgreich.
17:05:46.122 Post-shutdown script...
17:05:46.123 killall jackd
jackd: no process found
17:05:46.532 Post-shutdown script terminated mit Rückgabewert = 256.

```

my konfiguration:
realtime: off
frames/periode: 128
abtastrate:44100
perioden/puffer: 3
timeout:500
driver: firewire
schnittstelle: hw:0
audo: duplex

I hope you can help me ... i don't wanna use windows again - But i can't live without record something ...

Thanks,
justlifeable

ps: sorry,some words in jack are in german :p

---

### Post by kayosiii on 2010-06-28
check your permissions for /dev/raw1394 by issuing copying the following incantation into a shell...

ls -l /dev/raw1394

and post the results

---

### Post by justlifeable on 2010-06-28
When the firewire board ist connected he gives me this out:

```
crw-rw---- 1 root root 171, 0 2010-06-28 14:04 /dev/raw1394
```

Justlifeable

---

### Post by Pablo_F on 2010-06-28
Have you checked at the ffado site if your device is supported?

Anyway, I suggest you search / ask in the ffado users mailing list.

---

### Post by mrufino1 on 2010-06-28
I have the same board and it does work, and I use it on a t60 with a coolgear firewire card (TI chipset). It took a lot to get it going at one time but it works now. I'm a little hazy on all of the details but I can try to get you through it. I use AV linux now for music stuff and the board worked right away with that if I remember correctly. Maybe I don't remember correctly though, but if you look on av linux' forum there are some posts about it. If you search for phonic firewire linux or something like that on google  you may come across other discussions I had about it on different sites. I am not really doing much music production at the moment due to a return to school for my master's, but I'll see what I can remember. Don't give up though, it does work.
For the driver in the jack setup you need to choose firewire, and there is also a firewire driver I remember enabling in linux, but I can't remember the name off the top of my head. As soon as I do I will come back and edit the post. Sorry I can't be more immediate help but it will come back to me.

EDIT: ohci1394 is the driver I had to add to the permissions file. I remember that being what finally allowed my phonic mixer to talk to my IBM in linux (it had always worked fine in windows but I don't use win anymore for anything)

---

### Post by AutoStatic on 2010-06-29
Justlifeable,

Did you go through the steps here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?
And maybe you also need to disable CPU Frequency Scaling (Ondemand service) or set it to 'Performance' with the help of the CPU Frequency Scaling Monitor panel applet.
And what's the outcome of **cat /proc/interrupts** and **lspci** in a terminal?

---

### Post by mango42 on 2010-06-29
Should your 'schnittstelle' be set at hw:0 for input coming via a plugin firewire card? I'm also very hazy on this issue...

It's quite marvelous to see so many people junking windows for a life of commandline purgatory :lolflag:

Tenacity roolz, OK!

---

### Post by AutoStatic on 2010-06-29
> **mango42 said:**
> Should your 'schnittstelle' be set at hw:0 for input coming via a plugin firewire card? I'm also very hazy on this issue...hw:0 is your first Firewire card. If you only have one then leaving it to (default) should work too.

---

### Post by wergelt on 2010-06-29
I think the driver should be freebob not firewire for the Phonic devices.
Firewire is for the ffado supported devices

---

### Post by AutoStatic on 2010-06-29
ffado is the successor to the freebob project. The freebob driver entry in QjackCtl is only there for legacy reasons afaik:
```
/usr/bin/jackd -t2000 -dfreebob -r48000 -p256 -n3 -D
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1520256
no message buffer overruns
jackd: unknown driver 'freebob'
```

---

### Post by mango42 on 2010-06-30
> **AutoStatic said:**
> hw:0 is your first Firewire card. If you only have one then leaving it to (default) should work too.

Is there a surefire command to see how each piece of hardware relates to it's assigned 'hw:0' type value? Just being logical* (but clueless) I would expect hw:0.x always to refer to the first *internal* (sound)card/chip, hw:1.x the 1st discovered external (sound)card, etc...

But then, what do I know? Nada.

* reminds me of that old 'reverse deMorgan's Theorem':-

"Logic is mankind's most sophisticated tool yet devised to enable us to go utterly wrong with complete confidence." :) 

Pity BP didn't take that to heart a few decades back...

---

### Post by AutoStatic on 2010-06-30
> **mango42 said:**
> Is there a surefire command to see how each piece of hardware relates to it's assigned 'hw:0' type value? Just being logical* (but clueless) I would expect hw:0.x always to refer to the first *internal* (sound)card/chip, hw:1.x the 1st discovered external (sound)card, etc...You're not using Alsa when jackd runs with the firewire backend so hw:0 is the first card JACK recognises and that is almost certainly a Firewire device because the firewire/ffado driver can't address onboard, USB or PCI cards.

---

### Post by JC Cheloven on 2010-07-01
HI, I recently bought a Phonic Helix Board 18 firewire, which should be quite similar to yours, and it wors flawlessly for me. I made a little report a while ago:
[http://ubuntuforums.org/showthread.php?t=1505953](http://ubuntuforums.org/showthread.php?t=1505953)

Trying to guess what your problem may be, I've got the following suggestions/pointings for you:

- You need to use a real time kernel (not mild "multimedia kernel") to use firewire with the ffado driver, which is what applies anyway.

- The rt kernel for karmic (2.6.31-9-rt) was rock solid for me. I've read that it's not quite so for the rt kernel at lucid time (some problems in presence of nvidia cards, among others). In fact, afaik, UbStudio lucid ships a multimedia kernel by default. So I still do use UbStudio karmic for this reason. 

- Once you're sure you have a proper rt kernel, please check the rt stuff as indicated here [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
Edit.- regarding rt kernel, please see also [http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264) 

- Finally, ONCE EVERYTHING IS SETTLED, connect your fw device, start jack with firewire driver (not freebob), 48000 Hz, 3 periods/buffer, check the realtime box, and manually setup the correct number of ins/outs for your device. This way it works for me. 

Cheers
JC

---

### Post by mrufino1 on 2010-07-02
You don't need to use a real time kernel for the board to work, I don't and it works fine. I use AV Linux though, not ubuntustudio. I don't think I ever got the phonic board running in ubuntustudio.

 The plain AV linux Kernel works fine for me. I have no need to run at 1.5ms latency though, so I never really took it further. There is a realtime kernel for AV, but I only tried that once and there were many xruns. But the board is recognized. I'm sure if I kept at it, I could minimize those xruns, but as I said, no need for me- the mixer does zero latency monitoring anyway.

---

