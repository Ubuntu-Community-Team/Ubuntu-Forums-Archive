---
title: "What would it take to create a complete text-based server management console?"
date: 2006-07-31
forum: Server Platforms
---

### Post by JA2 on 2006-07-31
Has anyone here had experience with SCO OpenServer or UnixWare?  What would it take to build a complete textmode menu-driven management system similar to SCO's "scoadmin" utility?   

Something like that would be invaluable to new sysadmins having to configure the various aspects of the server, such as managing user accounts, setting up the LAMP stack, networking, firewalls, etc. I'm sure even aptitude could be integrated into this somehow to be able to add/remove packages.

Developers, I welcome your opinions.

---

### Post by Kurt` on 2006-07-31
> managing user accounts
# man useradd
# man passwd

> setting up the LAMP stack
# apt-get install apache2-mpm-prefork libapache2-mod-php4 mysql-server

> networking
# man ifconfig

> firewalls
# man iptables

I denno, I'd prefer to just use each of these seperately rather than have to navigate yet *another* interface. Maybe that's just me though. :)

---

### Post by LordHunter317 on 2006-07-31
More work than it would be worth, likely.  

I'm not sure why people are so bent on console GUI tools.  Unless they're well written (none are) they don't help anything.  Either you possess the knowledge or you don't.  Changing the way you display it usually doesn't help anything.

---

### Post by Socratez on 2006-08-01
I think it would be much easier to use Web base GUI tools through a webbrowser rather then sit at the server console. Webmin, ebox, and other tools can get the job done with quicker easier to navigate interfaces ... 

But if you must have console I think it would be quite the project ... let me know how that works out for u 


S

---

### Post by harisund on 2006-08-01
I like the console. I can administer pretty much every single aspect of my system from the console, so I don't find the need for another 'interface' as such

---

### Post by apjone on 2006-08-01
I wrote a php console to manage squid/dansguardian proxyserver setup. 

admin console allows you to see usage stats, blocked site's in last 48 (with ip/date/site search) , add and ban phrase's/sites/ip's via a webpage form with htpasswd login.
also i wrote a php form which allows users to request banned sites. They get blocked > click request site > and enter there name/email/reason for site. the site, date , time and ip address are collected vi hidden text fields and sent in the message to the admin.

---

### Post by apjone on 2006-08-01
I wrote a php console to manage squid/dansguardian proxyserver setup. 

admin console allows you to see usage stats, blocked site's in last 48 hours(with ip/date/site search) , add and ban phrase's/sites/ip's via a webpage form with htpasswd login.
also i wrote a php form which allows users to request banned sites. They get blocked > click request site > and enter there name/email/reason for site. the site, date , time and ip address are collected via hidden text fields and sent in the message to the admin.

---

