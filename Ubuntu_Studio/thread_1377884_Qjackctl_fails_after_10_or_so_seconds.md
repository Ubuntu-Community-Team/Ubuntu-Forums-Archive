---
title: "Qjackctl fails after 10 or so seconds"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by green1152 on 2010-01-10
Hi,
I'm having an issue with qjackctl. If I start it in both root or user it does the same thing. I noticed that this doesn't happen when the rt box is unchecked in settings and it only happens when jack is started. Here's what I've got from the log:

```
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
16:32:53.279 Server configuration saved to "/home/chase/.jackdrc".
16:32:53.285 Statistics reset.
16:32:53.376 Client activated.
16:32:53.378 JACK connection change.
16:32:53.404 JACK connection graph change.
16:32:53.425 XRUN callback (1).
cannot use real-time scheduling (FIFO at priority -4) [for thread -1238660240, from thread -1238660240] (22: Invalid argument)
16:32:55.384 XRUN callback (83 skipped).
16:32:57.397 XRUN callback (82 skipped).
16:32:59.415 XRUN callback (83 skipped).
16:33:01.422 XRUN callback (82 skipped).
jackd watchdog: timeout - killing jackd
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
```

Any ideas? Jack was working last time I used it with no problem. Today it is completely failing. I'm not sure if I installed something that might have done this or not.

Thanks for the help in advance.

---

### Post by green1152 on 2010-01-10
Update:
I got rid of the memory problem, but I'm still getting these XRUN Callbacks. Here's another one from the log:

```
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|512|3|48000|2|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
18:28:58.742 Server configuration saved to "/home/chase/.jackdrc".
18:28:58.747 Statistics reset.
18:28:58.847 Client activated.
18:28:58.850 JACK connection change.
18:28:58.884 JACK connection graph change.
18:28:58.912 XRUN callback (1).
18:29:00.861 XRUN callback (41 skipped).
18:29:02.868 XRUN callback (41 skipped).
18:29:04.884 XRUN callback (41 skipped).
18:29:06.894 XRUN callback (41 skipped).
jackd watchdog: timeout - killing jackd
```

---

### Post by green1152 on 2010-01-11
Update again:
I've reinstalled all that is jack with little success. I'm still getting about four of these XRUNS and then it kills jackd and freezes. Jack does start with real-time off, but I need it on.

Anyone?

---

### Post by AutoStatic on 2010-01-11
Hello green1152,

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
Paragraph on Real-Time Kernel & Xruns.
And what kind of soundcard do you have?

---

