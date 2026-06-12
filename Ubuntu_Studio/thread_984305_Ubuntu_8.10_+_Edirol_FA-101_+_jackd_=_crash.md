---
title: "Ubuntu 8.10 + Edirol FA-101 + jackd = crash"
date: 2008-11-16
forum: Ubuntu Studio
---

### Post by Acksys on 2008-11-16
Hello all,

I am trying to get jack to work with my Edirol FA-101. Everything seems to be configured correctly, but jackd crashes with no error message a few seconds after starting. Here is my jackd output, followed by package version information (up to date as of this writing):

```
fritz@xubuntu-studio:/boot/grub$ sudo /usr/bin/jackd --nozombies -t 2000 -v -R -dfreebob
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
new client: freebob_pcm, id = 1 type 1 @ 0x8f3ef58 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 1024
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.11
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 48000
LibFreeBoB MSG:   Period Size              : 1024
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
showDevice: not implemented
FreeBoB MSG: Register MIDI IN port dev1c_MidiPort_1
FreeBoB MSG: Register MIDI OUT port dev1p_MidiPort_1
FreeBoB MSG: Streaming thread running with Realtime scheduling, priority 14
FreeBoB MSG: Registering audio capture port C0_dev1c_MicIn1 left
registered port system:capture_1, offset = 4096
FreeBoB MSG: Registering audio capture port C1_dev1c_MicIn1 right
registered port system:capture_2, offset = 8192
FreeBoB MSG: Registering audio capture port C2_dev1c_LineIn 3+4 left
registered port system:capture_3, offset = 12288
FreeBoB MSG: Registering audio capture port C3_dev1c_LineIn 3+4 right
registered port system:capture_4, offset = 16384
FreeBoB MSG: Registering audio capture port C4_dev1c_LineIn 5+6 left
registered port system:capture_5, offset = 20480
FreeBoB MSG: Registering audio capture port C5_dev1c_LineIn 5+6 right
registered port system:capture_6, offset = 24576
FreeBoB MSG: Registering audio capture port C6_dev1c_LineIn 7+8 left
registered port system:capture_7, offset = 28672
FreeBoB MSG: Registering audio capture port C7_dev1c_LineIn 7+8 right
registered port system:capture_8, offset = 32768
FreeBoB MSG: Registering audio capture port C8_dev1c_SpdifIn left
registered port system:capture_9, offset = 36864
FreeBoB MSG: Registering audio capture port C9_dev1c_SpdifIn right
registered port system:capture_10, offset = 40960
FreeBoB MSG: Don't register capture port for dev1c_MidiPort_1
FreeBoB MSG: Registering playback audio port P0_dev1p_LineOut 1+2 left
registered port system:playback_1, offset = 0
FreeBoB MSG: Registering playback audio port P1_dev1p_LineOut 1+2 right
registered port system:playback_2, offset = 0
FreeBoB MSG: Registering playback audio port P2_dev1p_LineOut 3+4 left
registered port system:playback_3, offset = 0
FreeBoB MSG: Registering playback audio port P3_dev1p_LineOut 3+4 right
registered port system:playback_4, offset = 0
FreeBoB MSG: Registering playback audio port P4_dev1p_LineOut 5+6 left
registered port system:playback_5, offset = 0
FreeBoB MSG: Registering playback audio port P5_dev1p_LineOut 5+6 right
registered port system:playback_6, offset = 0
FreeBoB MSG: Registering playback audio port P6_dev1p_LineOut 7+8 left
registered port system:playback_7, offset = 0
FreeBoB MSG: Registering playback audio port P7_dev1p_LineOut 7+8 right
registered port system:playback_8, offset = 0
FreeBoB MSG: Registering playback audio port P8_dev1p_SpdifOut left
registered port system:playback_9, offset = 0
FreeBoB MSG: Registering playback audio port P9_dev1p_SpdifOut right
registered port system:playback_10, offset = 0
FreeBoB MSG: Don't register playback port dev1p_MidiPort_1
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
FreeBoB MSG: MIDI threads running with Realtime scheduling, priority 13
FreeBoB MSG: MIDI queue thread started
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
5938 waiting for signals
```

```
jackd: 0.109.2-3ubuntu1
libfreebob0: 1.0.11-0ubuntu1
kernel 2.6.27-3-rt

```

```
$ lspci
FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
```

I have tried changing various options for jackd with no success. There is a "whining" noise for the few seconds jackd runs, which stops when it exits.

If I start jack through qjackctl instead, it starts jack and connects, but then freezes.

Looks like it's "almost" working, so I'd greatly appreciate any suggestions!

---

### Post by Acksys on 2008-11-16
UPDATE: I tried this in 64 Studio 2.0 (i386) as well and experienced the exact same behavior.

```
libfreebob0: 1.0.3+svn443~bpo.1
jackd: 0.103.0
```

I also tried 64 Studio on a different machine (laptop) and was able to to get jackd running after passing **acpi=off noapic nolapic** to the kernel. Not sure which of those parameters is the magic bullet, or if all are required. Regardless, they did not solve the problem on the original machine, which is the one I want to use.

Looks like it's a problem specific to the hardware configuration of my machine. Any ideas?

---

### Post by kayosiii on 2008-11-17
for me libfreebob was the problem. bug report  here [https://bugs.launchpad.net/ubuntu/+source/libfreebob/+bug/293120](https://bugs.launchpad.net/ubuntu/+source/libfreebob/+bug/293120)
after trying older kernels to try and fix the problem- I got around it by compiling the latest libffado beta and  doing evil things to my system to get it  to work.  Hardy worked just fine for me though.

---

### Post by sebos69 on 2008-11-18
yep, at the moment, 8.10 seems to suck. I have the same edirol fa-101, and I went back to 8.04 where I can use <3ms latency rock stable.

---

### Post by Acksys on 2008-11-18
Thanks for the input. I think I will try 8.04 and see if it solves my issues.

---

### Post by darkdaysdawn on 2009-02-10
I have...in fact...I went and bought an FA-101 specifically because it has the number of ins/outs I need and it "supposedly" works with UbuntuStudio.  

However, I have had no luck either.  My specs and configs seem to match everything I've read here and elsewhere.

Did you go back to 8.04?  Did it work?

I once got JACK to start, but then Ardour wouldn't play or record.  Now I can't even get JACK to start.


notes:
-------
Linux Litch 2.6.27-3-rt #1 PREEMPT RT Mon Oct 27 03:02:33 UTC 2008 x86_64 GNU/Linux

05:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)

---

### Post by darkdaysdawn on 2009-02-18
Update:  I have Jack and Ardour running my FA-101 in UbuntuStudio 8.10 with both the generic kernel, and the older rt kernel.  However, both kernels produce an unacceptable number of XRUNS (the rt is slightly better, but it has its own issues and will only see 1 core of my 4 core CPU).

The issue that was keeping my FA-101 from working at all was the firewire interface in my PC.  I replaced it for one with a TI chipset, as recommended by Roland.  That definitely improved things.

Next I will try to confirm that there are no IRQ conflicts and give 8.04 another try.  However, I'm having a lot of trouble getting 8.04 to work with my NVIDIA 9800 GX.  Without the video drivers, I can't get 1900x1200 on my 26" screen, which kind of defeats the purpose of having all that real estate.

---

