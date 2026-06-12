---
title: "HDMI output on a Meerkat ION"
date: 2010-01-14
forum: Ubuntu Studio
---

### Post by MirrorMatter on 2010-01-14
Hello, everyone.

I work at a television station and we recently purchased a System76 Meerkat ION with the intended purpose of using the HDMI out port for broadcast purposes. We have an existing AJA HA5 box which is capable of converting HDMI to HD-SDI (HD-SDI being the baseband standard in professional broadcasting). The converter is only willing to accept the following values:

1920 x 1080 @ 29.97
1280 x 720 @ 59.94

I am wondering if it is possible to manually configure Xorg.conf (or whatever file is being edited by NVIDIA X Server Settings) to tell the HDMI output to only produce the latter resolution (1280 x 720). Otherwise, my boss wants it sent back.

Any ideas?

---

### Post by MirrorMatter on 2010-01-15
I may have added too much extraneous information in my initial post.  What I am wondering is simply this:

Is it possible to edit a configuration file to permanently set the output resolution of an HDMI port to 1280 x 720 and, if so, how can that be accomplished?

---

### Post by edlyk on 2010-04-07
I have the same issue, I can select 1280 x 720 output in Nvidia settings and it works great.  But with each reboot it reverts to 1920 x 1080.

---

### Post by carcare999 on 2011-02-10
One thing that might not be obvious to less observant owners of a hp  mini 311 is that they come in at least twenty different versions. (if  not more)

This in itself is not the crazy part, but rather that many problems user  A reports might not affect user B (since they don't actually have the  same hardware related to the problem).
============
[education blog](http://www.canshine.com/)
[Music](http://www.rockstopscene.co.uk)

---

