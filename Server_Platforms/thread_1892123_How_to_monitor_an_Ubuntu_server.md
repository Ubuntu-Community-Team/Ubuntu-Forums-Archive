---
title: "How to monitor an Ubuntu server?"
date: 2011-12-07
forum: Server Platforms
---

### Post by fernandoch on 2011-12-07
How do you guys monitor the performance of your servers?

Do you use any specific tool?

---

### Post by Habitual on 2011-12-07
for performance monitoring, I always install sysstat (sar).
I use Icinga to monitor Fault Tolerance, and Cacti to monitor additional performance/resource metrics.

For Security, I install fail2ban and ssh is by KEY ONLY.

Mileage may vary and I'm sure I'll have an "a-ha" senior moment by forgetting something obvious.

HTH.

---

### Post by fernandoch on 2011-12-07
No nagios then?

---

### Post by Habitual on 2011-12-07
> **fernandoch said:**
> No nagios then?

Icinga is a fork of nagios, so yes. :)

---

