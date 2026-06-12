---
title: "Call for Testing: Alsa 1.025"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-02-14
There's a new version of alsa bound for precise, and for the time being it's in the ubuntu audio dev ppa. Check out my post for the details if you want to help test:

[http://www.theorangenotebook.com/2012/02/call-for-testing-alsa-1025.html](http://www.theorangenotebook.com/2012/02/call-for-testing-alsa-1025.html)

The timeline on this testing (and most testing this week!) is Feb 16th so it can be completed in time for feature freeze.

I know some no sound issues have crept up during the precise cycle, so let's test and stamp them out.

---

### Post by prusswan on 2012-02-14
no sound issue persist (sound devices showing Dummy Output, requiring sudo alsa force-reload)

hardware info (when sound is working):
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 02bb
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f6500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel


```

---

### Post by dino99 on 2012-02-15
Seems faulty :( might be too late for Precise.

---

### Post by balloons on 2012-02-15
If you haven't could you file a bug report on these issues? Please make sure when filing to tag it "alsa-1.0.25", and mention you are testing from the ubuntu audio dev ppa. Here's some quick links for bug filing. Thanks for testing!

alsa-lib
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+filebug](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+filebug)

alsa-utils
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+filebug](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+filebug)

alsa-plugins
[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+filebug](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+filebug)

alsa-driver
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+filebug](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+filebug)

---

