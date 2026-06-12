---
title: "Latency compensation"
date: 2009-06-03
forum: Ubuntu Studio
---

### Post by dawiba on 2009-06-03
Okay, I'm going to have another go at UbuntuStudio this coming weekend.

What I'd like to know, if possible, is how can I compensate for latency when I'm recording audio?

This would apply if for example, I had Jack set to a high latency and couldn't reduce it.

Can anyone help?

---

### Post by thorgal on 2009-06-03
if you record in ardour, it will compensate the latency by realigning the wave form automatically, so you don't have to do anything there.

If you use software monitoring and play along some pre-existing tracks, or long hardware inserts, this is where latency issues arise and you need to compensate "manually". I believe there's a ladspa plugin where you can set the latency in number-of-frames so that the wave form is realigned by this amount. I also think you can declare a h/w latency in qjackctl\s setup window if you use some hardware insert chain and need to compensate for it. I never really tried that precisely since I use hardware monitoring when I record.

---

### Post by dawiba on 2009-06-04
Thanks Thorgal.

I normally use hardware monitoring (the Ardour default). However, when I deliberately set the latency to a high level, then there are timing issues. On my Mac, I can always do a quick check by looping the soundcard inputs to the outputs. Of course, it could be that I've suddenly forgotten how to play in time :)

Anyway, I see there's a program called Jack Delay which is supposed to measure latency, so I'll try that later on to see how it works.

The other part to my question, which I didn't ask first time, is how do I overcome midi latency? As I've said before, I like to record midi data and use that to trigger sounds in my keyboard. This has some inherent delay and I wondered how to advance the midi timing. The editor in Rosegarden shows the events not quite on the beat(s) but ever so slightly behind. It generally plays fine, so I guess there's some sort of compensation happening 'under the hood', but it looks weird because it doesn't line up with time divisions where it's supposed to. Again, on the Mac, I'll just open the relevant window and change the midi advance. Will Jack Delay help for this, or is there some midi utility that will help?

Many thanks.

---

### Post by thorgal on 2009-06-04
dawiba, have you tried to use jack_midi instead of ALSA midi ?

IIRC, paul Davis (ardour's author) has rewritten the a2jmidid that exposes ALSA seq MIDI ports to jack_midi, so that you benefit from jack's frame accurate sync'ing. It may be a bit experimental if you only rely on packaged softwares. Try to ask the jack-devel mailing list.

---

### Post by dawiba on 2009-06-04
Okay, I've downloaded a2jmidi and I've tried to install but get this after typing ./waf configure:

```
dawiba@dawiba-laptop:~$ cd a2jmidid-4
dawiba@dawiba-laptop:~/a2jmidid-4$ ./waf configure
Checking for program gcc : ok /usr/bin/gcc 
Checking for compiler version : ok 4.3.3 
Checking for program cpp : ok /usr/bin/cpp 
Checking for program ar : ok /usr/bin/ar 
Checking for program ranlib : ok /usr/bin/ranlib 
Checking for compiler could create programs : ok 
Checking for compiler could create shared libs : ok 
Checking for compiler could create static libs : ok 
Checking for flags -O2 : ok 
Checking for flags -g -DDEBUG : ok 
Checking for flags -g3 -O0 -DDEBUG : ok 
Checking for flags -Wall : ok 
Checking for gcc : ok 
Checking for package alsa : not found 
pkg-config cannot find alsa 
dawiba@dawiba-laptop:~/a2jmidid-4$ 
```

If I try to build next, I get this message:

```
dawiba@dawiba-laptop:~/a2jmidid-4$ ./waf
Project not configured (run 'waf configure' first) 
dawiba@dawiba-laptop:~/a2jmidid-4$ 

```
Any advice?

---

### Post by thorgal on 2009-06-04
check to see whether you have the package libasound-dev or something like that (search for libasound dev in e.g. synaptic).

---

### Post by thorgal on 2009-06-04
dawiba, try this one:

[http://jackaudio.org/files/midibridge-0.0.1.tar.bz2](http://jackaudio.org/files/midibridge-0.0.1.tar.bz2)

that's a2jmidid modified by Paul Davis.

---

### Post by dawiba on 2009-06-04
Thanks again Thorgal

I installed libasound (it was libasound-dev) but also had to install jack (libjack-dev I think it was). I also then had to install libdbus-1-dev to overcome another error.

I got these using Synaptic Package Manager after trying a couple of different ones to see which would allow the configure.

However..........

I did the configure using './waf configure' and then did the build using './waf'. Everything was fine until I came to install and got this

```


Configuration finished successfully; project is now ready to build. 
dawiba@dawiba-laptop:~/a2jmidid-4$ ./waf
[ 1/17] copy: org.gna.home.a2jmidid.service.in -> build/default/org.gna.home.a2jmidid.service
[ 2/17] cc: a2jmidid.c -> build/default/a2jmidid_1.o
[ 3/17] cc: log.c -> build/default/log_1.o
[ 4/17] cc: port.c -> build/default/port_1.o
[ 5/17] cc: port_thread.c -> build/default/port_thread_1.o
[ 6/17] cc: port_hash.c -> build/default/port_hash_1.o
[ 7/17] cc: dbus.c -> build/default/dbus_1.o
[ 8/17] cc: dbus_iface_introspectable.c -> build/default/dbus_iface_introspectable_1.o
[ 9/17] cc: dbus_iface_control.c -> build/default/dbus_iface_control_1.o
[10/17] cc: paths.c -> build/default/paths_1.o
[11/17] cc: jack.c -> build/default/jack_1.o
[12/17] cc: sigsegv.c -> build/default/sigsegv_1.o
[13/17] cc: a2jmidi_bridge.c -> build/default/a2jmidi_bridge_2.o
[14/17] cc: j2amidi_bridge.c -> build/default/j2amidi_bridge_3.o
[15/17] cc_link: build/default/a2jmidid_1.o build/default/log_1.o build/default/port_1.o build/default/port_thread_1.o build/default/port_hash_1.o build/default/dbus_1.o build/default/dbus_iface_introspectable_1.o build/default/dbus_iface_control_1.o build/default/paths_1.o build/default/jack_1.o build/default/sigsegv_1.o -> build/default/a2jmidid
[16/17] cc_link: build/default/a2jmidi_bridge_2.o -> build/default/a2jmidi_bridge
[17/17] cc_link: build/default/j2amidi_bridge_3.o -> build/default/j2amidi_bridge
Compilation finished successfully 
dawiba@dawiba-laptop:~/a2jmidid-4$ ./waf install
* installing a2j_control as /usr/local/bin/a2j_control
Could not install the file /usr/local/bin/a2j_control 
dawiba@dawiba-laptop:~/a2jmidid-4$ 
```

Once again, due to my ignorance of the workings of Linux, I'm stumped. Any ideas?

Thanks again

---

### Post by thorgal on 2009-06-04
```

sudo ./waf install

```

when you install to system directories, use sudo.

---

### Post by dawiba on 2009-06-04
Thanks again Thorgal

I installed libasound (it was libasound-dev) but also had to install jack (libjack-dev I think it was). I also then had to install libdbus-1-dev to overcome another error.

I got these using Synaptic Package Manager after trying a couple of different ones to see which would allow the configure.

However..........

I did the configure using './waf configure' and then did the build using './waf'. Everything was fine until I came to install and got this

```


Configuration finished successfully; project is now ready to build. 
dawiba@dawiba-laptop:~/a2jmidid-4$ ./waf
[ 1/17] copy: org.gna.home.a2jmidid.service.in -> build/default/org.gna.home.a2jmidid.service
[ 2/17] cc: a2jmidid.c -> build/default/a2jmidid_1.o
[ 3/17] cc: log.c -> build/default/log_1.o
[ 4/17] cc: port.c -> build/default/port_1.o
[ 5/17] cc: port_thread.c -> build/default/port_thread_1.o
[ 6/17] cc: port_hash.c -> build/default/port_hash_1.o
[ 7/17] cc: dbus.c -> build/default/dbus_1.o
[ 8/17] cc: dbus_iface_introspectable.c -> build/default/dbus_iface_introspectable_1.o
[ 9/17] cc: dbus_iface_control.c -> build/default/dbus_iface_control_1.o
[10/17] cc: paths.c -> build/default/paths_1.o
[11/17] cc: jack.c -> build/default/jack_1.o
[12/17] cc: sigsegv.c -> build/default/sigsegv_1.o
[13/17] cc: a2jmidi_bridge.c -> build/default/a2jmidi_bridge_2.o
[14/17] cc: j2amidi_bridge.c -> build/default/j2amidi_bridge_3.o
[15/17] cc_link: build/default/a2jmidid_1.o build/default/log_1.o build/default/port_1.o build/default/port_thread_1.o build/default/port_hash_1.o build/default/dbus_1.o build/default/dbus_iface_introspectable_1.o build/default/dbus_iface_control_1.o build/default/paths_1.o build/default/jack_1.o build/default/sigsegv_1.o -> build/default/a2jmidid
[16/17] cc_link: build/default/a2jmidi_bridge_2.o -> build/default/a2jmidi_bridge
[17/17] cc_link: build/default/j2amidi_bridge_3.o -> build/default/j2amidi_bridge
Compilation finished successfully 
dawiba@dawiba-laptop:~/a2jmidid-4$ ./waf install
* installing a2j_control as /usr/local/bin/a2j_control
Could not install the file /usr/local/bin/a2j_control 
dawiba@dawiba-laptop:~/a2jmidid-4$ 
```

Once again, due to my ignorance of the workings of Linux, I'm stumped. Any ideas?

Thanks again

---

