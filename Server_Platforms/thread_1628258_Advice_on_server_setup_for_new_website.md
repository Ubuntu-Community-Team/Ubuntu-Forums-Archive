---
title: "Advice on server setup for new website"
date: 2010-11-22
forum: Server Platforms
---

### Post by clay7 on 2010-11-22
Hello,

I am (hoepfully) about to launch a new web site and this is somewhat new territory for me. I've had a CentOS VPS for 4 years, but my dedicated Ubuntu server is something else, and I could use some advice.

The site will be in PHP and will have MySQL queries on every page. Dynamic URLs will account for about 35% of the traffic. There are only 23 pages to the site but they all either read from and/or write to MySQL. I'll manage it all via SSH and also by Webmin.

I was planning on having everthing on one HD on my one server. Money is the reason. Here are my questions:

1. What can I do to optimize the performance? Is there a way to allocate memory to just MySQL or just to Apache...this is an area I know very little about.

2. How many concurrent users can 4GB RAM support? I know there are a lot of variables. My LAMP is the "typical" setup, but it also handles mail for me via Postfix/Dovecot. The connection speed to the internet should not be a factor in this equation. 

3. As for security, I've changed Webmin's default port, made an alias for PhpMyAdmin, made an alias for Squirrelmail, and use strong passwords for all. Given that you can never have enough security, is there anything else I should do within reason?

Thanks very much,
Clay

---

### Post by SeijiSensei on 2010-11-22
1) Don't worry; Linux will take care of all of that for you.  Unless you plan on using some *really large* arrays in PHP, memory allocation isn't an issue.

2) More users than you're ever likely to have.

3) Iptables firewalling if you don't already have it in place.  Lock down ports for services like Webmin so they can only be accessed remotely from machines you control.  You might consider using OpenVPN to build a tunnel from your workstation to the server and limit all access to administrative functions to the tunnel interface.

I've run web servers with multiple virtual hosts on machines with as little as 256M or 512M of memory.  Often these servers handle mail as well.  Remember some of us were doing this on 386's a decade or more ago.  Nearly any modern machine has orders of magnitude more horsepower than you need for most file/web/mail services.

---

### Post by wongo888 on 2010-11-22
Once your website is nice and busy, perhaps straining to keep up with demand, then you can take a look at your logs and your system resources and try to optimize your system. Trying to optimize your system before you have any traffic is premature. It will likely take a few months to get busy, so read up on Apache's prefork MPM before then. 

[http://httpd.apache.org/docs/2.2/mod/prefork.html](http://httpd.apache.org/docs/2.2/mod/prefork.html)

[http://httpd.apache.org/docs/2.2/misc/perf-tuning.html](http://httpd.apache.org/docs/2.2/misc/perf-tuning.html)

MySQL speed can be improved by optimizing your queries and reducing joins. Again this is a huge topic and there are lots of books on this.

PHP security and server security in general is often a question of how secure do you need to be. You can count on being hacked at some point in the future. You can minimize payoffs to hackers by storing salted and hashed passwords, for example. There are a few other low hanging fruits (not an exhaustive list):

[LIST=1]
[*]Keep your server patched
[*]Use nmap to check your exposed ports
[*]Use a scanner like nikto to audit your web app
[*]Use PHPsecinfo to check your php.ini settings
[/LIST]

[http://cirt.net/nikto2](http://cirt.net/nikto2)

[http://phpsec.org/projects/phpsecinfo/](http://phpsec.org/projects/phpsecinfo/)

To give you a real world example. One membership website I worked on had 250,000 registered users but only about 5,000 were actually active on a daily basis. We had 5 high-end machines, two configured as firewalls/load balancers (OpenBSD/pf) and two web app servers and a single MySQL (all CentOS). We had constant traffic, but we were idle a lot of the time. That configuration could have handled a million users a day, they just never showed up. We burned through our money and everyone went home.

---

### Post by clay7 on 2010-11-22
Much thanks to both of you...I wasn't aware of much of what you each pointed out, so your advice was very much needed!

---

