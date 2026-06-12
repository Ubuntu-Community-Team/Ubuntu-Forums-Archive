---
title: "Sound issues (vague I know)"
date: 2015-02-20
forum: Ubuntu Studio
---

### Post by magicguitarman2 on 2015-02-20
Hi everyone,

I have a few things I need to find out about, having Googled the **** out of the internet. 

Here's my situation - I play guitar professionally but I have a loathing of windows and mac os so I use Linux. In the past I have been able to monitor the input on my sound card (M-audio 24/96) without latency and the listen to the rest of my system. Having used a practice amp for a number of years I'm now trying to downsize and go back to running everything through my speakers. Pulseaudio has decided I can only get down to about 1 second of delay now, which is of no use to me. Jackd works fine for listening to the guitar input, but I lose the ability to play Youtube videos, media players and TuxGuitar. Also, when quitting Jack, Pulseaudio doesn't come back to life anymore. 

I have tried a wide range of ideas and how-to guides with no success. I also play games in my (limited) spare time so using Jack 100% of the time is a last resort for me.

Please give me some tips, ideas, starting points, obvious things that are staring me in the face etc. I would hate to have to go back to Windows after all these years.

Thanks!

---

### Post by marseille2 on 2015-02-20
To watch Youtube, etc. while using jackd ... we have to **route pulseaudio through jackd**. To do that, these modules have to load:

 
[LIST]
[*]module-jack-sink 
[*]module-jack-source 
[/LIST]


For me, both would randomly disappear -- after a fresh December install of UbuntuStudio 14.04. But they  can be loaded (to act right), with the **pactl** command (*see this [post]("http://ubuntuforums.org/showthread.php?t=2261067&p=13208822#post13208822") for directions, and note that pulseaudio has to be on for it to work ... if it's not, see the Reset directions at the end*).[INDENT]*Side note: I think I saw an update to these modules under Trusty Updates, but double-check.*
[/INDENT]
 

In addition, make sure these settings are checked in **Qjacktl**, under the "**Misc**" tab. 

```
Qjacktl >> Settings (window) >> Misc (tab)


[LIST]
[*]Enable ALSA sequencer support 
[*]Enable D-Bus interface 
[*]Stop Jack audio server on application exit 
[/LIST]

```


[SIZE=5]Module Check[/SIZE]

I'm assuming module-jack-sink and module-jack-source are installed (*can't remember if they're in ubuntustudio by default*), but you can check by seeing the **list** of **every module** like this:

```
$ pulseaudio --dump-modules
```

If they're not there, install them.

To see more about what the modules are doing, issue the **pacmd** command (*pulseaudio has to be on for it to work*):

```
$ pacmd
```

**It's interactive** so, you'll see a prompt like this: **>>>**  .... After the prompt, type "list-modules". It should look like this:

```
>>> list-modules
```

Close the pacmd command with these keys:

```
CTRL + C
```


[SIZE=5]Latency[/SIZE]

As for latency ... I think talking to the veterans on #ubuntustudio IRC can give you the best advice for your system. But generally speaking, without knowing anything about your system or the kernel you're running ... Start by making sure you're using the low-latency kernel.

> $ uname -a

If the low-latency kernel is already in use, the next step is to verify and/or adjust your settings in **Qjacktl**. Make sure the "**Realtime**" box is checked. Then it's up to you to decide your sample and bit rate, and -- most importantly -- set the **Frames/Period** (*the lower we can get this setting the better the playback ... but it depends on your system's power. If the system can't handle it, XRUNS start and then ugly drop-outs happen during recording*).

```
Qjacktl > Settings (window) > Realtime (checkmark); Frames Period (choose between 16 - 4096) 
```

The most commonly recommended Qjacktl settings are:


[LIST]
[*]Realtime 
[*]Force 16-bit 
[*]Frames/Period 1024 
[/LIST]

But personally, I think there's still too much latency for recording audio ... so I lower the Frames/Period to the lowest my system can deal with.


----

[COLOR=#ff0000] P.S. If you've done all this -- load modules, and set Qjacktl -- but you still don't have pulseaudio, or Jackd is acting weird ... You might need to [/COLOR]**reset**[COLOR=#ff0000]. If so, see the directions in this [/COLOR][[COLOR=#0000ff]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2265205&p=13228748#post13228748")[COLOR=#ff0000].[/COLOR]

---

### Post by magicguitarman2 on 2015-02-23
Hi there, thanks so much for the reply. Sorry it's taken me so long to get back to you, family problems!

I have tried several guides with those pulse-audio jackd modules and I still have the same problem; Youtube (And vimeo/other internet players) and my local media players such as VLC and Clementine still refuse to play. The all load and respond normally but act as if paused on the first second of the song (or where ever in the songs timeline you place them). I have installed and loaded the modules again and it's still the same. PACMD gives me the following output:

```
xxx@xxx:~$ pacmdWelcome to PulseAudio! Use "help" for usage information.
>>> list-modules
26 module(s) loaded.
    index: 0
    name: <module-device-restore>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "4.0"
    index: 1
    name: <module-stream-restore>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "4.0"
    index: 2
    name: <module-card-restore>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "4.0"
    index: 3
    name: <module-augment-properties>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "4.0"
    index: 4
    name: <module-switch-on-port-available>
    argument: <>
    used: -1
    load once: no
    properties:
        
    index: 5
    name: <module-alsa-card>
    argument: <device_id="0" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1">
    used: 0
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "4.0"
    index: 6
    name: <module-alsa-card>
    argument: <device_id="1" name="pci-0000_05_01.0" card_name="alsa_card.pci-0000_05_01.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1">
    used: 2
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "4.0"
    index: 7
    name: <module-udev-detect>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "4.0"
    index: 8
    name: <module-native-protocol-unix>
    argument: <>
    used: -1
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "4.0"
    index: 9
    name: <module-default-device-restore>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "4.0"
    index: 10
    name: <module-rescue-streams>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
        module.version = "4.0"
    index: 11
    name: <module-always-sink>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "4.0"
    index: 12
    name: <module-intended-roles>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based of intended roles of devices"
        module.version = "4.0"
    index: 13
    name: <module-suspend-on-idle>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "4.0"
    index: 14
    name: <module-systemd-login>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each login session of this user"
        module.version = "4.0"
    index: 15
    name: <module-position-event-sounds>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "4.0"
    index: 16
    name: <module-filter-heuristics>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Colin Guthrie"
        module.description = "Detect when various filters are desirable"
        module.version = "4.0"
    index: 17
    name: <module-filter-apply>
    argument: <>
    used: -1
    load once: yes
    properties:
        module.author = "Colin Guthrie"
        module.description = "Load filter sinks automatically when needed"
        module.version = "4.0"
    index: 18
    name: <module-loopback>
    argument: <>
    used: -1
    load once: no
    properties:
        module.author = "Pierre-Louis Bossart"
        module.description = "Loopback from source to sink"
        module.version = "4.0"
    index: 19
    name: <module-x11-publish>
    argument: <display=:0.0>
    used: -1
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "X11 credential publisher"
        module.version = "4.0"
    index: 20
    name: <module-x11-bell>
    argument: <display=:0.0 sample=bell.ogg>
    used: -1
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "X11 bell interceptor"
        module.version = "4.0"
    index: 21
    name: <module-x11-cork-request>
    argument: <display=:0.0>
    used: -1
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "Synthesize X11 media key events when cork/uncork is requested"
        module.version = "4.0"
    index: 22
    name: <module-x11-xsmp>
    argument: <display=:0.0 session_manager=local/harry-desktop:@/tmp/.ICE-unix/2177,unix/harry-desktop:/tmp/.ICE-unix/2177>
    used: -1
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "X11 session management"
        module.version = "4.0"
    index: 23
    name: <module-cli-protocol-unix>
    argument: <>
    used: -1
    load once: no
    properties:
        module.author = "Lennart Poettering"
        module.description = "Command line interface protocol (UNIX sockets)"
        module.version = "4.0"
    index: 24
    name: <module-jack-source>
    argument: <>
    used: 0
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "JACK Source"
        module.version = "4.0"
    index: 25
    name: <module-jack-sink>
    argument: <>
    used: 0
    load once: yes
    properties:
        module.author = "Lennart Poettering"
        module.description = "JACK Sink"
        module.version = "4.0"



```

As far as I can see the modules are loaded at the bottom there but haven't been used?

I am also still having the problem that I cannot shut Jack down without a full restart. Any more information I can post?

Latency, once I'm using Jack, isn't a problem by the way. It's pulseaudio using loopback that has the 1 sec minimum delay on it.

---

### Post by marseille2 on 2015-02-23
Maybe post the output of 

```
$ pulseaudio --vv
```


I just upgraded my **pulseaudio** **and** the **sinks**, last night. The **updates** (14.04) **just came out**, and I'm not having any issues so far. So maybe consider that, too. 

I haven't had the pulseaudio latency problem myself, but I saw that we can check if it's using realtime like this:

```
$ pulseaudio -vv --realtime
```

If it's not on, check to see if the right permissions are set ...(See [this old Jaunty thread]("http://ubuntuforums.org/archive/index.php/t-1142694.html"); *more on pulseaudio latency and ubuntu permissions [here]("http://askubuntu.com/questions/518867/delay-while-recording-piano-input/518876#518876")*). 


Mine looks like this:

```
$ pulseaudio -vv --realtime
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 4.0
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux x86_64 3.13.0-44-lowlatency #73-Ubuntu SMP PREEMPT Tue Dec 16 00:48:57 UTC 2014
D: [pulseaudio] main.c: Found 8 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is 6315264835761c6aea76276454e499a4.
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/av/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

JackAudio also gives an [example]("https://github.com/jackaudio/jackaudio.github.com/wiki/WalkThrough_User_PulseOnJack")* **~/.pulse/daemon.conf ***file:


 ```

default-sample-format = float32le
default-sample-rate = 48000
realtime-scheduling = yes
exit-idle-time = -1

```

[Man page]("http://manpages.ubuntu.com/manpages/oneiric/man5/pulse-daemon.conf.5.html") also says to, "note that the server also reads a configuration script on startup ***default.pa*** that also contains runtime configuration directives."


----

I'm probably not much help after this ... and since it gets slow in this forum (probably the Multimedia Forum or Ask Ubuntu is better to help us with Pulseaudio specifics) ... we can always do a verbose output of the PulseAudio log and post it to launchpad, to escalate these weird issues (*See [directions]("https://wiki.ubuntu.com/PulseAudio/Log")*).

---

### Post by magicguitarman2 on 2015-02-23
Here is the output. I can even seem to get an error message from anything. It all thinks it's working fine.

```
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permittedD: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 4.0
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux x86_64 3.13.0-44-lowlatency #73-Ubuntu SMP PREEMPT Tue Dec 16 00:48:57 UTC 2014
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimised build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is 73f48ece77c9674d4904c2a352f2c2df.
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/harry/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.



```

---

### Post by marseille2 on 2015-02-24
I'm at my wit's end here. Besides upgrading the modules, and doing the recent upgrade of pulseaudio... this is getting tricky. 

Assuming DBUS is checked in Qjacktl settings (has to be to use pulse and jackd together) ... The only other thing I can think of is to disable on-board [motherboard] audio in the bios, and see if that makes a difference by just using the audio interface. But you might've done that anyway. So personally, I would escalate the issue in a more visible spot, and also try to catch one of the gurus on IRC at #ubuntustudio or [#opensourcemusicians]("http://webchat.freenode.net/?nick=OSMGuest.&channels=opensourcemusicians") ... I was told the latter channel is much more active.

EDIT: Be sure to check the [bug lists]("http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Community/") at PA. They say first check the list of [broken ALSA sound drivers]("http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/BrokenDrivers/") (which includes complaints about PA latency problems) before filing a report... and also give instructions how to do that for ubuntu. 

I'm sorry I can't be of much more help -- pulseaudio is a shared nightmare :lolflag: -- but if you do find out how to resolve this ... please share the solution!

---

### Post by magicguitarman2 on 2015-02-25
I didn't get any response in any of the IRC channels that I tried, so it's a system reinstall just now, and then onwards. Clean slate and all! I'll post a solution if I find one.

Thanks for your help!

---

