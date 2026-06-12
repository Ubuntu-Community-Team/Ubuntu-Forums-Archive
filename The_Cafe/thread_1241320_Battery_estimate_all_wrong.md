---
title: "Battery estimate all wrong?"
date: 2009-08-15
forum: The Cafe
---

### Post by Sashin on 2009-08-15
I have an acer timeline 4810T. The default gnome power applet seems to say it has 4 hours battery, while the applet and power top say it has 5-6.

Which is more accurate?

Has anyone else had similiar problems with battery estimations?

Is it possible to fix this problem, I've fully discharged and recharged in one session but it made no difference.

---

### Post by Revolutionary101 on 2009-08-15
I have had that problem with my Sony laptop. I have noticed though that the estimated time gets more accurate every time you discharge the battery.

---

### Post by Sashin on 2009-08-15
Isn't it bad for the battery to fully discharge it? And to do it several times would take a long time.

Have you tried powertop or the panel applet? Are they any better?

There must be another way to get the estimate better.

---

### Post by tgalati4 on 2009-08-15
Lithium Ion batteries need to be exercised.  Most of the on-board circuitry takes care of battery low-end, so use it until it's done.  I usually run it down to 10 to 15% then suspend or shutdown.  If you run it too low, you risk a sudden shutdown without saving your data.  This is due to the BIOS issuing a shutdown command if voltage dips to low, which can happen with a battery that's several years old.

You are lucky to get 300 cycles or 3 years whichever comes first.  In jaunty, you can see the graphs by right-clicking on the battery icon.  It keeps statistics on battery accuracy and it will get more accurate in time.

I've noticed a smaller difference between powertop and the gnome-battery applet on an older thinkpad.  They must integrate the power usage in different ways.

One thing you can be sure, you never have enough battery power.

---

### Post by coldReactive on 2009-08-15
I've had this problem with a Gateway laptop and another gateway laptop. Ubuntu would incorrectly report that the battery is at 5% and would shut down. I had to scramble to find a tutorial on how to make it so it didn't do that.

---

### Post by Sashin on 2009-08-15
So it gets more accurate over time and all I can do is wait?

---

### Post by gordonh on 2009-08-15
> **Sashin said:**
> I have an acer timeline 4810T. The default gnome power applet seems to say it has 4 hours battery, while the applet and power top say it has 5-6.

Which is more accurate?

Has anyone else had similiar problems with battery estimations?

Is it possible to fix this problem, I've fully discharged and recharged in one session but it made no difference.

Can I suggest that you could easily find out for yourself empirically in not more than 5-6 hours?

---

### Post by tgalati4 on 2009-08-16
gnome power manager 2.24.2 (Jaunty) keeps detailed statistics with an error estimate +/-%.  With only a couple of cycles, your error estimate will be 80%, so I will say that 5 hours +/- 4 hours is pretty accurate.  Only after power manager "learns" of your battery's behavior and power draw will its accuracy improve.  After 10-15 cycles it will be within 5 minutes or so of actual shutdown time.

Unless your battery has a problem, then it will shutdown suddenly without notice.

---

