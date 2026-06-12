---
title: "Is there anything else I should do to secure my server?"
date: 2010-02-03
forum: Security
---

### Post by Jekshadow on 2010-02-03
I am running UFW, which is set to deny everything but SSH on port 22, OpenVPN on port 1194 and HTTPS on port 443. SSH is set to only allow private key logins, and the root account is disabled. I have AppArmor running for all of my daemons (OpenVPN, Apache2, OpenSSH) and I have Fail2Ban running. 

Is there anything else I can do to secure my server from the Internet (it is directly connected, there is no NAT between the Internet and my server).

---

### Post by JT9161 on 2010-02-03
An IDS

---

### Post by Jekshadow on 2010-02-03
> **JT9161 said:**
> An IDS

Think Snort will work?
[http://www.snort.org/](http://www.snort.org/)

---

### Post by JT9161 on 2010-02-03
> **Jekshadow said:**
> Think Snort will work?
[http://www.snort.org/](http://www.snort.org/)

Well, it's and IDS

---

### Post by mgichoga on 2010-02-03
If you are running a web application it might be useful to look at [mod_security]("http://www.modsecurity.org/") It is an apache2 security module that protects against common sql injections, XSS attacks etc.They have a comprehensive howto on installing it with the basic signatures. 

--
M Gichoga

---

