---
title: "KXStudio: JACK not working with HDA ATI SB"
date: 2011-01-19
forum: Ubuntu Studio
---

### Post by GraysonPeddie on 2011-01-19
I just got rid of my SoundBlaster X-Fi sound card and went with on-board instead.

```
Tue Jan 18 23:18:57 2011: ------------------
Tue Jan 18 23:18:57 2011: Controller activated. Version 1.9.7 (4046) built on Tue Jan 18 18:10:45 2011
Tue Jan 18 23:18:57 2011: Loading settings from "/home/grayson/.config/jack/conf.xml" using expat_2.0.1 ...
Tue Jan 18 23:18:57 2011: setting engine option "driver" to value "alsa"
Tue Jan 18 23:18:57 2011: driver "alsa" selected
Tue Jan 18 23:18:57 2011: setting engine option "realtime" to value "true"
Tue Jan 18 23:18:57 2011: setting engine option "verbose" to value "false"
Tue Jan 18 23:18:57 2011: setting engine option "client-timeout" to value "500"
Tue Jan 18 23:18:57 2011: setting for driver "net" found
Tue Jan 18 23:18:57 2011: setting for driver "dummy" found
Tue Jan 18 23:18:57 2011: setting for driver "firewire" found
Tue Jan 18 23:18:57 2011: setting for driver "loopback" found
Tue Jan 18 23:18:57 2011: setting for driver "alsa" found
Tue Jan 18 23:18:57 2011: setting driver option "device" to value "hw:0"
Tue Jan 18 23:18:57 2011: setting driver option "rate" to value "44100"
Tue Jan 18 23:18:57 2011: setting driver option "period" to value "1024"
Tue Jan 18 23:18:57 2011: setting driver option "nperiods" to value "2"
Tue Jan 18 23:18:57 2011: setting driver option "hwmon" to value "false"
Tue Jan 18 23:18:57 2011: setting driver option "hwmeter" to value "false"
Tue Jan 18 23:18:57 2011: setting driver option "duplex" to value "true"
Tue Jan 18 23:18:57 2011: setting driver option "softmode" to value "false"
Tue Jan 18 23:18:57 2011: setting driver option "monitor" to value "false"
Tue Jan 18 23:18:57 2011: setting driver option "dither" to value "n"
Tue Jan 18 23:18:57 2011: setting driver option "shorts" to value "false"
Tue Jan 18 23:18:57 2011: setting for driver "netone" found
Tue Jan 18 23:18:57 2011: setting for internal "netmanager" found
Tue Jan 18 23:18:57 2011: setting for internal "audioadapter" found
Tue Jan 18 23:18:57 2011: setting internal option "playback" to value "none"
Tue Jan 18 23:18:57 2011: setting internal option "device" to value "hw:0"
Tue Jan 18 23:18:57 2011: setting internal option "rate" to value "96000"
Tue Jan 18 23:18:57 2011: setting for internal "profiler" found
Tue Jan 18 23:18:57 2011: setting internal option "cpu-load" to value "true"
Tue Jan 18 23:18:57 2011: setting for internal "netadapter" found
Tue Jan 18 23:18:57 2011: Listening for D-Bus messages
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: driver "alsa" selected
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:18:57 2011: Starting jack server...
Tue Jan 18 23:18:57 2011: JACK server starting in realtime mode with priority 10
Tue Jan 18 23:18:58 2011: control device hw:0
Tue Jan 18 23:18:58 2011: control device hw:0
Tue Jan 18 23:18:58 2011: Acquired audio card Audio0
Tue Jan 18 23:18:58 2011: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Jan 18 23:18:58 2011: control device hw:0
Tue Jan 18 23:18:58 2011: Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe7f4000 irq 16
Tue Jan 18 23:18:58 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Tue Jan 18 23:18:58 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jan 18 23:18:58 2011: ALSA: use 2 periods for capture
Tue Jan 18 23:18:58 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jan 18 23:18:58 2011: ALSA: use 2 periods for playback
Tue Jan 18 23:19:03 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:19:03 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:19:03 2011: [1m[31mERROR: Cannot open client name = dbusapi[0m
Tue Jan 18 23:19:03 2011: [1m[31mERROR: failed to create dbusapi jack client[0m
23:19:30.070 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackSocketClientChannel read fail
Cannot open qjackctl client
Tue Jan 18 23:19:30 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: Cannot create new client[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: Unknown request 4294967295[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: Abort![0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: info.si_signo = 6[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: Segmentation Fault![0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: info.si_signo = 11[0m
Tue Jan 18 23:19:30 2011: [1m[31mERROR: info.si_errno = 0[0m
23:25:43.545 Startup script...
23:25:43.547 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
23:25:43.957 Startup script terminated with exit status=32512.
23:26:09.229 D-BUS: JACK server could not be started. Sorry
Tue Jan 18 23:25:43 2011: ------------------
Tue Jan 18 23:25:43 2011: Controller activated. Version 1.9.7 (4046) built on Tue Jan 18 18:10:45 2011
Tue Jan 18 23:25:43 2011: Loading settings from "/home/grayson/.config/jack/conf.xml" using expat_2.0.1 ...
Tue Jan 18 23:25:43 2011: setting engine option "driver" to value "alsa"
Tue Jan 18 23:25:43 2011: driver "alsa" selected
Tue Jan 18 23:25:43 2011: setting engine option "realtime" to value "true"
Tue Jan 18 23:25:43 2011: setting engine option "verbose" to value "false"
Tue Jan 18 23:25:43 2011: setting engine option "client-timeout" to value "500"
Tue Jan 18 23:25:43 2011: setting for driver "net" found
Tue Jan 18 23:25:43 2011: setting for driver "dummy" found
Tue Jan 18 23:25:43 2011: setting for driver "firewire" found
Tue Jan 18 23:25:43 2011: setting for driver "loopback" found
Tue Jan 18 23:25:43 2011: setting for driver "alsa" found
Tue Jan 18 23:25:43 2011: setting driver option "device" to value "hw:0"
Tue Jan 18 23:25:43 2011: setting driver option "rate" to value "44100"
Tue Jan 18 23:25:43 2011: setting driver option "period" to value "1024"
Tue Jan 18 23:25:43 2011: setting driver option "nperiods" to value "2"
Tue Jan 18 23:25:43 2011: setting driver option "hwmon" to value "false"
Tue Jan 18 23:25:43 2011: setting driver option "hwmeter" to value "false"
Tue Jan 18 23:25:43 2011: setting driver option "duplex" to value "true"
Tue Jan 18 23:25:43 2011: setting driver option "softmode" to value "false"
Tue Jan 18 23:25:43 2011: setting driver option "monitor" to value "false"
Tue Jan 18 23:25:43 2011: setting driver option "dither" to value "n"
Tue Jan 18 23:25:43 2011: setting driver option "shorts" to value "false"
Tue Jan 18 23:25:43 2011: setting for driver "netone" found
Tue Jan 18 23:25:43 2011: setting for internal "netmanager" found
Tue Jan 18 23:25:43 2011: setting for internal "audioadapter" found
Tue Jan 18 23:25:43 2011: setting internal option "playback" to value "none"
Tue Jan 18 23:25:43 2011: setting internal option "device" to value "hw:0"
Tue Jan 18 23:25:43 2011: setting internal option "rate" to value "96000"
Tue Jan 18 23:25:43 2011: setting for internal "profiler" found
Tue Jan 18 23:25:43 2011: setting internal option "cpu-load" to value "true"
Tue Jan 18 23:25:43 2011: setting for internal "netadapter" found
Tue Jan 18 23:25:43 2011: Listening for D-Bus messages
Tue Jan 18 23:25:43 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: driver "alsa" selected
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:25:44 2011: Starting jack server...
Tue Jan 18 23:25:44 2011: JACK server starting in realtime mode with priority 10
Tue Jan 18 23:25:44 2011: control device hw:0
Tue Jan 18 23:25:44 2011: control device hw:0
Tue Jan 18 23:25:44 2011: Acquired audio card Audio0
Tue Jan 18 23:25:44 2011: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Jan 18 23:25:44 2011: control device hw:0
Tue Jan 18 23:25:44 2011: Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe7f4000 irq 16
Tue Jan 18 23:25:44 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Tue Jan 18 23:25:44 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jan 18 23:25:44 2011: ALSA: use 2 periods for capture
Tue Jan 18 23:25:44 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jan 18 23:25:44 2011: ALSA: use 2 periods for playback
Tue Jan 18 23:25:49 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:25:49 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:25:49 2011: [1m[31mERROR: Cannot open client name = dbusapi[0m
Tue Jan 18 23:25:49 2011: [1m[31mERROR: failed to create dbusapi jack client[0m
23:26:16.666 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackSocketClientChannel read fail
Cannot open qjackctl client
Tue Jan 18 23:26:16 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: Cannot create new client[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: Unknown request 4294967295[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: Abort![0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: info.si_signo = 6[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: Segmentation Fault![0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: info.si_signo = 11[0m
Tue Jan 18 23:26:16 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:28:50 2011: ------------------
Tue Jan 18 23:28:50 2011: Controller activated. Version 1.9.7 (4046) built on Tue Jan 18 18:10:45 2011
Tue Jan 18 23:28:50 2011: Loading settings from "/home/grayson/.config/jack/conf.xml" using expat_2.0.1 ...
Tue Jan 18 23:28:50 2011: setting engine option "driver" to value "alsa"
Tue Jan 18 23:28:50 2011: driver "alsa" selected
Tue Jan 18 23:28:50 2011: setting engine option "realtime" to value "true"
Tue Jan 18 23:28:50 2011: setting engine option "verbose" to value "false"
Tue Jan 18 23:28:50 2011: setting engine option "client-timeout" to value "500"
Tue Jan 18 23:28:50 2011: setting for driver "net" found
Tue Jan 18 23:28:50 2011: setting for driver "dummy" found
Tue Jan 18 23:28:50 2011: setting for driver "firewire" found
Tue Jan 18 23:28:50 2011: setting for driver "loopback" found
Tue Jan 18 23:28:50 2011: setting for driver "alsa" found
Tue Jan 18 23:28:50 2011: setting driver option "device" to value "hw:0"
Tue Jan 18 23:28:50 2011: setting driver option "rate" to value "44100"
Tue Jan 18 23:28:50 2011: setting driver option "period" to value "1024"
Tue Jan 18 23:28:50 2011: setting driver option "nperiods" to value "2"
Tue Jan 18 23:28:50 2011: setting driver option "hwmon" to value "false"
Tue Jan 18 23:28:50 2011: setting driver option "hwmeter" to value "false"
Tue Jan 18 23:28:50 2011: setting driver option "duplex" to value "true"
Tue Jan 18 23:28:50 2011: setting driver option "softmode" to value "false"
Tue Jan 18 23:28:50 2011: setting driver option "monitor" to value "false"
Tue Jan 18 23:28:50 2011: setting driver option "dither" to value "n"
Tue Jan 18 23:28:50 2011: setting driver option "shorts" to value "false"
Tue Jan 18 23:28:50 2011: setting for driver "netone" found
Tue Jan 18 23:28:50 2011: setting for internal "netmanager" found
Tue Jan 18 23:28:50 2011: setting for internal "audioadapter" found
Tue Jan 18 23:28:50 2011: setting internal option "playback" to value "none"
Tue Jan 18 23:28:50 2011: setting internal option "device" to value "hw:0"
Tue Jan 18 23:28:50 2011: setting internal option "rate" to value "96000"
Tue Jan 18 23:28:50 2011: setting for internal "profiler" found
Tue Jan 18 23:28:50 2011: setting internal option "cpu-load" to value "true"
Tue Jan 18 23:28:50 2011: setting for internal "netadapter" found
Tue Jan 18 23:28:50 2011: Listening for D-Bus messages
Tue Jan 18 23:29:09 2011: driver "alsa" selected
Tue Jan 18 23:29:09 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:29:25 2011: Starting jack server...
Tue Jan 18 23:29:25 2011: JACK server starting in realtime mode with priority 10
Tue Jan 18 23:29:25 2011: control device hw:0
Tue Jan 18 23:29:25 2011: control device hw:0
Tue Jan 18 23:29:25 2011: Acquired audio card Audio0
Tue Jan 18 23:29:25 2011: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Jan 18 23:29:25 2011: control device hw:0
Tue Jan 18 23:29:25 2011: Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe7f4000 irq 16
Tue Jan 18 23:29:25 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Tue Jan 18 23:29:25 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jan 18 23:29:25 2011: ALSA: use 2 periods for capture
Tue Jan 18 23:29:25 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jan 18 23:29:25 2011: ALSA: use 2 periods for playback
Tue Jan 18 23:29:30 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:29:30 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:29:30 2011: [1m[31mERROR: Cannot open client name = dbusapi[0m
Tue Jan 18 23:29:30 2011: [1m[31mERROR: failed to create dbusapi jack client[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: Cannot create new client[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: Unknown request 4294967295[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: Abort![0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: info.si_signo = 6[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: Segmentation Fault![0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: info.si_signo = 11[0m
Tue Jan 18 23:29:35 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:29:36 2011: ------------------
Tue Jan 18 23:29:36 2011: Controller activated. Version 1.9.7 (4046) built on Tue Jan 18 18:10:45 2011
Tue Jan 18 23:29:36 2011: Loading settings from "/home/grayson/.config/jack/conf.xml" using expat_2.0.1 ...
Tue Jan 18 23:29:36 2011: setting engine option "driver" to value "alsa"
Tue Jan 18 23:29:36 2011: driver "alsa" selected
Tue Jan 18 23:29:36 2011: setting engine option "realtime" to value "true"
Tue Jan 18 23:29:36 2011: setting engine option "verbose" to value "false"
Tue Jan 18 23:29:36 2011: setting engine option "client-timeout" to value "500"
Tue Jan 18 23:29:36 2011: setting for driver "net" found
Tue Jan 18 23:29:36 2011: setting for driver "dummy" found
Tue Jan 18 23:29:36 2011: setting for driver "firewire" found
Tue Jan 18 23:29:36 2011: setting for driver "loopback" found
Tue Jan 18 23:29:36 2011: setting for driver "alsa" found
Tue Jan 18 23:29:36 2011: setting driver option "device" to value "hw:0"
Tue Jan 18 23:29:36 2011: setting driver option "rate" to value "44100"
Tue Jan 18 23:29:36 2011: setting driver option "period" to value "1024"
Tue Jan 18 23:29:36 2011: setting driver option "nperiods" to value "2"
Tue Jan 18 23:29:36 2011: setting driver option "hwmon" to value "false"
Tue Jan 18 23:29:36 2011: setting driver option "hwmeter" to value "false"
Tue Jan 18 23:29:36 2011: setting driver option "duplex" to value "true"
Tue Jan 18 23:29:36 2011: setting driver option "softmode" to value "false"
Tue Jan 18 23:29:36 2011: setting driver option "monitor" to value "false"
Tue Jan 18 23:29:36 2011: setting driver option "dither" to value "n"
Tue Jan 18 23:29:36 2011: setting driver option "shorts" to value "false"
Tue Jan 18 23:29:36 2011: setting for driver "netone" found
Tue Jan 18 23:29:36 2011: setting for internal "netmanager" found
Tue Jan 18 23:29:36 2011: setting for internal "audioadapter" found
Tue Jan 18 23:29:36 2011: setting internal option "playback" to value "none"
Tue Jan 18 23:29:36 2011: setting internal option "device" to value "hw:0"
Tue Jan 18 23:29:36 2011: setting internal option "rate" to value "96000"
Tue Jan 18 23:29:36 2011: setting for internal "profiler" found
Tue Jan 18 23:29:36 2011: setting internal option "cpu-load" to value "true"
Tue Jan 18 23:29:36 2011: setting for internal "netadapter" found
Tue Jan 18 23:29:36 2011: Listening for D-Bus messages
Tue Jan 18 23:29:36 2011: Starting jack server...
Tue Jan 18 23:29:36 2011: JACK server starting in realtime mode with priority 10
Tue Jan 18 23:29:36 2011: control device hw:0
Tue Jan 18 23:29:36 2011: control device hw:0
Tue Jan 18 23:29:36 2011: Acquired audio card Audio0
Tue Jan 18 23:29:36 2011: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Jan 18 23:29:36 2011: control device hw:0
Tue Jan 18 23:29:36 2011: Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe7f4000 irq 16
Tue Jan 18 23:29:36 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Tue Jan 18 23:29:36 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jan 18 23:29:36 2011: ALSA: use 2 periods for capture
Tue Jan 18 23:29:36 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jan 18 23:29:36 2011: ALSA: use 2 periods for playback
Tue Jan 18 23:29:41 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:29:41 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:29:41 2011: [1m[31mERROR: Cannot open client name = dbusapi[0m
Tue Jan 18 23:29:41 2011: [1m[31mERROR: failed to create dbusapi jack client[0m
Tue Jan 18 23:29:41 2011: [1m[31mERROR: Unknown request 4294967295[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: Cannot create new client[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: Abort![0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: info.si_signo = 6[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: Segmentation Fault![0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: info.si_signo = 11[0m
Tue Jan 18 23:29:46 2011: [1m[31mERROR: info.si_errno = 0[0m
23:30:22.546 Startup script...
23:30:22.547 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
23:30:22.952 Startup script terminated with exit status=32512.
23:30:48.205 D-BUS: JACK server could not be started. Sorry
Tue Jan 18 23:30:22 2011: ------------------
Tue Jan 18 23:30:22 2011: Controller activated. Version 1.9.7 (4046) built on Tue Jan 18 18:10:45 2011
Tue Jan 18 23:30:22 2011: Loading settings from "/home/grayson/.config/jack/conf.xml" using expat_2.0.1 ...
Tue Jan 18 23:30:22 2011: setting engine option "driver" to value "alsa"
Tue Jan 18 23:30:22 2011: driver "alsa" selected
Tue Jan 18 23:30:22 2011: setting engine option "realtime" to value "true"
Tue Jan 18 23:30:22 2011: setting engine option "verbose" to value "false"
Tue Jan 18 23:30:22 2011: setting engine option "client-timeout" to value "500"
Tue Jan 18 23:30:22 2011: setting for driver "net" found
Tue Jan 18 23:30:22 2011: setting for driver "dummy" found
Tue Jan 18 23:30:22 2011: setting for driver "firewire" found
Tue Jan 18 23:30:22 2011: setting for driver "loopback" found
Tue Jan 18 23:30:22 2011: setting for driver "alsa" found
Tue Jan 18 23:30:22 2011: setting driver option "device" to value "hw:0"
Tue Jan 18 23:30:22 2011: setting driver option "rate" to value "44100"
Tue Jan 18 23:30:22 2011: setting driver option "period" to value "1024"
Tue Jan 18 23:30:22 2011: setting driver option "nperiods" to value "2"
Tue Jan 18 23:30:22 2011: setting driver option "hwmon" to value "false"
Tue Jan 18 23:30:22 2011: setting driver option "hwmeter" to value "false"
Tue Jan 18 23:30:22 2011: setting driver option "duplex" to value "true"
Tue Jan 18 23:30:22 2011: setting driver option "softmode" to value "false"
Tue Jan 18 23:30:22 2011: setting driver option "monitor" to value "false"
Tue Jan 18 23:30:22 2011: setting driver option "dither" to value "n"
Tue Jan 18 23:30:22 2011: setting driver option "shorts" to value "false"
Tue Jan 18 23:30:22 2011: setting for driver "netone" found
Tue Jan 18 23:30:22 2011: setting for internal "netmanager" found
Tue Jan 18 23:30:22 2011: setting for internal "audioadapter" found
Tue Jan 18 23:30:22 2011: setting internal option "playback" to value "none"
Tue Jan 18 23:30:22 2011: setting internal option "device" to value "hw:0"
Tue Jan 18 23:30:22 2011: setting internal option "rate" to value "96000"
Tue Jan 18 23:30:22 2011: setting for internal "profiler" found
Tue Jan 18 23:30:22 2011: setting internal option "cpu-load" to value "true"
Tue Jan 18 23:30:22 2011: setting for internal "netadapter" found
Tue Jan 18 23:30:22 2011: Listening for D-Bus messages
Tue Jan 18 23:30:22 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:22 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: driver "alsa" selected
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Saving settings to "/home/grayson/.config/jack/conf.xml" ...
Tue Jan 18 23:30:23 2011: Starting jack server...
Tue Jan 18 23:30:23 2011: JACK server starting in realtime mode with priority 10
Tue Jan 18 23:30:23 2011: control device hw:0
Tue Jan 18 23:30:23 2011: control device hw:0
Tue Jan 18 23:30:23 2011: Acquired audio card Audio0
Tue Jan 18 23:30:23 2011: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Jan 18 23:30:23 2011: control device hw:0
Tue Jan 18 23:30:23 2011: Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe7f4000 irq 16
Tue Jan 18 23:30:23 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Tue Jan 18 23:30:23 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jan 18 23:30:23 2011: ALSA: use 2 periods for capture
Tue Jan 18 23:30:23 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jan 18 23:30:23 2011: ALSA: use 2 periods for playback
Tue Jan 18 23:30:28 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:30:28 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:30:28 2011: [1m[31mERROR: Cannot open client name = dbusapi[0m
Tue Jan 18 23:30:28 2011: [1m[31mERROR: failed to create dbusapi jack client[0m
23:30:55.464 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackSocketClientChannel read fail
Cannot open qjackctl client
Tue Jan 18 23:30:55 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: Driver is not running[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: Cannot create new client[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: Unknown request 4294967295[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: Abort![0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: info.si_signo = 6[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: info.si_errno = 0[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: Segmentation Fault![0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: info.si_signo = 11[0m
Tue Jan 18 23:30:55 2011: [1m[31mERROR: info.si_errno = 0[0m
```

Please excuse the encoding errors. I am using [KXStudio](www.kxstudio.com), and I got rid of my X-Fi sound card and just use my on-board sound card for watching movies, play games, listen to music, and this is all done in Windows, so other than EAX 3.0/4.0/5.0, CMSS 3D, and X-Fi Crystalizer, I saw no benefits of using the discrete sound card, so I went back to on-board. This is temporary until I get my Echo Gina 3G delivered to my apartment, probably before the end of the week or next Monday. So, I hardly bought any games that uses Creative's technology, but then I don't want to digress too much.

So anyway, back to Linux/KXStudio/Jack. Is there anyway to get JACK to work with my HD Audio (HDA) ATI SB

uname -a:

```
Linux htpc 2.6.32-26-preempt #48-Ubuntu SMP PREEMPT Wed Nov 24 10:43:13 UTC 2010 x86_64 GNU/Linux
```

lspci | grep HDA

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

**Update**

I've decided to not bump my old thread, but for those who are interested in getting the problem solved, I just got an Echo Gina 3G and it is working just fine in KXStudio. I'm sorry I couldn't find out the solution to my problem, but oh well. Perhaps reinstalling KXStudio will do the trick for me, but I don't want to do that.

---

