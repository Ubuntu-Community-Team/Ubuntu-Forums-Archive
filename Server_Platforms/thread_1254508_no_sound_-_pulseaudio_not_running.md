---
title: "no sound - pulseaudio not running?"
date: 2009-08-31
forum: Server Platforms
---

### Post by gobbledigook on 2009-08-31
Hi!

I know lots of people have sound issues and it seems to be well covered, but i have been trawling the net for a couple of hours now with no idea what is wrong or how to fix it!

I have a headless 9.04 install which i'm planning on turning into a media center using xbmc. but first i thought i had better test the sound first and could get none!

so i have installed pulseaudia and with it esd and alsa, i have checked to make sure that in alsamixer the channels aren't muted by default.

i have followed the steps in the pulse audio section of the ubuntu wiki here: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

and the debugging sound issues bit here:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

i have run an alsa diagnostic script which you can see **[_here_]("http://www.alsa-project.org/db/?f=97ca3d091835533ddb59012e2120e15ad12fc047")**

the output of that suggests that pulseaudio is installed but not running, when i simply type pulseaudio into the command prompt i get: 

```

server@server:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_55c_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_10de_55c_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.

```

and i have also noticed that on start-up pulseaudio is in a different colour and states configured for per-user sessions? is this correct and how can i get it to change this?

all the driver and hardware info is listed in that diagnostic link but if you need any more info please ask!

any help greatly appreciated:)

Dan.

---

### Post by gobbledigook on 2009-08-31
hi, i think i have narrowed this down to an error with pulseaudio here is a -vv output clearly showing 2 errors loading certain modules. 

any ideas?

```

server@server:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -p                                                                             ipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -                                                                             Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonlitera                                                                             l -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-d                                                                             eclarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing                                                                             -noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -                                                                             Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-15-server #49-Ubuntu SMP Tue Aug 1                                                                             8 19:30:06 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is d043cdd148c306655637ad9f491c380c.
I: main.c: Using runtime directory /home/server/.pulse/d043cdd148c306655637ad9f4                                                                             91c380c:runtime.
I: main.c: Using state directory /home/server/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, t                                                                             otal size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-g                                                                             conf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/server/.puls                                                                             e/d043cdd148c306655637ad9f491c380c:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/server/.puls                                                                             e/d043cdd148c306655637ad9f491c380c:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-h                                                                             al-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_                                                                             alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_                                                                             55c_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sin                                                                             k_name=alsa_output.pci_10de_55c_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM front:0
I: alsa-util.c: Couldn't open PCM device front:0: Invalid argument
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround40:0
I: alsa-util.c: Couldn't open PCM device surround40:0: Invalid argument
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround41:0
I: alsa-util.c: Couldn't open PCM device surround41:0: Invalid argument
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround50:0
I: alsa-util.c: Couldn't open PCM device surround50:0: Invalid argument
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround51:0
I: alsa-util.c: Couldn't open PCM device surround51:0: Invalid argument
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Couldn't open PCM device surround71:0: Invalid argument
D: alsa-util.c: Trying hw:0 as last resort...
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: Invalid value for card
[B]E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 s                                                                             ink_name=alsa_output.pci_10de_55c_sound_card_0_alsa_playback_0 tsched=0"): initi                                                                             alization failed.[/B]
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_                                                                             55c_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 s                                                                             ource_name=alsa_input.pci_10de_55c_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM front:0
I: alsa-util.c: Couldn't open PCM device front:0: Invalid argument
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround40:0
I: alsa-util.c: Couldn't open PCM device surround40:0: Invalid argument
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround41:0
I: alsa-util.c: Couldn't open PCM device surround41:0: Invalid argument
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround50:0
I: alsa-util.c: Couldn't open PCM device surround50:0: Invalid argument
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround51:0
I: alsa-util.c: Couldn't open PCM device surround51:0: Invalid argument
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Couldn't open PCM device surround71:0: Invalid argument
D: alsa-util.c: Trying hw:0 as last resort...
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: Invalid value for card
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
**E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0                                                                              source_name=alsa_input.pci_10de_55c_sound_card_0_alsa_capture_0 tsched=0"): ini                                                                             tialization failed.**
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_                                                                             55c_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_                                                                             55c_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-e                                                                             sound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
I: module-default-device-restore.c: Saved default sink 'auto_null' not existant,                                                                              not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'auto_null.monitor' not                                                                              existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: module-device-restore.c: Restoring volume for sink auto_null.
I: module-device-restore.c: Restoring mute state for sink auto_null.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and cha                                                                             nnel map front-left,front-right
I: module-device-restore.c: Restoring volume for source auto_null.monitor.
I: module-device-restore.c: Restoring mute state for source auto_null.monitor.
I: source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 441                                                                             00Hz and channel map front-left,front-right
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-suspend-on-idle.c: Source auto_null.monitor becomes idle.
D: module-suspend-on-idle.c: Sink auto_null becomes idle.
I: module.c: Loaded "module-null-sink" (index: #9; argument: "sink_name=auto_nul                                                                             l").
I: module.c: Loaded "module-always-sink" (index: #10; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #11; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #12; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesk                                                                             top/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedes                                                                             ktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
I: module-suspend-on-idle.c: Source auto_null.monitor idle for too long, suspend                                                                             ing ...

```

---

