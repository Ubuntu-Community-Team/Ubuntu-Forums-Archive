---
title: "A story of a tricky hardware RAM problem"
date: 2017-08-19
forum: The Cafe
---

### Post by stlu on 2017-08-19
Hello Ubuntu users,

I wanted to share a story about my efforts to diagnose and solve a problem with a computer I bought 'refurbished' to serve as a Ubuntu server on my LAN.  I still don't know the exact problem, and it's probably going to remain a mystery forever, but at least I can describe it to you.

I've had this computer for about 1 1/2 years.  Back when I first used it, the problem was so annoying that I gave up and let it rot.  It would run fine for about a week or two, then just freeze at the hardware level.  There was never a kernel panic or anything, just a rock solid freeze.  Further, running memtest would pass. (I only ran one pass back then)

After a different computer died this month, I returned to investigating the problem, in hopes that I could replace my dead PC with this one.  I ran memtest for a week, and that showed up an error.  Except, a week later, the same test showed another error at a totally different memory address.  I became fairly certain that the memory modules were not the cause of the problem.

Finally, I was bored and observed that there was only one of the two cores being used, so I tried memtest's SMP mode.  Well this changed things.  I got a freeze at exactly 7:10 into the test.  Every time.  It happened around 6gb (of 8gb total).  Remaining confident that the memory was not the issue, I removed three of the four 2gb modules, thinking that maybe the issue was with addressing higher-numbered addresses. Sure enough, the memtest passed with SMP on.

So I decided to leave the system with only 2gb of RAM, and I haven't had a problem since.  It isn't smart to use this machine at all, but it's role is not critical to me.
But this story, if anything, shows how running memtest only once, or only on one core, can leave more tricky problems undetected.

---

