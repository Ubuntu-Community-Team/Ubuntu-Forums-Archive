---
title: "WPA option gone from network manager after update"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jeek Elemental on 2012-03-30
Using a
D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT3072]

as a wireless ap, running 12.04 on all pcs. Has been working fine for some weeks now.
After update today the wireless network was greyed out in the menu, edit connections/security now has no WPA option, which it was using before (no hw changes).
WEP does not seem to work, laptop tries to connect but gives up.

Internet over usb and ethernet card is working as before.

---

### Post by amaru01 on 2012-04-08
Hi,
I have the same problem.
Anybody?

---

### Post by Bucky Ball on 2012-04-08
The joys of beta testing an unreleased OS. Maybe a bug report is in order, although you would imagine this will be fixed in a forth-coming update ...

Wondering how many others have the same issue and if there is already a bug report ...

---

### Post by alphacrucis2 on 2012-04-08
Every thing is fine here. Still have WPA/WPA2 with all updates applied. You didn't apply a partial upgrade by any chance. They sometime remove packages you don't want to be removed.

---

### Post by Bucky Ball on 2012-04-08
> **alphacrucis2 said:**
> Every thing is fine here. Still have WPA/WPA2 with all updates applied. You didn't apply a partial upgrade by any chance. They sometime remove packages you don't want to be removed.

You are using 12.04 LTS?

---

### Post by alphacrucis2 on 2012-04-08
> **Bucky Ball said:**
> You are using 12.04 LTS?

Yep.

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"

```

---

