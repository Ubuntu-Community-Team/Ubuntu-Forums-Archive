---
title: "Display domain name instead of ip address"
date: 2008-12-05
forum: Server Platforms
---

### Post by laughinglizard on 2008-12-05
I set up a LAMP server about a year ago to host my website and it has been flawless with one exception.  When I type in my address [www.**.ca](www.**.ca), I go to my website, however instead of [www.**.ca](www.**.ca) being displayed in the address bar I get an ip address.  Is there a way to configure Apache2 to display the domain name instead of the ip?

Thanks, and I apologise if this has been answered elsewhere but I haven't been able to find it.

LL

---

### Post by wkitty42 on 2008-12-06
> **laughinglizard said:**
> I set up a LAMP server about a year ago to host my website and it has been flawless with one exception.  When I type in my address [www.**.ca](www.**.ca), I go to my website, however instead of [www.**.ca](www.**.ca) being displayed in the address bar I get an ip address.  Is there a way to configure Apache2 to display the domain name instead of the ip?

Thanks, and I apologise if this has been answered elsewhere but I haven't been able to find it.

LL
what do you have listed as your **ServerName** entry in your /etc/apache2/sites-available/* file(s)? ;)

---

### Post by laughinglizard on 2008-12-06
ServerName is my domain name.

---

### Post by R.Bucky on 2008-12-06
A couple of things come to mind. My LAMP server utilized the ServerName declaration in the /etc/apache2/httpd.conf. Additionally, ensure that you have the proper IP address with your domain company (e.g. Network Solutions or GoDaddy).

---

### Post by laughinglizard on 2008-12-06
I would assume that since my site is accessible from the web when you type in the domain name that all is well as far as ip routing goes.   The thing is when you type in my domain name "www.laughinglizard.ca" you go to my site, but the ip assigned to my modem is returned in the address bar, and I would like it to return with the domain name.

---

### Post by laughinglizard on 2008-12-06
Another assumption.  The domain is registered at Domains at Cost and is forwarded to my ip.  My guess is that in order to have the domain name returned in the address bar I will somehow have to resolve the ip to the name.  

If this is so, can anyone point me in the right direction to do this?

---

