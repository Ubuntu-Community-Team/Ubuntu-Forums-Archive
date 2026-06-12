---
title: "Apache - IIS - Apache"
date: 2009-06-18
forum: Server Platforms
---

### Post by tyampoo on 2009-06-18
Hi,

Learning ABC's of Linux and this is my first post. I am not even sure if this the right spot for my question.

This is what I have in my test env
Ubuntu 8.10 (static IP 192.168.10.20)
Apache2
A Web Application, say webapp
Windows XP with IIS 5.0, hosting webapp (static IP 192.168.10.30)
Windows 2003 with IIS 6.0 hosting webapp (static IP 192.168.10.40)
webapp is set to use "Integrated Windows Authentication"

What I want:
.reverse proxy to secure IIS box

my config:
in site, webApp i have,
NameVirtualHost 192.168.10.20:80

<VirtualHost 192.168.10.20:80>
  ProxyRequests off
  ProxyPass  /webApp [http://192.168.10.xx/webapp](http://192.168.10.xx/webapp)
  ProxyPassReverse  /webApp [http://192.168.10.xx/webapp](http://192.168.10.xx/webapp)

  Errorlog /var/log/apache2/error.log

  ProxyHTMLLogVerbose On
  LogLevel  debug
  CustomLog  /var/log/apache2/access.log combined
</VirtualHost>

webApp is enabled using a2ensite and default has been disabled

My problem:
when xx is 30 it works, asks for username/password and rest fine. 
when xx is 40, it ask for username/password and gives 404 page not found error the first time and if i hit enter again it now works.

My question:
1. Why am i getting such behavior?
2. If i am to replicate this in production server what are the things that i would need to consider?

As I said, I am new to Linux enviroment, please be kind to write bit more.

Thank u,
Tyampoo

---

### Post by tyampoo on 2009-06-18
I really anticipate replies from the community.

---

### Post by Wim Sturkenboom on 2009-06-19
Your title reads apache - iis - apache. However your problem refers to .30 and .40 which are windows machines. What am I missing here?

---

### Post by tyampoo on 2009-06-19
Thanks Wim,

The web requests to .30 and .40 are thru the apache (reverse proxy'd) to them. 

Thanks,

---

### Post by tyampoo on 2009-06-22
I guess someone might have come across this problem.

---

### Post by Wim Sturkenboom on 2009-06-23
Sorry, but can't help you further.

WimS

---

### Post by windependence on 2009-06-23
If you just want to set up a reverse proxy for the IIS machines, you can do it with Apache, or you can use something like squid.

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

[http://wiki.squid-cache.org/SquidFaq/ReverseProxy](http://wiki.squid-cache.org/SquidFaq/ReverseProxy)

This one looks like exactly what you want to do:

[http://blog.kukiel.net/2008/12/blog-post.html](http://blog.kukiel.net/2008/12/blog-post.html)

-Tim

---

### Post by tyampoo on 2009-06-23
Thank you Tim,

With ProxyPreseverHost set, it seems to work. I will close this thread for now.

Thanks again.

---

