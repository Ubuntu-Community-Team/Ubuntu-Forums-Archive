---
title: "jack sound output cracks (GT-100), changing buffer size and priority doesn't help"
date: 2013-07-04
forum: Ubuntu Studio
---

### Post by zeebe on 2013-07-04
Hi fellow Open Source users!
I've been using Linux for a while, and I also want to use Ubuntu Studio for audio production to get rid of Windows.
Everything works so far (the GT-100 is directly supported, cool!), but one problem persists. 

Problem: 
The sound output cracks arbitrarily. Sometimes a little, sometimes more. When looping a sample, the cracks appear at different positions.
No cracks on recordings

Software: 
Ubuntu Studio, Kernel Linux 3.8.0-25-lowlatency 
jackd 0.122, protocol 24 (no idea what that means ^^)
jackctr
superlooper
audacity

Hardware:
i7, 8GB, should be fast enough
Audio Interface: Boss GT-100

So-far-approaches:
I already tried the following approaches, which did not resolve the issue:
1.) Changed buffer size and cycles (when going below 128 samples, the input cracks as well, that's ok). With 512 samples (also tried 1024 and more), the input works (**no XRuns**), but while playing, it still cracks 
2.) Changed process priorities, standard: superlooper -6, jackd -20. Also disabled rt.
3.) Removed PulseAudio
4.) Updated everything 

I'm running out of ideas what else could be the problem, so I'd appreciate any help. If you need any more information, just tell me.

Greets - zee

---

### Post by zeebe on 2013-07-06
ok, this problem seems to be caused by a bug in the new usb kernel drivers: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1136110?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1136110?comments=all) .
Lets hope it will be fixed soon. 
Greets.

---

