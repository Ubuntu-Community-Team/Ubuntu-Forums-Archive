---
title: "JACK not working on ASUS M4A785TD-V EVO."
date: 2010-06-26
forum: Ubuntu Studio
---

### Post by Dangerouge on 2010-06-26
Hello, I'm using Ubuntu Studio 10.4 from an external hard disk, my main purpose being in using it for live performances. Now here's the thing, Q JACK Control isn't working for some reason on my home pc. I use this same USB HD at office and at rehearsals, and at both places it works like a dream, but when I get home, nothing to be heard. At home, I'm using ASUS M4A785TD-V EVO onboard 7.1. audio, which works fine with ALSA in for example, LMMS, but with JACK, I get nothing. There's also this issue that audio configuration tells me that I only have stereo audio, where I, as said before, should have 7.1. Previously JACK offered me 6 output channels at home, but because it wasn't working, I changed the driver, so now it also offers only 2. I'm confuzzled here, so help me, I'm pretty new to Ubuntu and to using Studio's capabilities.

---

### Post by Dangerouge on 2010-06-26
Ok, fixed! ^^ Set sound preferences to use 7.1 audio and JACK driver settings to HW0,0 and to 6 output channels (I only have a 5.1 speaker system), working like a charrrm!

---

### Post by Dangerouge on 2010-06-27
Nevermind, not working again, and I've changed nothing, what is this?? Help please. :)

---

### Post by cchhrriiss121212 on 2010-06-27
Here is a basic setup for jack:
driver: alsa (don't bother changing this)
uncheck all boxes on the left hand side (check realtime if you have your limits.conf set)
on the right hand side, interface: hw:0,0 and everything below as default
frames: 1024
sample: 48000
periods: 2

If it doesn't run then post the output of the message window

---

### Post by Dangerouge on 2010-06-27
Well, the server starts up just fine, but no sound gets through to the speakers... But maybe you can see something of a hint in that message list of the qjackctl?

Oh, and thank you ;)

---

### Post by Dangerouge on 2010-06-27
Oops, forgot the attachment, here it is!

---

### Post by cchhrriiss121212 on 2010-06-27
Looks fine to me. Check alsamixer for your output levels, then make sure you have the right connections in the connection window/patchage. Autoconnect will rarely work well with 5.1 setups.

---

### Post by Dangerouge on 2010-06-27
ALSA mixer's levels are quite ok, about half-way for everything... Hmm, I even tried putting a meterbridge to the alsa monitor channels, and it reports level changes as I have the mic input connected to all the outputs and I'm speaking in the mic.

---

### Post by Dangerouge on 2010-06-27
Whaat, it even works on jackd, but just not on qjackctl... This was the printout of jackd:
```
$ jackd -R -d alsa
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1351668
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
```

---

### Post by Dangerouge on 2010-07-02
Sorry to bump, but I need to get this solved, I'm a gigging musician... :(

Oh, btw, 48000Hz settings make the playing out of tune. 44100Hz is the way.

---

### Post by cchhrriiss121212 on 2010-07-02
So you can get sound to your speakers without qjackctl, but you can't with qjackctl?
If qjackctl does not work for you then could you post the output of the message window.

---

### Post by Pablo_F on 2010-07-02
Hi,

Needless to say, the jack setup depends a lot on your hardware. There is never a universal setup.

So I suggest you use the preset function in qjackctl's setup and you name these presets, for example, "home", "rehearsals" and "home". Each preset has a certain combination of options and parameters. This way you don't have to change the settings each time, only choose the working preset for each computer.

Now, for the home computer, can you open a terminal and give the output of the following informative commands?

cat /proc/asound/cards
aplay -l

---

### Post by Dangerouge on 2010-07-03
Message window reads:

```
19:52:16.692 Patchbay deactivated.
19:52:16.754 Statistics reset.
19:52:16.797 ALSA connection graph change.
19:52:17.063 ALSA connection change.
19:52:45.112 Startup script...
19:52:45.113 artsshell -q terminate
sh: artsshell: not found
19:52:45.517 Startup script terminated with exit status=32512.
19:52:45.517 JACK is starting...
19:52:45.517 /usr/bin/jackd -v -m -dalsa -dhw:0,0 -r44100 -p1024 -n3 -s -m -S -Xseq -H -M
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1351668
19:52:45.547 JACK was started with PID=2251.
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
apparent rate = 44100
new client: alsa_pcm, id = 1 type 1 @ 0x8df2580 fd = -1
creating alsa driver ... hw:0,0|hw:0,0|1024|3|44100|0|0|hwmon|hwmeter|soft-mode|16bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
new buffer size 1024
registered port system:capture_1, offset = 4096
registered port system:capture_2, offset = 8192
registered port system:playback_1, offset = 0
registered port alsa_pcm:monitor_1, offset = 12288
registered port system:playback_2, offset = 0
registered port alsa_pcm:monitor_2, offset = 16384
registered port system:playback_3, offset = 0
registered port alsa_pcm:monitor_3, offset = 20480
registered port system:playback_4, offset = 0
registered port alsa_pcm:monitor_4, offset = 24576
registered port system:playback_5, offset = 0
registered port alsa_pcm:monitor_5, offset = 28672
registered port system:playback_6, offset = 0
registered port alsa_pcm:monitor_6, offset = 32768
registered port system:playback_7, offset = 0
registered port alsa_pcm:monitor_7, offset = 36864
registered port system:playback_8, offset = 0
registered port alsa_pcm:monitor_8, offset = 40960
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
19:52:45.873 ALSA connection graph change.
registered port alsa_pcm:Midi-Through/midi_capture_1, offset = 4096
registered port alsa_pcm:Midi-Through/midi_playback_1, offset = 0
registered port alsa_pcm:TiMidity/midi_playback_1, offset = 0
registered port alsa_pcm:TiMidity/midi_playback_2, offset = 0
registered port alsa_pcm:TiMidity/midi_playback_3, offset = 0
registered port alsa_pcm:TiMidity/midi_playback_4, offset = 0
2251 waiting for signals
load = 0.1206 max usecs: 56.000, spare = 23163.000
19:52:47.578 Server configuration saved to "/home/aranubanti/.jackdrc".
19:52:47.580 Statistics reset.
19:52:47.583 Client activated.
19:52:47.588 JACK connection change.
19:52:47.594 JACK connection graph change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb5b5c000 fd = 15
start poll on 4 fd's
server thread back from poll
new client qjackctl using 16 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 16 for qjackctl starts at 2111083768
back from client event poll after 111 usecs
client qjackctl: wait_fd=14, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
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
load = 0.2907 max usecs: 107.000, spare = 23112.000
load = 0.3521 max usecs: 96.000, spare = 23123.000
load = 0.4129 max usecs: 110.000, spare = 23109.000
load = 0.4110 max usecs: 95.000, spare = 23124.000
load = 0.4338 max usecs: 106.000, spare = 23113.000
load = 0.5291 max usecs: 145.000, spare = 23074.000
load = 0.4756 max usecs: 98.000, spare = 23121.000
load = 0.4488 max usecs: 98.000, spare = 23121.000
load = 0.4290 max usecs: 95.000, spare = 23124.000
```and here are the other outputs:

```
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9e8000 irq 19
``````
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Pablo_F on 2010-07-03
Take a look at alsamixer. I see what could be a similar problem in:

[http://openartist.lefora.com/2009/08/24/jack-xruns/](http://openartist.lefora.com/2009/08/24/jack-xruns/)

Also, do you use your card for capture? If not, try playback only with hw:0,0.

Cheers! Pablo

---

### Post by sgx on 2010-07-03
> **Dangerouge said:**
> Sorry to bump, but I need to get this solved, I'm a gigging musician... :(

Oh, btw, 48000Hz settings make the playing out of tune. 44100Hz is the way.
Hi try starting jackd with

jackd -d alsa -r 44100

then start qjackctl and snoop around and make connections.

You might want to reinstall with a separate /home partition, so future reinstalls can keep most configurations, net/email accounts etc intact
by not reformatting /home each time.

Use synaptic to drastically reduce your load of un-needed programs, keep only what you need for the gigs, but don't remove things if you don't know what they do. Open Office, games, multiples of utilities, printing and gfx apps, net-tweak apps, all should go. And shutting down networks, bluetooth, webcam, powermanagement etc in the bios can be a good thing. Timidity should not be running or installed unless you need it.

 Change the synaptic preferences setting so that it keeps packages that you install in its cache, and start a collection. Sooner or later you'll want or need them.
 
/var/cache/apt/archives is usually where the the .deb package files are stored.
Keep in mind that most of linux is a rolling beta project, so it is on us as users to minimze conflicts and errors, by nuking the temptation to use linux as a 'does it all' environment. You're already on the right track when using external drives focussed on specific tasks, to good advantage.
I have one drive set to catch and run all the latest apps and updates, 
but very little of it makes its way into my audio setup.
Cheers

---

### Post by MIJ-VI on 2010-09-27
Update?..

---

