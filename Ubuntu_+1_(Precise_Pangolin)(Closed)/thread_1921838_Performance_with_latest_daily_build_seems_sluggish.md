---
title: "Performance with latest daily build seems sluggish. Everyone or just me?"
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kaldor on 2012-02-07
I've not been testing Ubuntu for the last few days now. So, I zsync'd the iso and put it on my USB drive. Everything feels like crap.

Window dragging lags, scrolling is choppy, launching programs is slow, the app menu lags when rolling over the options, etc. This is all off the liveUSB and it was really smooth and excellent the last time I tried a few days ago. Even booting up seemed to take longer.

Have there been any new packages that may have caused this regression? Thinking stuff related to unity, xorg, etc.

---

### Post by effenberg0x0 on 2012-02-07
> **kaldor said:**
> I've not been testing Ubuntu for the last few days now. So, I zsync'd the iso and put it on my USB drive. Everything feels like crap.

Window dragging lags, scrolling is choppy, launching programs is slow, the app menu lags when rolling over the options, etc. This is all off the liveUSB and it was really smooth and excellent the last time I tried a few days ago. Even booting up seemed to take longer.

Have there been any new packages that may have caused this regression? Thinking stuff related to unity, xorg, etc.

Hi Kaldor, 

Fresh installs of PP Alpha seem to run at a normal performance for me. 

My first bet would be related to VGA drivers and settings in the session. We know that in some cases (related specially to ATI hardware), there have been reports mentioning a need to adjust display settings at CCSM for a proper perfomance, for example (I remember "Sync to VBlank" being mentioned as mandatory for some ATI hardware). 

Regarding non-video related performance issues: We have also seen reports of longer boot times related to modem-manager and network-manager. And as these packages were removed, some users perceived immediate improvements in boot time.

It'd be interesting if you could grep your logs, to see if you can find some leads. And report them at a Launchpad bug report for the live session.

You'll have to investigate it a little. Please report your findings.

Regards,
Effenberg

---

### Post by kaldor on 2012-02-07
Typing from my main PC using the same USB drive. Everything here is working excellently. And just to clarify, this PC is the one with the Radeon card. The PC with the sluggishness is a laptop using the Nouveau driver with an 8400m. I also disabled sync to vblank to no avail in CCSM.

I'll hop on the laptop in a bit and take a look at the logs to see if there's anything interesting. 

Side note: The squared artwork is pretty sleek. I don't remember this a few days ago :)

---

### Post by ventrical on 2012-02-07
> **kaldor said:**
> I've not been testing Ubuntu for the last few days now. So, I zsync'd the iso and put it on my USB drive. Everything feels like crap.

Window dragging lags, scrolling is choppy, launching programs is slow, the app menu lags when rolling over the options, etc. This is all off the liveUSB and it was really smooth and excellent the last time I tried a few days ago. Even booting up seemed to take longer.

Have there been any new packages that may have caused this regression? Thinking stuff related to unity, xorg, etc.


  I haven't run the Live USB for a while now. But all is well  on regular installs.

---

### Post by mc4man on 2012-02-07
> **kaldor said:**
>  The PC with the sluggishness is a laptop using the Nouveau driver with an 8400m. I also disabled sync to vblank to no avail in CCSM.

With a laptop here that has a 8400m the live session is pretty good, it's when installed & using nvidia drivers that there are some performance breakdowns.

Many of those can be traced to either a small lag in or no upclocking of the gpu when needed which is currently way more often then  in compiz-0.8.x & early 0.9.x
(performance levels in Powermizer

Most noticeable in moving windows, scrolling in gedit & Firefox, either choppy or showing h-tearing in gedit
(there are a few other 'out of the blue' performance issues not related to the gpu clock/performance level

I've decided to force Max clock speeds when on ac thru xorg.conf

---

### Post by kaldor on 2012-02-08
Follow up.

I retried with today's daily build and everything is back to the way it should be. Next time I find one of these problems I'll wait a day before making a conclusion.

---

