---
title: "Fresh Hardy install and JACK crashes"
date: 2009-09-18
forum: Ubuntu Studio
---

### Post by kvk on 2009-09-18
I burned a DVD ISO from U. Studio for 64-bit 8.04 and performed a fresh install. Afterwards I ran the update manager for the first set of updates.

I've had U. Studio 8.10 up and running before on this computer, so the hardware itself isn't a deal breaker.

Hardware: Presonus FP10
kernel: 2.24-19-rt

*Created audio group= added User

*Set memlock = 80%, enable raw1394 (total memory = 4GB)

*Added:
@audio  -   rtprio       99
@audio	-   nice        -10
@audio  -   memlock     30000000

to /etc/security/limits.conf

JACK settings:
Driver: freebob
Priority: default
Realtime checked
Frames/Period: 64
Sample Rate: 44100
Periods/Buffer: 2
Interface:hw0

The problems are two:

1) Sudden freezes at random points. I had not experienced this with 8.10, but the refrain appears to be that 8.04 is the most stable and dependable, so I downloaded that version from U. Studio.

2)JACK crashes at random points. Sometimes it waits until I have opened Ardour and begun working, other time it barely lasts for a few seconds. Verbose message output:

```

17:10:12.051 ALSA connection graph change.
17:10:12.244 ALSA connection change.
17:10:18.906 Startup script...
17:10:18.906 artsshell -q terminate
17:10:19.662 Startup script terminated with exit status=256.
17:10:19.662 JACK is starting...
17:10:19.662 /usr/bin/jackd -v -R -p128 -dfreebob -dhw:0 -r44100 -p64 -n2 -D
17:10:19.665 JACK was started with PID=5835.
getting driver descriptor from /usr/lib64/jack/jack_dummy.so
getting driver descriptor from /usr/lib64/jack/jack_oss.so
getting driver descriptor from /usr/lib64/jack/jack_freebob.so
getting driver descriptor from /usr/lib64/jack/jack_alsa.so
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
new client: freebob_pcm, id = 1 type 1 @ 0x62b690 fd = -1
SSE2 detected
Freebob using Firewire port 0, node -1
new buffer size 64
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.7
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 44100
LibFreeBoB MSG:   Period Size              : 64
LibFreeBoB MSG:   Nb Buffers               : 2
LibFreeBoB MSG:   Directions               : 0
showDevice: not implemented
FreeBoB MSG: Register MIDI IN port dev1c_MIDI 1
FreeBoB MSG: Register MIDI OUT port dev1p_MIDI 1
FreeBoB MSG: Streaming thread running with Realtime scheduling, priority 14
FreeBoB MSG: Registering audio capture port C0_dev1c_Input 1L
17:10:21.234 ALSA connection graph change.
registered port system:capture_1, offset = 256
FreeBoB MSG: Registering audio capture port C1_dev1c_Input 2R
registered port system:capture_2, offset = 512
FreeBoB MSG: Registering audio capture port C2_dev1c_Input 3L
registered port system:capture_3, offset = 768
FreeBoB MSG: Registering audio capture port C3_dev1c_Input 4R
registered port system:capture_4, offset = 1024
FreeBoB MSG: Registering audio capture port C4_dev1c_Input 5L
registered port system:capture_5, offset = 1280
FreeBoB MSG: Registering audio capture port C5_dev1c_Input 6R
registered port system:capture_6, offset = 1536
FreeBoB MSG: Registering audio capture port C6_dev1c_Input 7L
registered port system:capture_7, offset = 1792
FreeBoB MSG: Registering audio capture port C7_dev1c_Input 8R
registered port system:capture_8, offset = 2048
FreeBoB MSG: Registering audio capture port C8_dev1c_S/PDIF Input 9L
registered port system:capture_9, offset = 2304
FreeBoB MSG: Registering audio capture port C9_dev1c_S/PDIF Input 10R
registered port system:capture_10, offset = 2560
FreeBoB MSG: Don't register capture port for dev1c_MIDI 1
FreeBoB MSG: Registering playback audio port P0_dev1p_Output 1L
registered port system:playback_1, offset = 0
FreeBoB MSG: Registering playback audio port P1_dev1p_Output 2R
registered port system:playback_2, offset = 0
FreeBoB MSG: Registering playback audio port P2_dev1p_Output 3L
registered port system:playback_3, offset = 0
FreeBoB MSG: Registering playback audio port P3_dev1p_Output 4R
registered port system:playback_4, offset = 0
FreeBoB MSG: Registering playback audio port P4_dev1p_Output 5L
registered port system:playback_5, offset = 0
FreeBoB MSG: Registering playback audio port P5_dev1p_Output 6R
registered port system:playback_6, offset = 0
FreeBoB MSG: Registering playback audio port P6_dev1p_Output 7L
registered port system:playback_7, offset = 0
FreeBoB MSG: Registering playback audio port P7_dev1p_Output 8R
registered port system:playback_8, offset = 0
FreeBoB MSG: Registering playback audio port P8_dev1p_S/PDIF Output 9L
registered port system:playback_9, offset = 0
FreeBoB MSG: Registering playback audio port P9_dev1p_S/PDIF Output 10R
registered port system:playback_10, offset = 0
FreeBoB MSG: Don't register playback port dev1p_MIDI 1
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
FreeBoB MSG: MIDI threads running with Realtime scheduling, priority 13
FreeBoB MSG: MIDI queue thread started
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
5835 waiting for signals
17:10:21.336 ALSA connection change.
17:10:21.940 Server configuration saved to "/home/arctos/.jackdrc".
17:10:21.940 Statistics reset.
17:10:22.056 Client activated.
17:10:22.057 JACK connection change.
17:10:22.060 JACK connection graph change.
new client: qjackctl, id = 2 type 2 @ 0x7fc24a131000 fd = 10
SSE2 detected
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=5, execution_order=0.
client qjackctl: wait_fd=9, execution_order=1 (last client).
-- jack_rechain_graph()
load = 0.6547 max usecs: 19.000, spare = 1432.000
17:10:27.251 ALSA connection graph change.
17:10:27.252 Shutdown notification.
17:10:27.253 JACK is stopping...
17:10:27.254 JACK is being forced...
cannot complete execution of the processing graph (Success)
zombified - calling shutdown handler
17:10:27.271 JACK has crashed.
17:10:27.275 ALSA connection change.
17:10:27.454 JACK was stopped successfully.
17:10:27.454 Post-shutdown script...
17:10:27.454 killall jackd
jackd: no process killed
17:10:27.872 Post-shutdown script terminated with exit status=256.

```

I'm wondering if I might have better luck with the 32-bit version, or perhaps the issue lies with the "ALSA connection graph change", which I do not recall seeing before.

Thanks so much!

---

### Post by cooper77z on 2009-09-18
Can't say for certain, but I lost control of my master volume when I installed OpenShot. :confused:

---

### Post by trulan on 2009-09-19
I don't know how fast your processor is, but running your buffering at 64 frames 2 periods sounds a little tight for an FP10 to be stable.  The thing I hated about freebob (why I went to the work of installing  ffado, even in Hardy) was that while ffado will give x-runs if you set the buffering too tight, freebob will just crash.  Since it is crashing at random intervals I would really suspect that that is the problem.  Try setting your buffering to 128 frames 2 periods and see if your stability improves.

---

### Post by kvk on 2009-09-19
Thanks, Trulan- I'm able to get a bit more time by increasing the frame rate, but even at 256 it decides to crash, and that's at a latency of 11.5 msec.

It's odd because my original setup on this machine, when I was running 8.10, was to start JACK with

jackd -R -P89 -p128 -dfirewire -dhw:0 -r44100 -p32 -n2

and once everything was up and running, I had no problems.

Now, three things are different now:

1. Running 8.04 with a different rt kernel
2. Running 64-bit instead of 32
3. Using freebob instead of ffado

The processor is an Intel Core 2 Duo @ 3ghz, and I have 4 gb RAM. I can experiment with setting the frame rate even higher, but the latency will go through the roof and the hardware doesn't seem to require it. 

So my options are to get ffado up and running to see what happens, or perhaps re-install everything with a 32-bit system. I've tried setting the time-out at a higher level, but that didn't seem to make any difference- only adjusting the frame rate.

What do you think?

---

### Post by trulan on 2009-09-19
;) You have a good bit more processor power than I do.  There's no reason 64*2 shouldn't work for you.
(Here are the results of some testing I did today, if you are curious: [http://ubuntuforums.org/showpost.php?p=7974992&postcount=61](http://ubuntuforums.org/showpost.php?p=7974992&postcount=61))

I would try ffado first (install it, along with upgrading jackd), using khashayar's ppa.  But I started out with Jaunty on my 64 bit system, and only used Hardy in 32 bit (Jaunty would freeze on that machine) so I really don't know how much difference you would see.

Another thing I've been experimenting with (this is in Karmic (9.10), but you could do the same thing on any version) is running an XFCE session instead of Gnome.  I'd been having issues with x-runs every time I maximized or minimized a window, and I was told this was probably due to using an on-board video card.  Anyway, I installed xcfe, and at the login screen I can choose to log in to either an xfce session or a gnome session.  I get noticeably better audio performance on xfce, and I can maximize and minimize windows to my heart's content with no x-runs.  Just an idea.

---

### Post by kvk on 2009-09-19
That's a great idea about using xfce! I will definitely run that! Heck, maybe that will solve the crash issue.

And I was already installing ffado from those repositories when I saw your response. :-)

Unfortunately, I'm encountering circular dependencies. I recall these from months ago, but I can't remember how I resolved them.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffado-dbus-server: Depends: libglibmm-2.4-1c2a (>= 2.18.0) but 2.16.4-0ubuntu1 is to be installed
                     Depends: libxml++2.6-2 (>= 2.24.0) but it is not installable
  ffado-tools: Depends: libglibmm-2.4-1c2a (>= 2.18.0) but 2.16.4-0ubuntu1 is to be installed
               Depends: libxml++2.6-2 (>= 2.24.0) but it is not installable
  libffado2: Depends: libglibmm-2.4-1c2a (>= 2.18.0) but 2.16.4-0ubuntu1 is to be installed
             Depends: libxml++2.6-2 (>= 2.24.0) but it is not installable
  libjack0: Depends: libfreebob0 (>= 1.0.11) but 1.0.7-1 is to be installed
E: Broken packages

```

---

### Post by trulan on 2009-09-19
Hmm - I know I didn't run into that when I installed stuff from that ppa - are you sure you are getting the packages for Hardy?  There are packages for Intrepid and Jaunty on there as well...I don't know what else would cause those dependency issues.

---

### Post by kvk on 2009-09-19
DOH!

My bad- fixed it. I had the wrong repository versions enabled. Everything seems to be running fine now using the ffado firewire driver, 128 frame sampling rate, 2 periods/buffer. I haven't yet tried to really push the set-up, but it's lasted long enough with no X-runs (under Gnome) to set all the mixer panels and define some of the plug-ins and such, so I think (hopefully) all is settled now.

Thanks!

---

