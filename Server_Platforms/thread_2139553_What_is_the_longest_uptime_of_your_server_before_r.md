---
title: "What is the longest uptime of your server before required a reboot?"
date: 2013-04-27
forum: Server Platforms
---

### Post by JnPson on 2013-04-27
I have heard or read that one Linux server had an uptime of some 2000+ days before it was rebooted. 

What is the longest uptime for your servers before a reboot was required? And what applications/servers was/is running on the servers?

I'm curious mostly because I want to learn what Linux is capable of and I wanna be amazed by Linux. 

My server has only been running for 
 ```
12:19:29 up 15 days, 18:55,  1 user,  load average: 0.64, 0.22, 0.13
```

---

### Post by HermanAB on 2013-04-27
Howdy, 

I have twice had web/email servers that ran for just a tad over four years with no maintenance, no updates and no downtime.  In both cases, the power supplies eventually failed.

So that goes all the way back to 2004.  Don't fix it if it ain't broke...

---

### Post by sandyd on 2013-04-27
So far, the longest time is 2 years (and still running).
I use KSplice with it so it never needs restarting.

Thought, I might need to break the trend soon because of Debian 7...

---

### Post by tgalati4 on 2013-04-27
tgalati4@Mint14-Extensa ~ $ uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    17 days, 01:16:17 | Linux 3.5.0-26-generic    Mon Apr  1 17:11:25 2013
     2    10 days, 01:07:06 | Linux 3.5.0-25-generic    Sun Mar 10 20:31:25 2013
     3     8 days, 07:08:15 | Linux 3.5.0-23-generic    Mon Feb 25 13:33:22 2013
     4     8 days, 06:30:06 | Linux 3.5.0-26-generic    Sun Mar 24 10:38:22 2013
->   5     7 days, 20:16:24 | Linux 3.5.0-27-generic    Fri Apr 19 14:58:07 2013
     6     7 days, 20:15:31 | Linux 3.5.0-27-generic    Fri Apr 19 14:58:01 2013
     7     4 days, 06:30:49 | Linux 3.5.0-23-generic    Wed Mar  6 07:28:22 2013
     8     4 days, 01:04:06 | Linux 3.5.0-23-generic    Thu Feb 21 08:20:30 2013
     9     3 days, 20:28:19 | Linux 3.5.0-23-generic    Thu Feb 14 15:50:40 2013
    10     3 days, 03:00:53 | Linux 3.5.0-26-generic    Thu Mar 21 07:36:53 2013
----------------------------+---------------------------------------------------
1up in     0 days, 10:13:43 | at                        Sat Apr 27 21:28:12 2013
no1 in     9 days, 04:59:54 | at                        Mon May  6 16:14:23 2013
    up    78 days, 00:03:44 | since                     Thu Feb 14 15:50:40 2013
  down   -6 days, -05:-39:- | since                     Thu Feb 14 15:50:40 2013

This is a crappy acer laptop.  

I've had a whitebox 1 GHz celeron with 512MB running Dapper Drake Desktop 6.06 continuously since 2006.  It's currently down for cleaning which I do once a year.  It really needs it.  I have an UPS on it that I've replaced the batteries twice now.  The UPS is more problematic than Ubuntu!  [http://ubuntuforums.org/showthread.php?t=1164132&highlight=uprecords](http://ubuntuforums.org/showthread.php?t=1164132&highlight=uprecords)

I typically do my updates once every 6 months, which normally require a reboot, since most of the security patches seem to affect the kernel.

---

### Post by MAFoElffen on 2013-04-27
I've been thinking along these lines... Prolonged uptime, I go through power supplies after about 2-3 years, like mentioned above. They would last longer if I blew them out better. I used to just go up and stay up. Now rethinking that strategy for pre-emptive maintenance and diagnostics before a breakdown occurs. 

I've been playing with clusters and server pools... I'm thinking that providing the server "service" in a way that the service is up, without it depending on a single server makes more sense to me... That way the service is still available when things happen or need to be done.

---

### Post by tgalati4 on 2013-04-27
You can also set temperature alarms, disk alarms, as well as UPS alarms to alert you of problems.  And with a 24/7 machine, you will get notices from all of your alarms at the most annoying times.  I once got a wakeup call at 4:30 am from my UPS on Christmas morning when I was out of town.  A Holiday drunk hit a power pole in my neighborhood knocking out power.  My UPS held up for a few minutes just long enough to send emails and text messages.  I thought my house was burning down--and there was nothing I could do about it.  So if you set alarms, remember that they will annoy you.

---

### Post by thnewguy on 2013-04-28
I avoid maintaining long uptimes. I need to make sure kernel/service updates don't introduce an error which might cause problems in the case of a reboot. For this reason I schedule regular reboots when I set aside time to make sure the system comes back up. Or, if the system doesn't come back up, my schedule is clear so I can focus on dealing with that one problem. I'd rather keep things running smoothly than have a long uptime.

The longest a machine has stayed up that I happened to be working on was around one year. I think that was a Red Hat box.

---

