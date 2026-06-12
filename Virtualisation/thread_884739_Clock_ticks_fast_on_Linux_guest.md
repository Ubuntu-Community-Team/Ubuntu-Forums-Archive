---
title: "Clock ticks fast on Linux guest"
date: 2008-08-09
forum: Virtualisation
---

### Post by divisortheory on 2008-08-09
I've found a few threads about this, but none of them have been sufficient to fix the problem for me it seems.

I'm using an Ubuntu guest on a Windows XP host and the clock on the guest ticks much faster than it's supposed to.  In the other threads I've found about this there were a number of suggestions:

*1) Upgrade your linux kernel, newer versions address this.*
 - I'm already using a newer version than the one that was suggested.  Mine is 2.6.24-19.generic

*2) Append "clock=pit" or "clock=pmtmr" to the end of the kernel line in the GRUB boot loader configuration file.*
 - I've tried both of these, although I believe pmtmr is the default on newer linux kernels.  pit seems to be the most accurate

*3) Synchronize time with VMWare Tools.*
 - This is currently enabled on my guest.

Before I did any of this, my clock was ticking at about 1 minute every 10 seconds.  Now seems to lose about 1 minute every hour.  So this definitely helped but it's still way too fast.  Is there anything else I can do?  Can I control the interval at which VMWare Tools syncs with the guest?  If so I can set it to synchronize with the guest like every 10 minutes or something.  It doesn't appera to have synchronized in the past 10 hours.

---

### Post by Masoris on 2008-08-12
[http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html](http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html)

---

### Post by dvord on 2008-11-03
Same thing.  Tried the suggestions in the link but my clock is running at double speed.

The article doesn't mention dual or quad core processors.  Mine is a quad.

---

