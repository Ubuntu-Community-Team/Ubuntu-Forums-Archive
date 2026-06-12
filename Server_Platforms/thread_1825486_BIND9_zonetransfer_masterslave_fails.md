---
title: "BIND9: zonetransfer master/slave fails"
date: 2011-08-15
forum: Server Platforms
---

### Post by rpnet.at on 2011-08-15
Hello community,
 
I hope someone can help me to solve my problem.
I've setup a bind dns master and slave. Both have a public ip-adresse.
 
The slave don't receive the masterzones an the log say
 

```
 failed while receiving responses: REFUSED
```
[LIST]
[*]I have allow-transfer option set for the slave ip
[*]allow-query {any;};
[*]Firewalls allow udp/tcp 53
[*]Both servers up
[*]Master load zones without error
[*]dig @master domain axfr on the master works
[*]dig @master domain axfr from the web doesn't work
[/LIST]Thanx for your help.
 
Regards Robert

---

### Post by SeijiSensei on 2011-08-16
Does the slave have an allow-transfer directive with the master's IP address and vice versa?  It sounds like you only have the allow-transfer directive on the master.

---

