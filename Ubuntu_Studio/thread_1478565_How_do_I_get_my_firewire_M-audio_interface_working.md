---
title: "How do I get my firewire M-audio interface working?"
date: 2010-05-09
forum: Ubuntu Studio
---

### Post by CShaum on 2010-05-09
I have a NRV-10 M-audio mixer board does anyone know how to get it to work? I installed jack and wineasio. But it doesn't recognize it. The board does come with a MS driver but 10.04 blocks that program to install it, do I need it?? I appreciate your input Thanks.

---

### Post by hxcobd on 2010-05-10
First things first:

1.) Does linux recognize it? Using either the sound widget (little speaker icon on the top panel) or the PulseAudio volume control, is the interface/mixer listed as available hardware?

2.) If these don't give you a straight answer, try installing something like Audacity and checking your devices; is it listed there?

Basically, if your linux install sees the interface and you can actively use it for playback/recording, you should be good to go. You won't need Windows drivers or WineASIO, at least yet.

---

### Post by CShaum on 2010-05-11
I can't find nowhere that linux recognize it. I find nowhere a phrase like firewire audio of similar. I have audacity already but it doesn't list it either. On the mixer board there is a blue light that comes on when its connected. But no light. I download the pulseaudio volume control and there's nothing listed there as well. What next?? Thanks

---

### Post by m4443 on 2010-05-16
There's driver project called FFADO, which handles firewire devices in linux. After fast searching, seems that your device is "reported to work", but is unstable.

[http://www.ffado.org/?q=node/29](http://www.ffado.org/?q=node/29)

Can't really help with the installation.

---

### Post by CShaum on 2010-05-16
Thanks, Let me try that and see if it works. I searched too but all I found was USB drivers. I did contact M-audio for a firewire driver for linux but no luck there. Installation will be the next hitch.

---

### Post by WestCoastSuccess on 2010-05-17
Perhaps try the instructions [here]("http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/") - they're for the FireWire Solo but may have takeaways for your unit.

Good luck!

---

### Post by ghostandmachine on 2010-05-18
Hello,

I've followed the WestCoastSuccess instructions for my Firewire Solo on Hardy and it worked perfectly.

but since I've updated to Lucid, my jackd connects for a bit then disconnects. 

I tried following the same directions but to no luck.

Is there a driver or lib change from the upgrade?

---

### Post by WestCoastSuccess on 2010-05-18
We use 8.04 exclusively because the real time kernel has been largely broken on every subsequent release. I don't know that this is your problem with Lucid (and we were just discussing this morning trying a sample upgrade to Lucid to see if the problems are fixed) but it's my only guess.

Are you using a real time kernel with your Lucid installation?

---

### Post by ghostandmachine on 2010-05-18
Yes I am. 

uname -a 
```
Linux ubuntu 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 10:42:21 UTC 2010 i686 GNU/Linux

```

After pressing the start button on jack this is the output

```
23:05:40.121 Patchbay deactivated.
23:05:40.129 Statistics reset.
23:05:40.218 ALSA connection graph change.
23:05:40.452 ALSA connection change.
23:05:53.774 Startup script...
23:05:53.775 artsshell -q terminate
sh: artsshell: not found
23:05:54.179 Startup script terminated with exit status=32512.
23:05:54.180 JACK is starting...
23:05:54.181 /usr/bin/jackd -v -P89 -u -dfirewire -dhw:0 -r44100 -p256 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2209206
23:05:54.217 JACK was started with PID=5116.
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: firewire_pcm, id = 1 type 1 @ 0x9539280 fd = -1
new buffer size 256
libffado 2.0.0 built Mar 31 2010 14:47:42
firewire MSG: Streaming thread running with Realtime scheduling, priority 89
firewire MSG: Registering audio capture port C0_dev0_LineIn 1+2 left
firewire MSG: Registering audio capture port C1_dev0_LineIn 1+2 right
firewire MSG: Registering audio capture port C2_dev0_SpdifIn 1+2 left
firewire MSG: Registering audio capture port C3_dev0_SpdifIn 1+2 right
firewire MSG: Registering audio playback port P0_dev0_LineOut 1+2 left
firewire MSG: Registering audio playback port P1_dev0_LineOut 1+2 right
firewire MSG: Registering audio playback port P2_dev0_SpdifOut 1+2 left
firewire MSG: Registering audio playback port P3_dev0_SpdifOut 1+2 right
registered port system:capture_1, offset = 1024
registered port system:capture_2, offset = 2048
registered port system:capture_3, offset = 3072
registered port system:capture_4, offset = 4096
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 1
client firewire_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
23:05:56.609 Server configuration saved to "/home/eric/.jackdrc".
23:05:56.610 Statistics reset.
23:05:57.237 Client activated.
23:05:57.246 JACK connection change.
23:05:57.277 JACK connection graph change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb6e97000 fd = 16
start poll on 4 fd's
server thread back from poll
new client qjackctl using 17 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 1
client firewire_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 17 for qjackctl starts at 95657727
back from client event poll after 20 usecs
client qjackctl: wait_fd=13, execution_order=1 (last client).
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
5116 waiting for signals
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
23:05:59.008 XRUN callback (1).
firewire MSG: xrun detected
client event poll on 17 for qjackctl starts at 97430313
back from client event poll after 96 usecs
load = 3.8680 max usecs: 449.000, spare = 5355.000
load = 4.4754 max usecs: 295.000, spare = 5509.000
load = 6.0196 max usecs: 439.000, spare = 5365.000
load = 5.9560 max usecs: 342.000, spare = 5462.000
load = 6.9666 max usecs: 463.000, spare = 5341.000
load = 8.1956 max usecs: 547.000, spare = 5257.000
load = 7.9744 max usecs: 450.000, spare = 5354.000
load = 7.7174 max usecs: 433.000, spare = 5371.000
load = 7.6492 max usecs: 440.000, spare = 5364.000
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
stopping driver
detaching driver
client event poll on 17 for qjackctl starts at 112280592
back from client event poll after 99 usecs
client event poll on 17 for qjackctl starts at 112280711
back from client event poll after 59 usecs
client event poll on 17 for qjackctl starts at 112280788
back from client event poll after 56 usecs
client event poll on 17 for qjackctl starts at 112280861
back from client event poll after 54 usecs
client event poll on 17 for qjackctl starts at 112280932
back from client event poll after 52 usecs
client event poll on 17 for qjackctl starts at 112281001
back from client event poll after 79 usecs
client event poll on 17 for qjackctl starts at 112281097
back from client event poll after 53 usecs
client event poll on 17 for qjackctl starts at 112281167
back from client event poll after 52 usecs
23:06:13.901 JACK connection graph change.
23:06:13.946 JACK connection change.
jack main caught signal 12
starting server engine shutdown
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 697578.000 usecs
max delay reported by backend: 697578.000 usecs
freeing engine shared memory
max usecs: 547.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
no message buffer overruns
23:06:14.196 Shutdown notification.
23:06:14.197 JACK is stopping...
23:06:14.199 JACK is being forced...
zombified - calling shutdown handler
23:06:14.401 JACK was stopped successfully.
23:06:14.401 Post-shutdown script...
23:06:14.402 killall jackd
jackd: no process found
23:06:14.831 Post-shutdown script terminated with exit status=256.
```

---

### Post by WestCoastSuccess on 2010-05-19
Your problem looks very similar to the bug [here]("http://trac.jackaudio.org/ticket/179") filed 3 days ago on the JACK bug tracking site.

Here are some things that occur to me:

- we use an older version of JACK (0.109.2). I notice you're using 0.118.0. In the past we tried some newer versions of JACK with poor results and had to downgrade.

- likewise Freebob/FFADO. I can't tell what version you're using, except to notice that you're using the "firewire" driver and we're using the old "freebob" driver. Do you have an option for "freebob" in the qjackctl settings? We tried FFADO in the past with poor results.

- do you have a check mark in the "real time" box in the qjackctl settings? It doesn't look like you do (our start up command as reported by qjackctl:

/usr/bin/jackd -v -R -P89 -t2000 -dfreebob -dhw:0 -r44100 -p32 -n3 -D

yours:

/usr/bin/jackd -v -P89 -u -dfirewire -dhw:0 -r44100 -p256 -n3

Note the absence of the "-R" flag, which is for real time).

- can you try starting qjackctl using sudo (ie: #sudo qjackctl)? If that makes it work, the problem is with your /etc/security/limits.conf.

- does your machine use frequency scaling on the CPU? If so, disable it as it can cause issues with JACK.

- try placing a check mark in the "no memory lock" box.

That's all I can think of at the moment - let me know if any of that helps.

---

### Post by ghostandmachine on 2010-05-19
> **WestCoastSuccess said:**
> Your problem looks very similar to the bug [here]("http://trac.jackaudio.org/ticket/179") filed 3 days ago on the JACK bug tracking site.

Here are some things that occur to me:

- we use an older version of JACK (0.109.2). I notice you're using 0.118.0. In the past we tried some newer versions of JACK with poor results and had to downgrade.

- likewise Freebob/FFADO. I can't tell what version you're using, except to notice that you're using the "firewire" driver and we're using the old "freebob" driver. Do you have an option for "freebob" in the qjackctl settings? We tried FFADO in the past with poor results.

- do you have a check mark in the "real time" box in the qjackctl settings? It doesn't look like you do (our start up command as reported by qjackctl:

/usr/bin/jackd -v -R -P89 -t2000 -dfreebob -dhw:0 -r44100 -p32 -n3 -D

yours:

/usr/bin/jackd -v -P89 -u -dfirewire -dhw:0 -r44100 -p256 -n3

Note the absence of the "-R" flag, which is for real time).

- can you try starting qjackctl using sudo (ie: #sudo qjackctl)? If that makes it work, the problem is with your /etc/security/limits.conf.

- does your machine use frequency scaling on the CPU? If so, disable it as it can cause issues with JACK.

- try placing a check mark in the "no memory lock" box.

That's all I can think of at the moment - let me know if any of that helps.


Real Time is Checked

When I try to run jackd using the "freebob" driver I get the error

```
jackd: unknown driver 'freebob'
```

I have jackd-firewire and libfreebob0 installed along with the libfreebob-dev.

On Hardy, I used the firewire driver instead of the freebob with no problems.

Running sudo qjackctl gives me the same errors.

Having a check mark next to "No memory lock" returns the same error.

In checking gconf-editor > apps > gnome-power-manager I don't see a cpu frequency so I'm guessing I'm not running it.

So I'm guessing the only way I can get this to work is to down grade everything that's jackd?


** Edit ** Just realized that I have no sound what so ever while running the real time kernel. The generic kernel plays sound just fine. alsamixer shows all the levels up and unmuted

---

### Post by trulan on 2010-05-20
To check your cpu frequency settings, either navigate you file manager to:
/sys/devices/system/cpu/cpu0/cpufreq/
Or, if you prefer a terminal, this line
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```will show you the available scaling governors.  (It will also tell you if your cpu does not support scaling.) This command
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```shows the current governor setting, and this one
```
sudo echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```will set the governor of cpu0 to "performance".  There's also cpu1 if you have a dual core and cpu's 2 and 3 for a quad core.

For running firewire, you really want your cpu set to performance.

I find it easiest to load the gnome CPU scaling panel applet - one for each CPU core - and control it that way.

Oh, and if you have no audio on your internal sound card, there has been an issue with HDA intel cards and the 2.6.31-rt kernel.  That should be unrelated to your firewire issue.

---

### Post by ghostandmachine on 2010-06-07
Ok,

So I added the CPU Frequencies to my menu panel and am running "performance".

Starting jackd, i now get this error

```
14:15:05.330 Patchbay deactivated.
14:15:05.341 Statistics reset.
14:15:05.467 ALSA connection graph change.
14:15:05.739 ALSA connection change.
14:15:07.146 Startup script...
14:15:07.148 artsshell -q terminate
sh: artsshell: not found
14:15:07.555 Startup script terminated with exit status=32512.
14:15:07.556 JACK is starting...
14:15:07.557 /usr/bin/jackd -v -P89 -m -dfirewire -dhw:0 -r44100 -p256 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2209206
14:15:07.570 JACK was started with PID=6509.
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: firewire_pcm, id = 1 type 1 @ 0x92aa280 fd = -1
new buffer size 256
libffado 2.0.0 built Mar 31 2010 14:47:42
firewire MSG: Streaming thread running with Realtime scheduling, priority 89
firewire MSG: Registering audio capture port C0_dev0_LineIn 1+2 left
firewire MSG: Registering audio capture port C1_dev0_LineIn 1+2 right
firewire MSG: Registering audio capture port C2_dev0_SpdifIn 1+2 left
firewire MSG: Registering audio capture port C3_dev0_SpdifIn 1+2 right
firewire MSG: Registering audio playback port P0_dev0_LineOut 1+2 left
firewire MSG: Registering audio playback port P1_dev0_LineOut 1+2 right
firewire MSG: Registering audio playback port P2_dev0_SpdifOut 1+2 left
firewire MSG: Registering audio playback port P3_dev0_SpdifOut 1+2 right
registered port system:capture_1, offset = 1024
registered port system:capture_2, offset = 2048
registered port system:capture_3, offset = 3072
registered port system:capture_4, offset = 4096
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 1
client firewire_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
14:15:09.623 Server configuration saved to "/home/eric/.jackdrc".
14:15:09.626 Statistics reset.
14:15:09.628 Client activated.
14:15:09.630 JACK connection change.
14:15:09.646 JACK connection graph change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb7858000 fd = 16
start poll on 4 fd's
server thread back from poll
new client qjackctl using 17 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 1
client firewire_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 17 for qjackctl starts at 1055962305
back from client event poll after 15 usecs
client qjackctl: wait_fd=13, execution_order=1 (last client).
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
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver
server thread back from poll
unloading driver
client event poll on 17 for qjackctl starts at 1058019181
back from client event poll after 32 usecs
client event poll on 17 for qjackctl starts at 1058020061
back from client event poll after 34 usecs
client event poll on 17 for qjackctl starts at 1058020203
back from client event poll after 12 usecs
client event poll on 17 for qjackctl starts at 1058020259
back from client event poll after 11 usecs
client event poll on 17 for qjackctl starts at 1058020313
back from client event poll after 11 usecs
client event poll on 17 for qjackctl starts at 1058020365
back from client event poll after 11 usecs
client event poll on 17 for qjackctl starts at 1058020416
back from client event poll after 11 usecs
client event poll on 17 for qjackctl starts at 1058020468
back from client event poll after 11 usecs
14:15:11.700 JACK connection graph change.
no message buffer overruns
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
14:15:12.029 Client deactivated.
cannot continue execution of the processing graph
14:15:12.031 JACK was stopped successfully.
14:15:12.032 Post-shutdown script...
14:15:12.033 killall jackd
 (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
14:15:12.497 Post-shutdown script terminated with exit status=256.
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
cannot continue execution of the processing graph (Resource temporarily unavailable)
jackd: no process found

```

then rerunning jackd is giving a different set of errors

```
14:17:52.340 Startup script...
14:17:52.341 artsshell -q terminate
sh: artsshell: not found
14:17:52.744 Startup script terminated with exit status=32512.
14:17:52.747 JACK is starting...
14:17:52.748 /usr/bin/jackd -v -P89 -m -dfirewire -dhw:0 -r44100 -p256 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2209206
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
14:17:52.800 JACK was started with PID=6620.
no message buffer overruns
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
new client: firewire_pcm, id = 1 type 1 @ 0x8b2a280 fd = -1
new buffer size 256
libffado 2.0.0 built Mar 31 2010 14:47:42
firewire MSG: Streaming thread running with Realtime scheduling, priority 89
firewire MSG: Registering audio capture port C0_dev0_LineIn 1+2 left
firewire MSG: Registering audio capture port C1_dev0_LineIn 1+2 right
firewire MSG: Registering audio capture port C2_dev0_SpdifIn 1+2 left
firewire MSG: Registering audio capture port C3_dev0_SpdifIn 1+2 right
registered port system:capture_1, offset = 1024
registered port system:capture_2, offset = 2048
registered port system:capture_3, offset = 3072
firewire MSG: Registering audio playback port P0_dev0_LineOut 1+2 left
firewire MSG: Registering audio playback port P1_dev0_LineOut 1+2 right
firewire MSG: Registering audio playback port P2_dev0_SpdifOut 1+2 left
firewire MSG: Registering audio playback port P3_dev0_SpdifOut 1+2 right
registered port system:capture_4, offset = 4096
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 1
client firewire_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
14:17:54.874 Server configuration saved to "/home/eric/.jackdrc".
14:17:54.875 Statistics reset.
14:17:54.878 Client activated.
14:17:54.880 JACK connection change.
14:17:54.895 JACK connection graph change.
server thread back from poll
new client: qjackctl, id = 2 type 2 @ 0xb7823000 fd = 16
start poll on 4 fd's
server thread back from poll
new client qjackctl using 17 for events
start poll on 4 fd's
server thread back from poll
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now firewire_pcm active ? 1
client firewire_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 17 for qjackctl starts at 1221211699
back from client event poll after 13 usecs
client qjackctl: wait_fd=13, execution_order=1 (last client).
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
6620 waiting for signals
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
load = 2.3260 max usecs: 270.000, spare = 5534.000
load = 3.3598 max usecs: 255.000, spare = 5549.000
load = 4.1782 max usecs: 290.000, spare = 5514.000
load = 4.2514 max usecs: 251.000, spare = 5553.000
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
stopping driver
14:18:01.690 JACK connection graph change.
detaching driver
client event poll on 17 for qjackctl starts at 1228023710
back from client event poll after 153 usecs
client event poll on 17 for qjackctl starts at 1228023881
back from client event poll after 42 usecs
client event poll on 17 for qjackctl starts at 1228023939
back from client event poll after 33 usecs
client event poll on 17 for qjackctl starts at 1228023986
back from client event poll after 69 usecs
client event poll on 17 for qjackctl starts at 1228024071
back from client event poll after 33 usecs
client event poll on 17 for qjackctl starts at 1228024118
back from client event poll after 33 usecs
client event poll on 17 for qjackctl starts at 1228024164
back from client event poll after 33 usecs
client event poll on 17 for qjackctl starts at 1228024212
back from client event poll after 45 usecs
14:18:01.705 Shutdown notification.
14:18:01.708 JACK is stopping...
14:18:01.711 JACK is being forced...
jack main caught signal 12
starting server engine shutdown
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 290.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
no message buffer overruns
zombified - calling shutdown handler
14:18:01.913 JACK was stopped successfully.
14:18:01.914 Post-shutdown script...
14:18:01.915 killall jackd
jackd: no process found
14:18:02.326 Post-shutdown script terminated with exit status=256.

```

I've read that running a 64bit system would help solve these errors (i'm running a 32bit)

Would that help fix these issues if and when I can even run a 64bit system?

---

### Post by AutoStatic on 2010-06-09
ghostandmachine, did you do a clean install of Lucid or did you do an upgrade?
And try lowering JACK's priority. 89 is too high, JACK's max. priority should be below 80 afaik.

---

### Post by WestCoastSuccess on 2010-06-09
Priority 89 is fine - we've been running with that for 2 years, rock solid.

The error begins with:

> firewire ERR: Could not start streaming threads: -1

Can you please post the output of lsmod (ie: open a terminal and type "lsmod" without the quotes and hit enter)?

---

### Post by AutoStatic on 2010-06-09
89 is too high. See: [http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)
Paragraph on Audio setup:
> We can (albeit oversimplifying) say that the higher the priority of a task the more likely it is to run undisturbed. With -rt kernels we have the option of making IRQ handlers run with a lower priority than certain user space applications. It is, for example, possible to run jackd with a priority greater then all IRQ’s which might disturb audio operation (like disk or network). We need the jackd -P switch for that.

Also the [FFADO website]("http://subversion.ffado.org/wiki/IrqPriorities") provides some insight:
> On a real-time kernel (one that includes the RT patches and has the CONFIG_PREEMPT_RT option enabled), all interrupt handler top halves run SCHED_FIFO, with a priority of 50 by default. To ensure glitch-free audio, it is important that those responsible for audio operation have a higher priority than the others. Moreover, the jackd realtime threads should run at a priority higher than the standard IRQs but lower than the audio-related ones (use the -P option to set it accordingly, or the "Priority" value in qjackctl).

In a default -rt kernel all IRQ handler threads have default priorities in the range of 40-60, so making jackd run with a priority of 70 is a good choice here.

If you run jackd with a prio above 80 it might get in the way of the prio assigned to the IRQ of the soundcard. And you really don't want that. So jackd should run max. 70, also because jackd's watchdog runs prio 10 higher, so ends up at 80.

---

### Post by ghostandmachine on 2010-06-10
@audiostatic

I started with an upgrade. Well sort of. What happened is I had my /home dir on a seperate drive. So when I copied everything back over from my external hdd, I had a feeling that all of my old config files were destroying my system.

So I just did a clean "clean" install of Lucid. Below shows my print of lsmod

```

eric@ubuntu:~$ lsmod 
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51914  1 
fbcon                  35102  73 
snd_usb_audio          75765  1 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_usb_lib            15658  1 snd_usb_audio
bitblit                 4707  1 fbcon
arc4                    1153  2 
softcursor              1189  1 bitblit
snd_hda_intel          21877  2 
usblp                  10481  0 
snd_seq_dummy           1338  0 
vga16fb                11385  0 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_seq_oss            26726  0 
vgastate                8961  1 vga16fb
ath5k                 121792  0 
snd_seq_midi            4557  0 
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
mac80211              204922  1 ath5k
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
nouveau               467048  3 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ath                     7611  1 ath5k
ttm                    49943  1 nouveau
snd_pcm                70662  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq                47263  10 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              126485  3 ath5k,mac80211,ath
drm_kms_helper         29297  1 nouveau
led_class               2864  1 ath5k
snd_timer              19098  2 snd_pcm,snd_seq
usb_storage            39425  1 
drm                   162471  4 nouveau,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
k8temp                  3024  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             5199  0 
dv1394                 15275  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 nouveau
snd                    54148  21 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
lp                      7028  0 
parport                32635  2 ppdev,lp
uvcvideo               56990  0 
raw1394                22271  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
joydev                  8708  0 
psmouse                63245  0 
serio_raw               3978  0 
dell_wmi                1793  0 
dcdbas                  5422  0 
b44                    25542  0 
ohci1394               26950  1 dv1394
usbhid                 36110  0 
hid                    67032  1 usbhid
ssb                    37336  1 b44
ieee1394               81181  3 dv1394,raw1394,ohci1394
mii                     4381  1 b44
sata_nv                19440  2 

```

When I did a fresh install, I still don't have a rt kernel. Do I just do a sudo apt-get install linux-headers-rt or is there a better way?


***Edit*** I also tried to put the priority down below 80 and I'm still getting that same errors.

---

### Post by AutoStatic on 2010-06-10
> **ghostandmachine said:**
> When I did a fresh install, I still don't have a rt kernel. Do I just do a sudo apt-get install linux-headers-rt or is there a better way?No, it's better to install the **linux-rt** meta-package. And you could also use Synaptic for that if you prefer the GUI way.
lsmod output looks good, the raw1394 module is loaded so when the permissions are set properly you should be able to use the Firewire card.


> **ghostandmachine said:**
> ***Edit*** I also tried to put the priority down below 80 and I'm still getting that same errors.Was that on your old upgraded installation or on your fresh install? I assume that this is about your old upgraded install.

---

### Post by ghostandmachine on 2010-06-11
> **AutoStatic said:**
> 
Was that on your old upgraded installation or on your fresh install? I assume that this is about your old upgraded install.

It's was on both. 

When I was running Hardy the priority was set to 89. With the upgrade I tried using below 80 I received errors and with the fresh install I received the same errors as well.

---

### Post by AutoStatic on 2010-06-11
So you still get this particular error:
```
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
stopping driver

```

Could you post the outcome of the terminal command **cat /proc/interrupts** ?

---

### Post by sinnet on 2010-06-13
While I make this post, I am listening to Chopin - Nocturne in E-Flat Major, Op. 55 using Ubuntu 10.4 with a M-Audio Firewire Solo interface, ffado drivers, VLC player with Jack plugin and is working pretty well.

Hopefully the suggestions I make in this thread I started can help you guys: [http://ubuntuforums.org/showthread.php?t=1508531](http://ubuntuforums.org/showthread.php?t=1508531)

Cheers

---

