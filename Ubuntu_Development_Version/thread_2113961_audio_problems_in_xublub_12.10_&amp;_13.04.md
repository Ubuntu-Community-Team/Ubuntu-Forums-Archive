---
title: "audio problems in xub/lub 12.10 &amp; 13.04"
date: 2013-02-08
forum: Ubuntu Development Version
---

### Post by Flipflop McFly on 2013-02-08
Morgaes from Multimedia & Video Support suggested I post here.

I've tried installing Xubuntu 12.10, Lubuntu 12.10, and Lubuntu 13.04 on my Sony Vaio PCG 792L laptop, and have never gotten a lick of sound out of it, despite trying many suggestions (ie, unmuting the speakers...)

I've currently re-installed Ubuntu 10.04, and it works as before... which is to say, with sound.

But I'd sure like to use a new Lubuntu, instead - it runs *so well* on this! (well... except for the above-mentioned...)

Anyway, I know fixing this one issue for this one kind of laptop may not be high on anyone's list of priorities (I installed Xubuntu 12.10 on an older Sony Vaio laptop, and it was a smashing success.) But, if anyone wants my stats, or knows how I might fix it, let me know.

Thanks!

FFMcF

---

### Post by kansasnoob on 2013-02-08
Let's start out with some very basic stuff. Would you please post the output of these two commands:

```
lspci | grep Audio
```

```
aplay --list-devices
```

But Morgaes pointed you in the right direction :)

In fact we're doing Alsa Smoke Tests the next several days:

[http://packages.qa.ubuntu.com/qatracker/milestones/256/builds/37166/testcases](http://packages.qa.ubuntu.com/qatracker/milestones/256/builds/37166/testcases)

---

### Post by kansasnoob on 2013-02-08
I posted a comment at Lubuntu QA also:

[https://lists.launchpad.net/lubuntu-qa/msg01807.html](https://lists.launchpad.net/lubuntu-qa/msg01807.html)

---

### Post by Flipflop McFly on 2013-02-08
Thanks for taking the time for this.

I'm running Lubuntu 12.10 right now, because I made two discs of Lub 13.04 (from [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)), and neither loaded right (the second was just in case the first burned poorly). I WAS able to run off the LiveCD of 13.04, which is why I feel confident that the same sound issue still exists - "speaker-test" remained silent.

I hope my posting my 12.10 stats is still helpful.

scuttlebutt@scuttlebutt:~$ lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

scuttlebutt@scuttlebutt:~$ aplay --list-devices

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ALSO from a previous install of 12.10, here's some more info:

Your ALSA information is located at [http://www.alsa-project.org/db/?f=9c5f7c05a4464f179ca20b787f8b23db37514e8a](http://www.alsa-project.org/db/?f=9c5f7c05a4464f179ca20b787f8b23db37514e8a)

(maybe that's no longer valid, since I've re-installed since then. But I don't remember what generates that useful link!)

Thanks again; hope it helps. Now back to looking at the blizzard.

---

### Post by kansasnoob on 2013-02-09
I've been studying, not nearly done yet, but I think these two bugs are related:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1065696](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1065696)

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1078317](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1078317)

If it's kernel related we may want to try a [Mainline Kernel]("https://wiki.ubuntu.com/Kernel/MainlineBuilds") but hold off for just a while and see what else we can learn.

---

