---
title: "Galago CPU Frequency Slow on Battery"
date: 2014-07-27
forum: System76 Support
---

### Post by vroom2 on 2014-07-27
Hey all!

I noticed that when I unplug my Galago Ultrapro, it becomes a little sluggish. Checking the CPU frequency through i7z, I notice that the cores are maxed out at 1.2ghz on battery. On AC they're typically at 3.0ghz depending on the cpu temperature. (Go Turboboost!) One more thing I notice is that if the system starts up on battery, it can get up to 2.0ghz (which is the base frequency) just fine, but if the AC is plugged and unplugged, it hits the frequency wall again.

I tried disabling and maxing out all of the cpu controllers and power saving programs, but I haven't had any luck at getting that barrier to go away.

Doing some research, I found this thread: [http://ubuntuforums.org/showthread.php?t=1077234]("http://ubuntuforums.org/showthread.php?t=1077234&page=3") In it, the solution is found to be flashing the bios, but since this is a really nice, brand new machine, I don't really want to go around doing something dangerous for atleast a couple of years.

Could someone confirm that it's not just me experiencing these slowdowns? Has anyone come up with a solution other than flashing the bios?

Thank you!

---

### Post by monocell on 2014-07-27
I had the same issue, i7z reporting max 1.3 while on battery, even under load. I fixed it by enabling intel_pstate module. Now it goes up to 3 on battery and under load, and as a bonus it seems my battery lasts longer when I use it normally.

---

### Post by vroom2 on 2014-07-27
Thank you, monocell! That did the trick! :-)

---

