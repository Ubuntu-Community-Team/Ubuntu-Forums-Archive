---
title: "ipw2200 on Pangolin Value"
date: 2007-04-19
forum: System76 Support
---

### Post by jhofmann on 2007-04-19
Problem:  The built-in wifi adapter (Inter PRO/Wireless 2915BCA) wasn't working well at home.  Worked fine around town with other Access Points, but not with the home AP.  On the other hand, a Linksys WPC11 Ver 3 worked out of the box perfectly.

Error Messages:  About every 20 seconds /var/log/messages shows ipw2200: detected firmware error.  Restarting.

Ping to a wired computer on the home network running about 25-50% packet loss, average time 150-300 ms over a one minute period.

Completely unusable behavior.

Much googling turned up Error 800  from Bugzilla, but no solution, and I couldn't find any recent work on the problem.  Intel suggested darkly "timing errors causing frame dropping".  

Here's where the System 76 part comes, maybe.
Solution:  Found the "antenna" option in modinfo output.  It says there are 4 settings
0 is default, both antennas; 1 is main antenna only; 2 is something called Slow_Diversity; and 3 is Aux antenna.

Carefully trying each option by using modprobe ipw2200 antenna=N, I learned that when antenna=3 results were just as good for the intel  2915 as they were for the Linksys pcmcia card, and in any case excellent.  Ping results now 0% lost packets, average time 2.28 ms over the same 1-minute interval.

I suppose this is all just informational, but if anyone has input I'd like to read it.  What does the solution have to do with the problem, for instance?

Jim.

---

### Post by hardyn on 2007-04-19
does sys76 sell support with their machines? or support through this forum only?

givem a call, if you are entitled to support.

good luck.

---

### Post by crichell on 2007-04-19
That is interesting.  Take a look at the pic I attached.  The Intel IPW2200 has two connectors.  Main and Aux.  Maybe the Main has loosened up or become disconnected.

---

### Post by jhofmann on 2007-04-23
You guessed right.  I wiggled the Main Antenna connector and now it works.  Thanks for the picture, too.  

Jim

---

