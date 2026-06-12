---
title: "Apache not logging anymore"
date: 2011-07-05
forum: Server Platforms
---

### Post by pungki on 2011-07-05
Hi All,

I'm using Ubuntu 10.04 64 bit Server Edition here. I'm running Apache as a web server. I just found that Apache is not logging to access.log and error.log anymore.

But the service is running well. Log parameter at /etc/apache2/apache2.conf seems to be OK. Here's the line :

ErrorLog /var/log/apache2/error.log
LogLevel warn
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

I already tried restart the server, but no luck. Is there any place should I check?

Please help.

Thanks

--
Pungki Arianto

---

### Post by windependence on 2011-07-05
Are you hosting more than one site on this box and do you want a log for each one?

-Tim

---

### Post by i.r.id10t on 2011-07-05
How big is hte existing log file?  I recall an old (apache 1.x IIRC) bug that wouldn't let the log file log new stuff if it was over 2gb

---

