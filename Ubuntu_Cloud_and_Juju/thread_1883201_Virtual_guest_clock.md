---
title: "Virtual guest clock"
date: 2011-11-18
forum: Ubuntu Cloud and Juju
---

### Post by nc_gatech on 2011-11-18
I want to synchronize the time on all our ec2 instances. All the  instances are m1.large and use Ubuntu 10.10 (running in paravirtual environment on xen). The time on most of the  instances is 30-60 seconds behind the actual time.

Let me ask first. Given the above information, what would be the right way to fix the clock?

I installed openntpd, and I could immediately see that it started making  the system call adjTime with the correct offset (~35 seconds), and the  system clock gradually moved towards the correct time.

So far so good. However, the value in the file  /sys/devices/system/clocksource/clocksource0 is "xen", which makes me  believe that the system clock on the virtual instance can suddenly jump back to  the host time. Most of the posts I have come online suggest that we  should set the clocksource to be "jiffies". But this doesn't work as the  only available clock sources are "xen" and "tsc".

Also, I am not sure if reboot would have any effect.

Any pointers/hints will be very helpful.

Thanks.

---

