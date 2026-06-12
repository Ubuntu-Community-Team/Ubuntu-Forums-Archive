---
title: "Has lesswatts.org been discontinued ?"
date: 2015-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by blade4 on 2015-11-22
It's been almost 4 years since I last used a linux distro so I'm a bit out of the loop here.

---

### Post by Habitual on 2015-11-22
It doesn't seem to have an A Record (An IP assigned to a web-serving host)

---

### Post by blade4 on 2015-11-22
> [COLOR=#000000]It doesn't seem to have an A Record (An IP assigned to a web-serving host)[/COLOR]

Ah fudge . It's not a temporary thing then is it.

---

### Post by Habitual on 2015-11-23
It doesn't seem so, no.
I also notice that Intel Corporation owns the domain.
The [waybackmachine]("http://web.archive.org/web/*/lesswatts.org") shows

       Saved 135 times                                            between     October 2, 2007     and     April 3, 2013.                     
and is consistent with whois info for the domain.
```
...
Domain ID: D148718546-LROR
Creation Date: 2007-07-27T20:01:29Z
Updated Date: 2013-06-12T00:20:22Z
Registry Expiry Date: 2021-07-27T20:01:29Z
...
```

---

### Post by tgalati4 on 2015-11-23
What did you need from the website?  Most of the power-saving routines for Intel processors have been merged into the current kernel or as utilities that you can add.  Things like scheduling, custom processor C-states, custom clock tables, custom voltage tables etc.

> 
tgalati4@Mint17 ~ $ apropos cpufreq
cpufreq-aperf (1)    - Calculates the average frequency over a time period
cpufreq-info (1)     - Utility to retrieve cpufreq kernel information
cpufreq-set (1)      - A small tool which allows to modify cpufreq settings.
tgalati4@Mint17 ~ $ cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.47 GHz
  available frequency steps: 1.47 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.47 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.47 GHz.
  cpufreq stats: 1.47 GHz:15.19%, 1.07 GHz:1.86%, 800 MHz:82.95%  (29933)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.47 GHz
  available frequency steps: 1.47 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.47 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.47 GHz:13.74%, 1.07 GHz:1.59%, 800 MHz:84.67%  (28767)


---

### Post by blade4 on 2015-11-24
> [COLOR=#000000]What did you need from the website? [/COLOR]

I was mostly looking to refresh my memory. I've been off linux for almost 4 years now and just recently installed wiley. 
Anyway, thanks for the info. Do you know if any other website has taken up the mantle ?

---

### Post by Habitual on 2015-11-24
The mantle of what?
What did lesswatts.org "do" or provide?

---

### Post by tgalati4 on 2015-11-24
Lesswatts.org was set up as a repository for open source Intel processor routines to save power.  This was a time when Intel was getting slapped by low-power server boards made by upstart companies.  Who can argue that a bunch of ARM9 processors on a server board can't perform what a Xeon does at a fraction of the the power.  200 watts vs 15 watts.

So Intel came up with methods to monitor wake-ups, which poke the processor and prevent the CPU from entering it's deep sleep, or power-saving mode.  Basically by identifying what processes or components (interrrupts) wake up the processor, you can turn them off or reschedule them to allow the CPU to sleep longer and save power.  Good for laptop/tablet battery life, not much use for a server which needs to run 100% get the workload/watts efficiency.

There were whitepapers, I have downloaded a few, which explain the technologies involved.  The advent of lower-power processors and system-on-a-chip architecture (think RaspberryPi) have made these efforts less useful today, but the basic principles can still be applied.

I don't know if an archive was set up.  Perhaps send an email to Intel for the history.

---

