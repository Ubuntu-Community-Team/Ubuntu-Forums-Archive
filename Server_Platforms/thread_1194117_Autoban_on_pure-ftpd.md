---
title: "Autoban on pure-ftpd"
date: 2009-06-22
forum: Server Platforms
---

### Post by Dy1anW on 2009-06-22
Can anyone let me know how to auto block IPs for 3 failed logins to pureftp?  It's just quite annoying to see multiple attempts by some script kiddie trying to gain admin priviliges (though I did once watch someone try to crack my server manually).

TIA.

---

### Post by zharmad on 2009-06-22
You may want to look into using Ossec-HIDS, it comes with some automated intrusion response, I believe that it could be setup add the IP address to hosts.deny after several failed login attempts.

---

### Post by HermanAB on 2009-06-22
Iptables has a very nice rate limit module which can prevent all kinds of abuse:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

That will make any script kiddie give up and go away.

---

### Post by CP1256 on 2009-06-22
You could also install Fail2ban.

---

