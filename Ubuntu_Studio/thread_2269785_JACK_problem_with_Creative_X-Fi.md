---
title: "JACK problem with Creative X-Fi"
date: 2015-03-18
forum: Ubuntu Studio
---

### Post by thorvi2008 on 2015-03-18
I have an external card SoundBlaster X-Fi Surround 5.1 and I'm trying to set it working with JACK in Ubuntu Studio. I want it to work as stereo (instead of 5.1 system).
PulseAudio has no problem with setting output card as SoundBlaster and everything works properly. However, no matter how I configure JACK (using QJackCtl) it directs audio to HDA Intel (build in speakers).

I've tried doing this:
[http://docs.fedoraproject.org/en-US/Fedora/15/html/Musicians_Guide/sect-Musicians_Guide-Integrating_PulseAudio_with_JACK.html](http://docs.fedoraproject.org/en-US/Fedora/15/html/Musicians_Guide/sect-Musicians_Guide-Integrating_PulseAudio_with_JACK.html)
And the only difference is that now PulseAudio is redirected to JACK, but I can't direct JACK to my SoundBlaster, instead of HDA Intel.

How can I set up JACK to work with my external soundcard, so I could use its output and inputs?

---

### Post by marseille2 on 2015-03-18
Qjacktl doesn't work that well for me either. It's good for connections, but I can't set jackd from it on-the-fly. So first make sure jackd and jackdbus are killed, then reset jackd from the command line. (See this how-to [example]("http://ubuntuforums.org/showthread.php?t=2268419&p=13242367#post13242367") -... it's the same procedure). 


If that's not enough, you probably have to reset (see this [post]("http://ubuntuforums.org/showthread.php?t=2265205&p=13228748#post13228748")), and reboot. 


If it gets trickier than that, you could also try setting the card as the default alsa sink in pulseaudio's default.pa (See this [example]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Set_default_input_sources")). Anything worse probably means disabling onboard audio in the bios (this is also one of the easier way outs), then try to start debugging.

---

### Post by thorvi2008 on 2015-03-18
Unfortunately, none of these solutions worked for me...
First two resulted in error while trying to run jackd, third didn't change anything, and my bios doesn't have option for disabling onboard audio card.

here's the result of commands:

[FONT=courier new]azv@azv:~$ killall jackdbus jackd
[/FONT][FONT=courier new]azv@azv:~$ cat /proc/asound/cards[/FONT]
[FONT=courier new] 0 [MID            ]: HDA-Intel - HDA Intel MID[/FONT]
[FONT=courier new]                      HDA Intel MID at 0xf4c00000 irq 43[/FONT]
[FONT=courier new] 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI[/FONT]
[FONT=courier new]                      HDA ATI HDMI at 0xf0040000 irq 45
[/FONT][FONT=courier new] 2 [S51            ]: USB-Audio - SB X-Fi Surround 5.1[/FONT]
[FONT=courier new]                      Creative Technology SB X-Fi Surround 5.1 at usb-0000:00:1a.0-1.2, full speed[/FONT]

[FONT=courier new]
[/FONT]
[FONT=courier new]azv@azv:~$ jackd --realtime -d alsa -r441000 -C hw:2 -P hw:2[/FONT]
[FONT=courier new]jackdmp 1.9.10[/FONT]
[FONT=courier new]Copyright 2001-2005 Paul Davis and others.[/FONT]
[FONT=courier new]Copyright 2004-2013 Grame.[/FONT]
[FONT=courier new]jackdmp comes with ABSOLUTELY NO WARRANTY[/FONT]
[FONT=courier new]This is free software, and you are welcome to redistribute it[/FONT]
[FONT=courier new]under certain conditions; see the file COPYING for details[/FONT]
[FONT=courier new]no message buffer overruns[/FONT]
[FONT=courier new]no message buffer overruns[/FONT]
[FONT=courier new]no message buffer overruns[/FONT]
[FONT=courier new]JACK server starting in realtime mode with priority 10[/FONT]
[FONT=courier new]audio_reservation_init[/FONT]
[FONT=courier new]Acquire audio card Audio1[/FONT]
[FONT=courier new]creating alsa driver ... hw:1|hw:1|1024|2|441000|0|0|nomon|swmeter|-|32bit[/FONT]
[FONT=courier new]configuring for 441000Hz, period = 1024 frames (2.3 ms), buffer = 2 periods[/FONT]
[FONT=courier new]ALSA: final selected sample format for capture: 24bit little-endian[/FONT]
[FONT=courier new]ALSA: use 2 periods for capture[/FONT]
[FONT=courier new]ALSA: final selected sample format for playback: 24bit little-endian[/FONT]
[FONT=courier new]ALSA: use 2 periods for playback[/FONT]
[FONT=courier new]ALSA: cannot set hardware parameters for playback
ALSA: configure playback channel[/FONT]
[FONT=courier new]Cannot start driver[/FONT]
[FONT=courier new]JackServer::Open failed with -1[/FONT]
[FONT=courier new]Failed to start server

[/FONT]Doed anybody have any ideas how to make it work? :(

---

### Post by marseille2 on 2015-03-18
[SIZE=5]Pulseaudio 2 Channel Set-Up[/SIZE]

Force pulseaudio to use a 2-channel set-up edit daemon.conf. From ubuntu help pages: 

Remove the semicolon at the start of the line and change the line according to your surround sound configuration (see [more]("https://help.ubuntu.com/community/SurroundSound")): 


[LIST]
[*]For 2.0 channel sound: **default-sample-channels = 2** 
[*]For 4.0 channel sound: **default-sample-channels = 4** 
[*]For 5.0 channel sound: **default-sample-channels = 5** 
[*]For 5.1 channel sound: **default-sample-channels = 6** 
[*]For 7.1 channel sound: [B]default-sample-channels = 8

[/B] 
[/LIST]
Save the file the restart your computer. 

EXAMPLE: 

```
$ sudo gedit /etc/pulse/daemon.conf
```

> ; default-sample-format = s16le
; default-sample-rate = 44100
; alternate-sample-rate = 48000
**default-sample-channels = 2**
; default-channel-map = front-left,front-right

[SIZE=5] Troubleshooting Jackd[/SIZE]

Pulseaudio with Jackd can get really tricky, and getting them to play well together really depends on timing. So don't give up just yet. It may be that you have to be exacting, when it comes to *order* in trouble-shooting.

- Check to see if Pulseaudio is running (if the server is connected -- sound output works --, it's on. IMO, **pasystray** is the better than the default volume control for audio work, since it tells you what sinks you have up -- no guess work, and easier access).


- Check to see if Jackd and Jackdbus are running.


- Open Qjacktl and make sure the **settings** are how you want. 
[LIST]
[*]Set the correct card input/output, sample and bit rate, realtime or not, etc. 
[*]Set _midi driver_ to none. 
[*]Also, for pulseaudio to work, make sure dbus is checked, i.e. -- checkmark "_Enable D-Bus interface_". Turn it off if you only want Jackd -- this is the preference for dedicated audio). 
[*]Then quit the app. 
[*]Note: If you edit _/etc/pulse/default.pa_ to set the USB card as the default audio card, leave Qjacktl's input and output device fields as default. If you did not edit default.pa, confirm your preferred card number, and change it accordingly. 

Chances are... if you turn on the USB card **after** you log-in, it will always come up as the 3rd card (assuming you have only 3), since the kernel first recognizes onboard audio, then your HDMI card. 

BUT! If the USB card is plugged in **at boot** ... there's a chance it will come up as Card 2, if the kernel recognizes it before the HDMI card. ... That's what's happening with me after upgrading from 14.04 version 1 to version 2. (I'm guessing that a clean install of version 2 won't have this issue.) 
[/LIST]
 

- Kill jackd and jackdbus if they're on


- Delete: 

[LIST]
[*][COLOR=#333333][FONT=Arial]*all files* in .config/jackd[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=Arial]*qjacktl* file in .config/rnbc.org[/FONT][/COLOR] 
[/LIST]
[COLOR=#333333][FONT=Arial]

- Stop pulseaudio from autospawning.

[/FONT][/COLOR]```
[COLOR=#333333][FONT=Arial]**$ echo autospawn = no > $HOME/.config/pulse/client.conf**[/FONT][/COLOR]
```


- Delete Folder:
[LIST]
[*] [COLOR=#333333][FONT=Arial].config/pulse
[/FONT][/COLOR] 
[/LIST]
[COLOR=#333333][FONT=Arial]

- Reboot.


- Login.



Theoretically... this is the point when things should be back to the *default state*. You should be able to fire up ALSA audio apps (like Hydrogen or LMMS) without fiddling with jackd or Qjacktl ... but most likely *they will use the default audio card* -- card zero (0). If you already set the USB card to be the default card in  **/etc/pulse/default.pa**, they will use it. If not, you'll have to change the sink from pulseaudio's volume control... (the UI is bad here, so what appears to be a sound card label/title --at the right-- is actually a button). 


[COLOR=#333333][FONT=Arial] [SIZE=5] Default.pa[/SIZE][/FONT][/COLOR]


If changing the sink from volume control doesn't work, again... you may have to force pulseaudio to do what you want by editing /etc/pulse/default.pa. Since our systems are unique to our personal gear, IMO it's good to check out some examples and see what works, and what doesn't. Arch has a [page]("https://bbs.archlinux.org/viewtopic.php?id=181681") that gives a good idea where to start. But it's a good idea to read the man page, and see what you can find in Ubuntu community pages for: default.pa, daemon.conf, and read about pulseaudio's _pacmd_ interactive command. You never know if all you have to do is load a sink correctly.





[/FONT][/COLOR]

---

### Post by thorvi2008 on 2015-03-19
I did what you wrote above, but the result is:
I can now run Jack server and tell it to use my external sound card, which doesn't make any errors, but the output sound still goes through my onboard sound card.
However if I kill jackd and jackdbus and try to run jackd from terminal, I get error:

[COLOR=#000000][FONT=courier new]azv@azv:~$ jackd --realtime -d alsa -r441000 -C hw:2 -P hw:2[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]jackdmp 1.9.10[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]Copyright 2001-2005 Paul Davis and others.[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]Copyright 2004-2013 Grame.[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]jackdmp comes with ABSOLUTELY NO WARRANTY[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]This is free software, and you are welcome to redistribute it[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]under certain conditions; see the file COPYING for details[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]no message buffer overruns[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]no message buffer overruns[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]no message buffer overruns[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]JACK server starting in realtime mode with priority 10[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]audio_reservation_init[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]Failed to acquire device name : Audio2 error : Device reservation request with priority 2147483647 denied for "Audio2" via RequestRelease()[/FONT][/COLOR]
[FONT=courier new][COLOR=#000000]Audio device  hw:2 cannot be acquired...[/COLOR][/FONT]
[COLOR=#000000][FONT=courier new]Cannot initialize driver[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]JackServer::Open failed with -1[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]Failed to start server

[/FONT][/COLOR]Although sometimes it gives the same error as before.

---

### Post by marseille2 on 2015-03-19
Hmmm... there's a thread at Linuxmusicians with the same [issue]("http://linuxmusicians.com/viewtopic.php?f=27&t=11090"). It accuses pulseaudio, but apparently Jackdbus wasn't killed. To kill it they used:

```
 $ killall -9 jackdbus
```

I think this is why another old Ubuntu thread I saw a while back, said to issue this command twice ... 

```

$ killall jackdbus jackd
$ killall jackdbus jackd
```


If that doesn't solve it, you might want to post your /etc/pulse/daemon.conf, as well as the /etc/pulse/default.pa file ... and consider this [quote]("http://steve-conrad.com/blog/?p=45"):

[INDENT]"The trick is to get jack and PulseAudio working at the same time. If  pulse gets a lock on the soundcard before jackd has a chance, then Jack  won’t work. If PulseAudio tries to connect to a jack sink before jackd  is running it will fail."
[/INDENT]


PS: Another good option is to search for, and/or pose your problem on AskUbuntu.com. It's a pretty active sight, and they have some seriously good threads on pulseaudio.

---

### Post by thorvi2008 on 2015-03-21
My daemon.conf:

```
# This file is part of PulseAudio.#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.


## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.


; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no


; high-priority = yes
; nice-level = -11


; realtime-scheduling = yes
; realtime-priority = 5


; exit-idle-time = 20
; scache-idle-time = 20


; dl-search-path = (depends on architecture)


; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa


; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0


resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no


flat-volumes = no


; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000


; default-sample-format = s16le
; default-sample-rate = 44100
; alternate-sample-rate = 48000
default-sample-channels = 2
; default-channel-map = front-left,front-right


default-fragments = 8
default-fragment-size-msec = 10


; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0



```

And default.pa:

```
#!/usr/bin/pulseaudio -nF#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.


# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)


.nofail


### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav


.fail


### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore


### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties


### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available


### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-jack-sink
load-module module-jack-source


### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif


.ifexists module-android-audio-hal.so
load-module module-android-audio-hal
.endif


### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif


### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif


.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif


### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix


### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish


### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv


### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor


### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore


### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams


### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink


### Honour intended role device property
load-module module-intended-roles


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle


### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif


### Enable positioned event sounds
load-module module-position-event-sounds


### Cork music/video streams when a phone stream is active
#load-module module-role-cork


### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply


# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.


### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system


### Register ourselves in the X11 session manager
#load-module module-x11-xsmp


### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif


### Make some devices default
#set-default-sink output
#set-default-source input



```


I managed to redirect Pulse output to Jack, while leaving input as my external card. That way, when I load loopback module, I can use my external card's inputs with Jack. Of course, Jack output is still my onboard device which is not the best solution, but works temporarily...

---

### Post by marseille2 on 2015-03-23
It would be good to get other's input here, but just eyeballing the files, I would try to set the default sink and source (for your card / ALSA) in the default.pa, if you want to do a set-and-forget. Personally, I think is a good demo of how to it (see [Arch Linux]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Set_default_input_sources")). 

And since you're loading the jack-sinks on boot, that's something to consider when you map out how you're going to set up the cards. It might be easier to load the alsa sinks at the command line when you need them (see pacmd command in Arch Linux wiki link above). But it's really up to your own work-flow needs.

---

