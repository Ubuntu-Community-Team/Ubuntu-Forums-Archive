---
title: "Does fail2ban start automatically each time system starts?"
date: 2016-03-10
forum: Server Platforms
---

### Post by Grigoriy on 2016-03-10
I've just installed Fail2ban on Ubuntu 14.04 and there's something I  want to ask: Does fail2ban start automatically each time system starts? I  think so, but just want to make sure, since I've read somewhere online  that one should use chkconfig command to autostart fail2ban (not like  Ubuntu has this command anyhow)...

---

### Post by Habitual on 2016-03-10
[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)

---

### Post by TheFu on 2016-03-10
```
sudo /sbin/iptables -L

```will show what firewall rules are up. Is there any fail2ban in there?

---

### Post by Grigoriy on 2016-03-10
Thanks both of you. Fail2ban does run.

---

