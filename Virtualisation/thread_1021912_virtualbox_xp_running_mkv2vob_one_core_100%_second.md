---
title: "virtualbox xp running mkv2vob one core 100% second core 12 %"
date: 2008-12-26
forum: Virtualisation
---

### Post by Russell Burrows on 2008-12-26
I have Ubuntu 8.10 no problems and virtualbox runs good running tinyxp.

As soon as I run mkv2vob to transcode a x264 video file on my dual core toshiba laptop satellite l305d-s5892 I get:

Core one at 100% and core two from nine % to 17%

Is there any way to even out the loads on these two cores?

Thank you.

---

### Post by Dedoimedo on 2008-12-26
Unless the kernel can do it + application can do it, any hack on your behalf will be suboptimized. Multiple cores are a good idea, but not all OS / applications (with system access) can utilize them in the best fashion.

This may interest you:
[http://en.wikipedia.org/wiki/Non-Uniform_Memory_Access](http://en.wikipedia.org/wiki/Non-Uniform_Memory_Access)

Dedoimedo

---

### Post by Russell Burrows on 2008-12-26
Thanks.

I am going to give this a try_:

[http://www.hardware.info/en-US/news/ym2cmZqYwp2a/Problems_updating_to_a_dualcore_CPU_Not_anymore/](http://www.hardware.info/en-US/news/ym2cmZqYwp2a/Problems_updating_to_a_dualcore_CPU_Not_anymore/)

---

