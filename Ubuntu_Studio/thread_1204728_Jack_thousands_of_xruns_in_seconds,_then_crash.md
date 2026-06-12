---
title: "Jack thousands of xruns in seconds, then crash"
date: 2009-07-05
forum: Ubuntu Studio
---

### Post by ENatanael on 2009-07-05
I've recently compiled a new rt kernel: 2.6.29.5-rt22. 
I've added this: "none /tmp tmpfs defaults 0 0" to /etc/fstab
I've added this: 
> 
@audio - rtprio 99
@audio - nice -19
@audio - memlock 307807
to /etc/security/limits.conf
Now when I try to run jackd through qjackctl I get thousands of notifications in just a matter of seconds. If I run it without Realtime it doesn't crash, but with, it takes about 20 seconds and then it becomes totally inresponsive. The time it takes to crash is the same independent of the settings.
The amount of xruns varies with my Frames/Period settings. The lower the value, the more notifications I get.
 Here is an exemple from the Messages window when running jack without Realtime mode. I then stopped the server after a couple of seconds:
> 
11:04:54.290 Patchbay deactivated.
11:04:55.550 Statistics reset.
11:04:56.393 ALSA connection graph change.
11:04:56.667 ALSA connection change.
11:05:03.941 Startup script...
11:05:03.944 artsshell -q terminate
sh: artsshell: not found
11:05:04.363 Startup script terminated with exit status=32512.
11:05:04.365 JACK is starting...
11:05:04.368 /usr/bin/jackd -v -t1000 -dalsa -dhw:0 -r44100 -p4096 -n2 -S
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
11:05:04.403 JACK was started with PID=6308.
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
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
new client: alsa_pcm, id = 1 type 1 @ 0x8ade758 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|4096|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 4096 frames (92.9 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
new buffer size 4096
registered port system:capture_1, offset = 16384
registered port system:capture_2, offset = 32768
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
6308 waiting for signals
11:05:06.556 Server configuration saved to "/home/erik/.jackdrc".
11:05:06.563 Statistics reset.
11:05:06.615 Client activated.
11:05:06.621 JACK connection change.
11:05:06.628 JACK connection graph change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb7f2d000 fd = 14
start poll on 4 fd's
server thread back from poll
new client qjackctl using 15 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 15 for qjackctl starts at 3106969230
back from client event poll after 124 usecs
client qjackctl: wait_fd=9, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
client event poll on 15 for qjackctl starts at 3107038240
back from client event poll after 97 usecs
11:05:06.729 XRUN callback (1).
client event poll on 15 for qjackctl starts at 3107209070
back from client event poll after 91 usecs
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
client event poll on 15 for qjackctl starts at 3107379910
back from client event poll after 83 usecs
client event poll on 15 for qjackctl starts at 3107550735
back from client event poll after 314 usecs
client event poll on 15 for qjackctl starts at 3107722579
back from client event poll after 472 usecs
client event poll on 15 for qjackctl starts at 3107893406
back from client event poll after 1112 usecs
client event poll on 15 for qjackctl starts at 3108064233
back from client event poll after 84 usecs
client event poll on 15 for qjackctl starts at 3108235073
back from client event poll after 1633 usecs
client event poll on 15 for qjackctl starts at 3108405907
back from client event poll after 169 usecs
client event poll on 15 for qjackctl starts at 3108576739
back from client event poll after 308 usecs
client event poll on 15 for qjackctl starts at 3108747919
back from client event poll after 121 usecs
client event poll on 15 for qjackctl starts at 3108918745
back from client event poll after 299 usecs
11:05:08.634 XRUN callback (11 skipped).
client event poll on 15 for qjackctl starts at 3109089570
back from client event poll after 477 usecs
client event poll on 15 for qjackctl starts at 3109260424
back from client event poll after 629 usecs
client event poll on 15 for qjackctl starts at 3109431249
back from client event poll after 802 usecs
client event poll on 15 for qjackctl starts at 3109602081
back from client event poll after 986 usecs
client event poll on 15 for qjackctl starts at 3109772898
back from client event poll after 140 usecs
client event poll on 15 for qjackctl starts at 3109943730
back from client event poll after 358 usecs
client event poll on 15 for qjackctl starts at 3110114559
back from client event poll after 486 usecs
client event poll on 15 for qjackctl starts at 3110285431
back from client event poll after 622 usecs
client event poll on 15 for qjackctl starts at 3110456249
back from client event poll after 804 usecs
client event poll on 15 for qjackctl starts at 3110627083
back from client event poll after 2431 usecs
client event poll on 15 for qjackctl starts at 3110797905
back from client event poll after 2169 usecs
client event poll on 15 for qjackctl starts at 3110968728
back from client event poll after 318 usecs
11:05:10.661 XRUN callback (11 skipped).
client event poll on 15 for qjackctl starts at 3111139558
back from client event poll after 99 usecs
client event poll on 15 for qjackctl starts at 3111310388
back from client event poll after 663 usecs
client event poll on 15 for qjackctl starts at 3111481213
back from client event poll after 853 usecs
client event poll on 15 for qjackctl starts at 3111652085
back from client event poll after 1995 usecs
client event poll on 15 for qjackctl starts at 3111822911
back from client event poll after 129 usecs
client event poll on 15 for qjackctl starts at 3111993732
back from client event poll after 311 usecs
client event poll on 15 for qjackctl starts at 3112164559
back from client event poll after 492 usecs
client event poll on 15 for qjackctl starts at 3112335515
back from client event poll after 82 usecs
client event poll on 15 for qjackctl starts at 3112506343
back from client event poll after 708 usecs
client event poll on 15 for qjackctl starts at 3112677177
back from client event poll after 982 usecs
client event poll on 15 for qjackctl starts at 3112848024
back from client event poll after 2053 usecs
client event poll on 15 for qjackctl starts at 3113018843
back from client event poll after 196 usecs
11:05:12.667 XRUN callback (11 skipped).
client event poll on 15 for qjackctl starts at 3113189670
back from client event poll after 378 usecs
client event poll on 15 for qjackctl starts at 3113360499
back from client event poll after 552 usecs
client event poll on 15 for qjackctl starts at 3113531328
back from client event poll after 84 usecs
client event poll on 15 for qjackctl starts at 3113702149
back from client event poll after 80 usecs
client event poll on 15 for qjackctl starts at 3113873142
back from client event poll after 80 usecs
client event poll on 15 for qjackctl starts at 3114043974
back from client event poll after 918 usecs
client event poll on 15 for qjackctl starts at 3114214799
back from client event poll after 249 usecs
client event poll on 15 for qjackctl starts at 3114385626
back from client event poll after 427 usecs
client event poll on 15 for qjackctl starts at 3114557682
back from client event poll after 364 usecs
client event poll on 15 for qjackctl starts at 3114728632
back from client event poll after 417 usecs
client event poll on 15 for qjackctl starts at 3114899461
back from client event poll after 1652 usecs
11:05:14.673 XRUN callback (10 skipped).
client event poll on 15 for qjackctl starts at 3115072439
back from client event poll after 80 usecs
client event poll on 15 for qjackctl starts at 3115243260
back from client event poll after 795 usecs
client event poll on 15 for qjackctl starts at 3115417692
back from client event poll after 398 usecs
client event poll on 15 for qjackctl starts at 3115589246
back from client event poll after 807 usecs
client event poll on 15 for qjackctl starts at 3115761143
back from client event poll after 552 usecs
client event poll on 15 for qjackctl starts at 3115931875
back from client event poll after 170 usecs
client event poll on 15 for qjackctl starts at 3116102738
back from client event poll after 309 usecs
client event poll on 15 for qjackctl starts at 3116273593
back from client event poll after 461 usecs
client event poll on 15 for qjackctl starts at 3116444420
back from client event poll after 665 usecs
client event poll on 15 for qjackctl starts at 3116615253
back from client event poll after 798 usecs
client event poll on 15 for qjackctl starts at 3116787849
back from client event poll after 193 usecs
client event poll on 15 for qjackctl starts at 3116958681
back from client event poll after 366 usecs
11:05:16.683 XRUN callback (11 skipped).
client event poll on 15 for qjackctl starts at 3117129502
back from client event poll after 84 usecs
client event poll on 15 for qjackctl starts at 3117300327
back from client event poll after 725 usecs
client event poll on 15 for qjackctl starts at 3117471155
back from client event poll after 904 usecs
client event poll on 15 for qjackctl starts at 3117641980
back from client event poll after 3241 usecs
client event poll on 15 for qjackctl starts at 3117812810
back from client event poll after 232 usecs
client event poll on 15 for qjackctl starts at 3117985408
back from client event poll after 644 usecs
client event poll on 15 for qjackctl starts at 3118157031
back from client event poll after 83 usecs
client event poll on 15 for qjackctl starts at 3118328411
back from client event poll after 143 usecs
client event poll on 15 for qjackctl starts at 3118499265
back from client event poll after 88 usecs
client event poll on 15 for qjackctl starts at 3118670090
back from client event poll after 82 usecs
client event poll on 15 for qjackctl starts at 3118840913
back from client event poll after 129 usecs
client event poll on 15 for qjackctl starts at 3119011744
back from client event poll after 174 usecs
11:05:18.689 XRUN callback (11 skipped).
client event poll on 15 for qjackctl starts at 3119182570
back from client event poll after 73 usecs
client event poll on 15 for qjackctl starts at 3119353395
back from client event poll after 657 usecs
client event poll on 15 for qjackctl starts at 3119524231
back from client event poll after 820 usecs
client event poll on 15 for qjackctl starts at 3119695063
back from client event poll after 216 usecs
client event poll on 15 for qjackctl starts at 3119866584
back from client event poll after 468 usecs
client event poll on 15 for qjackctl starts at 3120037412
back from client event poll after 143 usecs
client event poll on 15 for qjackctl starts at 3120208243
back from client event poll after 809 usecs
client event poll on 15 for qjackctl starts at 3120379128
back from client event poll after 932 usecs
client event poll on 15 for qjackctl starts at 3120550390
back from client event poll after 663 usecs
client event poll on 15 for qjackctl starts at 3120721269
back from client event poll after 783 usecs
client event poll on 15 for qjackctl starts at 3120892093
back from client event poll after 968 usecs
client event poll on 15 for qjackctl starts at 3121062916
back from client event poll after 126 usecs
11:05:20.696 XRUN callback (11 skipped).
client event poll on 15 for qjackctl starts at 3121233739
back from client event poll after 306 usecs
client event poll on 15 for qjackctl starts at 3121404628
back from client event poll after 404 usecs
client event poll on 15 for qjackctl starts at 3121575504
back from client event poll after 545 usecs
client event poll on 15 for qjackctl starts at 3121746338
back from client event poll after 712 usecs
client event poll on 15 for qjackctl starts at 3121917156
back from client event poll after 885 usecs
client event poll on 15 for qjackctl starts at 3122087982
back from client event poll after 925 usecs
11:05:21.764 Client deactivated.
11:05:21.768 JACK is stopping...
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
marking client qjackctl with SOCKET error state = Not triggered errors = 0
trying to lock graph to remove 1 problems
we have problem clients (problems = 1
++ Removing failed clients ...
client alsa_pcm error status 0
client qjackctl error status 10000000
removing failed client qjackctl state = Not triggered errors = 10000000
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
freeing shared port segments
stopping server thread
last xrun delay: 72.000 usecs
max delay reported by backend: 3650.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
11:05:21.933 JACK was stopped successfully.
11:05:21.938 Post-shutdown script...
11:05:21.940 killall jackd
jackd: ingen process avslutad
11:05:22.414 Post-shutdown script terminated with exit status=256.

I'm running Jaunty.

---

### Post by sgx on 2009-07-05
Hi, maybe try it using

memlock   unlimited

and if nothing improves, just comment out the memlock line.

Have you used a stock 2.6.28/2.6.29 kernel? I get excellent audio results
with those, setting priority in qjackctl to 60. Is your network, bluetooth
and webcams, motherboard audio etc etc all disabled?

Have you run the alsaconf utility after updating all alsa/libalsa2 apps and libraries?
Death to all xruns!

---

### Post by ENatanael on 2009-07-14
Thanks for answearing and sorry for the late reply!
memlock didn't do any difference. The kernel I used was from kernel.org. I don't have any webcam or bluetooth, but my network is always on. In what way does this impact jack?
At the moment I unfortunately don't have any other soundcard than the one on my motherboard so I can't disable it. 
The alsaconf utility seems not to be avivible for Ubuntu anymore...

---

### Post by trulan on 2009-07-14
Some onboard cards simply do not like to duplex (record and playback simultaneously).  Try setting Jack to 'playback only' or 'record only' and see what you can get.  There may be a way to get it to work using Duplex, but I haven't found it yet, other than using a better sound card.

---

### Post by thorgal on 2009-07-14
open a terminal and try this (make sure qjackctl is not running):

```

# just to be sure jackd is not already running
killall -9 jackd

# start up jack
/usr/bin/jackd -R -P 70 -dalsa -dhw:0 -r48000 -p128 -n3

```

see if you get many xruns like that. If not, you can set this up in qjackctl.

---

### Post by ENatanael on 2009-07-19
Trulan: Thank you! Playback only works fine, but it's impossible to start with Capture only. Error message:
```

09:11:53.389 JACK is starting...
 09:11:53.390 /usr/bin/jackd -v -R -P60 -t1000 -dalsa -dhw:0 -r44100 -p128 -n2 -C -S
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 getting driver descriptor from /usr/lib/jack/jack_freebob.so
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 09:11:53.424 JACK was started with PID=6381.
 no message buffer overruns
 getting driver descriptor from /usr/lib/jack/jack_net.so
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 server `default' registered
 cannot lock down memory for jackd (Cannot allocate memory)
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 start poll on 3 fd's
 loading driver ..
 new client: alsa_pcm, id = 1 type 1 @ 0x868c7a8 fd = -1
 apparent rate = 44100
 creating alsa driver ... -|hw:0|128|2|44100|0|0|nomon|swmeter|-|16bit
 control device hw:0
 configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 impossible sample width (1) discovered!
 09:11:53.546 JACK was stopped with exit status=1.
 09:11:53.548 Post-shutdown script...
 09:11:53.548 killall jackd
 jackd: ingen process avslutad
 09:11:53.971 Post-shutdown script terminated with exit status=256.
 09:11:55.513 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```Thorgal: This resulted in an error:
```
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
jackd watchdog: timeout - killing jackd
```

---

### Post by thorgal on 2009-07-20
... looks strange to me .. but again, depends on your hardware. What's your audio interface ? 

You could try the same setting but with -r 44100. It could be that the sample rate set to 48000 is causing a hick-up. My own RME system does not like -n 3, I have to use -n 2. But if you use an onboard intel HDA based chip, -n 3 should be better.

---

### Post by ENatanael on 2009-07-20
All combinations with 48000/44100 sample rate and 3/2 buffers gave the same error.
From the lspci command:
```

00:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
---
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

There are quite a lot from VIA too, and I've heard they aren't good for audio...

---

### Post by thorgal on 2009-07-20
what about 

```

cat /proc/asound/cards

```

?

---

### Post by ENatanael on 2009-07-20
cat /proc/asound/cards gave:
```

 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC850 at 0xbc00, irq 22

```

---

### Post by thorgal on 2009-07-21
I don't want to talk bad but VIA is not really a good choice, especially for RT stuff. If you have some bucks to spend, get a decent audio interface (USB, firewire, cardbus, PCI) that is fully supported by your favorite OS :) It does not have to be something expensive or fancy, you could start by a modest dual analog channel interface (with or without mic preamps). In general, the _M-Audio Delta_ line is worth the money for the sound quality and affordable price. They require a PCI slot so if you have a desktop with such a slot, you should do fine. If you have a laptop, then check USB interfaces (USB 1.1, as USB 2 devices are not following any standard and are prone to not work at all in linux) or firewire (more pricy but probably better in terms of latency (no CPU cycles involved, unlike USB).

---

### Post by ENatanael on 2009-07-21
I'm getting a new laptop in about a week, so I guess I'll just have to get it a firewire soundcard.
But thanks anyway, at least I've learnt some!

---

