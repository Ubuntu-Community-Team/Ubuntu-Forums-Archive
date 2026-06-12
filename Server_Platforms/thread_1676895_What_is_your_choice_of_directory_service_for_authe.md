---
title: "What is your choice of directory service for authentication, contact info, etc?"
date: 2011-01-27
forum: Server Platforms
---

### Post by samosamo on 2011-01-27
Microsoft's Active Directory seems to dominate.  I absolutely refuse to use a Microsoft product for something so critical.  I've tried Apple's Open Directory but it's not all that great and since their line of server products is looking bleak, I'm looking for something else.

---

### Post by HermanAB on 2011-01-28
Howdy,

If you have Windows clients, then you have to use MS Active Directory.

If not, then you can use any one of a slew of directory servers, most of which are based on LDAP, but there is/was also PAM MySQL, NIS, NIS+, or even RADIUS would work.

RADIUS is nice, because it can use either MySQL or PostgreSQL as the back-end.  I never liked LDAP, which is what MS uses in Active Directory.

[http://www.gnu.org/software/radius/](http://www.gnu.org/software/radius/)
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

Also, there are no NIS clients for Windows, but there are RADIUS clients.  So RADIUS is an option in a mixed Windows/Linux/Apple network.

---

### Post by samosamo on 2011-01-28
> **HermanAB said:**
> Howdy,

If you have Windows clients, then you have to use MS Active Directory.

If not, then you can use any one of a slew of directory servers, most of which are based on LDAP, but there is/was also PAM MySQL, NIS, NIS+, or even RADIUS would work.

RADIUS is nice, because it can use either MySQL or PostgreSQL as the back-end.  I never liked LDAP, which is what MS uses in Active Directory.

[http://www.gnu.org/software/radius/](http://www.gnu.org/software/radius/)
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

Also, there are no NIS clients for Windows, but there are RADIUS clients.  So RADIUS is an option in a mixed Windows/Linux/Apple network.

That sounds great. RADIUS is new to me. I'll check it out.

---

### Post by samosamo on 2011-03-21
bump still lookin

---

