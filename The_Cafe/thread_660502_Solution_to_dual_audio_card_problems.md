---
title: "Solution to dual audio card problems"
date: 2008-01-06
forum: The Cafe
---

### Post by Lostincyberspace on 2008-01-06
I got this link from a friend it has the ability to merge sound cards into one (through software not hardware). it also has a lot of other things that are good about it check it out.

[http://pulseaudio.org/wiki](http://pulseaudio.org/wiki)

You can also install it through synaptic and apt-get

```
sudo apt-get install pulseaudio*
```

There are some plugins too that are easiest to get through synaptic since you can search for them.

You can also change the audio output levels for individual applications and much more.

---

### Post by ~LoKe on 2008-01-06
I had a bad experience with pulseaudio when I tried it a while back.  It messed up TeamSpeak and I couldn't fix it even after removing all pulseaudio packages.  But now that I don't use TS, I think I might give it a shot.

---

### Post by Lostincyberspace on 2008-01-06
I have had no problems the 20 or so minutes I have used it.

---

### Post by ~LoKe on 2008-01-06
That didn't take long.

> [22:05:40 loke]$ sudo pulseaudio
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: socket-server.c: socket(PF_INET6): Address family not supported by protocol
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-tcp" (argument: "auth-ip-acl=127.0.0.1;192.168.0.0/16"): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.
[~]

> [22:05:51 loke]$ pulseaudio
N: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
N: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
N: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

---

### Post by Lostincyberspace on 2008-01-06
It should be running already 
>  E: pid.c: Daemon already running.
go into synaptic and do a search for pulseaudio and you will find the GUIs there and the plugins you will need for most things. I had the same problem but I figured it out in about 30 secs when I go the same thing twice after doing the extra installs

---

### Post by ~LoKe on 2008-01-06
Sure, it's running, but it ain't workin'. ;)

I set up MPD to use pulse, and it won't even play.  I used mplayer -ao pulse file.avi and it's playing through my headphones.  Grrr!  What's the command for the gui? (I'm not using a WM/DE with menus, so it needs to be something I can launch from the terminal).

---

### Post by Lostincyberspace on 2008-01-06
Do you have the gstreamer plugins you need them I will et the package names for you

but the manager is 
paman

preferences is
paprefs

Volume control
pavucontrol

Volume meter
pavumeter

I will post again with the packages

---

### Post by ~LoKe on 2008-01-06
No output devices listed in paman, pavucontrol segfaults on me. ;)

Maybe I'll just install gnome and try to mess with the GUI's there.  I had it working before (if only for a short while).

---

### Post by Lostincyberspace on 2008-01-06
Here is a screen shot of synaptic with all the packages I have installed for it.
[http://s262.photobucket.com/albums/ii97/lostinbrave/?action=view&current=packagesforpulseaudio.png](http://s262.photobucket.com/albums/ii97/lostinbrave/?action=view&current=packagesforpulseaudio.png)

It should be easily readable and should only have to type the names of what you want to use there.

---

### Post by ~LoKe on 2008-01-06
Thanks!  I'll check to make sure I have all those, but I did a search for pulseaudio in synaptic and installed everything.  Gonna try in gnome.

---

### Post by Lostincyberspace on 2008-01-06
Try the programs again it should work now.

---

### Post by ~LoKe on 2008-01-06
Still no devices nor sinks, and I have all the packages.  Perhaps I screwed up/forgot to do something with the configuration file.

---

### Post by ~LoKe on 2008-01-06
Not sure what I did, but...
> [23:13:15 loke]$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

---

### Post by Lostincyberspace on 2008-01-06
Start amarok or something and see if it plays

I am right now trying to figure out why it wont play sound from smplayer.

---

### Post by Lostincyberspace on 2008-01-06
What programs are you having problems with? `loke

---

### Post by ~LoKe on 2008-01-06
> **Lostincyberspace said:**
> What programs are you having problems with? `loke

All of them? :P

I have no sound through pulse, simply because it won't connect.  paman says "connection refused", so I can't use it at all.

---

### Post by Lostincyberspace on 2008-01-06
Thats weird it works fine here now that I got the smplayer problem figured out.

I don't know enough to help you out sorry only been using it since I started the post.

---

### Post by ~LoKe on 2008-01-06
Hm...could you paste here your /etc/pulse/client.conf?

---

### Post by Lostincyberspace on 2008-01-06
```
# $Id: client.conf.in 1285 2006-08-19 01:18:57Z lennart $
#
# This file is part of PulseAudio.
#
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

## Configuration file for pulseaudio clients. Default values are
## commented out.  Use either ; or # for commenting

## Path to the pulseaudio daemon to run when autospawning.
; daemon-binary = /usr/bin/pulseaudio

## Extra arguments to pass to the pulseaudio daemon
; extra-arguments = --log-target=syslog --exit-idle-time=5

## The default sink to connect to
; default-sink = 

## The default source to connect to
; default-source =

## The default sever to connect to
; default-server =

## Autospawn daemons?
; autospawn = 0

### Cookie file
; cookie-file = 

### Disable shared memory data transfer
; disable-shm = 0

```

This might not do any thing I don't know.

---

### Post by ~LoKe on 2008-01-06
How about /etc/pulse/default.pa, as well?  (And anything else in /etc/pulse, I seem to have removed it. :D)

---

### Post by Lostincyberspace on 2008-01-07
Here are the two other files

daemon.conf

```
# $Id: daemon.conf.in 1287 2006-08-19 01:20:40Z lennart $
#
# This file is part of PulseAudio.
#
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

## Configuration file for the pulseaudio daemon. Default values are
## commented out.  Use either ; or # for commenting

# Extra verbositiy
; verbose = 0

## Daemonize after startup
; daemonize = 0

## Quit if startup fails
; fail = 1

## Renice the daemon to level -15 and try to get SCHED_FIFO
## scheduling. This a good idea if you hear annyoing noise in the
## playback. However, this is a certain security issue, since it works 
## when called SUID root only. root is dropped immediately after gaining
## the nice level and SCHED_FIFO scheduling on startup.
; high-priority = 0

## Disallow module loading after startup
; disallow-module-loading = 0

## Terminate the daemon after the last client quit and this time
## passed. Use a negative value to disable this feature.
; exit-idle-time = -1

## Unload autoloaded modules after being idle for this time 
; module-idle-time = 20

## Unload autoloaded sample cache entries after being idle for this time 
; scache-idle-time = 20

## The path were to look for dynamic shared objects (DSOs aka
## plugins).  You may specify more than one path seperated by
## colons. 
; dl-search-path = /usr/lib/pulse-0.9/modules/

## The default script file to load. Specify an empty string for not
## loading a default script file. The 
; default-script-file = 

## The default log target. Use either "stderr", "syslog" or
## "auto". The latter is equivalent to "sylog" in case daemonize is
## true, otherwise to "stderr".
; log-target = auto

## The resampling algorithm to use. Use one of src-sinc-best-quality,
## src-sinc-medium-quality, src-sinc-fastest, src-zero-order-hold,
## src-linear, trivial. See the documentation of libsamplerate for an
## explanation for the different methods. The method 'trivial' is the
## only algorithm implemented without usage of floating point
## numbers. If you're tight on CPU consider using this. On the other
## hand it has the worst quality of all.
; resample-method = sinc-fastest

## Create a PID file in /tmp/pulseaudio-$USER/pid. Of this is enabled
## you may use commands like "pulseaudio --kill" or "pulseaudio
## --check". If you are planning to start more than one pulseaudio
## process per user, you better disable this option since it
## effectively disables multiple instances.
; use-pid-file = 1

## Do not install the CPU load limit, even on platforms where it is
## supported. This option is useful when debugging/profiling 
## PulseAudio to disable disturbing SIGXCPU signals.
; no-cpu-limit = 0

## Run the daemon as system-wide instance, requires root priviliges
; system-instance = 0

## Resource limits, see getrlimit(2) for more information
; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 200
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = 25

## Disable shared memory data transfer 
; disable-shm = 0

```

default.pa
```

#!/usr/bin/pulseaudio -nF 

#
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


### Load audio drivers statically
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

.ifexists /usr/lib/pulse-0.9/modules/module-hal-detect.so

### Automatically load driver modules depending on the hardware available
load-module module-hal-detect

.else

### Alternatively use the static hardware detection module (for systems that
### lack HAL support
load-module module-detect

.endif

### Load audio drivers automatically on access
#add-autoload-sink output module-oss device="/dev/dsp" sink_name=output source_name=input
#add-autoload-source input module-oss device="/dev/dsp" sink_name=output source_name=input
#add-autoload-sink output module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#add-autoload-source input module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#add-autoload-sink output module-alsa-sink sink_name=output
#add-autoload-source input module-alsa-source source_name=input

.ifexists /usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so

### Load esound protocol
load-module module-esound-protocol-unix

.endif

### Load native protocol
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make some devices default
#set-default-sink output
#set-default-source input

.nofail

### Load something to the sample cache
load-sample x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-dir-lazy /usr/share/sounds/*.wav

### Load X11 bell module
load-module module-x11-bell sample=x11-bell

### Publish connection data in the X11 root window
load-module module-x11-publish

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
load-module module-gconf


```

I hope this helps.

---

### Post by ~LoKe on 2008-01-07
Woot!  It connects now, but I can't get it to find my audio device.

---

### Post by Lostincyberspace on 2008-01-07
thank you for the thank you.

I have no other advice for you. I don't really know how it works yet.

---

### Post by ~LoKe on 2008-01-07
Score!  Pulse works, in mplayer at least, though the sound keeps skipping/freezing.  But it's progress!

---

### Post by Lostincyberspace on 2008-01-07
You need to set mplayer to use esd driver or something I think. I have to do that with Smplayer it messes up and doesn't play otherwise.

---

