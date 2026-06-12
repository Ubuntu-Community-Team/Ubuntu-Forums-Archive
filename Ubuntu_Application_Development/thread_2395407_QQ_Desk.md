---
title: "QQ Desk"
date: 2018-07-01
forum: Ubuntu Application Development
---

### Post by quequotion on 2018-07-01
So I finally got around to [trying this again]("https://ubuntuforums.org/showthread.php?t=2354059").

After pulling many, many teeth, I finally have [a working package in a working PPA]("https://launchpad.net/~quequotion/+archive/ubuntu/qqdesk/+packages")!

I call this fork of indicator-cpufreq "indicator-powersave". In fact, it no longer depends on cpufreq; but uses sysfs to control various power consumption options. It is not an automated daemon like tlp, but a user-discretion utility.

It has a backend bash script, /usr/bin/throttle, which can be used independently on the command line.

---

