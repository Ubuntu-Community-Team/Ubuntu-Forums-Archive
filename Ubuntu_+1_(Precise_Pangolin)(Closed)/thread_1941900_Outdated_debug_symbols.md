---
title: "Outdated debug symbols?"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by screaminj3sus on 2012-03-16
I keep getting this issue trying to report a bug I've been happening (empathy-chat sometimes crashes after resuming from suspend).

After submitting the report apport retracts it and emails me this:

> Thank you for your report!

However, processing it in order to get sufficient information for the
developers failed (it does not generate a useful symbolic stack trace). This
might be caused by some outdated packages which were installed on your system
at the time of the report:

outdated debug symbol package for libv4l-0: package version 0.8.6-1ubuntu1 dbgsym version 0.8.5-3ubuntu2
outdated debug symbol package for libgconf2-4: package version 3.2.5-0ubuntu1 dbgsym version 3.2.3-0ubuntu0.1


Please upgrade your system to the latest package versions. If you still
encounter the crash, please file a new report.

Thank you for your understanding, and sorry for the inconvenience!



But my system is fully updated... I just ran another update to make sure and the only thing updated was wpasupplicant.

---

### Post by dino99 on 2012-03-16
> **screaminj3sus said:**
> I keep getting this issue trying to report a bug I've been happening (empathy-chat sometimes crashes after resuming from suspend).

After submitting the report apport retracts it and emails me this:



But my system is fully updated... I just ran another update to make sure and the only thing updated was wpasupplicant.

is that repo activated into your sources.list ?

[http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) precise main restricted universe multiverse

---

### Post by screaminj3sus on 2012-03-16
> **dino99 said:**
> is that repo activated into your sources.list ?

[http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) precise main restricted universe multiverse

It wasn't in there, so I added it and ran an update. Nothing got updated :/

---

