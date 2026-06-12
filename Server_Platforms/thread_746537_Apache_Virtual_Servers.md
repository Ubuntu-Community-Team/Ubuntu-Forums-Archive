---
title: "Apache Virtual Servers?"
date: 2008-04-05
forum: Server Platforms
---

### Post by drew17112 on 2008-04-05
I have a computer in my basement running the server edition of feisty. It uses a wireless usb adapter to connect to my router. The router runs DDWRT and uses the DDNS function to tell its IP address to my domain (the-yeah-gang.com) hosted on afraid.org. Currently nothing is running on the pc except for Webmin, apache2, and proftpd. when i installed feisty i didnt install a LAMP or DNS server. In the end i want to be able to.

A. serve a website to anyone who browses to "the-yeah-gang.com" or "www.the-yeah-gang.com"

B. serve a DIFFERENT website to a user who browses to "mysubdomain.somerandomsiteonafraid.com"

C. be able to add more sites to this list

D. use ONLY "A" records to accomplish this.

---

### Post by conjur3r on 2008-04-07
Your requirements describe a typical [NameVirtualHost]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") setup.  Lucky for you, the Apache package is ready to go with configs ready for you to add ontop of.

All your A records will point to the same IP address.  Apache will then decide which website to serve depending on the domain entered.

---

### Post by drew17112 on 2008-04-20
> **conjur3r said:**
> Your requirements describe a typical [NameVirtualHost]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") setup.  Lucky for you, the Apache package is ready to go with configs ready for you to add ontop of.

All your A records will point to the same IP address.  Apache will then decide which website to serve depending on the domain entered.

Awesome, that worked great, I used webmin to configure it after figuring out what values i needed to use where and stuff. THANKS though, this is freaken awesome. :D

---

