---
title: "Apparmor error 'log contains invalid mode senw'"
date: 2013-10-06
forum: Security
---

### Post by Hungry Man on 2013-10-06
```
 aa-logprof

```Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.


Log contains unknown mode senw.

---

### Post by tlu on 2013-10-18
> **Hungry Man said:**
> 
Log contains unknown mode senw.

Yes, same here in Saucy. Hadn't seen that in Raring. Did you create a bug report?

---

### Post by Hungry Man on 2013-10-18
No bug report. It was intermittent and now it is seemingly gone. Not sure what it was about.

---

### Post by tlu on 2013-11-19
[https://bugs.launchpad.net/apparmor/+bug/1243932](https://bugs.launchpad.net/apparmor/+bug/1243932)

---

