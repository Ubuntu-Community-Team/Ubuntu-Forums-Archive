---
title: "JACK doesn't send sound to soundcard"
date: 2009-01-05
forum: Ubuntu Studio
---

### Post by markusii on 2009-01-05
Hi all, I just installed Ubuntu 8.04 and then used the ubuntustudio-audio metapackage to get Ubuntu Studio for my audio work.
My situation is that I can get JACK to start up fine in playback only mode, with 0 xruns, and no errors in the messages window, then I can start up JACK-using programs that successfully connect and run fine, audio level meters and all, but no sound comes through my card. Duplex works sometimes, other times it drowns in xruns. Pulseaudio is still installed, and I tried using these directions [here]("http://ubuntuforums.org/showthread.php?t=843012") under "PulseAudio through JACK" to get sinks but when one starts, the other dies. If I kill PA, then start JACK, then start PA, JACK starts sucking up xruns - if I login with PA, then start JACK, PA dies. Aside from that, JACK runs properly.
I was even able to mix down a project in Ardour, and then close JACK Control and listen to it (with PA I presume), but I can't listen to it in Ardour through JACK.

Here is some information you might find useful:
uname -a
```
Linux mark-desktop 2.6.24-22-rt #1 SMP PREEMPT RT Mon Nov 24 20:47:19 UTC 2008 i686 GNU/Linux
```

from /etc/security/limits.conf
```
@audio           -       rtprio          99
@audio           -       nice            -19
@audio           -       memlock         925880
@pulse-rt           -       rtprio          99
@pulse-rt           -       nice            -19

```

from /etc/group
```
audio:x:28:mark,root
pulse-rt:x:29:mark
```

from lspci -v
```
00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at ec00 [size=32]

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

my jackd starting command in JACK Control
```
 /usr/bin/jackd -R -t5000 -dalsa -dhw:0 -r48000 -p512 -n2 -P
```
with the script in the "Execute script after startup" box of course.

dmesg complains about segfaults referencing whatever JACK-using program I run, but never JACK itself. /var/log/messages says it can't use the pulseaudio-jack sink because "operation not permitted."

HELP!

---

### Post by jorgose on 2009-01-05
maybe you have the same problem as me, did you try to run it as root. If it works the connecting applications must also be started as root...

---

### Post by markusii on 2009-01-05
Well sure if I run pulseaudio as root it doesn't die, but still no sinks, and that's still not my main issue. What I really care about is getting JACK to pass sound through speakers at all.

---

### Post by jorgose on 2009-01-06
if jack runs as root, it can only connect **clients that were also startet as root**. this isn't a solution but at least you get some sounds.

---

### Post by ussndmac on 2009-01-06
Every time I try to load the jack modules in Pulse I get the error:

Module init failed

This happens for both the sink and source.

I have received no replies to my queries about these modules and what conditions have to exist to have them load properly. In the Pulse irc channel.

---

### Post by markusii on 2009-01-06
Ok, if I run qjackctl and all clients with sudo, then it all works perfectly, but only if pulseaudio has been killed.
So am I missing an account privilege here? Maybe I can use a workaround and use some kind of command for the menu items that would use sudo and automagically put in my password? I really don't like having a terminal open for every audio app I'm using...

---

### Post by markusii on 2009-02-16
Well, editing the menu to use gksudo lets me use the GUI menu to open my software, but I'm still wondering if anyone knows what permissions my main user account seems to be missing to let JACK apps use the soundcard.
Ideas? Suggestions? Any help is greatly appreciated.

---

