---
title: "Updating Jack, Ardour, Alsa, LV2..."
date: 2010-06-07
forum: Ubuntu Studio
---

### Post by Megatron3000 on 2010-06-07
Hello, i'm using the 2.6.28 rt kernel with ubuntu 8.04, and am making music. Jack and Ardour can't really handle what i'm trying to do, and the hardware should be up for it. Yesterday i realised my Jack is quite the old version (i think 1.0.9). The new one 1.9.5 has support for multicore and all of that jazz, but it's not in synaptic. Ardour and Alsa and more are also old versions, though they all appear to be the newest available in synaptic. Is there a way to upgrade all of these, without having to compile them? Thanks!

---

### Post by sgx on 2010-06-07
> **Megatron3000 said:**
> Hello, i'm using the 2.6.28 rt kernel with ubuntu 8.04, and am making music. Jack and Ardour can't really handle what i'm trying to do, and the hardware should be up for it. Yesterday i realised my Jack is quite the old version (i think 1.0.9). The new one 1.9.5 has support for multicore and all of that jazz, but it's not in synaptic. Ardour and Alsa and more are also old versions, though they all appear to be the newest available in synaptic. Is there a way to upgrade all of these, without having to compile them? Thanks!

[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

this is an ongoing topic back on page 2 here, Mr Falk has a PPA repository with what you need, but the surrounding apps needed to bring 8.04 to 10.4 might be too much, so it may be better to do a fresh install. You can install plain Ubuntu, then add the Ubuntu Studio collection from the Meta packages Universe section using synaptic, or install the studio itself.
If you have specific things to accomplish, people can comment on
similar usage, and what you might expect or need. If you do backups and
are ready with new install media, you can add the falk ppa with directions at the webpage, if you just update the latest kernel, jackd, and ardour to start, it might work. Ardour will likely bring in a long list of updates, nothing out of the ordinary for such a time 
differential.
Cheers

---

### Post by Pablo_F on 2010-06-07
I don't think you will find recent versions of applications precompiled for a hardy based system. You would have a hard time for building them form source too. In the last two years, a lot of development has taken place upstream and many libraries are outdated. I strongly recommend upgrading to lucid or at least karmic. If you want to be even more close to the latest upstream releases without the need of compiling, some PPA's are your friend.

Cheers! Pablo

---

### Post by eric71 on 2010-06-08
64 Studio 3 is built on Ubuntu Hardy. If you add this source in Synaptic:

deb [http://apt.64studio.com/backports](http://apt.64studio.com/backports) hardy-backports main

you'll be able to get newer versions of many audio apps, including jack and Ardour.

---

