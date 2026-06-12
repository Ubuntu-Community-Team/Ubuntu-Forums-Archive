---
title: "Jackd not working 12.04"
date: 2013-01-11
forum: Ubuntu Studio
---

### Post by tontis on 2013-01-11
Hey,
I recently re-installed ubuntu 12.04 and did [this]("https://help.ubuntu.com/community/UbuntuStudioPreparation") tutorial installing the audiopackages including qjackctl. For some reason qjackctl won't work, and since I'm quite the newbie at this, I have no idea why.
This error code is produced:

```
20:02:26.955 Patchbay deactivated.
20:02:26.960 Statistics reset.
20:02:26.965 ALSA connection change.
20:02:26.977 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
20:03:25.593 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Fri Jan 11 20:03:25 2013: Starting jack server...
Fri Jan 11 20:03:25 2013: JACK server starting in realtime mode with priority 10
Fri Jan 11 20:03:25 2013: [1m[31mERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[0m
Fri Jan 11 20:03:25 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[0m
Fri Jan 11 20:03:25 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
Fri Jan 11 20:03:25 2013: [1m[31mERROR: Cannot initialize driver[0m
Fri Jan 11 20:03:25 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
Fri Jan 11 20:03:25 2013: [1m[31mERROR: Failed to open server[0m
Fri Jan 11 20:03:26 2013: Saving settings to "/home/bixop/.config/jack/conf.xml" ...
20:03:28.230 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

these are screens of my settings in qjackctl.
[ATTACH]229898[/ATTACH]

[ATTACH]229899[/ATTACH]


Very thankful for any help!

---

### Post by ABOBA on 2013-01-13
How much soundcards do you have?
Is it Ubuntu Studio or Ubuntu?
If this is Ubuntu Studio you can set Priority to 89.
Try to kill PulseAudio with 
```
pulseaudio -k
```
After this try to run Jack.
If all okey and Jack runs correctly then the reason of problem is conflict between Jack and PulseAudio.
It is a command to start PulseAudio
```
pulseaudio --start
```

---

### Post by jejeman on 2013-01-14
> **ABOBA said:**
> HTry to kill PulseAudio with 
```
pulseaudio -k
```
After this try to run Jack.
If all okey and Jack runs correctly then the reason of problem is conflict between Jack and PulseAudio.
It is a command to start PulseAudio
```
pulseaudio --start
```This is true only if you have set respawn to "no".

---

### Post by tontis on 2013-01-15
Hey, thx for the replies.

I tried pulseaudio -k

Now jackd seems to start, however there's still some errortext, I'm not sure why, what it does or if it's even important. It's the following:
```
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

The entire code:
```
17:05:20.412 Patchbay deactivated.
17:05:20.420 Statistics reset.
17:05:20.466 ALSA connection change.
17:05:20.850 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
17:05:20.861 ALSA connection graph change.
17:05:24.885 D-BUS: JACK server is starting...
Tue Jan 15 17:05:24 2013: Starting jack server...
Tue Jan 15 17:05:24 2013: JACK server starting in realtime mode with priority 10
Tue Jan 15 17:05:24 2013: Acquired audio card Audio0
Tue Jan 15 17:05:24 2013: creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
Tue Jan 15 17:05:24 2013: Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfe6fc000 irq 43
Tue Jan 15 17:05:24 2013: configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
Tue Jan 15 17:05:24 2013: ALSA: final selected sample format for capture: 32bit integer little-endian
Tue Jan 15 17:05:24 2013: ALSA: use 2 periods for capture
Tue Jan 15 17:05:24 2013: ALSA: final selected sample format for playback: 32bit integer little-endian
Tue Jan 15 17:05:24 2013: ALSA: use 2 periods for playback
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
17:05:24.902 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Tue Jan 15 17:05:24 2013: graph reorder: new port 'system:capture_1'
Tue Jan 15 17:05:24 2013: New client 'system' with PID 0
Tue Jan 15 17:05:24 2013: graph reorder: new port 'system:capture_2'
Tue Jan 15 17:05:24 2013: graph reorder: new port 'system:playback_1'
Tue Jan 15 17:05:24 2013: graph reorder: new port 'system:playback_2'
Tue Jan 15 17:05:25 2013: Saving settings to "/home/bixop/.config/jack/conf.xml" ...
17:05:27.150 JACK connection change.
17:05:27.168 Server configuration saved to "/home/bixop/.jackdrc".
17:05:27.168 Statistics reset.
17:05:27.176 Client activated.
17:05:27.184 JACK connection graph change.
Tue Jan 15 17:05:27 2013: New client 'qjackctl' with PID 2622
Tue Jan 15 17:06:06 2013: Ignoring JACK server start request because server is already started.
17:06:12.537 ALSA connection graph change.
17:06:12.614 ALSA connection change.
17:06:12.615 ALSA connection graph change.
17:06:12.814 ALSA connection change.
17:06:17.226 XRUN callback (1).
17:10:37.199 XRUN callback (2).
```

To answer your questions - I have two soundcards but is currently only using one. I am running normal ubuntu with most of the soundpackages from ubuntu studio installed.

---

