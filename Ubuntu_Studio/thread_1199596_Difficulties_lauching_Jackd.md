---
title: "Difficulties lauching Jackd"
date: 2009-06-29
forum: Ubuntu Studio
---

### Post by Ellipsis81 on 2009-06-29
Hi,

I'm new to the Ubuntu community and am enjoying the experience considerably, but I'm having difficulties running Jackd in Ubuntu Studio. I'm running Hardy Heron and would like to use my Tapco Link.Firewire interface but attempts with both Freebob and ffado's firewire driver have  been unsuccessful. The Jackd msg window reads-

[PHP]
17:34:13.428 Patchbay deactivated.
17:34:13.681 Statistics reset.
17:34:13.692 JACK is starting...
17:34:13.693 /usr/bin/jackd -v -R -P60 -dfirewire -r44100 -p128 -n3
17:34:13.816 ALSA connection graph change.
17:34:13.817 JACK was started with PID=10708.
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
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
new client: firewire_pcm, id = 1 type 1 @ 0x8076848 fd = -1
new buffer size 128
02239146899:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Nov 22 2008 23:12:02
17:34:13.896 ALSA connection change.
17:34:14.005 JACK was stopped successfully.
17:34:14.006 JACK has crashed.
17:34:15.908 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
[/PHP]


In fact, even if I try launching Jack without the interface (as ffado describes its support status as unknown), jack still crashes with the following msg- 



[PHP]18:26:43.493 Patchbay deactivated.
18:26:43.741 Statistics reset.
18:26:43.752 JACK is starting...
18:26:43.753 /usr/bin/jackd -v -R -P60 -dalsa -dhw:0 -r44100 -p128 -n3 -Xraw
18:26:44.090 ALSA connection graph change.
18:26:44.091 JACK was started with PID=12877.
18:26:44.095 ALSA connection change.
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
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
new client: alsa_pcm, id = 1 type 1 @ 0x8064f58 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the capture device "hw:0" is already in use. Please stop the application using 
18:26:44.218 JACK was stopped successfully.
it and run JACK again
cannot load driver module alsa
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
18:26:46.186 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/PHP]


I have followed many helpful threads and different jack setup configurations but I think I've stretched the limits of my limited linux knowledge. Please excuse my ignorance and correct me on any poor netiquette, and thanks in advance for any guidance you can offer!   

I@n

---

### Post by raboofje on 2009-06-29
> **Ellipsis81 said:**
> creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again

Not sure about the first one, but the second one is easy: some other application is using the device.

Try this:

```
lsof /dev/snd/*
```

---

### Post by Ellipsis81 on 2009-06-29
Cheers raboofje,

The result of lsof /dev/snd/*-


COMMAND     PID    USER   FD   TYPE DEVICE SIZE  NODE NAME
mixer_app 16716 pugwash   19u   CHR  116,0      13087 /dev/snd/controlC0


I killed the mixer_app and tried reloaded jack, to receive a similar hw:0 msg-

```
23:00:07.127 Patchbay deactivated.
23:00:07.233 Statistics reset.
23:00:07.252 JACK is starting...
23:00:07.252 /usr/bin/jackd -v -R -P60 -dalsa -dhw:0 -r44100 -p128 -n3 -Xraw
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
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
new client: alsa_pcm, id = 1 type 1 @ 0x8064f58 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
23:00:07.527 ALSA connection graph change.
23:00:07.528 JACK was started with PID=25372.
23:00:07.531 ALSA connection change.
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
23:00:07.819 JACK was stopped successfully.
23:00:09.628 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

But curiously, repeating the command lsof /dev/snd/* gave 

COMMAND     PID    USER   FD   TYPE DEVICE SIZE  NODE NAME
qjackctl. 25366 pugwash   13u   CHR  116,1      83469 /dev/snd/seq


Which seems closer to a solution right? any thoughts?

Thanks again,

I@n

---

### Post by ezio_rec on 2009-06-29
Do you have on board audio device enabled ?

---

### Post by Ellipsis81 on 2009-06-29
Thnx ezio_rec,

I presume so, system > default soundcard gives the option of Intel or pulseaudio and I get sound for all applications with either setting... except those which run on jackd. 

I've just switched from XP, using Ableton Live etc and am keen to try out Linux as a more stable alternative to music production. Ubuntu Studio looks great and I like the appeal of patching programs together, its just that all audio programs seem to require jackd, which requires me to learn more in order to get it started! 

Is there some sort of conflicting order in which ALSA or Pulseaudio access the soundcard, which causes the hw;0 problem and prevents Jackd from starting?

---

### Post by Grishka on 2009-06-29
closing all applications that use sound (internet browser included), before starting JACK, remedies this situation for me.

---

### Post by raboofje on 2009-06-29
> **Ellipsis81 said:**
> The result of lsof /dev/snd/*-

COMMAND     PID    USER   FD   TYPE DEVICE SIZE  NODE NAME
mixer_app 16716 pugwash   19u   CHR  116,0      13087 /dev/snd/controlC0

```
creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
23:00:07.527 ALSA connection graph change.
23:00:07.528 JACK was started with PID=25372.
23:00:07.531 ALSA connection change.
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
```

Hum. I can think of 2 reasons for this: 

1) you weren't allowed to see the process using /dev/snd/? - try with 'sudo'
2) the device was in use though the OSS compatibility layer - try ' sudo lsof /dev/dsp* ' also.

---

### Post by Ellipsis81 on 2009-06-30
No joy after disabling all other applications I'm afraid. and 'sudo lsof /dev/dsp*' command results in-

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/pugwash/.gvfs
      Output information may be incomplete.

I stumbled upon the command 'jackd -d alsa -P hw:0,0 -C hw:0,2'

which 'Runs jackd in full-duplex mode using the ALSA hw:0,0 device for playback and the hw:0,2 device for capture.' And lo and behold- 

```
no message buffer overruns
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0,0|hw:0,2|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
```

So finally jackd runs! albeit, with a string of Xruns. Following this, I can open jackd-based applications and get sound (with noticable crackling) but, as its in playback mode, I assume I can't record. 

Getting close, but still no cigar!

---

