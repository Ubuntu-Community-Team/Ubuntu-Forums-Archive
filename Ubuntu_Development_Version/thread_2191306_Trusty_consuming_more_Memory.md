---
title: "Trusty consuming more Memory?"
date: 2013-12-01
forum: Ubuntu Development Version
---

### Post by fantab on 2013-12-01
I have noticed that Trusty is consuming more 'memory' than the earlier versions. For instance, in 13.10, with no additional applications open, but the default processes the RAM consumption is about 600Mib-700Mib, under the same conditions 14.04 consumes 1.12Gib-1.15Gib of RAM.

I also disable a few of 'Startup Applications', and I have same 'Startups' in both.
I have swappiness set to '20'... in both, 14.04 and 13.10.

(CPU consumption is about same, in both).

Has anybody else noticed this?
I was wondering if its just me, or does it affect more users.
What could be the reason, a bug or a new feature or something else?

Regards...

---

### Post by mc4man on 2013-12-02
Don't see anything near that here.
A minute or so after boot/login with no apps  run is  typically  around 400

---

### Post by ventrical on 2013-12-02
1. Trusty with 14 tabs open in FF + CCSM cube etc....
2. Trusty with only ccsm cube etc..

---

### Post by sammiev on 2013-12-02
Here's Trusty Gnome with FF open in many tabs.

---

### Post by fantab on 2013-12-06
Thank you all for the feedback.

Ubuntu boots 'now' with around 370Mb-390Mb of RAM consumption. (No steps were taken towards acheiving this).

However it sometimes starts with consuming 600Mb-700Mb and with firefox and other applications it shoots to above 1Gb.
When it does so I have checked the logs, dmesg etc. but nothing tells me what's going on or why RAM consumption shoots up.
I reboot when I see bloated Memory consumption, and after reboot things are back to around 400Mb. In last few days I must have booted Ubuntu about 8-10 times, out of which on three ocassions I have the said issue.

Any ideas?

---

### Post by mc4man on 2013-12-06
I might start with creating a start up script using pidstat to write to a log file, maybe like 30 reports 5 sec apart (could be allowed to overwrite previous log
(you could 1st. create a base log to compare if desired

Then if you can find 'offending' pid(s) take a further look

Man pidstat for info (part of sysstat package

---

