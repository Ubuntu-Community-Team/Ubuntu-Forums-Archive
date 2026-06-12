---
title: "[SOLVED] Differences -rt &amp;amp; generic kernels?"
date: 2008-11-28
forum: Ubuntu Studio
---

### Post by rylleman on 2008-11-28
What is the difference between the generic kernel and the realtime one?

I use my machines for graphics and video editing, no audio recording/editing.
Do I really need the -rt kernel? Noticing it is a bit behind the generic in versioning.

---

### Post by Abu_Dayya on 2008-11-28
realtime kernel is better suited for audio recording and provides low audio latency

read this thread
[http://ubuntuforums.org/showthread.php?t=658923](http://ubuntuforums.org/showthread.php?t=658923)

Hope that helps

---

### Post by Stochastic on 2008-11-28
Strong audio timing is the only benefit to the rt kernel, and in 8.10 there are major bugs in the rt kernel so it'd be smart to stick with vanilla.

---

### Post by rylleman on 2008-11-28
Thanks, 
that was what I suspected. I've had some serious problems since 8.10 upgrade with nvidia and alsa so I'm gonna try to switch to generic kernel to see if thing improve.

---

### Post by markbuntu on 2008-11-30
The current rt kernel will not work with the nvidia or ati drivers, or see more than one core of a cpu. It would really pay to wait a while on this one

---

