---
title: "Join Kylin to Active Directory (&quot;getent passwd&quot; not working, &quot;getent hosts&quot; working)"
date: 2018-07-11
forum: Server Platforms
---

### Post by asadraza5 on 2018-07-11
Hi.

I am trying to join a Kylin Server to the MS Active Directory Domain using SSSD SAMBA and KERBEROS.

The domain has been joined but there is a problem. 


The following command does not show any record of the domain user

#getent passwd domainUser



Whereas the following command shows the record of the domain host

#getent hosts domainHost

And therefore I am not able to login as a domain user on the Kylin Server.

---

### Post by wildmanne39 on 2018-07-11
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

