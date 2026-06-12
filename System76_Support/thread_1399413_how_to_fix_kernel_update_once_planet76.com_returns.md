---
title: "how to fix kernel update once planet76.com returns?"
date: 2010-02-05
forum: System76 Support
---

### Post by tlroche on 2010-02-05
I posted [here]("http://ubuntuforums.org/showthread.php?t=1399404") regarding kludging the wireless on a box which had its kernel update broken by the [planet76.com downtime]("http://ubuntuforums.org/showthread.php?t=1399130"). I'm wondering, how to actually fix this? I.e., once planet76.com returns, how to fix the broken kernel=```
Ubuntu, Linux 2.6.31-19-generic
```?

---

### Post by jdb on 2010-02-05
> **tlroche said:**
> I posted [here]("http://ubuntuforums.org/showthread.php?t=1399404") regarding kludging the wireless on a box which had its kernel update broken by the [planet76.com downtime]("http://ubuntuforums.org/showthread.php?t=1399130"). I'm wondering, how to actually fix this? I.e., once planet76.com returns, how to fix the broken kernel=```
Ubuntu, Linux 2.6.31-19-generic
```?

The Kernel isn't broken but it is lacking the fix that system76 put in the old kernel.

Assuming they have a fix for the new Kernel, when system76 comes back up & you install the 76 drivers the fix will be applied to the new Kernel.

jdb

---

### Post by thomasaaron on 2010-02-08
Please try reinstalling the -19 kernel via Synaptic Package Manager. That will automagically apply the driver fix... or it should. If not, though, the System76 Driver will do the trick.

---

