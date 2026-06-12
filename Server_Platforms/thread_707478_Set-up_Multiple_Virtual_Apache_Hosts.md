---
title: "Set-up Multiple Virtual Apache Hosts?"
date: 2008-02-25
forum: Server Platforms
---

### Post by Xarok on 2008-02-25
So I've set up a general LAMP site before, but now I need to host multiple sites.

I've recently made a fresh install of Xubuntu 6.06 with Apache2, PHP5, MySQL

I don't understand how to create mutliple virtual hosts.

How can I have three seperate websites, one listening on port 81, another on port 82, and the last one on port 83?

Thanks

---

### Post by Average Joe on 2008-02-25
I think I have done something similar. I have two websites running. One that I use for testing and is only visible locally on 127.0.0.1:80, and one that is visible for the entire world on the IP address that I use from my router, also on port 80.

You can find my initial set-up routine [here]("http://ubuntuforums.org/showthread.php?t=255464"). Although I have changed a few things since, like setting setting one website up for the outside world, I think you will get the point. In your case you could probably just change some ports in the settings I have used.

---

### Post by Mithrilhall on 2008-02-25
Try installing Webmin. It looks like setting up virtual hosts is easy via its interface.


[http://sourceforge.net/project/showfiles.php?group_id=17457&package_id=13391](http://sourceforge.net/project/showfiles.php?group_id=17457&package_id=13391)

---

### Post by Keywil on 2008-02-25
I got it going on my box just using Apache1.3 localhost and listened on different ports. 

The Document root had to start from root /var/www/html/...

In my directories I have
 /var/www/html/test1/index.html
 /var/www/html/test2/index.html

I configured apache to also listen to port 8000 (edit httpd.conf)

```
#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, in addition to the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to 
# prevent Apache from glomming onto all bound IP addresses (0.0.0.0)
#
#Listen 12.34.56.78:80
Listen 80
Listen 8000
```
Then modified the virtual hosts to point to the different folders... 
```
NameVirtualHost *:80
NameVirtualHost *:8000
#
# NOTE: NameVirtualHost cannot be used without a port specifier 
# (e.g. :80) if mod_ssl is being used, due to the nature of the
# SSL protocol.
#

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for requests without a known
# server name.
#
<VirtualHost *:80>
    ServerAdmin webmaster@dummy-host.example.com
    DocumentRoot /var/www/html/test1
    ServerName test1.com
</VirtualHost>
<VirtualHost *:8000>
 DocumentRoot /var/www/html/test2
 ServerName test2.com
</VirtualHost>
```

Restart apache, open a browser and voila - [http://localhost](http://localhost)  displays /test1/index.html  and [http://localhost:8000](http://localhost:8000) displays /test2/index.html

---

