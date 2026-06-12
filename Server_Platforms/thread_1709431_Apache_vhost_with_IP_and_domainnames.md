---
title: "Apache vhost with IP and domainnames"
date: 2011-03-18
forum: Server Platforms
---

### Post by mzoller on 2011-03-18
I would like to set up apache so that:

URL: [http://123.123.123.123](http://123.123.123.123) -> goes to site1 (for z-push)

URL [http://some.domain.name](http://some.domain.name) -> goes to site2
...
URL [http://some.otherdomain.name](http://some.otherdomain.name) -> goes to site3

Is it possible with only 1 IP or do i need 2 IPs? 

I have tried several configurations, but they always seem to lead to a dead end with either the IP-site or the domain-sites not working. There has to be a right way to do this. 

Help appreciated!

---

### Post by SeijiSensei on 2011-03-18
You'd need to add two <VirtualHost> containers for the name-based servers, then reconfigure the catch-all host in /etc/apache2/sites-enabled/000-default so the DocumentRoot points to site1.

---

### Post by wongo888 on 2011-03-18
Read the section under 'Basic Settings'

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by mzoller on 2011-03-20
thanks - I didn't realize the order of catch-all and VirtualHost Containers made a difference. It works now

---

