---
title: "LDAP search DN with multiple OU"
date: 2013-06-27
forum: Server Platforms
---

### Post by Mickael69 on 2013-06-27
Hi everybody,

I need your help... 

I’m using a pam_ldap.so with ldap.conf to use a TACACS server with AD. It’s working without problem. 
I try to search in multilple OU an user of the AD, with the command ldapsearch in the first time and in particular with the ldap.conf? 
In fact the problem is the time of connection (around 10 seconds) with between tacacs server and the AD beacause the ldap search in all the AD and not in particular OU (2 OU for my case).
I googling but no result, just result with the filter but I don't want it. 
Eg: 
Search DN: OU=Users1,OU=OU1,DC=ad,DC=xxxxx,DC=fr
Search DN: OU=Users2,OU=OU2,DC=ad,DC=xxxxx,DC=fr

I hope you understand my problem and you can help me...


Thanks for your feedback,

Regards

---

### Post by Mickael69 on 2013-07-02
Up!

---

### Post by coffeecat on 2013-07-03
Not an Ubuntu, Linux & OS **chat** thread.

*Thread moved to **Server Platforms**.*

---

### Post by Mickael69 on 2013-07-16
Nobody use LDAP ?

---

