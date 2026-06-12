---
title: "squid cache proxy server acl rules guideline"
date: 2010-02-06
forum: Server Platforms
---

### Post by salim.madni on 2010-02-06
Dear Respected Sir,
 
Good day, this is glad to hear all about squid proxy. the issue is with us to creating rules,policies
 
we need clarification, is there someone can just giude to us. we are planning very soon to switch from ISA proxy to squid cache proxy.
 
1) say we have some ips 192.168.1.101,192.168.1.103,192.168.1.110, we want to block the sites for them, like flash,movies youtube etc
2) next for same above group, we have 2 schedule to run internet from/to time, say sat-wed it run 08:00-18:00, on thursday it run only 09:00-14:00
3) 1 more group there that has 24 hours internet some ips say, 192.168.1.50,192.168.1.60,192.168.1.70. so the rule we apply in no1 and no2, we want bypass everything.
 
can someone advise us, we post to various forums, read various example. but does not work out due to lack of our knowledge.

---

### Post by Barriehie on 2010-02-06
> **salim.madni said:**
> Dear Respected Sir,
 
Good day, this is glad to hear all about squid proxy. the issue is with us to creating rules,policies
 
we need clarification, is there someone can just giude to us. we are planning very soon to switch from ISA proxy to squid cache proxy.
 
1) say we have some ips 192.168.1.101,192.168.1.103,192.168.1.110, we want to block the sites for them, like flash,movies youtube etc
2) next for same above group, we have 2 schedule to run internet from/to time, say sat-wed it run 08:00-18:00, on thursday it run only 09:00-14:00
3) 1 more group there that has 24 hours internet some ips say, 192.168.1.50,192.168.1.60,192.168.1.70. so the rule we apply in no1 and no2, we want bypass everything.
 
can someone advise us, we post to various forums, read various example. but does not work out due to lack of our knowledge.

What have you got so far that doesn't work?

---

### Post by salim.madni on 2010-02-06
see my queries are clear what i want for

there r 2 schedule how they can work together, do i need to make duplcate acl for 2 different timings and days or single list of acl but how?

and there are exceptional users tooo

---

