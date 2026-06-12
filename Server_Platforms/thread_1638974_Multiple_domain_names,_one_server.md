---
title: "Multiple domain names, one server"
date: 2010-12-06
forum: Server Platforms
---

### Post by DanHorniblow on 2010-12-06
Hi, I currently have two no-ip domain names being forwarded on port 80 from my router to my ubuntu server 10.10 running apache.

I want each domain name to have a different web root.

For example I want [http://domain1.no-ip.org](http://domain1.no-ip.org) to point to a web root of /var/www/domain1/ and [http://domain2.no-ip.org](http://domain2.no-ip.org) to point to a web root of /var/www/domain2/

how would I do something like this?

I have webmin installed if that helps

Also anyone know of a good email server package for ubuntu server 10.10

:D

---

### Post by stlsaint on 2010-12-06
What you are referring to is called virtual hosting. It is done various ways depending on what web server you are using. If you are using apache then go to the apache website and search for their virtual hosting tutorial. 
(sorry i would give you a direct link but im at work and not on personal machine!):guitar:

---

### Post by DanHorniblow on 2010-12-08
Thanks will look at that tonight

:)

---

### Post by R.Bucky on 2010-12-08
This article explains the VirtualHost config [http://nwlinux.com/blog/hosting-2-domains-with-1-server/]("http://nwlinux.com/blog/hosting-2-domains-with-1-server/")

---

