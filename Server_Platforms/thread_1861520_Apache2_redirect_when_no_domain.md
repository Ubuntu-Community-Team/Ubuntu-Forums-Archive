---
title: "Apache2 redirect when no domain"
date: 2011-10-15
forum: Server Platforms
---

### Post by DoubleD33D on 2011-10-15
I'm using NameVirtualHost to direct a domain to a folder. But now when you go to just the server IP, you get the domains folder and not the default. My second domain(as a test) goes to its folder correctly. I want it so that if someone is trying to view the servers ip, they will get a folder that is chmod'ed to 700 so that they will get forbidden.

Ubuntu Server 11.10 64Bit
Latest apache, php5

---

### Post by Vegan on 2011-10-15
are you looking for changing the default folder?

that is found by default in

/var/www

---

### Post by volkswagner on 2011-10-15
When using NameVirtualHosts Apache will forward non-matching requests to the virtual host that comes first (alpha-numerically).

If you want to force a different default, change the names of you vhost files so your server with 700 as the root comes first.

I think the default is actually 000-default.  The leading zeros make it come first for non matching hostnames including ip requests.

---

### Post by SeijiSensei on 2011-10-17
> **DoubleD33D said:**
> I want it so that if someone is trying to view the servers ip, they will get a folder that is chmod'ed to 700 so that they will get forbidden.

By default they get the "It Works!" page that is packaged as /var/www/index.html since /var/www is the DocumentRoot in the 000-default configuration.

You can't really hide the fact that a web server is listening on port 80 just by returning a Forbidden.  The remote client will still know the port is open and a server listening there.  Just install **nmap** and run it against your server to see.

---

