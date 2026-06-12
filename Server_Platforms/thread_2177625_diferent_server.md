---
title: "diferent server?"
date: 2013-09-29
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-09-29
It's possible to setup dns server and apache on other server? I have bind9 and apache on same server and i want to move apache to other server. How to point domain name with apache server?

---

### Post by sandyd on 2013-09-29
> **Bondar_Mircea said:**
> It's possible to setup dns server and apache on other server? I have bind9 and apache on same server and i want to move apache to other server. How to point domain name with apache server?

```

$ttl 38400
@ IN SOA ns1.beestudio.ro. admin.beestudio.ro. (
2013092925
10800
3600
604800
38400 )
@ IN NS ns1.beestudio.ro.
@ IN NS ns2.beestudio.ro.
@ IN MX 10 mail.beestudio.ro.
@ IN A 5.12.101.175
ns1 IN A 5.12.101.175
ns2 IN A 5.12.101.175
mail IN A 5.12.101.175
www IN A 5.12.101.175

```

Change the IPs on the following lines to the IPs of your new apache server
```

@ IN A 5.12.101.175
www IN A 5.12.101.175

```
Restart bind9

---

### Post by Bondar_Mircea on 2013-09-29
Can i use internal ip like: 192.168.0.25?

---

### Post by Bondar_Mircea on 2013-09-29
I want to this: When client try to access ns1.beestudio.ro i want to deny access like this. If you acces ns1.rdsnet.ro nothing display. ..if you enter rdsnet.ro the page of rds diplay..How can i do this on my server?

---

