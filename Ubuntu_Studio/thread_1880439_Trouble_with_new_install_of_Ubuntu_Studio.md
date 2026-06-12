---
title: "Trouble with new install of Ubuntu Studio"
date: 2011-11-13
forum: Ubuntu Studio
---

### Post by jroa on 2011-11-13
I just did a fresh install of Ubuntu Studio 11.10 and I have been trying to get it to work for the last day and a half.  Surprisingly, my wireless adapter worked perfectly on the first boot.  However, I can't seem to get any sound out of my machine.

I checked the checked the checksum of the iso before burning and checked the media after burning.  Both were fine.  The last time I used Ubuntu was 10.04 and my sound worked fine back then, so I assumed that it should work fine with a newer version.

Should I just install regular Ubuntu 11.10, get the sound working, and then install the studio applications manually, or should I keep jacking around with this install?

---

### Post by jejeman on 2011-11-13
I suppose that cabels are connected fine.
give us output from
```
aplay -l
```And alsao say if it is laptop, desktop?

---

### Post by jroa on 2011-11-14
Sorry for the delay.  I had to go to work.

The cables are fine.  When I boot into Windows, the sound works.  Before installing Ubuntu Studio, I had Fedora 14 on the same partition and it worked there as well.

Here is the output for aplay -l.

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The computer is a desktop with an integrated sound card.  I tried running Audacity and recording with a mic.  Usually, I would be able to see the sound wave as I play back, but it showed just a straight line, so the input and output are not working.

Before the install, I installed Ubuntu Studio on a virtual machine and had the same issue.  I was hoping that a full install would give different results, but it did not.

I think I am going to download and burn a live Ubuntu CD to make sure the problem is not with Ubuntu.

---

### Post by jejeman on 2011-11-14
The card is supported by alsa. Open alsamixer and see if there is something muted or turn down. Also check sound preferences for same things.

---

