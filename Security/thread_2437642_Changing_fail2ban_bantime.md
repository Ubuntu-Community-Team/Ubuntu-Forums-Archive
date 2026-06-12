---
title: "Changing fail2ban bantime"
date: 2020-02-27
forum: Security
---

### Post by rogerk03 on 2020-02-27
Just wondering anyone knows if changing fail2ban bantime effects previous bans or only future bans?

For example if I change the bantime to 1 day, and it was previously 1 week, will all IPs be unbanned that have been banned for 24 hours or more, or does fail2ban respect the previous 1 week and wait 1 week to unban the IPs banned when the 1 week was in place?  I'm guessing changing the ban to 24 hours affects all IPs regardless what the bantime was when they were banned, but thought I'd check.

Apologies if this is the wrong forum, security seemed appropriate.

Thanks.

---

### Post by EuclideanCoffee on 2020-02-27
Since one jail manages how each ban incident should be handled (banned and unbanned), then the ban time should update, yes. The time should change.

But if you're unsure, you can check the ban time this way.

fail2ban-client get <JAIL> bantime

---

