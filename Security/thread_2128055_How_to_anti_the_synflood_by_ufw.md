---
title: "How to anti the synflood by ufw?"
date: 2013-03-22
forum: Security
---

### Post by roamer2998 on 2013-03-22
Hi all, I'm new to Linux, I have a question: how to anti the synflood by ufw?

Best regards,

---

### Post by denis21-ru on 2013-03-22
Use: 
```
echo "net.ipv4.tcp_syncookies = 1" >> /etc/sysctl.conf
```

---

### Post by roamer2998 on 2013-03-23
> **denis21-ru said:**
> Use: 
```
echo "net.ipv4.tcp_syncookies = 1" >> /etc/sysctl.conf
```

Thank you.

---

