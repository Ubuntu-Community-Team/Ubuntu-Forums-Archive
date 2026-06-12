---
title: "Apache NameVirtualHost"
date: 2011-07-13
forum: Server Platforms
---

### Post by windwardquay on 2011-07-13
I am using name based virtual hosts on a dedicated Ubuntu 10.04 box.

Before now I have simply added my virtual hosts to the default but now I realise this may be wrong. I read [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html) from which I gather that I should perhaps have a separate file for each virtual host and create the symnlink.

However if I have multiple virtualhost files other than _default_ I still need NameVirtualHosts somewhere but where?

For the moment I have added it to the foot of the default file but it strikes me that it may be better to leave the default alone. After all if I am going to edit it for one thing why not add all the virtualhosts to the default as well?

---

### Post by Bachstelze on 2011-07-13
On Natty it's in /etc/apache2/ports.conf

---

### Post by windwardquay on 2011-07-13
Aha - same on LL.

Looks like as good a place as any.

Job done many thanks.

---

