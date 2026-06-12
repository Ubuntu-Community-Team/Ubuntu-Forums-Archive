---
title: "ufw blocks in log"
date: 2018-09-03
forum: Security
---

### Post by mborl on 2018-09-03
My ufw log shows that ufw is blocking something twice every hour. Is this normal behavior (I'm not too familiar with ufw)? This is a little disconcerting since there are those who argue that linux users do not necessarily need to have their firewall enabled.

---

### Post by The Cog on 2018-09-03
Two blocks an hour sounds remarkably few. 

Since the firewall is blocking them then they are not a danger to you. Even without a firewall they are probably not a danger - probably addressed to a service that is not running anyway. However, without seeing the log entries we can not know what they are about.

---

### Post by mborl on 2018-09-03
Thanks for the reply. Thinking about it now, I am wondering if it could be clamav's freshclam daemon since it checks for updates every hour.

---

