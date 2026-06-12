---
title: "Using UTC as localtime"
date: 2007-03-09
forum: Server Platforms
---

### Post by jfdill_2 on 2007-03-09
I'm switching some (and maybe eventually all) Linux / Unix servers that I maintain to use UTC as localtime.  I'm still thinking this through, there may be practical considerations for abandoning this idea and just putting up with future changes to DST.

1. In a perfect world, logs should be in UTC and log reporting and web statistics tools should be able to handle the translation from UTC to local time if desired.

2. In a perfect world, TZ should be tied to the individual user preferences and not applied universally at the system level.  This is a much better approach to allow users from multiple timezones to share one system with expected results, but also introduces additional complexity e.g. how to handle user scheduled tasks, and how to store and retrieve user TZ information.

The justification for changing to UTC is primarily for reporting purposes i.e. I will be able to say with 100% certainty that servers will not be affected if there is a change to DST, no verification is necessary, and I don't have to prove anything.  Patches are already done on a regular schedule anyway, but there could still be a little sliver of doubt.  I am already aware of several facts which don't really need to be repeated:

1. in /etc/default/rcS UTC=yes specifies that RTC is UTC (on Ubuntu and Debian derrivatives)

2. systems that dual-boot with Windows (which are generally NOT servers anyway) need UTC=no because Windows and its applications do not consistently respect RealTimeIsUniversal, therefore RTC must be localtime for the time to be consistent under Windows and its applications

3. most time-dependent functions on POSIX systems reference UTC and not time as represented by applying the offset specified by the local timezone, BUT there are some exceptions, most notably cron and atd which run according to local time

4. most e-mail clients translate time of sent message to local time, so e-mail sent by server on UTC is not an issue

Reading log files in UTC I think I can get used to.  The issues lie where users interface with the system, either shell access or reporting such as web statistics, those should probably be rendered in localtime.  Web applications are another area to look at--most should interpret time correctly, but there are probably some exceptions.

For cron, atd, and BackupPC, I have just added the following to the beginning of the init.d startup scripts, but there is probably a more universal way to implement this:

export TZ=GMT+5 # substitute your localtime or preference here

A better approach might be to check if localtime = UTC, then if that is the case, reference another variable from /etc/default/rcS for applications such as cron that you may want to run relative to local time rather than UTC.  Translating all cron jobs to their respective UTC times would add complexity to install scripts which add cron entries.

I decided to use a straight offset to UTC so that things will always happen at a consistent time w.r.t. UTC that will not be affected by DST changes--this also eliminates the possibility of tasks being skipped at the beginning of DST or run twice at the end of DST, although several implementations of cron now have hacks to cope with this.  Using UTC also eliminates ambiguity in log files at the end of DST where 1-2am timestamps occur twice.

For my intents and purposes, I think this is "close enough" even though w.r.t. local time it will shift by an hour when there are DST changes.  Mainly, this is going to affect maintenance tasks that run once a day outside "normal operating hours".  If I had a more international user base, it might make sense to just let things run relative to UTC, or set a different offset.

---

### Post by Mr. C. on 2007-03-10
This seems like a lot of work for seemingly little benefit.  What real problem are you trying to solve?  Updating tzdata files is pretty trivial, and occurs so rarely, as to be a non-issue.

Pretending that you machine is sitting in Greenwich vs. in your own location seems peculiar, but if that works for you.

Good luck,
MrC

---

