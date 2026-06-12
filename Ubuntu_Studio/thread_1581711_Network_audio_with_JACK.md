---
title: "Network audio with JACK"
date: 2010-09-25
forum: Ubuntu Studio
---

### Post by mada3k on 2010-09-25
Hi!

I post this question here in the studio forums bacause i guess heres probably the best knowledge of this.

My plan is to send audio from two machines to a headless server thats connected to my monitors (speakers) I'm using one PC with Ubuntu and I also have an MacBook with OSX that i would like to involve (that i've installed JackOSX on).

I've used the howto in this Wiki
[http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack](http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack)

I run jackd with netone on the clients
```
mada-mbp:~ mada$ sudo jackd -d netone
Password:
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
NetOne driver started
AutoConfig Override !!!
AutoConfig Override: capture_channels_audio = 2
AutoConfig Override: capture_channels_midi = 1
AutoConfig Override: playback_channels_audio = 2
AutoConfig Override: playback_channels_midi = 1
MTU is set to 1400 bytes

```

I run the netsource at my sound-server with success
```
root@server:~# jack_netsource -H 192.168.3.20
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Not Connected
Connected :-)
netjack: at frame 000890 -> total netxruns 1  (0%) queue time= 85334

```

Seems like a successfull connection to me. On the MacBook the built-in speakers go mute and the selected audio-out is "JackRouter". UDP data is flowing thru the network, but the output from the sound-server is completly silent.

Do I need some jack_connect'ing or something? But I can't find any decent information.

---

### Post by mada3k on 2010-09-25
Nevermind. NetJack on JackOSX is broken.

Using JackTrip instead, works nice!

---

### Post by IndieRockSteve on 2011-10-01
I'm trying to get this to work but jack_netsource says Not Connected and I can't get audio to work.

how did you get this to work with jacktrip?

---

### Post by sgx on 2011-10-01
Here is someone with a how-2 example:

[http://adamwesterberg.se/netaudio/](http://adamwesterberg.se/netaudio/)

Here are some docs/pics:

[https://ccrma.stanford.edu/groups/soundwire/software/jacktrip/](https://ccrma.stanford.edu/groups/soundwire/software/jacktrip/)

this may offer a clue:

[http://www.mail-archive.com/sursound@music.vt.edu/msg01240.html](http://www.mail-archive.com/sursound@music.vt.edu/msg01240.html)

It may help to keep steady audio input, while you search for the magic
connection ;)

Cheers

---

