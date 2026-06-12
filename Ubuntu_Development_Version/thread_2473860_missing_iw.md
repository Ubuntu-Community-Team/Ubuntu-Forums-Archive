---
title: "missing iw ?"
date: 2022-04-16
forum: Ubuntu Development Version
---

### Post by him610 on 2022-04-16
```
hugh@V3-572Ga:~$ Uld
Linux V3-572Ga 5.15.0-25-generic #25-Ubuntu SMP Wed Mar 30 15:54:22 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Jammy Jellyfish (development branch)
Release:	22.04
Codename:	jammy
XFCE

```
It seems like ***iw*** was missing in 22.04 beta. Found it necessary to download post-installation.

---

### Post by DuckHook on 2022-04-16
Similarly, Jammy is missing *hddtemp*. Cannot even install it, as it is entirely missing from the repos. It was still available in Impish and I have not heard that it has been deprecated, so no idea why it's missing.

At least *iw* is available for custom installation. These are time&#8209;honoured and important utilities.

Sometimes, dev's decisions are really *huh?*

---

### Post by deadflowr on 2022-04-16
> Similarly, Jammy is missing hddtemp.
There was another thread about that here: [https://ubuntuforums.org/showthread.php?t=2473063]("https://ubuntuforums.org/showthread.php?t=2473063")

---

### Post by Hreinsi on 2022-04-16
Thats why. [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1002484](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1002484)

---

### Post by him610 on 2022-04-16
I noticed the results of * iw reg get* missing in wireless-info text after downloading and running *wireless-info*. So, yes, it is in repository.

---

### Post by DuckHook on 2022-04-16
> **deadflowr said:**
> There was another thread about that here: [https://ubuntuforums.org/showthread.php?t=2473063]("https://ubuntuforums.org/showthread.php?t=2473063")

> **Hreinsi said:**
> Thats why. [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1002484](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1002484)
Thanks for this guys.

From that bug report:> hddtemp is a software from another age that will not be shipped with
Debian Bookworm release [1].&#8230;makes me feel so old. Apparently, I'm from another age.

@him610

*iw* isn't the only tool no longer included by default. *ifconfig* has also been treated the same way.

Apparently, the new way is to use *ip*. I still haven't gotten used to it yet.

---

