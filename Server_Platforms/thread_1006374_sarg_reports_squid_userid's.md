---
title: "sarg reports squid userid's"
date: 2008-12-09
forum: Server Platforms
---

### Post by insurin on 2008-12-09
I am running 

squid 3
samba 
Sarg
 
Squid is my proxy for Windows clients in an Active Directory Domain. I have this setup so that it authenticates users transparenlty. 
When browsing my squid log "access.log" I can see data being generated and usernames from AD.

When using sarg to generate reports, under the colum "USERID" all I am seeing is the IP address and not the AD username. Does anyone know how to correct this so it displays AD usernames instead.

---

### Post by gavinhughes86 on 2009-03-02
Hi 

I have a simailar setup
My solution was to edit the /etc/squid/sarg.conf file
change the following

```

# TAG:  user_ip yes/no
#       Use Ip Address instead userid in reports.
#       sarg -p
user_ip no


```
As for webmin Im not certain but under squid report generator > report options
set:
**Use IP addresses instead of user IDs? : no**

Not exactly the best way to word that question doh!

Post back let us know how you get on,

---

