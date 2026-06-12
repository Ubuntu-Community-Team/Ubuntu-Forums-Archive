---
title: "Suggestion for default install"
date: 2013-11-08
forum: System76 Support
---

### Post by hggdh on 2013-11-08
First of all, sorry if this is not the correct venue.

Got my laptop, seems to be exactly what I needed/expected. Thank you, System76.

Now, I think that in general, users would benefit if the following packages were also installed by default:

* ntp -- ntpdate has been announced deprecated; eventually we will have no option but to replace it. And yes, there is a bug opened on it, quite a long time ago. But my main issue with ntpdate is that it will only sync on IF up. So, if you keep your machine up, with no changes on NICs or reboots, the clock will slowly diverge. NTP solves this.

* rng-tools -- allows for better entropy pools, lowering the change of starvation.

This is it.

Cheers,

---

