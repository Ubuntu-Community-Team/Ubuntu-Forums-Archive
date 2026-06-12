---
title: "Why does Ubuntu perform so poorly in graphics tests?"
date: 2012-02-22
forum: The Cafe
---

### Post by nrundy on 2012-02-22
[http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129.html](http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129.html)
[http://www.phoronix.com/scan.php?page=article&item=macosx_108dp1_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=macosx_108dp1_ubuntu&num=1)

Is it mostly due to the graphics drivers in Linux? 

Is it that the drivers for linux graphics cards haven't had the same effort and time put into their development? If developers put more time and energy into improving the drivers for Linux then Linux graphics performance would be on par with Windows/Mac? Or is it something more intrinsic to Linux?

---

### Post by JDShu on 2012-02-22
I should preface by noting that both benchmarks focus on the open source Intel drivers.

> **nrundy said:**
> [http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129.html](http://www.tomshardware.com/reviews/chrome-17-firefox-10-ubuntu,3129.html)
[http://www.phoronix.com/scan.php?page=article&item=macosx_108dp1_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=macosx_108dp1_ubuntu&num=1)

Is it mostly due to the graphics drivers in Linux? 


Yes, although sometimes the compositor affects things as well.

The graphics card is in most aspects the single most complicated piece of hardware in your computer today. Writing them is hard, so the number of programmers who can are few. There are even fewer programmers who are willing and legally can write open source drivers.

Unfortunately in the case of Intel, there is a bit of a fork in efforts, where Intel is writing one mature and developed open source driver, while volunteers and other companies are writing a different one, which shares code with other open source driver efforts.

> 
Is it that the drivers for linux graphics cards haven't had the same effort and time put into their development? 
Yes. Basically.

> 
If developers put more time and energy into improving the drivers for Linux then Linux graphics performance would be on par with Windows/Mac?
Yes, the teams that write proprietary drivers are reputably much larger and have more resources than the open source developers.

> 
Or is it something more intrinsic to Linux?

Arguable. There is an argument that the Linux kernel's "unstable ABI" is discouraging hardware makers from making drivers for Linux. This is a huge debate in itself. In the case of Intel anyway, it's not an issue of willingness.

---

