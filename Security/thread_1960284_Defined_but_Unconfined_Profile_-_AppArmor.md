---
title: "Defined but Unconfined Profile - AppArmor"
date: 2012-04-17
forum: Security
---

### Post by Hungry Man on 2012-04-17
I use DNSCrypt and keep the daemon in an AA profile. The problem is that I need to run sudo restart dnscrypt on system start or it remains unconfined.

Is there a solution to this?

---

### Post by Dave_L on 2012-04-17
Are you asking how to run "restart dnscrypt" automatically as root on system start?

---

### Post by Hungry Man on 2012-04-17
I suppose; if that would solve the issue.

---

### Post by Dave_L on 2012-04-17
An easy thing to try is to add it to /etc/rc.local, just before the last line "exit 0":

```
restart dnscrypt
exit 0
```

---

### Post by Hungry Man on 2012-04-17
I'll give that a shot, thanks.

---

