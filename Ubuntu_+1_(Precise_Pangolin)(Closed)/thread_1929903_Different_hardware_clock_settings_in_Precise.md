---
title: "Different hardware clock settings in Precise?"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Irihapeti on 2012-02-22
I've been noticing something rather odd recently with my clock settings.

I multiple boot with Lucid, Precise and also (occasionally) Windows Vista. I've applied a registry fix to Vista so that it recognises the hardware clock as set to UTC, and I've disabled getting time settings from Microsoft.

If I've been running Lucid and then boot into Vista, I get the (Vista) system clock showing the correct time. But, if I've been running Precise and I then boot into Vista, the system clock shows a time that's 13 hours ahead of the correct time. To me, it looks as though the hardware clock has been set to NZDT and Vista then adds the 13 hours correction to what it thinks is UTC.

My question is: does anyone know if some change has been made to the way Ubuntu handles time settings? I've also occasionally noticed clock anomalies when booting between the two Ubuntu versions and there's a delay in NTP updating.

---

### Post by AnrDaemon on 2012-02-22
Check for discrepancies in
date ; hwclock --show --utc
under PP.

---

### Post by Irihapeti on 2012-02-22
Here's the result:

```
date ; hwclock --show --utc
Thu Feb 23 13:38:16 NZDT 2012
Thu 23 Feb 2012 13:38:17 NZDT  -0.406819 seconds

```

---

### Post by AnrDaemon on 2012-02-22
That means, 12.04 keep your HW clock in UTC.
If it'd be otherwise, the reading would not match.

---

### Post by Irihapeti on 2012-02-22
Then there must be something else happening that's causing the discrepancy. I'll keep looking.

I'd report a bug, if I knew what to report it against.

---

### Post by AnrDaemon on 2012-02-22
Try something like
Boot OS #1, check readouts
Boot LiveCD, check readouts
Boot OS #2, check readouts
Boot LiveCD, check readouts
Boot OS #3, check readouts
Boot LiveCD, check readouts

Lay down your findings on a paper. Try to draw some clues...

I suggest 10.04 LiveCD.

---

### Post by Irihapeti on 2012-02-23
I found the answer. :redface:

/etc/default/rcS had the setting "UTC=no" :oops:

I'm not sure how that came to happen, but it's changed now and everything seems to be working properly.

---

