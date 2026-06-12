---
title: "Issue running do-release-upgrade on Ubuntu 10.10 - Error in function pulse?"
date: 2011-07-24
forum: Server Platforms
---

### Post by victorhooi on 2011-07-24
Hi,

I'm running a install of Ubuntu 10.10 x86_64 (Maverick):

I attempted to do a "do-release-upgrade", and it errored out on me:
```

Get:241 http://au.archive.ubuntu.com/ubuntu/ natty/main locales all 2.13+git20100825-4 [3496kB]
10% [241 locales 4097B/3496kB 0%]                                                                                                   682B/s 14d 16h 26min 58sError in function pulse


A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

Traceback (most recent call last):

File "/tmp/update-manager-MjCQqA/DistUpgradeViewText.py", line 42, in
pulse
apt.progress.text.AcquireProgress.pulse(self, owner)

File "/usr/lib/python2.6/dist-packages/apt/progress/text.py", line
164, in pulse
apt_pkg.time_to_str(eta))

OverflowError: signed integer is greater than maximum
```

I've attached the main.log (split up, due to file size limit on these forums) and apt.log files mentioned.

It said to post a bug report, but I thought I'd post here just in case first, before filing a bug report.

Any thoughts/suggestions?

Cheers,
Victor

---

