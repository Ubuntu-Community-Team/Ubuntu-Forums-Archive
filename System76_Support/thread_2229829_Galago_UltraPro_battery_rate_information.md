---
title: "Galago UltraPro battery rate information"
date: 2014-06-15
forum: System76 Support
---

### Post by hsggebhardt on 2014-06-15
Hi, I have a new Galago Ultrapro from System76. There is a problem reading the battery discharge rate using the sysfs interface. I get the following error when running on battery power:
```
 $ cat /sys/class/power_supply/BAT0/current_now
cat: /sys/class/power_supply/BAT0/current_now: No such device
```
However, clearly I do have a battery :). The other sysfs files work fine, and current_now also works if charging or otherwise on AC.

This is important, because some software such as the 'acpi' command or lxpanel (from the LXDE desktop environment) make use of this feature to estimate how long the battery will last. I would like to know!

Any suggestions?

---

