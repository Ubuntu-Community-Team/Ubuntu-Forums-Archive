---
title: "Edirol FA-66 and jack"
date: 2008-08-05
forum: Ubuntu Studio
---

### Post by Miesco on 2008-08-05
I am trying to get my FA-66 to work.  Is it suppost to show up as a sound card?  I only get this from cat /proc/asound/cards:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 19


Here's what happends why I try to run jack with freebob:
20:47:12.571 JACK is starting...
20:47:12.571 /usr/bin/jackd -R -P60 -p128 -dfreebob -dhw:0 -r44100 -p128 -n3 -D
20:47:12.583 JACK was started with PID=6580.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
Freebob using Firewire port 0, node -1
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
20:47:13.461 ALSA connection graph change.
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 1.
LibFreeBoB ERR: Could not do CMP for connection 0
FreeBoB ERR: Could not start streaming threads
DRIVER NT: could not start driver
cannot start driver
20:47:13.585 ALSA connection change.
20:47:33.463 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
jackd watchdog: timeout - killing jackd
could not attach as JACK client (server has exited)
20:47:33.586 ALSA connection graph change.
20:47:33.632 JACK was stopped successfully.
20:47:33.632 Post-shutdown script...
20:47:33.632 killall jackd
20:47:33.632 JACK has crashed.
jackd: no process killed
20:47:34.047 Post-shutdown script terminat


It sometimes works, but only shows up as one port in jack, midiport or something, there is like 6 outs and 6 ins that should show up.  Any help would be appreciated, i've been looking through forums and asking on IRC for hours.

---

### Post by Miesco on 2008-08-06
I can get past that, I got it working, sort of.  It only loads one port: 
0:dev1c_midiport_1, if you look at the log it says it registers all 6 or whatever...  How come its only loading one port?

   1.
      11:55:02.087 Startup script...
   2.
      11:55:02.087 artsshell -q terminate
   3.
      11:55:02.506 Startup script terminated with exit status=256.
   4.
      11:55:02.506 JACK is starting...
   5.
      11:55:02.507 /usr/bin/jackd -v -R -P60 -p128 -dfreebob -r48000 -p1024 -n2 -D
   6.
      getting driver descriptor from /usr/lib/jack/jack_alsa.so
   7.
      getting driver descriptor from /usr/lib/jack/jack_freebob.so
   8.
      getting driver descriptor from /usr/lib/jack/jack_oss.so
   9.
      getting driver descriptor from /usr/lib/jack/jack_dummy.so
  10.
      jackd 0.109.2
  11.
      Copyright 2001-2005 Paul Davis and others.
  12.
      jackd comes with ABSOLUTELY NO WARRANTY
  13.
      This is free software, and you are welcome to redistribute it
  14.
      under certain conditions; see the file COPYING for details
  15.
      JACK compiled with System V SHM support.
  16.
      server `default' registered
  17.
      cannot remove `/dev/shm/jack-1000' (Permission denied)
  18.
      cannot lock down memory for jackd (Cannot allocate memory)
  19.
      registered builtin port type 32 bit float mono audio
  20.
      registered builtin port type 8 bit raw midi
  21.
      clock source = system clock via clock_gettime
  22.
      loading driver ..
  23.
      new client: freebob_pcm, id = 1 type 1 @ 0x806fac0 fd = -1
  24.
      Freebob using Firewire port 0, node -1
  25.
      new buffer size 1024
  26.
      JACK: unable to mlock() port buffers: Cannot allocate memory
  27.
      11:55:02.551 JACK was started with PID=9058.
  28.
      JACK: unable to mlock() port buffers: Cannot allocate memory
  29.
      LibFreeBoB MSG: FreeBoB Streaming Device Init
  30.
      LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.7
  31.
      LibFreeBoB MSG:  Device information:
  32.
      LibFreeBoB MSG:  Device options:
  33.
      LibFreeBoB MSG:   Port                     : 0
  34.
      LibFreeBoB MSG:   Device Node Id           : -1
  35.
      LibFreeBoB MSG:   Samplerate               : 48000
  36.
      LibFreeBoB MSG:   Period Size              : 1024
  37.
      LibFreeBoB MSG:   Nb Buffers               : 2
  38.
      LibFreeBoB MSG:   Directions               : 0
  39.
      showDevice: not implemented
  40.
      11:55:03.191 ALSA connection graph change.
  41.
      FreeBoB MSG: Register MIDI IN port dev1c_MidiPort_1
  42.
      FreeBoB MSG: Register MIDI OUT port dev1p_MidiPort_1
  43.
      FreeBoB MSG: Streaming thread running with Realtime scheduling, priority 64
  44.
      FreeBoB MSG: Registering audio capture port C0_dev1c_MicIn1 left
  45.
      FreeBoB MSG: Registering audio capture port C1_dev1c_MicIn1 right
  46.
      FreeBoB MSG: Registering audio capture port C2_dev1c_LineIn 3+4 left
  47.
      FreeBoB MSG: Registering audio capture port C3_dev1c_LineIn 3+4 right
  48.
      FreeBoB MSG: Registering audio capture port C4_dev1c_SpdifIn left
  49.
      FreeBoB MSG: Registering audio capture port C5_dev1c_SpdifIn right
  50.
      FreeBoB MSG: Don't register capture port for dev1c_MidiPort_1
  51.
      FreeBoB MSG: Registering playback audio port P0_dev1p_LineOut 1+2 left
  52.
      FreeBoB MSG: Registering playback audio port P1_dev1p_LineOut 1+2 right
  53.
      FreeBoB MSG: Registering playback audio port P2_dev1p_LineOut 3+4 left
  54.
      FreeBoB MSG: Registering playback audio port P3_dev1p_LineOut 3+4 right
  55.
      FreeBoB MSG: Registering playback audio port P4_dev1p_SpdifOut left
  56.
      FreeBoB MSG: Registering playback audio port P5_dev1p_SpdifOut right
  57.
      FreeBoB MSG: Don't register playback port dev1p_MidiPort_1
  58.
      registered port system:capture_1, offset = 4096
  59.
      registered port system:capture_2, offset = 8192
  60.
      registered port system:capture_3, offset = 12288
  61.
      registered port system:capture_4, offset = 16384
  62.
      registered port system:capture_5, offset = 20480
  63.
      registered port system:capture_6, offset = 24576
  64.
      registered port system:playback_1, offset = 0
  65.
      registered port system:playback_2, offset = 0
  66.
      registered port system:playback_3, offset = 0
  67.
      registered port system:playback_4, offset = 0
  68.
      registered port system:playback_5, offset = 0
  69.
      registered port system:playback_6, offset = 0
  70.
      ++ jack_rechain_graph():
  71.
      client freebob_pcm: internal client, execution_order=0.
  72.
      -- jack_rechain_graph()
  73.
      FreeBoB MSG: MIDI threads running with Realtime scheduling, priority 63
  74.
      FreeBoB MSG: MIDI queue thread started
  75.
      libiec61883 warning: Established connection on channel 0.
  76.
      You may need to manually set the channel on the receiving node.
  77.
      libiec61883 warning: Established connection on channel 1.
  78.
      You may need to manually set the channel on the transmitting node.
  79.
      9058 waiting for signals
  80.
      11:55:03.443 ALSA connection change.
  81.
      11:55:04.865 Server configuration saved to "/home/shawn/.jackdrc".
  82.
      11:55:04.867 Statistics reset.
  83.
      11:55:04.899 Client activated.
  84.
      11:55:04.901 JACK connection change.
  85.
      11:55:04.903 JACK connection graph change.
  86.
      new client: qjackctl, id = 2 type 2 @ 0xb7f19000 fd = 13
  87.
      cannot lock down memory for RT thread (Cannot allocate memory)
  88.
      ++ jack_rechain_graph():
  89.
      client freebob_pcm: internal client, execution_order=0.
  90.
      client qjackctl: start_fd=5, execution_order=0.
  91.
      client qjackctl: wait_fd=12, execution_order=1 (last client).
  92.
      -- jack_rechain_graph()
  93.
      load = 1.2985 max usecs: 554.000, spare = 20779.000
  94.
      load = 1.9336 max usecs: 548.000, spare = 20785.000
  95.
      load = 2.2301 max usecs: 539.000, spare = 20794.000
  96.
      load = 2.3760 max usecs: 538.000, spare = 20795.000
  97.
      load = 2.5005 max usecs: 560.000, spare = 20773.000
  98.
      load = 2.5300 max usecs: 546.000, spare = 20787.000
  99.
      load = 2.5306 max usecs: 540.000, spare = 20793.000
 100.
      11:55:15.215 Shutdown notification.
 101.
      11:55:15.221 JACK is stopping...
 102.
      11:55:15.228 JACK is being forced...
 103.
      cannot complete execution of the processing graph (Success)
 104.
      zombified - calling shutdown handler
 105.
      11:55:15.230 ALSA connection graph change.
 106.
      11:55:15.231 JACK has crashed.
 107.
      11:55:15.347 ALSA connection change.
 108.
      11:55:15.440 JACK was stopped successfully.

---

### Post by pointydrip on 2009-08-13
We're you ever able to get the FA-66 working?
I am experiencing the same problem and am stuck.
I'm running Jaunty and jackd starts properly (FFADO, etc..) but I can't seem to get anything but the midi port in Qjackctl connections.

the one error message that I get running jackd that hints at the problem is this:

client freebob_pcm error status 0
 client qjackctl error status 10000000

no idea what it means

---

