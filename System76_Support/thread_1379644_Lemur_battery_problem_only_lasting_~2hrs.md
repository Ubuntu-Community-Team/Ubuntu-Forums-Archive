---
title: "Lemur battery problem: only lasting ~2hrs"
date: 2010-01-12
forum: System76 Support
---

### Post by Phil Urich on 2010-01-12
So, my family went and got my sister a Lemur UltraThin for Christmas (arrived recently since we ordered it WAY too late, but it came in time for the new school year).  So far for the most part she's quite satisfied, but unfortunately there's one rather crucial exception: the battery life.  Even with the wireless off and the screen dimmed, she's still only getting around 2 hours of battery life, which unfortunately isn't nearly enough to make it through the day's classes.

It came with 9.10, naturally, and we've done the upgrade to the latest System76 driver (updating first with Synaptic, and then running the utility to install the latest drivers).

Is this right?  I had read between 4 and 5 hours in varying answers.  I did go with the 7200rpm drive as the only modification from the stock configuration, which I suppose would drain more battery power, but it wouldn't really halve the battery life, right?

Here's the battery state and info (I'm typing this from it right now . . . I'm too used to my netbook, the keys are too big, heh).  In this case the screen is dimmed almost but not all the way, and naturally the wireless is on:

[quote=/proc/acpi/battery/BAT0/info]
present:                 yes
design capacity:         2800 mAh
last full capacity:      2741 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 260 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            BAT
serial number:           0001
battery type:            LION
OEM info:                NOTEBOOK
[/quote]

[quote=/proc/acpi/battery/BAT0/state]
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      832 mAh
present voltage:         10799 mV
[/quote]

---

### Post by thomasaaron on 2010-01-13
No, it should get about 4 hours. There's a chance she got a dud battery, but the readings you posted seem to indicate otherwise.

What all has been installed on the computer? I'm wondering if there is something constantly running that is taking a toll on the battery. If she goes to System monitor and lets us know the top several processes that seem to be using CPU time...

Don't worry. If you got a dud battery, we can get you a new one.

---

### Post by Paul Stone on 2010-01-13
These links may (or may not) be helpful.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1)

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php)

Good luck!  :)

---

### Post by Paul Stone on 2010-01-13
One more...

[https://wiki.ubuntu.com/ReducedPowerUsage](https://wiki.ubuntu.com/ReducedPowerUsage)

Edit: That wiki appears to contain old information, which may no longer apply.

---

### Post by thomasaaron on 2010-01-14
The Lemur definitely should get about 4 hours with normal usage. So, unless something she downloaded is causing problems...

---

### Post by Phil Urich on 2010-01-16
The only software changes she made were installing MythTV (which didn't work and caused problems, so that's gone now anyways) and installing Pidgin since Empathy wasn't working right.  

At first I thought myself that MythTV was a likely culprit, but she's used the laptop since then and it doesn't seem to have changed the rate at which the battery is draining.  But that being said, she hasn't used it a huge amount in the past few days.  Literally at this very moment though she has the laptop running, having unplugged it after a full charge, to do a more scientific test and see exactly how long the battery lasts (letting it entirely run down).

I had her on the phone and got her to check the System Monitor, but apparently every process was sleeping . . . except for gnome-system-monitor which was using 18% ;)

---

### Post by Phil Urich on 2010-01-17
My sister's test came up with a result of an hour and fifty minutes, so, just shy of two hours.

Looking at Top right now, all I can really see is Firefox (what I'm typing this in), Xorg, gnome-terminal (which I'm running top in, which hangs around a bit lower) and occasionally compiz.real pops up with a brief CPU spike, or a bit lower devkit-power-daemon.  But nothing even into the double digits of CPU%, and I don't see anything that looks like it could be the culprit.

The "present rate: unknown" in regards to the discharge rate weirds me out a little, but I guess that's to be expected with the hardware?  I've never had a new laptop myself, heh, so I only really have experience with laptop hardware that the kernel has long since mastered every inch of.

I've been reluctant to follow any of the suggestions PowerTop proffers for fear of muddying the issue here, but for what it's worth the main suggestion has been enabling USB autosuspend.

---

### Post by thomasaaron on 2010-01-18
Please send an email to me (support..at.system76...dot...com) and we'll make arrangements to get you a new battery.

---

### Post by PatrickVogeli on 2010-01-18
have you looked you have uninstalled all mythtv packages?? the mythtv package is just a metapackage that will install a bunch of packages additionally, but when uninstalling the mythtv packages, those additional packages won't uninstall. 

If you haven't uninstalled mythtv completely, you could have some myth related stuff running constantly, like myth-backend.

---

