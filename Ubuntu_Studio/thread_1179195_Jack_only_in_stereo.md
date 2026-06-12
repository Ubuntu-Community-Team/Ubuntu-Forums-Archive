---
title: "Jack only in stereo"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by tolotos on 2009-06-05
Hello all together

Today I have installed Ubuntu Studio 9.04 and I'm quite impressed by the huge amount of possibilitys. Especially the sound server jack, is very interesting, but unfortunatly I still have some problems with it.
My Soundcard is a Creative Sound Blaster Live (5.1), which is detected by alsa and all channels are working (tested with: speaker-test -Dplug:surround51 -c6 -l1 -twav).
However there are only two writable clients in the Connections dialog of Jack Control. These clients are my front-left and front-right speakers.
Since this is my first time using Jack I don´t have any clue of how to solfe this problem.

Any help is greatly appreciated.

Thanks

tolotos

---

### Post by Grishka on 2009-06-05
> **tolotos said:**
> Hello all together

Today I have installed Ubuntu Studio 9.04 and I'm quite impressed by the huge amount of possibilitys. Especially the sound server jack, is very interesting, but unfortunatly I still have some problems with it.
My Soundcard is a Creative Sound Blaster Live (5.1), which is detected by alsa and all channels are working (tested with: speaker-test -Dplug:surround51 -c6 -l1 -twav).
However there are only two writable clients in the Connections dialog of Jack Control. These clients are my front-left and front-right speakers.
Since this is my first time using Jack I don´t have any clue of how to solfe this problem.

Any help is greatly appreciated.

Thanks

tolotos

have you tried changing the number of channels in JACK settings?

---

### Post by tolotos on 2009-06-05
Well I cant change the channels option and its predefined value is default. However I can select the number of output channels. But doing this I get an error message:
[COLOR=#ff0000]Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
The message window says:
[COLOR=#999999]9:59:25.436 Logging started --- Fri Jun 5 19:59:25 2009 ---[/COLOR]
 [COLOR=#999999]19:59:25.604 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:59:25.859 Statistics reset.[/COLOR]
 [COLOR=#66cc99]19:59:26.005 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]19:59:26.649 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:02:46.467 Startup script...[/COLOR]
 [COLOR=#990099]20:02:46.469 artsshell -q terminate[/COLOR]
 [COLOR=#999999]20:02:46.873 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]20:02:46.874 JACK is starting...[/COLOR]
 [COLOR=#990099]20:02:46.875 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -P -o5[/COLOR]
 [COLOR=#999999]20:02:46.880 JACK was started with PID=3912.[/COLOR]
 [COLOR=#999999]20:02:47.672 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]20:02:47.672 Post-shutdown script...[/COLOR]
 [COLOR=#990099]20:02:47.673 killall jackd[/COLOR]
 [COLOR=#999999]20:02:48.095 Post-shutdown script terminated with exit status=256.[/COLOR]

Is there any additional debugging output I could post?

---

### Post by tolotos on 2009-06-26
Well, I still haven`t stopped trying and failing. If it provides some clues: I`am using the 64 bit Version of Ubuntu.

Any help or some hints were I could continue asking would be greatly appreciated.

Thanks

tolotos

---

### Post by tolotos on 2009-06-29
blubb

---

### Post by Stochastic on 2009-06-30
Can you check the 'verbose' box in qjackctl settings and retry with multiple channels (six channels should be correct for your card) and repost any error messages you get.

---

### Post by tolotos on 2009-07-02
Hello Stochastic

Thanks for your reply.
I have done as you said and attached the logging to this post. The first 24 lines are always the same. After that the messages vary. I have made several test runs with different settings. With two channels, with 5 channels and with 6 channels. 
I have posted the results, starting from the 24th line.

2Channel ouput:
```

server `default' registered
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|-|2048|2|44100|0|2|nomon|swmeter|-|32bit
control device hw:0
23:17:18.264 JACK was started with PID=7412.
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x1cb7a20 fd = -1
new buffer size 2048
7412 waiting for signals
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 3 fd's
load = 0.0480 max usecs: 41.000, spare = 42625.000
23:17:20.341 Server configuration saved to "/home/b1/.jackdrc".
23:17:20.342 Statistics reset.
23:17:20.386 Client activated.
23:17:20.387 JACK connection change.
23:17:20.390 JACK connection graph change.
load = 0.0439 max usecs: 17.000, spare = 42649.000
SSE2 detected
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0x7f8955900000 fd = 13
start poll on 4 fd's
server thread back from poll
new client qjackctl using 14 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 14 for qjackctl starts at 3321752731
back from client event poll after 71 usecs
client qjackctl: wait_fd=9, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
load = 0.1087 max usecs: 74.000, spare = 42592.000
load = 0.1293 max usecs: 64.000, spare = 42602.000
load = 0.1373 max usecs: 62.000, spare = 42604.000
load = 0.1413 max usecs: 62.000, spare = 42604.000
load = 0.1433 max usecs: 62.000, spare = 42604.000
load = 0.1455 max usecs: 63.000, spare = 42603.000
load = 0.1431 max usecs: 60.000, spare = 42606.000
load = 0.1442 max usecs: 62.000, spare = 42604.000
load = 0.1471 max usecs: 64.000, spare = 42602.000
load = 0.1474 max usecs: 63.000, spare = 42603.000
load = 0.1452 max usecs: 61.000, spare = 42605.000
load = 0.1464 max usecs: 63.000, spare = 42603.000
load = 0.1623 max usecs: 76.000, spare = 42590.000
load = 0.2171 max usecs: 116.000, spare = 42550.000
load = 0.2445 max usecs: 116.000, spare = 42550.000
load = 0.1949 max usecs: 62.000, spare = 42604.000
load = 0.1689 max usecs: 61.000, spare = 42605.000
load = 0.1595 max usecs: 64.000, spare = 42602.000
load = 0.1524 max usecs: 62.000, spare = 42604.000
load = 0.1489 max usecs: 62.000, spare = 42604.000
load = 0.1459 max usecs: 61.000, spare = 42605.000
load = 0.1491 max usecs: 65.000, spare = 42601.000
load = 0.1484 max usecs: 63.000, spare = 42603.000
load = 0.1492 max usecs: 64.000, spare = 42602.000
load = 0.1508 max usecs: 65.000, spare = 42601.000
load = 0.1480 max usecs: 62.000, spare = 42604.000
load = 0.1490 max usecs: 64.000, spare = 42602.000
load = 0.1448 max usecs: 60.000, spare = 42606.000
load = 0.1462 max usecs: 63.000, spare = 42603.000
load = 0.1434 max usecs: 60.000, spare = 42606.000
load = 0.1397 max usecs: 58.000, spare = 42608.000
23:17:52.346 Client deactivated.
23:17:52.347 JACK is stopping...
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
start poll on 3 fd's
jack main caught signal 15
starting server engine shutdown
stopping driver
unloading driver
freeing shared port segments
server thread back from poll
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 8621.000 usecs
freeing engine shared memory
max usecs: 116.000, engine deleted
WARNING: 1 message buffer overruns!
cleaning up shared memory
cleaning up files
unregistering server `default'
23:17:52.370 JACK was stopped successfully.
23:17:52.371 Post-shutdown script...
23:17:52.372 killall jackd
jackd: no process killed
23:17:52.825 Post-shutdown script terminated with exit status=256.
23:18:19.493 Startup script...
23:18:19.494 artsshell -q terminate
sh: artsshell: not found
23:18:19.919 Startup script terminated with exit status=32512.
23:18:19.920 JACK is starting...
23:18:19.920 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p2048 -n2 -P -o6
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
23:18:19.957 JACK was started with PID=7459.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|-|2048|2|44100|0|6|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: cannot set channel count to 6 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0xf4da20 fd = -1
start poll on 3 fd's
starting server engine shutdown
freeing shared port segments
server thread back from poll
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
23:18:20.028 JACK was stopped successfully.
23:18:20.029 Post-shutdown script...
23:18:20.029 killall jackd
jackd: no process killed
23:18:20.461 Post-shutdown script terminated with exit status=256.
23:18:22.134 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
23:18:49.757 Logging stopped --- Thu Jul 2 23:18:49 2009 ---

```5Channel:

```

server `default' registered
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|-|2048|2|44100|0|5|nomon|swmeter|-|32bit
control device hw:0
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
23:20:26.641 JACK was started with PID=7825.
new client: alsa_pcm, id = 1 type 1 @ 0x103fa20 fd = -1
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: cannot set channel count to 5 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
WARNING: 1 message buffer overruns!
cleaning up shared memory
cleaning up files
unregistering server `default'
23:20:26.659 JACK was stopped successfully.
23:20:26.660 Post-shutdown script...
23:20:26.660 killall jackd
jackd: no process killed
23:20:27.074 Post-shutdown script terminated with exit status=256.
23:20:28.685 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


```6Channel:

```
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
23:19:03.917 JACK was started with PID=7516.
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: alsa_pcm, id = 1 type 1 @ 0x24dba20 fd = -1
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|-|2048|2|44100|0|6|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: cannot set channel count to 6 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
23:19:03.945 JACK was stopped successfully.
23:19:03.946 Post-shutdown script...
23:19:03.946 killall jackd
jackd: no process killed
23:19:04.377 Post-shutdown script terminated with exit status=256.
23:19:05.989 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
23:19:59.573 Logging stopped --- Thu Jul 2 23:19:59 2009 ---

```The first 24 lines are:
```

23:20:19.745 Logging started --- Thu Jul 2 23:20:19 2009 ---
23:20:19.759 Patchbay deactivated.
23:20:19.775 Statistics reset.
23:20:19.997 ALSA connection graph change.
23:20:20.199 ALSA connection change.
23:20:26.184 Startup script...
23:20:26.184 artsshell -q terminate
sh: artsshell: not found
23:20:26.587 Startup script terminated with exit status=32512.
23:20:26.588 JACK is starting...
23:20:26.589 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p2048 -n2 -P -o5
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.

```If there is something more I could do, just tell me.

Thanks in advance 

tolotos

---

### Post by tolotos on 2009-07-04
Hello

:):):):):):):):)

It works, thanks to a brilliant tutorial at [http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)
Just define a virtual soundcard  with 6 channesl in .asoundrc and use it with jack.

Now I am enjoying 5.1 sound in jack^^

---

