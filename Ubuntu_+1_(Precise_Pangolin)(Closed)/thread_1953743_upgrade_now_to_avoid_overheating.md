---
title: "upgrade now to avoid overheating?"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mercedes on 2012-04-06
Greetings (again) from a chronic newbie.

I just installed oneiric on a Thinkpad T61, which I am using while my primary (Zareason) computer is in the shop. I had been reading about overheating problems with a variety of Core2 computers, and now I see that I'm having the same problem: CPU temperature breifly went up to 92 deg C today, while running only the handful of programs I need for work. 

I understand that this issue, while not really fixed, has been patched in Precise. So close to release date, I'm thinking about upgrading now to avoid overheating and harming my computer (rather than trying the numerous workarounds various people have suggested). I use this computer about 8 hrs/ day for work (mostly for pretty pedestrian word-processing-type tasks). 

Would I be running a big risk if I upgraded now?

Thanks for taking the time to read this,

Mercedes

---

### Post by xyzzyman on 2012-04-06
> **mercedes said:**
> Greetings (again) from a chronic newbie.

I just installed oneiric on a Thinkpad T61, which I am using while my primary (Zareason) computer is in the shop. I had been reading about overheating problems with a variety of Core2 computers, and now I see that I'm having the same problem: CPU temperature breifly went up to 92 deg C today, while running only the handful of programs I need for work. 

I understand that this issue, while not really fixed, has been patched in Precise. So close to release date, I'm thinking about upgrading now to avoid overheating and harming my computer (rather than trying the numerous workarounds various people have suggested). I use this computer about 8 hrs/ day for work (mostly for pretty pedestrian word-processing-type tasks). 

Would I be running a big risk if I upgraded now?

Thanks for taking the time to read this,

Mercedes

Even on Oneiric I only peaked at 80degreesC with my Core 2 Duo T9400 (2.53GHz). So far on Precise I still am hitting 77degrees while compiling or transcoding 1080p video files. You shouldn't be hitting 90degrees under regular use even without some of the tweaks in Precise... Unless you're having an issue with the fan not turning on, etc...

As far as your question, you can always try a live cd of precise and see if that makes a difference. If it does you can try upgrading, but updates are still over 100 MB's worth a day and pretty consistent so no guarantees no major issues.

---

### Post by mercedes on 2012-04-09
I opted not to upgrade, just because I don't want to run any risks on my main work computer. I ended up installing lm-sensor and thinkfan, and it seems that the problem is solved. It will be interesting to see how this issue plays out in Precise.

---

### Post by craig10x on 2012-04-10
I'm running 12.04 beta2 on hard install for a while now and i have definitely noticed a difference...I have Psensor installed and temperatures are generally much lower then they were prior to the patch being added into the kernel... 

I get the impression that it very much now manages the power much like the way it does on windows (which of course, was the goal)....

So, it should work well for you when you are ready to move over to 12.04...

---

### Post by xyzzyman on 2012-04-10
> **craig10x said:**
> I'm running 12.04 beta2 on hard install for a while now and i have definitely noticed a difference...I have Psensor installed and temperatures are generally much lower then they were prior to the patch being added into the kernel... 

I get the impression that it very much now manages the power much like the way it does on windows (which of course, was the goal)....

So, it should work well for you when you are ready to move over to 12.04...

What's your processor?

---

### Post by Linuxisfast on 2012-04-11
Ubuntu 12.04 beta uses less CPU and runs cooler compared to older Oneiric. This on my AMD C50 Asus Eeepc netbook. Also CPU load is far less as I can monitor with indicator-multiload, earlier on the CPU load would be sustained, now its far less.

---

