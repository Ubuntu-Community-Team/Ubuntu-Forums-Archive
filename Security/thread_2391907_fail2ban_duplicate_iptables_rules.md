---
title: "fail2ban duplicate iptables rules"
date: 2018-05-14
forum: Security
---

### Post by sniper8752 on 2018-05-14
I am running Ubuntu server with fail2ban.  I noticed in my INPUT chain, there are several rules like this:
```
-A INPUT -p tcp -m multiport --dports 22 -j f2b-sshd
```
I had gone through and deleted all but one, and now there are several copies of this line in my chain again.  How do I prevent more than one of these being generated?

---

