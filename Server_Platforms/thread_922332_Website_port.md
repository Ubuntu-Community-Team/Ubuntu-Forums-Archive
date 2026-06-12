---
title: "Website port"
date: 2008-09-17
forum: Server Platforms
---

### Post by amai on 2008-09-17
what I have read seems you can only configure your sites either on port 80 or 8080.
-is it possible to configure sites on other port(lets say randomly port 20198).

In summary is this possible.
[www.learning.com:20198](www.learning.com:20198)

or it can only be
[www.learning.com:80](www.learning.com:80)
[www.learning.com:8080](www.learning.com:8080)

---

### Post by bigfatdummy on 2008-09-17
Common 'extra httpd ports 81 99 8888 9999, but I would use 8888 as it is the most commonly used alternative to 80 and 8080.

To do this, edit the "httpd.conf" file.

Use "Find" or scroll down to find "Listen 80".

Change this port number to the port that you want to use on your webserver. For example, use "8888".

Use "find" once again to look for "ServerName". Scroll down few lines and you should see the server name you entered during installation. At the end of your server name, change port 80 to 8888.

Save the changes, and restart the Apache server.

You might want to search the internet for commonly assigned ports before you randomly assign a port. A quick google search found this site [http://www.iss.net/security_center/advice/Exploits/Ports/]("http://www.iss.net/security_center/advice/Exploits/Ports/")

---

### Post by amai on 2008-09-17
OK does it mean, i can then assign any port as long as it is not used for something else.

and people will still access my site

---

### Post by lazyart on 2008-09-17
Yes.

Many corporate firewalls will only allow web browsers to use 80 and 443 (http and https).  Folks browsing from home shouldn't have a problem though.

---

