---
title: "Sound stopped working"
date: 2017-04-01
forum: System76 Support
---

### Post by opus1 on 2017-04-01
Starting around 2 weeks ago the sound on my meerkat would just stop working. When I use pavucontrol, on the "output devices" tab, under "Hardware Output Devices" it says "No output devices available".  Under "All output devices" it says "Dummy Output". 

I went to [http://support.system76.com/articles/audio/](http://support.system76.com/articles/audio/) and used all the command line commands listed there, but it failed to bring back the audio.  The only way to get the system to list my soundcard in pavucontrol is to reboot the entire system, which is kind of inconvenient for the other users!

When I do lspci -v | grep -A6 Audio, I get:

```
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
	Subsystem: Intel Corporation Sunrise Point-LP HD Audio
	Flags: bus master, fast devsel, latency 32, IRQ 280
	Memory at df140000 (64-bit, non-prefetchable) [size=16K]
	Memory at df120000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl
```

And when I do aplay -l, I get:
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

...but still no soundcard in pavucontrol.

Is there a way to get the soundcard to be recognized by the system without rebooting??

---

### Post by opus1 on 2017-04-01
Looked at /var/log/syslog and saw several of the same warnings between the last time we heard sound and when we discovered it wasn't working:

```
Apr  1 09:03:02 opus pulseaudio[2231]: [pulseaudio] sink-input.c: Failed to create sink input: sink is suspended.
Apr  1 09:12:01 opus pulseaudio[2231]: [alsa-sink-ALC283 Analog] alsa-sink.c: Error opening PCM device front:0: Device or resource busy

```
None of which have appeared since I rebooted.

Also lots of other things like:
```
Apr  1 12:22:40 opus pulseaudio[189]: [pulseaudio] authkey.c: Failed to open cookie file '/home/bob/.config/pulse/cookie': No such file or directory
Apr  1 12:22:40 opus pulseaudio[189]: [pulseaudio] authkey.c: Failed to load authentication key '/home/bob/.config/pulse/cookie': No such file or directory
Apr  1 12:22:40 opus pulseaudio[29240]: [pulseaudio] pid.c: Stale PID file, overwriting.
Apr  1 12:22:40 opus pulseaudio[29240]: [pulseaudio] socket-server.c: bind(): Address already in use
Apr  1 12:22:40 opus pulseaudio[29240]: [pulseaudio] module.c: Failed to load module "module-native-protocol-unix" (argument: ""): initialization failed.
Apr  1 12:22:40 opus pulseaudio[29240]: [pulseaudio] main.c: Module load failed.
Apr  1 12:22:40 opus pulseaudio[29240]: [pulseaudio] main.c: Failed to initialize daemon.
Apr  1 12:22:40 opus pulseaudio[29231]: [pulseaudio] main.c: Daemon startup failed.
Apr  1 12:22:40 opus pulseaudio[189]: [pulseaudio] shm.c:  shm_unlink(/pulse-shm-796968502) failed: No such file or directory
Apr  1 12:22:40 opus pulseaudio[189]: [pulseaudio] shm.c:  shm_unlink(/pulse-shm-3528759038) failed: No such file or directory

```
...but I think these are associated with my son logging on while I was logged on (e.g., switching users)

---

### Post by opus1 on 2017-04-01
I was able to get the sound card to be recognized by pavucontrol by issuing a ```
sudo alsa force-reload
``` I had done that earlier and it didn't seem to work, but it did tonight. It also solved a problem with you tube not working ([https://ubuntuforums.org/showthread.php?t=2357412](https://ubuntuforums.org/showthread.php?t=2357412)). I'll mark this as solved and hopefully the reload trick will continue working in the future.

---

