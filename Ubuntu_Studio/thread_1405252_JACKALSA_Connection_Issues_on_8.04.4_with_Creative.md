---
title: "JACK/ALSA Connection Issues on 8.04.4 with Creative SB0350"
date: 2010-02-12
forum: Ubuntu Studio
---

### Post by bcschmerker on 2010-02-12
I had initially been unsuccessful in getting my Creative Laboratories SB0350 (ALSA:snd-emu10k1) to connect to JackAudio, but was able to get a consistent connection with reduced settings.  The following text was captured from StdOut in JACK Audio Connection kit during my first attempted Connect:
```
09:49:43.870 JACK is starting...
09:49:43.871 /usr/bin/jackd -v -p128 -t5000 -dalsa -r32000 -p256 -n16 -D -Chw:2,0 -Phw:2,3 -s -Xseq -H
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
09:49:43.927 JACK was started with PID=10035.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: alsa_pcm, id = 1 type 1 @ 0x8069928 fd = -1
apparent rate = 32000
creating alsa driver ... hw:2,3|hw:2,0|256|16|32000|0|0|hwmon|swmeter|soft-mode|32bit
control device hw:2
configuring for 32000Hz, period = 256 frames (8.0 ms), buffer = 16 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: got smaller periods 2 than 16 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
starting server engine shutdown
server thread back from poll
freeing shared port 
09:49:43.962 JACK was stopped successfully.
segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'

```With /usr/bin/jackd -v -p128 -t5000 -dalsa -r32000 -p256 -n2 -D -Chw:2,0 -Phw:2,3 -s -Xseq -H, I had an apparently successful startup.  What issues should be addressed to improve capacity of the connection?

---

### Post by AutoStatic on 2010-02-12
Hello bcschmerker. Why 32000 Hz as Samplerate? I would try 44100 Hz or 48000 Hz. Or is 32000 the 'native' samplerate of your card? And does your Soundblaster have the hardware ID 2? Could you post the outcome of **aplay -l**? And why are you setting different input and output devices?

---

### Post by bcschmerker on 2010-02-14
> **AutoStatic said:**
> Hello bcschmerker. Why 32000 Hz as Samplerate? I would try 44100 Hz or 48000 Hz. Or is 32000 the 'native' samplerate of your card? And does your Soundblaster have the hardware ID 2? Could you post the outcome of **aplay -l**? And why are you setting different input and output devices?I found confirmation of the 48 kHz rate only after the periods-per-buffer issue was fixed; I worked down from 48 kHz when I had the problem connecting to JackD.  Periods-per-buffer proved the first issue for JACK.

The list of Devices from aplay -l is pretty comprehensive for the SB0350, with 41 Subdevices among five Devices:
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by AutoStatic on 2010-02-14
Thanks! Now I understand your settings better.
Did you suspend or kill PulseAudio before starting JACK?
Suspending: **pasuspender -- your-jackd-command**
Killing: create a* ~/.pulse/client.conf* file with the line *autospawn = no* and kill PulseAudio the with **pulseaudio -k**

This should prevent JACK from not starting up because it can't load the alsa driver module. It's been a while though since I've touched any 8.04 installation.

---

### Post by bcschmerker on 2010-02-15
> **AutoStatic said:**
> Thanks! Now I understand your settings better.
Did you suspend or kill PulseAudio before starting JACK?
Suspending: **pasuspender -- your-jackd-command**
Killing: create a* ~/.pulse/client.conf* file with the line *autospawn = no* and kill PulseAudio the with **pulseaudio -k**

This should prevent JACK from not starting up because it can't load the alsa driver module. It's been a while though since I've touched any 8.04 installation.I presume that:```
pulseaudio -k
```is used in an Execute-upon-Startup script for the JACK Audio Connection Kit?  This line defaults to:```
artsshell -q terminate
```in my particular case, as does Execute-after-Shutdown to:```
killall jackd
```I can also set GNOME-Sound-Properties to default all sources and sinks to ALSA to expedite the switchover from PulseAudio to JACK.

---

### Post by AutoStatic on 2010-02-15
Like I said, I haven't touched a 8.04 in a long time. I can't recall how QjackCtl was implemented, on Jaunty and Karmic */usr/bin/qjackctl* is a wrapper script that suspends PulseAudio and starts qjackctl.bin, don't know if that goes for 8.04 too. But a **less /usr/bin/qjackctl** should make that clear. If it's a binary then you'll have to suspend PulseAudio before starting JACK.

---

### Post by bcschmerker on 2010-02-16
From a check of GNOME System Monitor, PASuspender is working as advertised with QJackCtl running.  Typically, JACKd runs with a 48 kHz sample rate and a 256-frame buffer size.  Maximum scheduling delay is 62.469 ms.  No Xruns; however, Messages show a bunch of late driver wakeups.  At this time, my installation cannot run an RT kernel due to compatibility issues with AMD processors such my Everex' Athlon X2 5600+.

What would contribute to late driver wakeups in an AMD installation?

---

### Post by AutoStatic on 2010-02-16
What are your current JACK settings? I think your Periods/Buffer setting is too high, it is higher than 10 now I guess. You should try setting it to 2.

---

### Post by bcschmerker on 2010-02-17
> **AutoStatic said:**
> What are your current JACK settings? I think your Periods/Buffer setting is too high, it is higher than 10 now I guess. You should try setting it to 2.I stopped it long enough to get the Messages from JackD startup, which read as follows:
```
20:35:27.322 /usr/bin/jackd -v -p128 -t5000 -dalsa -r48000 -p256 -n2 -D -Chw:2,0 -Phw:2,3 -s -Xseq -H
20:35:27.326 JACK was started with PID=8282.
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
20:35:27.525 ALSA active patchbay scan...
20:35:27.530 ALSA connection change.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: alsa_pcm, id = 1 type 1 @ 0x8069928 fd = -1
apparent rate = 48000
creating alsa driver ... hw:2,3|hw:2,0|256|2|48000|0|0|hwmon|swmeter|soft-mode|32bit
control device hw:2
configuring for 48000Hz, period = 256 frames (5.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
new buffer size 256
20:35:27.652 ALSA connection graph change.
registered port system:capture_1, offset = 1024
registered port system:capture_2, offset = 2048
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
registered port system:playback_5, offset = 0
registered port system:playback_6, offset = 0
registered port system:playback_7, offset = 0
registered port system:playback_8, offset = 0
registered port system:playback_9, offset = 0
registered port system:playback_10, offset = 0
registered port system:playback_11, offset = 0
registered port system:playback_12, offset = 0
registered port system:playback_13, offset = 0
registered port system:playback_14, offset = 0
registered port system:playback_15, offset = 0
registered port system:playback_16, offset = 0
20:35:27.732 ALSA active patchbay scan...
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
20:35:27.767 ALSA connection graph change.
registered port alsa_pcm:Midi-Through/midi_capture_1, offset = 1024
registered port alsa_pcm:Midi-Through/midi_playback_1, offset = 0
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_capture_1, offset = 2048
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_playback_1, offset = 0
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_capture_33, offset = 3072
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_playback_33, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_1, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_2, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_3, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_4, offset = 0
8282 waiting for signals
20:35:27.940 ALSA active patchbay scan...
load = 0.2438 max usecs: 26.000, spare = 5307.000
late driver wakeup: nframes to process = 512.
20:35:29.558 Server configuration saved to "/home/bcschmerker/.jackdrc".
20:35:29.561 Statistics reset.
20:35:29.601 Client activated.
20:35:29.610 JACK connection change.
20:35:29.620 JACK connection graph change.
...
```QJACKCtl previously alerted me to the Periods/Buffer issue; it runs consistently at 2 periods/buffer.

---

### Post by AutoStatic on 2010-02-18
Nice! So it's working well now?

---

### Post by bcschmerker on 2010-02-19
JACKd runs well enough, notwithstanding the occasional failure to terminate PulseAudio, as shown in the accompanying StdOut excerpt.  The main issue from my perspective is late driver wakeup, with some drivers taking up to 1024 nframes to respond:
```
22:32:24.862 Startup script...
22:32:24.863 pulseaudio -k
E: main.c: Failed to kill daemon.
22:32:25.282 Startup script terminated with exit status=256.
22:32:25.283 JACK is starting...
22:32:25.284 /usr/bin/jackd -v -p128 -t5000 -dalsa -r48000 -p512 -n2 -D -Chw:2 -Phw:2 -s -Xseq -H
22:32:25.289 JACK was started with PID=11480.
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: alsa_pcm, id = 1 type 1 @ 0x8069928 fd = -1
apparent rate = 48000
creating alsa driver ... hw:2|hw:2|512|2|48000|0|0|hwmon|swmeter|soft-mode|32bit
control device hw:2
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
new buffer size 512
registered port system:capture_1, offset = 2048
registered port system:capture_2, offset = 4096
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
registered port alsa_pcm:Midi-Through/midi_capture_1, offset = 2048
registered port alsa_pcm:Midi-Through/midi_playback_1, offset = 0
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_capture_1, offset = 4096
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_playback_1, offset = 0
22:32:25.343 ALSA connection graph change.
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_capture_33, offset = 6144
registered port alsa_pcm:Audigy-2-ZS--SB0350-/midi_playback_33, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_1, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_2, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_3, offset = 0
registered port alsa_pcm:Emu10k1-WaveTable/midi_playback_4, offset = 0
11480 waiting for signals
load = 0.4688 max usecs: 100.000, spare = 10566.000
22:32:27.312 Server configuration saved to "/home/bcschmerker/.jackdrc".
22:32:27.315 Statistics reset.
22:32:27.321 Client activated.
22:32:27.326 JACK connection change.
22:32:27.341 JACK connection graph change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb7d58000 fd = 18
start poll on 4 fd's
server thread back from poll
new client qjackctl using 19 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client event poll on 19 for qjackctl starts at 3760414150
back from client event poll after 120 usecs
client qjackctl: wait_fd=15, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
load = 0.9469 max usecs: 152.000, spare = 10514.000
load = 0.8344 max usecs: 77.000, spare = 10589.000
load = 4.3456 max usecs: 838.000, spare = 9828.000
load = 2.8666 max usecs: 148.000, spare = 10518.000
load = 2.0146 max usecs: 124.000, spare = 10542.000
load = 2.1746 max usecs: 249.000, spare = 10417.000
load = 1.8139 max usecs: 155.000, spare = 10511.000
late driver wakeup: nframes to process = 1024.
load = 1.5492 max usecs: 137.000, spare = 10529.000
late driver wakeup: nframes to process = 1024.
load = 1.5528 max usecs: 166.000, spare = 10500.000
load = 1.8546 max usecs: 230.000, spare = 10436.000
load = 2.6008 max usecs: 357.000, spare = 10309.000
load = 2.2895 max usecs: 211.000, spare = 10455.000
22:32:39.939 Client deactivated.
22:32:39.977 JACK is stopping...
server thread back from poll
+++ deactivate qjackctl
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll
marking client qjackctl with SOCKET error state = Running errors = 0
trying to lock graph to remove 1 problems
we have problem clients (problems = 1
++ Removing failed clients ...
client alsa_pcm error status 0
client qjackctl error status 10000000
removing failed client qjackctl state = Running errors = 10000000
removing client "qjackctl"
removing client "qjackctl" from the processing chain
+++ deactivate qjackctl
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
-- Removing failed clients ...
after removing clients, problems = 0
start poll on 3 fd's
jack main caught signal 15
starting server engine shutdown
stopping driver
server thread back from poll
unloading driver
22:32:40.046 ALSA connection graph change.
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 11365.000 usecs
freeing engine shared memory
max usecs: 838.000, engine deleted
WARNING: 2 message buffer overruns!
cleaning up shared memory
cleaning up files
22:32:40.245 ALSA connection graph change.
unregistering server `default'
22:32:40.254 JACK was stopped successfully.
```

---

