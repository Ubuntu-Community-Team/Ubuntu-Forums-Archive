---
title: "Access log blank?"
date: 2008-02-06
forum: Server Platforms
---

### Post by z00lander on 2008-02-06
I took over our webserver after someone left our company and it is doing something odd that I as a noob can't figure out.  I was looking at the web stats and it only showed one day.  I thought webalizer was messed up until I looked at the access log file.  It was blank, nothing in it at all.  After researching the install, it looks like it only worked on the first day that it was setup.  The ex employee is less than helpful, can someone give me an idea on what is going on?

Thanks in advance for any  help.

---

### Post by freebeer on 2008-02-07
I believe Apache, on Ubuntu, writes its log in a different area than that "standard" areas that most documentation claim.  I think the standard location is /var/log whereas on Ubuntu it's /var/log/apache2.  Check there for the log files.  

As for webalyzer, it probably was set up using default settings, rather than with adjusted settings. (ie it was reading from /var/log and not /var/log/apache2)

That's my guess, anyway.  :D

---

### Post by k_grdn on 2008-02-07
Hi,

Grep Log your vhost file (/etc/apache2/sites-enabled/vhost) for your site, look for output similar to the following:

ErrorLog /var/log/apache2/error.log
LogLevel warn
CustomLog /var/log/apache2/access.log combined

The output will be the location of your logs.

Regards,

k_grdn

---

