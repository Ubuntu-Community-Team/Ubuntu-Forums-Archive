---
title: "jack server won't start."
date: 2012-01-16
forum: Ubuntu Studio
---

### Post by Niels Olson on 2012-01-16
Hi. Qjackctl can't get the server to start. I have a condenser mic going into an m-audio mobile pre on hw:2 and the internal soundcard on hw:3 sending output to an amplifier. I want to speak into the mic, and hear my voice amplified. I have read many threads, and tried many configs. It worked once somewhere in the middle, and promptly never worked again. What should I do?

```
14:58:13.197 D-BUS: JACK server could not be started. Sorry
Mon Jan 16 14:58:12 2012: Saving settings to "/home/niels/.config/jack/conf.xml" ...
...
Mon Jan 16 14:58:12 2012: driver "alsa" selected
...
Mon Jan 16 14:58:12 2012: Saving settings to "/home/niels/.config/jack/conf.xml" ...
Mon Jan 16 14:58:12 2012: Starting jack server...
Mon Jan 16 14:58:12 2012: JACK server starting in realtime mode with priority 10
Mon Jan 16 14:58:13 2012: control device hw:2
Mon Jan 16 14:58:13 2012: control device hw:3
Mon Jan 16 14:58:13 2012: [1m[31mERROR: Failed to acquire device name : Audio2 error : Input/output error[0m
Mon Jan 16 14:58:13 2012: [1m[31mERROR: Audio device hw:2 cannot be acquired, trying to open it anyway...[0m
Mon Jan 16 14:58:13 2012: [1m[31mERROR: Failed to acquire device name : Audio3 error : Input/output error[0m
Mon Jan 16 14:58:13 2012: [1m[31mERROR: Audio device hw:3 cannot be acquired, trying to open it anyway...[0m
Mon Jan 16 14:58:13 2012: creating alsa driver ... hw:3|hw:2|1024|3|44100|1|1|nomon|swmeter|-|32bit
Mon Jan 16 14:58:13 2012: control device hw:3
Mon Jan 16 14:58:13 2012: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
Mon Jan 16 14:58:13 2012: ALSA: final selected sample format for capture: 24bit little-endian
Mon Jan 16 14:58:13 2012: [1m[31mERROR: ALSA: cannot set channel count to 1 for capture[0m
Mon Jan 16 14:58:13 2012: [1m[31mERROR: ALSA: cannot configure capture channel[0m
Mon Jan 16 14:58:13 2012: [1m[31mERROR: Cannot initialize driver[0m
Mon Jan 16 14:58:13 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Mon Jan 16 14:58:13 2012: [1m[31mERROR: Failed to open server[0m
14:58:16.444 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

---

### Post by CivilizationII on 2012-02-20
You need to force the hardware interface selected. PLease look at [http://ubuntuforums.org/showthread.php?t=1919665#4](http://ubuntuforums.org/showthread.php?t=1919665#4)

---

