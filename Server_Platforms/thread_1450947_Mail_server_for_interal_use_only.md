---
title: "Mail server for interal use only"
date: 2010-04-09
forum: Server Platforms
---

### Post by Hokorippoi on 2010-04-09
I am talking classes at a university. One of my classes has a large group project. 
Part of the project has me setting up a mail server.  I don't have a domain to use for this server, So I need to have it setup for local use only. but I have not been able to find much info on how to do so for local use only. 

EDIT: got some of it working. 
Still would like a good guild about this.

---

### Post by HermanAB on 2010-04-10
Citadel.  You can set it up in about 30 minutes.  They even have a pre-installed Vmware image:
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

---

### Post by ruuden on 2010-04-10
you might want to set up a local DNS server too. 

```
sudo apt-get install bind9 bind9utils
```

---

### Post by Tylerjd on 2010-04-10
And webmin for easy administration of the DNS or mailserver... [http://www.webmin.com/](http://www.webmin.com/)

---

