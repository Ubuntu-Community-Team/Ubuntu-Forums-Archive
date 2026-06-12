---
title: "Can't keep JACK running."
date: 2009-04-11
forum: Ubuntu Studio
---

### Post by m.lp.ql.m on 2009-04-11
I'm trying to get Ubuntu Studio up and running on my Dell Latitude D620 laptop. I realize this is probably not the best machine for the job, but it'll have to do for now, and, likewise, I'm not udderly concerned with studio-quality performance. Just getting the thing up and running for now would be nice!  :)

Vitals:
Installed all the ubuntustudio packages from the repositories from my working Kubuntu 8.10 installation
realtime kernel 2.6.24-23
2G RAM

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
 Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (r
ev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (r
ev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (r
ev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                                                                                                          er #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                                                                                                          er #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                                                                                                          er #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                                                                                                          er #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Control                                                                                                                          ler (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (re                                                                                                                          v 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Con                                                                                                                          troller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeFo                                                                                                                          rce Go 7300] (rev a1)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethe                                                                                                                          rnet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Conne                                                                                                                          ction (rev 02)

I've done most of the things listed here [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") and here [https://help.ubuntu.com/community/HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration")
at least the ones up to getting JACK installed, and configured. (Which is tough when qjackctl locks up every time!)

My first problem: starting JACK and keeping it running. When I use qjackctl, qjackctl locks up after 5 seconds or so. This is all I can capture from the JACK messages window: 
[IMG]https://bspace.berkeley.edu/access/content/user/319511/jackmessages.png[/IMG]

I've tried the advice listed here [http://ubuntuforums.org/showthread.php?t=850952&highlight=ich7]("http://ubuntuforums.org/showthread.php?t=850952&highlight=ich7") without any luck. jackd from the terminal returns :
> mark@m:/etc$ jackd -R -dalsa -dhw:0 -p1024 -n3
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 3 periods for playback
jackd watchdog: timeout - killing jackd
Aborted


Any other ideas?

---

### Post by thorgal on 2009-04-11
I suggest you update jackd. 0.109.x is not to be used according to its author. The 0.116.x serie is way better. Your last setting (n=3, p=1024) is fine (I saw you tried my advice to some other user). I would decrease the priority of the jackd RT thread down to 70 (you're at the moment at 89). 

I have a Dell Latitude D800, not as recent as yours, but similar. The latest jackd (in fact the development version) + latest kernel (2.6.29 + RT patch) are transforming this machine into a useful piece of h/w in my studio! who would have guessed ? :lol:

So if you are comfortable compiling kernel and apps, I would not hesitate. If not, I would wait a bit until all these goodies become officially packaged. I think 64studio 3.0 will be based on kernel 2.6.29. I don't know much about ubuntu studio. Depends on Jaunty I guess ?

---

### Post by neu2buntu on 2009-04-11
try >setup>timeout(msec) and raise it to 5000 to see if it makes any difference

---

### Post by m.lp.ql.m on 2009-04-12
Thanks for the quick responces! 

Raising timeout to 5000 made no difference. I compiled and installed JACK 0.116.2 with not much more difference.

> 
mark@m:/etc$ jackd -R -dalsa -dhw:0 -p1024 -n3
jackd 0.116.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
jackd watchdog: timeout - killing jackd
Aborted


Here, still, the timeout figure in qjackctl makes no diff.

I'm not up for compiling the kernel, maybe if I had less homework at the moment. :)

Any other ideas?

---

### Post by neu2buntu on 2009-04-12
this was happening to me a week or so ago after i was messing with my settings.... open qjackctl and try changing "midi driver" to raw from seq. i think this may have been part of my problem,cant remember

---

