---
title: "UFW Blocked IP in Apache Log"
date: 2011-06-07
forum: Security
---

### Post by prkns on 2011-06-07
I've setup the Uncomplicated Firewall (UFW) on Ubuntu 10.04 LTS and blocked an IP address. UFW status shows that the firewall is active and the IP in question is denied. The issue is that I'm seeing the blocked IP address in my Apache logs. Am I missing something?

---

### Post by doas777 on 2011-06-07
lets see your rule:
```
sudo ufw status
```

---

