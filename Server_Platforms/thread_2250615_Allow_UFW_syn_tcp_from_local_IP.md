---
title: "Allow UFW syn tcp from local IP"
date: 2014-10-29
forum: Server Platforms
---

### Post by andrew102 on 2014-10-29
Basically, have a UFW rule to allow from 10.x.x.x on port 8080 (tomcat)

10.x.x.x is the load balancer server. I've noticed SYN attempts being blocked every 30sec or less. Presumably because UFW just sees the one IP and detects it as a DoS attempt.

How do I tell UFW (probably in before.rules) to just allow these connections.

---

### Post by Habitual on 2014-10-30
I use these 2 rules on my hosted system:
```
ufw allow in on eth1 from 10.0.0.0/8
ufw allow in on eth0 from 10.0.0.0/8
```

Hope that helps.

---

### Post by nerdtron on 2014-10-31
I believe you can add rules on the /etc/ufw/before.rules

See on the syntax here (more like iptables) [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by andrew102 on 2014-11-06
Thanks, still think that the limit of 3, burst 10 must be having some sort of impact.

---

