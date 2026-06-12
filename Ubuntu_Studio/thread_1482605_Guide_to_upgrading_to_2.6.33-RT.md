---
title: "Guide to upgrading to 2.6.33-RT?"
date: 2010-05-13
forum: Ubuntu Studio
---

### Post by Cclips on 2010-05-13
So I'm using 10.04, and it is still on the 2.6.32 kernel, which while it has a preempt patch, utterly fails in comparison to the RT patch from 2.6.31 or whatever was in Karmic. I was wondering if anyone could give me a guide to installing the 2.6.33-RT kernel. I've found mixed results on the web as to the release date of the 2.6.33, it seems the kernel is out, but the RT patch isn't? If someone could clear that up as well I would be grateful.

Thanks

---

### Post by hxcobd on 2010-05-13
There's this common misconception that you need an "-RT" kernel image in order to use realtime audio, for some reason. This is untrue and generally just wasted effort. You may want to scope out the RT audio tutorial in my sig for the lowdown.

---

### Post by Cclips on 2010-05-13
Hmm, well I tried to do some simple guitar tuning and the latency was pretty bad. It is simply the switch to 10.04 not being optimized for latency? US 9.10 was pretty solid in terms of latency from the get go...

---

### Post by hxcobd on 2010-05-13
There shouldn't be much (or any) difference, assuming your hardware was pretty well-supported from the get-go in both 9.10 and 10.04.

Adding the 3 lines of RT-capable code to limits.conf and then tweaking JACK appropriately should give you the performance you're used to. What are your JACK settings?

---

### Post by Cclips on 2010-05-13
I just followed your video tutorials and it works wonderfully, my latency problems are absent, and it works like a peach. It makes me wonder just what the RT patch does that takes so long to develope/distribute.

Thanks again, your videos are a great resource.

---

### Post by hxcobd on 2010-05-13
I've been wondering that myself for a long time as well, my friend. I fail to understand why an edit so simple demands an entire new kernel header...

Glad it worked out for you, though!

---

### Post by trulan on 2010-05-13
In answer to the question in the first post, here's some info on that kernel:
[http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264)
Not that I'm saying you should use the RT kernel; if the generic is working for you, great!

Why does the RT kernel seem to be so slow in coming?  Well, the demand for it is much lower, and the team of developers is much smaller.  It does however fill a very much needed place in the Linux world, both in manufacturing (which is driving the continuing development) and in Linux audio.

---

### Post by mango42 on 2010-05-14
Pardon my perennial ignorance but is this why I am getting loads of xruns in 10.04 64bit (on an nVidia SLI equipped laptop) with *only* QJackCtl/Jackd running?

Couple that with a lack of **QTractor** and a readable 16:10 screen resolution (where has my favourite 1440x900 disappeared to and how do I regain it?) this talk of rolling yer own RT kernel is too scary for an old codger like me, so back to 9.10 whilst you boffins thrash it out.

The Lucid Studio install, however, was the very smoothest yet - well done, devs!

---

### Post by bojo42 on 2010-05-21
just to clear things up:
- there is no rt patchset for 2.6.32
- therefore you only have the 2.6.31 based RT kernel in Ubuntu 10.04

and yes in case you can live without an RT kernel you REALLY should stay on regular kernels. But for my experience there are cases where you still need the RT kernel to get good latency without xruns. therefore i did packages for a 2.6.33 RT kernel, see my PPA:

[https://launchpad.net/~bojo42/+archive/rt](https://launchpad.net/~bojo42/+archive/rt)

---

### Post by psidrum on 2010-05-21
I use Softmode in Jack on a dualcore amd64, running WineAsio VSTs and they all sound great with multiple apps open

---

