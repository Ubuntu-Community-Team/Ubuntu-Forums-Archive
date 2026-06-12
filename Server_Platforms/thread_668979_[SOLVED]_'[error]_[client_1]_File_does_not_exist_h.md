---
title: "[SOLVED] '[error] [client ::1] File does not exist: /htdocs'"
date: 2008-01-16
forum: Server Platforms
---

### Post by Sporkman on 2008-01-16
I'm getting a tons of these in /var/log/apache2/err.log in Gutsy:

[Wed Jan 16 00:22:11 2008] [error] [client ::1] File does not exist: /htdocs

...but I've never seen it in Feisty. I've gratuitously created /htdocs directories in various places to appease it, such as in /var/www * its subdirectories, in my document root (different from /var/www), in /etc/apache2, etc...

Any ideas?

---

### Post by Newmaniese on 2008-01-16
I am having the same issue. It doesn't make any sense. I wet through /etc/apache2/apache2.conf and all the other config files but I can't find where there is any reference to /htdocs. This is strange; please anyone with any guesses?

---

### Post by Newmaniese on 2008-01-16
Ok I figured it out. 

In a VirtualHost if there is no DocumentRoot defined Apache automatically uses /htdocs as the document root. The easy way to fix this is to define DocumentRoot on each of your VirtualHost. I hope that helps

---

### Post by Sporkman on 2008-01-16
> **Newmaniese said:**
> Ok I figured it out. 

In a VirtualHost if there is no DocumentRoot defined Apache automatically uses /htdocs as the document root. The easy way to fix this is to define DocumentRoot on each of your VirtualHost. I hope that helps

DocumentRoot is defined for all my VirtualHosts...


????

---

### Post by Sporkman on 2008-01-16
Ok, I've figured it out...

The "[client ::1]" represents the loopback connection, so this is invoked from some internal process, and "::1" = the loopback address 127.0.blah blah.

Now all the virtualhosts I have are defined by explicit IP addresses. There is no virtualhost defined for the loopback IP. Furthemore, there was no default DocumentRoot defined in /etc/apache2.conf.

So I added:

DocumentRoot "/home/www"

in /etc/apache2.conf & the problem appears to be solved.

---

### Post by altonbr on 2008-05-14
> **Sporkman said:**
> Ok, I've figured it out...

The "[client ::1]" represents the loopback connection, so this is invoked from some internal process, and "::1" = the loopback address 127.0.blah blah.

Now all the virtualhosts I have are defined by explicit IP addresses. There is no virtualhost defined for the loopback IP. Furthemore, there was no default DocumentRoot defined in /etc/apache2.conf.

So I added:

DocumentRoot "/home/www"

in /etc/apache2.conf & the problem appears to be solved.

Aaaaaah, that makes sense.

What I'll do instead is change the IP address from being explicit to *. Last time I ever do that!

---

