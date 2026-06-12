---
title: "watchdog module not forcing reboots when loaded from /etc/init.d/watchdog"
date: 2009-09-28
forum: Server Platforms
---

### Post by vertigo23 on 2009-09-28
OS: Ubuntu Hardy 8.04.2 amd64
Hardware: Supermicro Intel Server Platform

Scenario:

Install 'watchdog' package on an IPMI-equipped system.  Set up /etc/default/watchdog to use the "ipmi_watchdog" module, and /etc/watchdog.conf to use "watchdog-device = /dev/watchdog"

In /etc/modprobe.d you may also need to do the following:
blacklist iTCO_wdt
alias char-major-10-130 ipmi_watchdog
options ipmi_watchdog timeout=60 action=reset start_now=1


Expected outcome:

/etc/init.d/watchdog will load the ipmi_watchdog module.  If the /usr/sbin/watchdog process dies (or verifies a failure condition), the system should be reset after 60 seconds.

Note that if I manually modprobe "ipmi_watchdog" without the daemon running, the system will (correctly) reset after 60 seconds.  So I know the watchdog timer hardware and the kernel module are functional.


Actual outcome:

After killing /usr/sbin/watchdog, the system does not reset.  Triggering a failure condition monitored by /usr/sbin/watchdog does not cause a reset.

---

