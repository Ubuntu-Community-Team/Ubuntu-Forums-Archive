---
title: "kernel contest for hard-edged conditions"
date: 2010-01-01
forum: Ubuntu Studio
---

### Post by bluesscream on 2010-01-01
Happy New Year!
bluesscream has some free days 'between the years' as they say in his country. So he messes around with audio live performance and latencies, compiles some (for him) new software and kernels, 
found i. e. ck bfs 
[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/)
compiled 2.6.32-ck2 (be a little careful, may be setting timer at max 10000 eats system performance)
and tested this against karmic repo's 2.6.31-9-rt and 2.6.31-17-generic (all with maximized frequency scaling)
his impressions: 
-17-generic will do realtime jobs in standard conditions
If someone needs wine-wineasio vst support Con Kolivas' patch works best.
For highest end  native linux audio -9-rt with tweaked irq and priority  is the best choice [http://ubuntuforums.org/showthread.php?t=1328175](http://ubuntuforums.org/showthread.php?t=1328175).
Made these tests under jackd 1.9.4 with svn compiled Bristol [http://sourceforge.net/projects/bristol/](http://sourceforge.net/projects/bristol/) and horgand [http://horgand.berlios.de/](http://horgand.berlios.de/) (both easy to compile, should be updated in unbuntu's repos - their obsolete versions have not even old jack support)
That's just bluesscream's experience under very limited time and hardware conditions.

---

### Post by AutoStatic on 2010-01-02
Nice! I really want to try BFS too, did you experience any noticeable improvements concerning latency, drop-outs etc?

---

### Post by bluesscream on 2010-01-03
I did it for nosiness, masochism and ever-present greed for another 1/2 ms lower latency ;) I guess numbers will not say much considering varieties of hardware and individual settings.  For a ck/bfs patched 2.6.32.2 I can't verify noticeable audio benefits against tweaked cfs 2.6.31-9-rt except when using a wine/wineasio/reaper/vsti-instruments setting which here is stable w. no xruns at jack 4ms latency (64 frames, 3 buffers). 
Noticeable I find the stupendous realtime capabilities of actual karmic's 2.6.31.17-generic: There will be no more need for any other kernels if one can live with standard audio apps on a low end to midrange hardware at 8 to 16 ms jack latency free of xruns and crackling. Had a nice experience with actual aeolus, it runs stable at 4ms jack-latency in all these kernels and environments. Most important for successfull audio production still will be maximized cpu-frequency.
But further on we should hold an eye on Con Kolivas' patches. I'll watch their updates and give them a try immediately insofar I have the leisure...

---

### Post by AutoStatic on 2010-01-04
I'll give it a go too one of these days. But like you, I'm very satisfied with the 2.6.31-9-rt kernel and indeed, the generic kernel does well too.

---

