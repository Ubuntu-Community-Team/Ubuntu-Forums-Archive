---
title: "Host file and virtual hosts"
date: 2012-01-28
forum: Server Platforms
---

### Post by davidtheo on 2012-01-28
Hi, 

Can someone please tell me how to set up a host and virtual hosts when I have two or more sites

I have these domains

[www.davidtheo.com]("http://www.davidtheo.com")
[www.stroodcrafts.co.uk]("http://www.stroodcrafts.co.uk")

My host file is

127.0.0.2  [www.stroodcrafts.co.uk]("http://www.stroodcrafts.co.uk")
127.0.0.3 [www.davidtheo.com]("http://www.davidtheo.com")

my virtualHost files are 

NameVirtualHost 127.0.0.2:80 <VirtualHost www.stroodcrafts.co.uk:80>     ServerName [www.stroodcrafts.co.uk]("http://www.stroodcrafts.co.uk")     DocumentRoot /***/***/www.stroodcrafts.co.uk     <Directory /***/***/www.stroodcrafts.co.uk/>     Options Indexes FollowSymLinks MultiViews     AllowOverride All     </Directory> </VirtualHost>

and

NameVirtualHost 127.0.0.3:80 <VirtualHost www.davidtheo.com:80>     ServerName [www.davidtheo.com]("http://www.davidtheo.com")     DocumentRoot /***/***/www.stroodcrafts.co.uk     <Directory /***/***/www.stroodcrafts.co.uk/>     Options Indexes FollowSymLinks MultiViews     AllowOverride All     </Directory> </VirtualHost>


But when I try to go to [www.stroodcrafts.co.uk]("http://www.stroodcrafts.co.uk") I get an Server not found error
and when I go to [www.davidtheo.com]("http://www.davidtheo.com") I get the default apache2 index page

I am using the same IP address for both sites

please help

---

### Post by TheFu on 2012-01-29
I'm not certain I completely understand your intentions, but you probably do not want to specify the external DNS names inside your /etc/hosts file at all.  VirtualHosts in a web server like apache do not necessarily tie to the /etc/hosts file on the same server. It is the "Name" in the apache configuration files that matter.  

This guide may be helpful: [http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html](http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html)

The outside, public DNS does need to point to your public IP(s) correctly.  That is critical for this to work.

---

### Post by satanselbow on 2012-01-29
> **davidtheo said:**
> Hi, 

Can someone please tell me how to set up a host and virtual hosts when I have two or more sites

I have these domains

[www.davidtheo.com]("http://www.davidtheo.com")
[www.stroodcrafts.co.uk]("http://www.stroodcrafts.co.uk")


As stated above you really need to let us know what you are trying to achieve...

Do you want to serve these domains yourself - or set up a development environment so you can mimic your hosting service?

Your 2nd domain is currently available for registration so posting it on an internet forum is really not a good idea if you have plans to register it yourself ;)

---

