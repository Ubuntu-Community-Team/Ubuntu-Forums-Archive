---
title: "Apache listen on localhost only"
date: 2009-01-14
forum: Server Platforms
---

### Post by ade234uk on 2009-01-14
I have a lamp server set up for testing sites. What I would like to know is how I lock down apache to only listen on localhost only?

---

### Post by Titan8990 on 2009-01-14
You could just set up a IPTABLES rule to block all incoming traffic on port 80. Although, if you are behind a router, your webserver is not accessible to the internet anyways (unless you have taken the necessary steps).

---

### Post by RobNY on 2009-01-14
Research the BindAddress (1.3) and Listen (2.0) directives for apache.  Here's two starting points for you:

[http://httpd.apache.org/docs/1.3/bind.html]("http://httpd.apache.org/docs/1.3/bind.html")

[http://httpd.apache.org/docs/2.0/mod/mpm_common.html#listen]("http://httpd.apache.org/docs/2.0/mod/mpm_common.html#listen")

---

### Post by Kismet on 2009-01-14
<Location "/">
	Order Deny,allow
	Deny from all
	Allow from 127.0.0.0/255.0.0.0 ::1/128
</Location>

in your site-enabled site.

Should limit apache serving to anyone but localhost for anything under
/.

---

### Post by Iowan on 2009-01-14
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache") help page should be useful.
In brief:> Change ports.conf so that it contains:
Listen 127.0.0.1:80

---

