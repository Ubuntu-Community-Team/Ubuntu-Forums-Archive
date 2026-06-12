---
title: "pgsql network access headache"
date: 2010-09-02
forum: Server Platforms
---

### Post by fusebox on 2010-09-02
Hi people

I've just finished installing 9.10 server plus postgresql 8.4
The problem is i can't access pgsql over network despite having set listen_addresses = '*' and added ```
host all all 192.168.1.0/24  md5
```  in both *postgresql.conf* and *pg_hba.conf* respectively.

I even configured iptables to allow traffick thru port 5432 using
```
iptables -A INPUT -p tcp --dport 5432 -j ACCEPT
``` but i still can't connect to my db even thru pgadmin3.
All other services are accessible over network - even mysql!

I've searched thru this forum but no thread has a solution to this problem.

Does anyone have a fix for this?

---

