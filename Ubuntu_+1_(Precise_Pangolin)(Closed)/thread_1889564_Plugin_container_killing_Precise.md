---
title: "Plugin container killing Precise"
date: 2011-12-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-01
The plugin container is just turning Precise into molases (very non-responsive dektop).with high CPU usage.

---

### Post by r_mano on 2012-01-25
Yes, and Natty too. Spinning like crazy as soon as you have some tab with flash in it. 

There is a proposal to stop it here [http://blog.gnu-designs.com/solved-firefox-high-cpu-load-with-plugin-container/](http://blog.gnu-designs.com/solved-firefox-high-cpu-load-with-plugin-container/) , but it's a bit a hammer version. 

Annoying.

---

### Post by effenberg0x0 on 2012-01-26
> **ventrical said:**
> The plugin container is just turning Precise  into molases (very non-responsive dektop).with high CPU usage.

I believe I had posted about it here in the previous cycle. In my case  it always was flash-related. I just had to kill or remove flash and  things were fine again.

I also remember one time I found out that NVidia installation was  completely messed up. There was a soft-link loop in /usr/lib/libGL*  & /usr/lib32/libGL*, some other links were pointing to mesa, and  some to nvidia - it was unusable. I had to manually check and fix each  link.

<Rant> I have recently become very frustrated with Flash and am  trying to remove it from most of my installs. Why is it that no release  simply works reasonably well after so much time? It was supposed to be  mature right now. I'd be OK with a couple bugs, of course. But, at least  in my personal experience (browser opened for days - many tabs), there  hasn't been a single usable release until now. And we've been out of  luck with FOSS flash plugins so far :( And HTML5.... Oh well, where is  it?</rant>

Regards,
Effenberg

---

### Post by r_mano on 2012-01-26
In the firefox thread someone says that it's a problem of interaction with the plugin-container when showing flash content and Download Helper extension (see [https://support.mozilla.org/en-US/questions/708035](https://support.mozilla.org/en-US/questions/708035) ).

I will try to disable DH to test it (although it's a pity). 

<rant approved>

---

### Post by r_mano on 2012-01-26
No, disabling Download Helper did not help. Definitely helps disabling flash plugin, but well...

---

### Post by ventrical on 2012-01-26
One of my installs of Precise will now only  play HD video versions on youtube by default and will not play because that machine does not have the HD gear to run it.

---

