---
title: "Arecord | Aplay works, Qjacktl system-&gt;system does not."
date: 2012-08-15
forum: Ubuntu Studio
---

### Post by williamstome on 2012-08-15
Hey all-
I had qjackctl working at one point, but it has mysteriously stopped.

All I want to do (so far) is pipe microphone -> headphones through jackd.

I know my mic and headphones are working correctly, as I can do ```
arecord -D hw:1,0 -f S32_LE | aplay
```
and it works like a charm.

In qjackctl, I set the input device to hw:1,0 and connect system->system in the connections window, but all I hear is static.

Here is the full output in qjackctl:
12:23:15.585 Patchbay deactivated.
12:23:15.590 Statistics reset.
12:23:15.591 ALSA connection change.
12:23:15.606 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:23:18.880 D-BUS: JACK server is starting...
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:23:18.902 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: driver "alsa" selected
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Starting jack server...
Wed Aug 15 12:23:18 2012: JACK server starting in realtime mode with priority 10
Wed Aug 15 12:23:18 2012: control device hw:0
Wed Aug 15 12:23:18 2012: control device hw:0
Wed Aug 15 12:23:18 2012: Acquired audio card Audio0
Wed Aug 15 12:23:18 2012: creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|32bit
Wed Aug 15 12:23:18 2012: control device hw:0
Wed Aug 15 12:23:18 2012: configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
Wed Aug 15 12:23:18 2012: ALSA: final selected sample format for capture: 32bit integer little-endian
Wed Aug 15 12:23:18 2012: ALSA: use 2 periods for capture
Wed Aug 15 12:23:18 2012: ALSA: final selected sample format for playback: 32bit integer little-endian
Wed Aug 15 12:23:18 2012: ALSA: use 2 periods for playback
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:capture_1'
Wed Aug 15 12:23:18 2012: New client 'system' with PID 0
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:capture_2'
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:playback_1'
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:playback_2'
12:23:21.169 JACK connection change.
12:23:21.170 Server configuration saved to "/home/tom/.jackdrc".
12:23:21.170 Statistics reset.
12:23:21.203 Client activated.
12:23:21.257 JACK connection graph change.
Wed Aug 15 12:23:21 2012: New client 'qjackctl' with PID 17107
12:23:23.884 JACK connection change.
Wed Aug 15 12:23:23 2012: Connecting 'system:capture_1' to 'system:playback_1'
Wed Aug 15 12:23:23 2012: Connecting 'system:capture_2' to 'system:playback_2'

---

### Post by smartboyhw on 2012-08-16
> **williamstome said:**
> Hey all-
I had qjackctl working at one point, but it has mysteriously stopped.
 
All I want to do (so far) is pipe microphone -> headphones through jackd.
 
I know my mic and headphones are working correctly, as I can do ```
arecord -D hw:1,0 -f S32_LE | aplay
```
and it works like a charm.
 
In qjackctl, I set the input device to hw:1,0 and connect system->system in the connections window, but all I hear is static.
 
Here is the full output in qjackctl:
12:23:15.585 Patchbay deactivated.
12:23:15.590 Statistics reset.
12:23:15.591 ALSA connection change.
12:23:15.606 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:23:18.880 D-BUS: JACK server is starting...
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:23:18.902 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: driver "alsa" selected
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Saving settings to "/home/tom/.config/jack/conf.xml" ...
Wed Aug 15 12:23:18 2012: Starting jack server...
Wed Aug 15 12:23:18 2012: JACK server starting in realtime mode with priority 10
Wed Aug 15 12:23:18 2012: control device hw:0
Wed Aug 15 12:23:18 2012: control device hw:0
Wed Aug 15 12:23:18 2012: Acquired audio card Audio0
Wed Aug 15 12:23:18 2012: creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|32bit
Wed Aug 15 12:23:18 2012: control device hw:0
Wed Aug 15 12:23:18 2012: configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
Wed Aug 15 12:23:18 2012: ALSA: final selected sample format for capture: 32bit integer little-endian
Wed Aug 15 12:23:18 2012: ALSA: use 2 periods for capture
Wed Aug 15 12:23:18 2012: ALSA: final selected sample format for playback: 32bit integer little-endian
Wed Aug 15 12:23:18 2012: ALSA: use 2 periods for playback
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:capture_1'
Wed Aug 15 12:23:18 2012: New client 'system' with PID 0
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:capture_2'
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:playback_1'
Wed Aug 15 12:23:18 2012: graph reorder: new port 'system:playback_2'
12:23:21.169 JACK connection change.
12:23:21.170 Server configuration saved to "/home/tom/.jackdrc".
12:23:21.170 Statistics reset.
12:23:21.203 Client activated.
12:23:21.257 JACK connection graph change.
Wed Aug 15 12:23:21 2012: New client 'qjackctl' with PID 17107
12:23:23.884 JACK connection change.
Wed Aug 15 12:23:23 2012: Connecting 'system:capture_1' to 'system:playback_1'
Wed Aug 15 12:23:23 2012: Connecting 'system:capture_2' to 'system:playback_2'
 
Hi williamstome.
 
First of all, next time paste the log in paste.ubuntu.com. It is very inconvenient to read such a big log in the forum.
 
I will try to contact the Ubuntu Studio team to see if they have any problems on this matter.
 
If you keep getting that error and think it's a software problem, report a bug on Launchpad.
 
Regards,
Howard Chan
Ubuntu Studio Team member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by maciekpruski on 2012-08-16
Is hw:1 your default soundcard or an external interface? if the latter than you should change settings in the "interface" field in qjackctl menu and not the "input device" field. At least that worked for me when I had a similar problem.
I'm assuming that you also checked if your card's volume levels are raised in alsamixer? (sometimes they are default at zero volume, especially if it is not the first card alsa reckognizes).
hope that helps

---

