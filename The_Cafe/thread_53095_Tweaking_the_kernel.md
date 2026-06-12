---
title: "Tweaking the kernel"
date: 2005-07-30
forum: The Cafe
---

### Post by Jujimufu on 2005-07-30
Can someone list some good websites or resources for tweaking the linux kernel?  I'm interested in learning more about this for increasing system performance and to satiate my own curiosity.  Thanks!

---

### Post by macgyver2 on 2005-07-30
The best place to start is in the kernel itself.  99% of the options are documented and they'll give you jumping off points for specifics you can just lookup on google.  For instance, preemptability, the different schedulers...

Also, specifically to performance...sometimes you can get better performance by getting rid of things you don't need in the kernel.  If you never use certain options, get rid of them.  If you only use them occasionally, consider making them modules (if they already are not).

And [here]("http://www.kernelnewbies.org/")'s a site I know of that might have some info you're looking for.

---

