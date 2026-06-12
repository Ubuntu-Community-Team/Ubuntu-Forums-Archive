---
title: "Speed Difference in Firefox 3.6 &amp; 3.7"
date: 2009-11-13
forum: The Cafe
---

### Post by sports fan Matt on 2009-11-13
Is there much of a speed difference?  And what addons work with the versions?

(I know with Firefox 3.7 I had issues trying to type in the search box)

---

### Post by squilookle on 2009-11-13
I can't even get 3.7 to run. I just got 3.6b2 running (the first one crashed as soon as it started) and its fast enough. 

I'm not even sure if theres a notable difference between 3.6b2and 3.5. Don't get me wrong: the faster the better, but I have no complaints about the speed of 3.5. Maybe I'll notice something after I've used it for a while. 

But so far, so good.

---

### Post by slumbergod on 2009-11-13
I didn't try 3.7 but when I installed 3.6b2 I found it to be more or less the same as 3.5.x, which is plenty fast enough for me anyway. It's only the slow startup that is a bit long but considering I only start it once a day that isn't really an issue either.

I also tried Chrome and I didn't think that was any faster either.

---

### Post by perfectska04 on 2009-11-13
> **slumbergod said:**
> I didn't try 3.7 but when I installed 3.6b2 I found it to be more or less the same as 3.5.x, which is plenty fast enough for me anyway. It's only the slow startup that is a bit long but considering I only start it once a day that isn't really an issue either.

I also tried Chrome and I didn't think that was any faster either.

I agree, on a regular desktop - the performance difference is hardly noticeable between all the current offerings; it's often best to choose the most stable release. Firefox takes a bit longer to start up and shut down, though.

However, I can't say the same for underpowered hardware, such as netbooks. The difference between Firefox and Chromium is like night and day, specially for the more complex websites and when dealing with multiple tabs.

---

### Post by wilee-nilee on 2009-11-13
Generally you can force the add-ons to work, the easiest way is the add-on nightly tester tools.

---

### Post by lovinglinux on 2009-11-13
> **wilee-nilee said:**
> generally you can force the add-ons to work, the easiest way is the add-on nightly tester tools.

+1

---

### Post by wojox on 2009-11-13
I compiled 3.7 about a month ago. I keep switching around for the latest and greatest. Tried Opera and Chrome. Always come back to Firefox in the repo's. I think what helps is just to configure it properly. Lovinglinux's Firefox optimization page is a great tutorial to keep it running lean and mean.

---

### Post by phrostbyte on 2009-11-13
Firefox 3.6 is at least 2x faster with JavaScript performance on 64-bit Ubuntu (vs 3.5). This is because the 64-bit Firefox 3.5 (or below) lacks a JavaScript compiler. There isn't much of any difference in the 32-bit versions however.

---

### Post by lovinglinux on 2009-11-13
> **phrostbyte said:**
> There isn't much of any difference in the 32-bit versions however.

Perhaps on fast machines with dual core, but in my setup (P4) there is a considerable difference. I did some tests with 3.6a1 compiled with optimization flags and it got 10% better performance on Peacekeeper benchmark. Nevertheless, the most important difference was that 3.6.a1 was able to play flash video much better than 3.5, almost without stuttering.

---

### Post by phrostbyte on 2009-11-13
> **lovinglinux said:**
> Perhaps on fast machines with dual core, but in my setup (P4) there is a considerable difference. I did some tests with 3.6a1 compiled with optimization flags and it got 10% better performance on Peacekeeper benchmark. Nevertheless, the most important difference was that 3.6.a1 was able to play flash video much better than 3.5, almost without stuttering.

Fair enough, 10% is not within my subjective opinion of significant. :) If you compare the 64-bit version of 3.5, and 3.6, you may notice a ~250% improvement.

---

### Post by lovinglinux on 2009-11-13
> **phrostbyte said:**
> Fair enough, 10% is not within my subjective opinion of significant. :) If you compare the 64-bit version of 3.5, and 3.6, you may notice a ~250% improvement.

I agree with you, but as I said, the major difference is when playing flash. I guess I find 10% significant, because I have been optimizing Firefox for a long time and a 250% improvement from where I'm now would be a miracle :)

To understand what I'm talking about, I started optimizing Firefox 3.0 just after Jaunty release, when I was getting 220 points in the Peacekeeper benchmark and ended up with 1100 on 3.6.a1. You can see my benchmark chart and optimization techniques at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by phrostbyte on 2009-11-14
> **lovinglinux said:**
> I agree with you, but as I said, the major difference is when playing flash. I guess I find 10% significant, because I have been optimizing Firefox for a long time and a 250% improvement from where I'm now would be a miracle :)

To understand what I'm talking about, I started optimizing Firefox 3.0 just after Jaunty release, when I was getting 220 points in the Peacekeeper benchmark and ended up with 1100 on 3.6.a1. You can see my benchmark chart and optimization techniques at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

That's a really good writeup. :)

---

### Post by lovinglinux on 2009-11-14
> **phrostbyte said:**
> That's a really good writeup. :)

Thank you.

---

