---
title: "scripts in power.d not executing"
date: 2009-08-28
forum: System76 Support
---

### Post by felixnine on 2009-08-28
running 9.04 on a panp. it seems that my custom power event scripts (ac power) are not executing when i plug and unplug my laptop. i've put them in both

```

/etc/pm/power.d
/usr/lib/pm-utils/power.d

```

but nothing happens. i know nothing happens because i have them echo something to a file when they are exeuted.

also of note, the command on_ac_power always returns 255, which means "power state could not be determined." related?

(i know it's working somehow; my display dims when i unplug it)

---

### Post by thomasaaron on 2009-08-31
There is a bug in power management for the Pangolin. Suspend/Hibernate should still work fine. The fix is actually available, but it requires compiling the kernel with certain options.

This should be fixed in Karmic.

---

### Post by felixnine on 2009-08-31
neat. suspend and hibernate do work fine. what do i need to do to compile into the kernel?

also: the sleep.d scripts are working, i believe, but the power.d scripts are not.

---

### Post by thomasaaron on 2009-08-31
I'm not really that familiar with compiling kernels. However, there are already some threads dealing with this issue.

[http://ubuntuforums.org/showthread.php?t=1213976&highlight=pangolin+power+management\](http://ubuntuforums.org/showthread.php?t=1213976&highlight=pangolin+power+management\)

---

