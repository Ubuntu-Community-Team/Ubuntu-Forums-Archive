---
title: "IPtables help (open port xxxx)"
date: 2006-01-19
forum: Server Platforms
---

### Post by yanik on 2006-01-19
Hi everyone,

I have a questions about iptables.  I whish to administer a remote server with webmin, but the problem is every ports are closed except a couple of useful ones.  I can log in as root on ssh.

I'd like to add a rule to accept connexion ONLY from my IP, for TCP port 10000 so I can do my thing thru webmin.  

Thanks.

---

### Post by yanik on 2006-01-19
nevermind, it easier than I thought:

iptables -A RH-Firewall-1-INPUT -p tcp -m tcp -s someIP --dport 10000 -j ACCEPT

---

