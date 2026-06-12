---
title: "Need Jack to run 88.2Khz 24 bit Audio"
date: 2009-12-09
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2009-12-09
Right now Jack seems to work fine at 48kHz but I need it to run at 88.2kHz, but when I set it to 88.2 I get this:

> 18:54:22.130 JACK is starting...
18:54:22.130 /usr/bin/jackd -R -dalsa -dhw:0 -r88200 -p256 -n2
18:54:22.135 JACK was started with PID=5320.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 88200
creating alsa driver ... hw:0|hw:0|256|2|88200|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 88200Hz, period = 256 frames (2.9 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
18:54:22.615 JACK was stopped successfully.
18:54:22.616 Post-shutdown script...
18:54:22.616 killall jackd
jackd: no process found
18:54:23.029 Post-shutdown script terminated with exit status=256.
18:54:24.213 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I've got an RME HDSP MADI

Thanks,

Ben

---

### Post by VertexPusher on 2009-12-10
It seems that your card does not support 88.2kHz sample rate. Use this command to find out:

```
speaker-test -l 1 -D hw:0 -f S32_LE -c 2 -r 88200
```

If your card or its driver don't support 88.2kHz, you can still run Jack at that rate, but you need to insert a format converter between Jack and the card driver. This is done by replacing "hw:0" with "plughw:0" in Jack's configuration panel.

---

### Post by pepsifx357 on 2009-12-10
I tried that code for 44.1 48 and 88.2

This card support up to 96kHz audio.

> ben@HMS_Audio:~$ speaker-test -l 1 -D hw:0 -f S32_LE -c 2 -r 44100

speaker-test 1.0.20

Playback device is hw:0
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Access type not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument

> ben@HMS_Audio:~$ speaker-test -l 1 -D hw:0 -f S32_LE -c 2 -r 48000

speaker-test 1.0.20

Playback device is hw:0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Access type not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument


> ben@HMS_Audio:~$ speaker-test -l 1 -D hw:0 -f S32_LE -c 2 -r 88200

speaker-test 1.0.20

Playback device is hw:0
Stream parameters are 88200Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Access type not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument

If I remove device 0 and replace it with default I get this:

> ben@HMS_Audio:~$ speaker-test -l 1 -D default -f S32_LE -c 2 -r 88200

speaker-test 1.0.20

Playback device is default
Stream parameters are 88200Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 88200Hz (requested 88200Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 13.367347


Although default must not be right, because I tested it with 192000 and got the same result, this card does not support the 192kHz sample rate.

EDIT:

I got it working, or so it seems.  I adjusted the clock from alsamixer.  I'm still trying to get the card to sync from external wordclock though.

---

### Post by VertexPusher on 2009-12-10
> **pepsifx357 said:**
> This card support up to 96kHz audio.
Yes, but that does not necessarily mean that it supports anything _between_ 48 and 96.

However, your test results show that the problem must be elsewhere. Maybe the card does not support the S32_LE sample format. Again, "plughw" would fix this because it can do both rate and format conversion, whenever necessary.

> If I remove device 0 and replace it with default I get this:

Although default must not be right, because I tested it with 192000 and got the same result, this card does not support the 192kHz sample rate.
The "default" PCM is similar to the "plughw" PCM. Here's a comparison (playback only):
[[IMG]http://img265.imageshack.us/img265/9883/alsa.png[/IMG]](http://img265.imageshack.us/i/alsa.png/)
"plug" is the sample rate/format converter.
"dmix" is the stream mixer.
"hw" is the hardware device.

dmix works with a fixed rate and format that is compatible with the hw device used as its slave. Each client application gets its own plug instance. As you can see, the only difference is that "default" allows sound card sharing while "plughw" is exclusive to one client at a time. Both perform rate/format conversion if required.

---

### Post by pepsifx357 on 2009-12-18
Would this explain why now I get channels coming out of the card that are mixed up?  Channel 1 feeds channel 5 ect.

---

