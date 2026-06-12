---
title: "jack won't start - firewire, ffado, Echo Audiofire 4"
date: 2011-01-18
forum: Ubuntu Studio
---

### Post by danzvash on 2011-01-18
I have a fresh install of Maverick 64 bit running on a Thinkpad W510.
I plug in my brand new **Echo Audiofire 4** firewire audio interface and expect to be up and running in a second, due to the level of support it's supposed to have. But instead I get this:
```
$ jackd -d firewire -n 3 -p 2048
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
08585073206:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:17:24
[COLOR="Red"]**firewire ERR: FFADO: Error creating virtual device**[/COLOR]
Cannot attach audio driver
JackServer::Open() failed with -1
no message buffer overruns
Failed to start server
```


So, no Jack! Not quite the start with this interface I expected.

This is not a question of old stack / new stack. I don't have the old stack in play at all:
```
$ lsmod | grep 'firewire\|1394'
firewire_ohci          24615  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core

```


I have read
[https://help.ubuntu.com/community/FireWire]("https://help.ubuntu.com/community/FireWire")
[https://help.ubuntu.com/community/UbuntuStudioPreparation#FireWire%20%28IEEE%201394%29%20sound%20cards%20and%20cameras]("https://help.ubuntu.com/community/UbuntuStudioPreparation#FireWire%20%28IEEE%201394%29%20sound%20cards%20and%20cameras")
[https://ieee1394.wiki.kernel.org/index.php/Juju_Migration]("https://ieee1394.wiki.kernel.org/index.php/Juju_Migration")

... and I can't see that I'm missing anything that's been documented.

***So: does anybody know what the hell is going on with my setup??***

**More info:**

My user is in the audio group.
I have created a very liberal /etc/udev/rules.d/60-ffado.rules consisting of
```
SUBSYSTEM=="firewire", GROUP="audio"
```

Which results in these nodes being created:
```
$ ls -al /dev/fw*
crw-rw---- 1 root audio 251, 0 2011-01-18 22:45 /dev/fw0
crw-rw---- 1 root audio 251, 1 2011-01-18 22:47 /dev/fw1

```

Also:
```
$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x2500000000000000  0x00250000  0x00000AF4   Echo Digital Audio - AudioFire4
   1       0xf0def1ff2b98c6ff  0x00F0DEF1  0x00000000   Linux Firewire - 
no message buffer overruns

```

Output from ***ffado-test Discover*** is attached in a file.

Kernel version: 2.6.35-24-generic
libffado2:   2.0.1+svn1856-1ubuntu1 
jackd2: 1.9.5~dfsg19ubuntu1                              
jackd2-firewire: 1.9.5~dfsg-19ubuntu1

---

### Post by danzvash on 2011-01-31
Well the reason for this is that libffado 2.0.1+svn1856-1ubuntu1 doesn't work with the new (Juju) firewire stack.

So, you have to use ohci1394 from the old firewire stack.

Now jack is starting, but I'm getting horrendous x-run problems at the moment at a not-low latency of 17.4ms ( /usr/bin/jackd -P70 -t1000 -dfirewire -r44100 -p256 -n3). Whereas I can run Jack on the crappy onboard Intel audio at 11.6ms with no problem (chopping and changing tracks in Mixxx, recording stereo tracks in Ardour), no x-runs - I can't get any decent performance out my Audiofire4.

Furthermore, if I then switch back to the Intel onboard soundcard to run jack, I get x-runs at the previously stable setting.

And I see this from the terminal window where I ran ffado-mixer from:
04387011812: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -70652127369.014221! (correcting to nominal)
(repeated ~ 5 times per second)

Only a reboot fixes this.

Anybody actually using an Echo Audiofire4 out there with good results?

---

### Post by danzvash on 2011-01-31
Well the reason for this is that libffado 2.0.1+svn1856-1ubuntu1 doesn't work with the new (Juju) firewire stack.

So, you have to use ohci1394 from the old firewire stack.

Now jack is starting, but I'm getting horrendous x-run problems at the moment at a not-low latency of 17.4ms ( /usr/bin/jackd -P70 -t1000 -dfirewire -r44100 -p256 -n3). Whereas I can run Jack on the crappy onboard Intel audio at 11.6ms with no problem (chopping and changing tracks in Mixxx, recording stereo tracks in Ardour), no x-runs - I can't get any decent performance out my Audiofire4.

Furthermore, if I then switch back to the Intel onboard soundcard to run jack, I get x-runs at the previously stable setting.

And I see this from the terminal window where I ran ffado-mixer from:
04387011812: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -70652127369.014221! (correcting to nominal)
(repeated ~ 5 times per second)

Only a reboot fixes this.

Anybody actually using an Echo Audiofire4 out there with good results?

---

### Post by fedexnman on 2011-02-01
not on 10.10  , the  best performance was on ubuntustudio9.10 with rt kernel  , and 10.04 was okay  but i got xruns time to time and the ffado mixer  did'nt work in 10.04 , but worked in 9.10 .  hopefully  ubuntustudio 11.04  will be better for firewire and linux audio (fingers crossed).

---

### Post by fedexnman on 2011-02-01
the ubuntustudio site still has ubuntustudio 9.10 for a downloadable option  too.

---

