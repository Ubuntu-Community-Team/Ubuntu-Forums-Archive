---
title: "Firewall logger not Firestarter nor sudo privileged"
date: 2009-10-09
forum: Security
---

### Post by sopadeajo on 2009-10-09
read this:

[http://ubuntuforums.org/showthread.php?t=1282587](http://ubuntuforums.org/showthread.php?t=1282587)

---

### Post by sopadeajo on 2009-10-09
In fact i have checked that Firestarter makes an exact output of messages file log

---

### Post by lovinglinux on 2009-10-09
> **sopadeajo said:**
> In fact i have checked that Firestarter makes an exact output of messages file log

Firestarter needs root priviledges to change iptables rules and to display the status of established connections, but not for displaying blocked connection logs. 

You can get the same logs in real-time with this:

```
tail -f /var/log/messages | grep eth0
```

Just replace eth0 with your network card.

---

### Post by sopadeajo on 2009-10-09
Yes, OK.

---

