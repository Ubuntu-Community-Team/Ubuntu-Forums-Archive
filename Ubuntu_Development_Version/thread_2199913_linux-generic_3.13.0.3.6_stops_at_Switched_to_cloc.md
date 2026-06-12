---
title: "linux-generic 3.13.0.3.6 stops at Switched to clocksource tsc"
date: 2014-01-16
forum: Ubuntu Development Version
---

### Post by VMC on 2014-01-16
All [G,X,U]buntu's display the same behavior. The last message is "*Switched to clocksource tsc*", afterwards it hangs .
If I edit grub linux line and add *nomodeset* it boots, but then installing nvidia drivers it has reduced resolution.

Downgrading to  linux-generic 3.12.0-7 works.

This is on today's latest ISO.
 
I'm curious if anyone else with similar integrated nvidia as mine have the same issue.
Launchpad had bug report that may be this issue but for some reason I can't now find it.

Here's the [changes]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES") for the current kernel that mention "[COLOR=#000000]drm/nouveau: fix null ptr dereferences on some boards". Not sure if that's the problem.

Edit: Possible related bug reports: [/COLOR]#1269296, #1269558

---

### Post by Bashing-om on 2014-01-16
VMC; Hi !

Have you tried changing your clock source ? I am aware the tsc is the preferred source. Right off the top of my head I do not recall the means to change the clocking source (3 sources are available), but, if ya need, I can hunt up the documentation.

[INDENT][INDENT]not much
[INDENT][INDENT][INDENT]but it is a thought
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zika on 2014-01-16
File /sys/devices/system/clocksource/clocksource0/current_clocksource can have values tsc hpet acpi_pm, check /sys/devices/system/clocksource/clocksource0/available_clocksource...
Kernel boot line switch should be clocksource_failover=one_of_those_given_above if I remeber well... Also, hpet=force at kernel line might help...

---

### Post by VMC on 2014-01-17
The newest kernel , 3.13.0-4-generic, fixed this topic issue, as it did on the two bug reports I link to above.

---

