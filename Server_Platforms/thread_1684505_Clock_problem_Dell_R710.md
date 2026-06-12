---
title: "Clock problem Dell R710"
date: 2011-02-09
forum: Server Platforms
---

### Post by radiognome on 2011-02-09
I have this problem with (one of my) servers, a Dell R710, running Lucid.

[Time not kept on NTP server]("http://ubuntuforums.org/showthread.php?t=1683236")

After one more day of trying, the problem reduces as this:

No matter how I set the system-clock (from hardwareclock or NTP-server), after approx. 4.4 minutes the time falls back 4.4 minutes and stays there. Having NTP on or of makes no difference.

When NTP is on, it says it is synced with an offset of ±266 seconds or so to all of the servers
With the NTP-daemon off, I simply find different times with the commands 'date' and 'hwclock -r'.

I tried different 'clocksource=' settings at boot (hpet, tsc and acpi_pm) but that did not change the behavior. ±5 minutes correct time and correct NTP-sync etc.. then ±4.4 minutes behind everyone and admitting to do so......

Please, I am running out of clever ideas about the cause. Anyone a clever suggestion where I can look (on the server or on the interweb)??

Kind regards, Martin

---

### Post by vguzman on 2012-09-05
radiognome: Did you resolve this issue?
I'm facing this same problem.  But the problem is not exactly with time synchronization, but with server freezing.  It just hangs for 266 seconds, that's why the time lost sync. 
The server is Dell too, but my OS is CentOS, kernel 2.6.18-274.18.1.
Thank you,

VG

---

