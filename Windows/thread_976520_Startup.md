---
title: "Startup"
date: 2008-11-09
forum: Windows
---

### Post by inxygnuu on 2008-11-09
I have noticed that When my Windows Vista starts, the thing that takes longer than anything else, is just the loading of that dumb little circle animation that makes the fancy sounds. is there a way to disable that? I am asking this because it takes my computer an extra 30 seconds to load a useless animation. this may also be a non-harmful way to speed up someone else's computer by removing/disabling an almost useless animation w/ sound.

thanks in advance,
Evan

---

### Post by RoyalShrubber on 2008-11-09
I don't think any animation will add 30 seconds to boot time, these things are designed to be lightweight, you could only save few milliseconds if you disabled animation. The problem probably lies in bad drivers/software that runs at startup. Remove the crap and report. 
If it's not like 5 minutes then I'd say it's not big problem, how long does your Vista takes to boot? 

You could even put Vista to sleep or in hibernation mode instead of using classic full shut down - this way Vista will open way faster.

---

### Post by inxygnuu on 2008-11-09
about 160 seconds; and It seem as what it is doing is it shows my mouse, then it goes black, wits, then shows that animation. I think that loading the animation (finding the file and loading it all up) is slowing boot up time. Also, what about when I need to restart my computer? In fact, I keep it on most of the time...

---

### Post by Grant A. on 2008-11-09
Is this a computer with Windows Vista preloaded? Long boot times are sometimes caused by malware, or possibly bloatware from when you bought the computer. I noticed after I removed the HP Advisor from my computer, the boot time sped up considerably. If you don't have a virus scanner you can find a free one [here](http://free.avg.com/).

---

### Post by RJARRRPCGP on 2008-11-09
> **inxygnuu said:**
> about 160 seconds; and It seem as what it is doing is it shows my mouse, then it goes black, wits, then shows that animation. I think that loading the animation (finding the file and loading it all up) is slowing boot up time. Also, what about when I need to restart my computer? In fact, I keep it on most of the time...

I had the same problem, too, Vista boots like Windows without prefetch! 

Just like Windows 2000, where it takes its sweet time to boot and when you keep it logged in, it's fine.

---

### Post by inxygnuu on 2008-11-12
> **Grant A. said:**
> Is this a computer with Windows Vista preloaded? Long boot times are sometimes caused by malware, or possibly bloatware from when you bought the computer. I noticed after I removed the HP Advisor from my computer, the boot time sped up considerably. If you don't have a virus scanner you can find a free one [here](http://free.avg.com/).

Yes, it came with it, but I clean installed it after Ubuntu ate it:lolflag: so, it can't be any of that because i have my system with scanners that don't boot with the system.:)

---

### Post by Viranh on 2008-11-13
go to run ( in Vista you need to use super+R I think) and type either msconfig or services.msc. services.msc is supposed to be safer. You will be able to choose "selective startup" and uncheck any unnecessary programs in the services tab. This should speed up boot time.

---

### Post by Betsybuntu on 2008-11-14
Microsoft has a nice application for servicing services in Vista that has better UI and more options than MSConfig. In Services.msc you have access to the "Delayed Start" option, coming soon in 7 is "Triggered Start" as well. Above MSConfig, Services, and Windows Defender is AutoRuns if you're knowledgeable enough to use it correctly.

Whatever you do, remember to leave the ReadyBoost service enabled.

---

### Post by inxygnuu on 2008-11-15
Bumpity bump :(

---

