---
title: "[natty] Can't spin down HDDs"
date: 2011-01-10
forum: Server Platforms
---

### Post by size_XXM on 2011-01-10
At first I thought /etc/hdparm.conf isn't being applied, but apparently I can't even spin the drives down manually - hdparm -y does nothing at all, hdparm -Y seems to put the link rather than the device to sleep, according to kern.log. Either way the drives keep spinning. Anyone else with this problem or (preferably) a solution? The hardware involved is a pair of Sammies (HD154UI) - none of which hold the system partition - hooked up to Intel's Johnstown (D945GSEJT) board.

Bug (with more info) filed [here](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/701144).

Thanks for any help in advance.

---

