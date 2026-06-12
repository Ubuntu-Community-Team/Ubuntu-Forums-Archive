---
title: "bind fails first attempt, then works"
date: 2011-01-10
forum: Server Platforms
---

### Post by logandzwon on 2011-01-10
Hi guys,
  I'm having an issue with a BIND server.  After a restart, (or randomly, I assume whenever a cache expires,) when I try to resolve any domain I get a "Host yahoo.com not found: 2(SERVFAIL)" Eventually it starts working and works fine till the cache expires again;

Any ideas?


[root@ns002 etc]# host yahoo.com
Host yahoo.com not found: 2(SERVFAIL)
[root@ns002 etc]# host yahoo.com
Host yahoo.com not found: 2(SERVFAIL)
[root@ns002 etc]# host yahoo.com
Host yahoo.com not found: 2(SERVFAIL)
[root@ns002 etc]# host yahoo.com
Host yahoo.com not found: 2(SERVFAIL)
[root@ns002 etc]# host yahoo.com
Host yahoo.com not found: 2(SERVFAIL)
[root@ns002 etc]# host yahoo.com
Host yahoo.com not found: 2(SERVFAIL)
[root@ns002 etc]# host yahoo.com
yahoo.com has address 67.195.160.76
yahoo.com has address 69.147.125.65
yahoo.com has address 72.30.2.43
yahoo.com has address 98.137.149.56
yahoo.com has address 209.191.122.70
yahoo.com mail is handled by 1 a.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 b.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 c.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 d.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 e.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 f.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 g.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 h.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 i.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 j.mx.mail.yahoo.com.
yahoo.com mail is handled by 1 k.mx.mail.yahoo.com.

---

### Post by logandzwon on 2011-01-10
Well, I think the problem is somewhere with the router/switches/firewalls upstream of this server.  I set DNS to not randomize the query-source port.  This has fixed the query problems.

---

