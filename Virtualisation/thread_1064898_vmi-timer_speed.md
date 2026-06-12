---
title: "vmi-timer speed"
date: 2009-02-09
forum: Virtualisation
---

### Post by hreintke on 2009-02-09
LS,

I an running WinXP as host OS on a system using a e6600 CPU running on 2.57Ghz (overlock mode 9 x 306) instead of the standard 2.40 Ghz ( 9 X 266).

In the vmware workstation 6.5.1 I have a Ubuntu 8.04 server guest. In the guest and the vmx vmi is enabled. I see it is working correctly as the ubuntu reports vmi-timer as its clocksource.

The problem is that the clock in the guest is running 15% too fast (15% = 2.57/2.4). I tried setting the host.cpumhz=2570000 in the config.ini of the workstation installation but that setting has no effect.

I also tried other clocksource options (acpi_pm, pit, jiffies) but also then the colck keeps running 15% too fast 

Resetting the CPU to the standard settings (9 X 266) results in correctly working timing on the ubuntu host, independent of setting of host.cpumhz.

Question :

    * Is the vmi-timer clocksource dependent on the fsb speed or the clockspeed of the CPU ?

    * Is it possible to influence the "speed" of the vmi-timer ?

Kind regards.

Herman

---

