---
title: "Trying to clean up after avg"
date: 2009-08-08
forum: Security
---

### Post by Brian R. on 2009-08-08
I installed avg 8.5 as a deb file and as it has no gui i decided to get rid of it. Could not find any uninstall in the commands for it, so went in to nautilus as root, did a search for all the files with avg in the name, and deleted them all that way. But was left with one file in /proc named loadavg 0 bytes long, which i cannot remove. I have changed the owner to me with read write permissions, but it still refuses to be deleted. How can i get rid of it.
Thank you

---

### Post by Amilo1718 on 2009-08-08
maybe a reboot can do the trick?

---

### Post by cariboo on 2009-08-08
You will still have remnants of avg left if you remove it manually. To uninstall a .deb simply open Synaptic package manager and search for the package you want to remove, or open a terminal and type:

```
sudo apt-get purge <name of package>
```

---

### Post by niteshifter on 2009-08-08
Hi,

The file /proc/loadavg has nothing to do with AVG anti-virus. That's a psuedo-file that contains current system load averages. You don't want to remove it - things like top and system monitor will break.

---

### Post by Brian R. on 2009-08-09
Thanks for that information i will leave it alone then.

---

