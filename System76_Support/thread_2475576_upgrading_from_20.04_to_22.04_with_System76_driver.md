---
title: "upgrading from 20.04 to 22.04 with System76 driver/kernel"
date: 2022-06-01
forum: System76 Support
---

### Post by ccrs8 on 2022-06-01
I have a 2 year old Lemur Pro currently running Xubuntu 20.04.  When I first installed Xubuntu 20.04 on it, there were a lot of minor bugs with the generic kernel that were resolved by installing the System76 driver and pinning the System76 repo in order to use the system76 kernel.  If my experience with my previous System76 laptop is an indication, after a few years the need for the System76-provided kernel is gone as the generic kernel catches up to the hardware needs.

Anyway, how should I go about upgrading to 22.04 once the upgrade is avaialable?  If I unpin the System76 repo before the upgrade, will that allow the upgrade to go forward and install the generic Xubuntu 22.04 kernel?  Or is my best/only option a clean install?

---

### Post by TheFu on 2022-06-01
22.04 will use newer kernels than what 20.04 uses. Hardware support from 2020 should be included to the same level as the latest 20.04 kernels.

Can't say if an upgrade is ever a good idea.  Always have a backup that you 100% know how to restore for when things go sideways.  Also, wait until the LTS-to-LTS upgrade is actually offered. That won't be for a few months, so you have time.  20.04 support regardless of flavor has 11 months remaining. No hurry to move.  Always remember, "new" is the enemy of "stable."

I'm still using 18.04 on most of my systems, BTW.

---

### Post by &amp;KyT$0P# on 2022-06-01
Is there a specific reason you need the generic kernel or don't want the System76 driver?

---

