---
title: "Ebox DNS cname records"
date: 2010-10-29
forum: Server Platforms
---

### Post by ic3000 on 2010-10-29
Hi to all!

I'm using ubuntu 10.04 server and ebox 1.5 from ubuntu repositories for DNS on my school. Until now i had zero problems with the configuration.

We are moving to Google Apps for mail and to use the adress "mail.myschool.com" we need to configure a CNAME on the server.

I found that ebox 1.5 on the repositories dont have a option to configure CNAME dns records.

I know that i can had a line on /etc/bind/myschool.com and it works ok until the server is rebooted, but when this happen this line is overwritten by ebox.

Does anyone know a good way to configure CNAME records on ebox so that on reboot everything stays as configured before?

Thanks in advance!

---

