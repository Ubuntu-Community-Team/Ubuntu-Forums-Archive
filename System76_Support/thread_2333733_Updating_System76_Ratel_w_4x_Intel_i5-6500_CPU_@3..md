---
title: "Updating System76 Ratel w/ 4x Intel i5-6500 CPU @3.2GHz - Odd Error Msg"
date: 2016-08-12
forum: System76 Support
---

### Post by re1d on 2016-08-12
I am having this issue on a System76 Ratel, new this spring, running a 6th generation i5-6500 3.2GHz CPU, a Samsung 850 SSD, and the optional NVIDIA GeForce GT730 video subsystem. I updated to 16.04 about a month after it came out, with no issues. 

Recently while doing updates, I get the following message:  ```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
```  This shows up on the terminal window that reflects your update progress. Each time it occurs, a lo-o-o-ong wait ensues, after which the update finally seems to complete. It runs normally otherwise. If I run Software Updater again, it just says that software is up to date - no error.

This hasn't actually prevented updating yet, but it has occurred several times. It would *seem* to be saying that firmware is missing for the CPU. Yet the computer runs just fine. 

Has anyone else run into this, and if it is a problem is there a fix? Thanks!  :confused:

---

### Post by re1d on 2016-08-15
Got this answer from System76 Support:

[COLOR=#574F4A][FONT=&amp]"There are a few bugs surrounding the Intel graphics driver in your system. I know the next kernel has several updates to that driver purposed. If there isn't anything wrong with your system right now, it will be safe to ignore that message. I'm guessing it goes away soon. It's only a warning message, not an error."
[SIZE=2]
So that may be it - aside from causing updates to take a  long time, it seems to have had no ill effects. Here's hoping it's a bug that's squashed soon!

[/SIZE]
[/FONT][/COLOR]

---

