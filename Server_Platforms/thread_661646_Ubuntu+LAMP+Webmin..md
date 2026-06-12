---
title: "Ubuntu+LAMP+Webmin."
date: 2008-01-08
forum: Server Platforms
---

### Post by Silent Knight on 2008-01-08
Hi,

I've just installed Ubuntu 7.04 Server with LAMP and Webmin 1.390.
Now I can access Webmin fine etc.

I'm still very new to all of this so I was wondering now that I have everything installed and I want to start hosting PHP based sites where exactly would I upload them too on the server? Which directory does the content need to sit in and how would I configure Webmin to host the content?

Thanks a bunch!!

Regards,
Hanré

---

### Post by smartalecks on 2008-01-08
not sure about web admin stuff, but the path is usually /var/www

---

### Post by Silent Knight on 2008-01-08
Right, I just had a quick look and there is no /var/www directory...
Does that possibly mean that I've done something I was not suppose to along the way?

I thought when I run the installation and select the LAMP install it automatically install the PHP/MySQL/Apache webserver?

---

### Post by gnelson on 2008-01-08
It should install those components..  If you type "localhost" in the address bar or your browser, you should get an Apache welcome page.

---

### Post by Silent Knight on 2008-01-08
If I am doing it from another host does it have to go through a specific port to access the Apache page?

From my Windows machine I can access the Webmin Admin page via: [https://WEBSERVE:10000](https://WEBSERVE:10000)

When I try just going to [http://WEBSERVE](http://WEBSERVE) I just get an error saying 'Page Cannot be displayed'

---

### Post by methodical on 2008-01-08
Do you have port 80 open on your router?

---

### Post by Silent Knight on 2008-01-08
Yes it is, there are no ports blocked on my router.

---

### Post by DSK on 2008-01-08
Does
[https://WEBSERVE:10000/apache/](https://WEBSERVE:10000/apache/)
show that you have apache webserver running?

Mine has a virtual server listed with:
address = any
server name = auotmatic
port=any
Document Root = /var/www/

---

### Post by Silent Knight on 2008-01-11
Thanks for the help guys!

It seems that the distro I used was somehow corrupted and didn't install everything correctly...

I have now downloaded a new one 7.10 and installed and it all works.

Only question I have now is, if I want to install a template PHP site that I downloaded from Joomlashack.com, how would I go about doing this so I can browse to it?

So far I've downloaded the ZIP file, unzipped it and then copied the folder with all contents via winscp over to /var/www BUT when I browse to [http://webserver/Joomla](http://webserver/Joomla) it comes up with a message saying 'Direct Access to this location is not allowed.' 

Thanks again!

---

### Post by chris.zeman on 2008-01-12
Did you install Joomla itself, or just upload a template?

---

