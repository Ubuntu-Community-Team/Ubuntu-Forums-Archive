---
title: "snd_pcm_avail() returned a value that is exceptionally large"
date: 2010-05-10
forum: System76 Support
---

### Post by akwala on 2010-05-10
Is anyone else seeing the following error on a System76 Serval?[FONT=monospace]
[/FONT]```
pulseaudio[5077]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 18446744073709544436 bytes (418293516369 ms).
pulseaudio[5077]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
```
My ALSA & kernel versions:
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
```Bug reports:
[https://bugs.launchpad.net/fedora/+source/linux-meta/+bug/374002](https://bugs.launchpad.net/fedora/+source/linux-meta/+bug/374002)
[https://bugs.launchpad.net/linux/+bug/464442](https://bugs.launchpad.net/linux/+bug/464442)

---

### Post by isantop on 2010-05-10
Are you using Fedora? We don't get errors like that on the Serval in the shop. It may simply be an Ubuntu thing.

---

### Post by akwala on 2010-05-10
> **isantop said:**
> Are you using Fedora? We don't get errors like that on the Serval in the shop. It may simply be an Ubuntu thing.
I only have Ubuntu 10.04 on my Serval. Yes, it probably is an Ubuntu/ALSA thing.

---

### Post by isantop on 2010-05-10
Two questions:

1. What is your model number? You can check from the System76 Driver.

2. Did you upgrade to 10.04 or did you do a clean install?

---

### Post by akwala on 2010-05-10
> **isantop said:**
> 
1. What is your model number? You can check from the System76 Driver.
serp4

> **isantop said:**
> 2. Did you upgrade to 10.04 or did you do a clean install?
upgraded 9.10 -> 10.04

---

### Post by akwala on 2010-05-11
Here's the excerpt from syslog that shows the error...

---

### Post by isantop on 2010-05-11
What symptom does this cause? Does the audio stutter or skip, or stop, or become lower quality, etc?

---

### Post by akwala on 2010-05-11
> **isantop said:**
> What symptom does this cause? Does the audio stutter or skip, or stop, or become lower quality, etc?
I am not 100% sure that this error causes or contributes to the stuttering/skipping. In this particular occurrence, the sound was OK for the first few seconds, then the skipping/stuttering started, and within less than a minute an error mentioning GStreamer popped up. It was the first time that I'd seen this error and, unfortunately, I didn't capture it Will try to reproduce and post it.

---

### Post by akwala on 2010-05-11
Reproduced it at the first attempt...
- started with skipping/stuttering
- skipped to next track
- more skipping/stuttering
- skipped to next track
- error!
[I]- sound stops
- error box on desktop can't be closed.[/I]
...all within seconds.

---

### Post by isantop on 2010-05-12
Try having a look at [this thread](http://ubuntuforums.org/showthread.php?p=9288726#post9288726), specifically post number 39. They may help fix your problem.

---

### Post by akwala on 2010-05-12
> **isantop said:**
> Try having a look at [this thread]("http://ubuntuforums.org/showthread.php?p=9288726#post9288726"), specifically post number 39. They may help fix your problem.
:)
Yep, did that, and it did fix the stuttering/skipping. The "exceptionally large value" hasn't happened since this fix and hopefully it'll stay that way.

Thanks.

---

### Post by akwala on 2010-05-16
The problem returned, but updating to the latest dev ALSA driver seems to have helped -- see my comment #12 on this bug report: [https://bugs.launchpad.net/linux/+bug/464442](https://bugs.launchpad.net/linux/+bug/464442)

Repo for the dev drivers: ppa:ubuntu-audio-dev/ppa -- install the linux-alsa-driver-modules package corresponding to your kernel version.

---

