---
title: "Local clock jitter 500ms (according to ntp root dispersion)"
date: 2015-11-18
forum: Server Platforms
---

### Post by donbowman on 2015-11-18
I have 3 servers runny Wily. All 3 are showing the same problem (500ms clock jitter according to ntp root dispersion).

Root dispersion is the jitter vs the received ntp clock (e.g. it shows how inaccurate the local clock is). I am expecting this to be ~50ms

All 3 servers are synched to a stratum-1 upstream clock that is 4ms away +- 0.2ms.

I have tried 'tsc','hpet', and 'acpi_pm' as clock sources, they do not affect this.

I have tried chrony vs ntpd, both show the same issue.

I tried running 'lowlatency' kernel instead of generic, same issue.

I tried upgrading to 4.3 kernel, same issue.

This is a big problem for me since they run ceph mons, and the clock skew keeps getting a mon kicked out of the cluster. They also run rabbitmq and it is having trouble.

My other servers (running vivid) show ~50ms of root dispersion.

My first thought was (these 3 servers are X5650 based) was this was the nonstop vs invariant vs constant tsc issue (but the acpi or hpet should have fixed that then), so i have disabled C-states (dell m610, i disabled C1E and c-states, i also set 'performance' in the power management)... None of this had any affect. Once the ntp clock locks, gettimeofday is |500ms|. (The x5650 has nonstop-tsc and constant-tsc but not invariant-tsc fwiw).

I've kind of run out of ideas as to what to check. Also, i don't understand why the server running vivid (which is identical hardware) is fine (root dispersion == 90ms on it) when the 3 running wily have an unacceptable root dispersion.

---

### Post by tgalati4 on 2015-11-18
I would file a bug against kernel 3.20 or whatever [version]("http://http://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version") above Vivid where it breaks.  If these are monitoring/configuring servers, is there a reason why you can't run 14.04 LTS?

*ntp* with a proper drift file can get + or  - 1 ms, so even 50 ms is huge for an hourly drift.  *ntp* fails with 500 ms drift (as you have discovered).  A chronometer is certified at +6 to -4 seconds per day.  I guess it is better to be early than late to a meeting.

Some reading:

[http://superuser.com/questions/745018/ntp-how-are-ntp-servers-so-accurate](http://superuser.com/questions/745018/ntp-how-are-ntp-servers-so-accurate)

[http://doc.ntp.org/4.2.6p2/miscopt.html#driftfile](http://doc.ntp.org/4.2.6p2/miscopt.html#driftfile)

[http://www.atmythoughts.com/living-in-a-tech-family-blog/2014/2/28/what-time-is-it](http://www.atmythoughts.com/living-in-a-tech-family-blog/2014/2/28/what-time-is-it) (mac-based, but good explanation)

[http://www.math.ucla.edu/~jimc/documents/bugfix/12-ntp-wont-sync.html](http://www.math.ucla.edu/~jimc/documents/bugfix/12-ntp-wont-sync.html)

1999 vintage, whitebox PC, Dapper Drake, 6.06 LTS, sub-millisecond drift:

---

### Post by donbowman on 2015-11-18
Thanks.
It doesn't seem to be drift, e.g. its not trending up or down, its oscillating around a value.
And, its on each ntp request.

I tried disabling the various CONFIG_NO_HZ* options, and that had no affect [this was my first suspicion, its the only config-change between 3.19 (vivid) and 4.20(wily)].

Note that the wall-clock is in general correct on them. chrony suggests that 1 server is 55.915 +- 0.009ppm, and another is 58ppm.

I'm a bit baffled how hpet and tsc and acpi_pm all give this same 500ms root dispersion.

---

### Post by Bucky Ball on 2015-11-18
*Thread moved to **Server Platforms**.*

Three servers running an interim release? I would be looking to stick with LTS releases, but you might have a specific reason not to (and spare time to upgrade three servers every six months, which is not a great plan). Good luck with finding a fix. :)

---

### Post by tgalati4 on 2015-11-19
Yes, it is confusing that all three clock sources are off.  You would expect at least one clock source to be accurate enough to keep time.

Post the output of each server:

```
ntpq -4c pe -c as
```

Run 14.04 in a Live Session.  Install *ntp* (it will be in RAM only), set up your *ntp* configuration file and run some queries.

After looking at the specs for the Dell m610; this is a blade server.  Perhaps there is a Dell utility to configure the blade clocks to synchronize to a chassis or master clock.  I don't know.  I don't have experience with this hardware.

---

### Post by donbowman on 2015-11-19
I switched one of them back to ntp from chrony to run that query (both daemons gave the same behaviour anyway).

ps I really like the live session idea, I will try that next.

From the server i switched back to ntp, this is the output. Its the rootdisp in the ntpq -c rl that
is what I am focused on.
```
[FONT=lucida console]
[/FONT]
 
[FONT=courier new]$ ntpq -4c pe -c as [/FONT]
[FONT=courier new]     remote           refid      st t when poll reach   delay   offset  jitter[/FONT]
[FONT=courier new]==============================================================================[/FONT]
[FONT=courier new]+ntp1.torix.ca   .PPS.            1 u  112  128  377    4.478   -5.543  10.003[/FONT]
[FONT=courier new]+ntp2.torix.ca   .PPS.            1 u   46  128  377    4.530   13.793  17.184[/FONT]
[FONT=courier new]*ntp3.torix.ca   .PPS.            1 u  112  128  377    4.516   -6.610  13.084[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]ind assid status  conf reach auth condition  last_event cnt[/FONT]
[FONT=courier new]===========================================================[/FONT]
[FONT=courier new]  1 12868  941a   yes   yes  none candidate    sys_peer  1[/FONT]
[FONT=courier new]  2 12869  941a   yes   yes  none candidate    sys_peer  1[/FONT]
[FONT=courier new]  3 12870  961a   yes   yes  none  sys.peer    sys_peer  1[/FONT]

[FONT=courier new]$ ntpq -c rl[/FONT]
[FONT=courier new]associd=0 status=0615 leap_none, sync_ntp, 1 event, clock_sync,[/FONT]
[FONT=courier new]version="ntpd 4.2.6p5@1.2349-o Fri Oct 23 16:44:04 UTC 2015 (1)",[/FONT]
[FONT=courier new]processor="x86_64", system="Linux/4.3.0-040300-generic", leap=00,[/FONT]
[FONT=courier new]stratum=2, precision=-22, rootdelay=4.529, rootdisp=**533.016**,[/FONT]
[FONT=courier new]refid=206.108.0.133,[/FONT]
[FONT=courier new]reftime=d9f90d33.32355470  Fri, Nov 20 2015  3:08:35.196,[/FONT]
[FONT=courier new]clock=d9f90ea6.695041cf  Fri, Nov 20 2015  3:14:46.411, peer=12870, tc=7,[/FONT]
[FONT=courier new]mintc=3, offset=6.222, frequency=39.600, sys_jitter=16.220,[/FONT]
[FONT=courier new]clk_jitter=13.628, clk_wander=2.261[/FONT]
```







Yes it would be cool if dell ran a reference clock down the backplane, but i'm pretty sure no.
[and these blades all worked well before i upgraded to wily].

---

### Post by Bucky Ball on 2015-11-19
(Please use code tags for terminal stuff. See last link in my signature. Thanks. :))

---

### Post by tgalati4 on 2015-11-19
Check the Dell website for a firmware update.  Perhaps there is a fix, since this seems to be a problem deep into the hardware.

---

### Post by bee4oo on 2015-11-21
That looks like a problem with the upstream torix.ca servers. All three seem to report a large dispersion (even though they are stratum 1), which clients include in their dispersion. The fix is simple, find better servers. :D

---

