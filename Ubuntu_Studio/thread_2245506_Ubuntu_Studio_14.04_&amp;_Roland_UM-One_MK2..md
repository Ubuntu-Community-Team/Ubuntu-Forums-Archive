---
title: "Ubuntu Studio 14.04 &amp; Roland UM-One MK2."
date: 2014-09-24
forum: Ubuntu Studio
---

### Post by Hanjaya on 2014-09-24
Hi,

I have the latest Ubuntu Studio 14.04 updates & upgrades. I am trying to connect a synthesizer to Ardour3 using Roland UM-One MK2 midi interface. After physically connecting them, I saw there are activities on the Roland LED lights when I was pressing the synthesizer. However I did not get any midi signal in Ardour. I have tried changing the MIDI system inside Ardour to "Legacy ALSA raw", "Legacy ALSA sequencer", "JACK1", "JACK2" but still not getting any MIDI signal at all.

Please help.

Thanks.

hc.

---

### Post by Hanjaya on 2014-09-24
Anyone, please help. Btw, do I need to use jack audio connection kit?

Thx.

Hc.

---

### Post by jejeman on 2014-09-25
Of course you need to use JACK, Ardour requires it.
Plug in UM-one and give
```
amidi -l
```

---

### Post by Hanjaya on 2014-09-26
Hi,

Here is the message:

```
hanjaya@hanjaya-MXC061:~$ amidi -l
Dir Device    Name
IO  hw:1,0,0  UM-ONE MIDI 1
```

I open up **QjackCtl > Connect > MIDI** and there is nothing there, however on **ALSA** tab:

Readable Clients / Output Ports:
14: MIDI Through
20: UM-ONE

Writable Clients / Input Ports:
14: MIDI Through
20: UM-ONE

hc.

---

### Post by jejeman on 2014-09-26
Exactly. You need to use those ports from ALSA, because it is an ALSA device.
I guess Ardour uses JACK MIDI, so you need to bridge the ALSA MIDI and JACK MIDI by using ether a2jmidid or MIDI driver in JACK command.

---

### Post by Hanjaya on 2014-09-27
On Ubuntu Software Center showed that a2jmidid daemon already been installed. Then I did:

```
hanjaya@hanjaya-MXC061:~$ a2jmidid -e
JACK MIDI <-> ALSA sequencer MIDI bridge, version 8 (7383d268c4bfe85df9f10df6351677659211d1ca) built on Wed Dec 31 16:00:00 1969
Copyright 2006,2007 Dmitry S. Baikov
Copyright 2007,2008,2009,2011,2012 Nedko Arnaudov

Bridge starting...
Using JACK server 'default'
Hardware ports will be exported.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
ERROR: a2j_jack_client_create: Cannot create jack client
ERROR: a2j_start: a2j_new() failed.
hanjaya@hanjaya-MXC061:~$ 
```

Any idea?

Thanks.

hc.

---

### Post by jejeman on 2014-09-27
Is it not obvious?
> jack server is not running or cannot be startedFirst start JACK, then run a2jmidid.

---

### Post by Hanjaya on 2014-09-27
Hi jejeman,

Thanks for your help, I will try it later. Sorry and bare with me, all this is still new to me, I'm trying to grasp it:)

Hc.

---

