---
title: "Scripts can't access database"
date: 2009-01-06
forum: Server Platforms
---

### Post by wattaman on 2009-01-06
Well, I've just solved a problem and hit another one. But, since I'm decided not to pay an expert this time, I must search for help myself.
So, I've just set up my server. I have Ubuntu 8.04.1, PHP5, MySql5, apache2 and webmin to administer it.

Now, my host told me I have 2 IP and I like to host 2 domains on the server, each with its own IP. I've already set up the domains in webmin (or I thought I did) but it seems that both domains are using only one IP, showing both the same site. I've configured the domains in apache where I've added the IPs for each domain in the Virtual Server Details-Address field.

Please tell me what am I missing. What I must to do for any domain/IP to show, in browser, its own site?
Thank you!

---

### Post by Iowan on 2009-01-06
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a How-To for name-based virtual hosting.  I'll see if I can find one for (what apparently is more normal) IP-based.
Found [this]("http://httpd.apache.org/docs/1.3/vhosts/ip-based.html") on Apache's site.

---

