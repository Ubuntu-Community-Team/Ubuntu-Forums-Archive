---
title: "Intel Iris Pro downclocking on battery"
date: 2014-08-21
forum: System76 Support
---

### Post by vroom2 on 2014-08-21
Some time back I posted a question asking about why my CPU was downclocking when on battery. I got it resolved by adding intel_pstate=enable to the grub boot options.

But now I'm starting to notice another downclocking problem: The GPU is being downclocked as well! I'm on the Galago Ultrapro.

Here's a few stats I gathered:
```
[B]Plugged in:
[/B]FPS: 23.9
Frequency: 1200MHz
GPU Watts: 33.85
GPU Busy: 100%

**Battery:**
FPS: 4.5
Frequency: 200MHz
GPU Watts: 1.93
GPU Busy: 100%
```
I've spent time researching the problem, and have found no good solutions.

Thank you!

---

### Post by monocell on 2014-08-21
Do you get the frequency from /sys/class/drm/card0/gt_cur_freq_mhz ? Mine doesn't go down when on battery for some reason. Not sure if that is good or bad since I rarely do graphic intensive stuff.I'm currently using 3.15 kernel, do you use a different one?

---

### Post by vroom2 on 2014-08-21
I got the frequency statistic from intel-gpu-overlay. My kernel version is currently 3.13. I'll try upgrading it.

---

### Post by monocell on 2014-08-21
Installing intel-gpu-overlay caused my gpu frequency to drop to 200. I can cause it to go up while on ac by moving windows around and stuff like that, but on battery it stays on 200 now. Might be worth looking what those tools actually do....

---

### Post by vroom2 on 2014-08-21
Interesting... So, I tried your method of viewing the frequency, and it says it's at 1200MHz even on battery. Yet there's still a significant drop in FPS. Comparing both the intel-gpu-overlay and /sys/class/drm/card0/gt_cur_freq_mhz, I'm thinking that the file shows the requested frequency rather than the true frequency.

Upgrading the kernel didn't help either, unfortunately. :-(

---

### Post by monocell on 2014-08-21
The frequency reported through the sys/class/... seems to be the same as requested frequency in intel-gpu-overlay, so most likely I was wrong about what the frequency was before.

---

### Post by vroom2 on 2014-08-21
I put in a support case. I'll post back once I get a reply.

---

### Post by vroom2 on 2014-08-21
So, System76 replied, and gave me the "It's not a bug, it's a feature!" style of reply. I was told that it's a BIOS "feature" and that they have no intentions to fix it.

I'm a bit unsatisfied by this, as I'm not getting the promised performance, and System76 doesn't have any plans to help get that missing performance back.

---

### Post by monocell on 2014-08-22
I tried to play with some i915 module parameters but without success. Have no more ideas right now...

---

### Post by vroom2 on 2014-08-29
Monocell, I recall in an old post that you tried installing the BIOS driver from Clevo? I'm curious to know if you're still using that and if it still continues to downclock the GPU.

---

### Post by monocell on 2014-08-29
I'm still using it and have not noticed any problems yet. However, It still downclocks.

---

### Post by vroom2 on 2014-08-29
Alright. Thank you, monocell. :-)

---

