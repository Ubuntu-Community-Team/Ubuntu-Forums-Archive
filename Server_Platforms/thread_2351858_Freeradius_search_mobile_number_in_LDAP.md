---
title: "Freeradius: search mobile number in LDAP"
date: 2017-02-07
forum: Server Platforms
---

### Post by robpere on 2017-02-07
I could install and configure Freeradius. At the moment I have to configure the Users file, here an example: 
"user1"      Called-Station-Id := +41791234567

When I log in with user1, an SMS authentication is started and if ok, the Radius Server sends an accept. This is fine.

As  we have already LDAP, I would like that the freeradius Server checks   the LDAP for the mobile number. The user1 exist in LDAP and his phone   number is saved in the LDAP-Attribute "mobile". 

Can somebody  help me to achive this?

---

