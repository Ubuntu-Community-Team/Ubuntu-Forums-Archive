---
title: "apache, file scanning"
date: 2009-09-10
forum: Security
---

### Post by [pl]ice on 2009-09-10
hello,

Many ppl are scanning my domains for scripts/phpmyadmin etc,
is there a sensible way to block it through firewall, without blocking a normal user, who is trying to view the page?
 The sites are clean, no unnecessary scripts etc. but it's a worry :(

thanks
 

[Sun Dec 14 00:43:05 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin2
[Sun Dec 14 00:43:06 2008] [error] [client 195.134.93.90] File does not exist: /var/www/mysql2
[Sun Dec 14 00:43:06 2008] [error] [client 195.134.93.90] File does not exist: /var/www/admin2
[Sun Dec 14 00:43:07 2008] [error] [client 195.134.93.90] File does not exist: /var/www/db2
[Sun Dec 14 00:43:07 2008] [error] [client 195.134.93.90] File does not exist: /var/www/dbadmin2
[Sun Dec 14 00:43:08 2008] [error] [client 195.134.93.90] File does not exist: /var/www/web
[Sun Dec 14 00:43:08 2008] [error] [client 195.134.93.90] File does not exist: /var/www/admin
[Sun Dec 14 00:43:08 2008] [error] [client 195.134.93.90] File does not exist: /var/www/admin
[Sun Dec 14 00:43:09 2008] [error] [client 195.134.93.90] File does not exist: /var/www/admin
[Sun Dec 14 00:43:09 2008] [error] [client 195.134.93.90] File does not exist: /var/www/mysql-admin2
[Sun Dec 14 00:43:10 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin2
[Sun Dec 14 00:43:10 2008] [error] [client 195.134.93.90] File does not exist: /var/www/mysqladmin2
[Sun Dec 14 00:43:11 2008] [error] [client 195.134.93.90] File does not exist: /var/www/mysql-admin2
[Sun Dec 14 00:43:11 2008] [error] [client 195.134.93.90] script '/var/www/main.php' not found or unable to stat
[Sun Dec 14 00:43:12 2008] [error] [client 195.134.93.90] File does not exist: /var/www/myadmin
[Sun Dec 14 00:43:12 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin
[Sun Dec 14 00:43:12 2008] [error] [client 195.134.93.90] File does not exist: /var/www/xampp
[Sun Dec 14 00:43:13 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin
[Sun Dec 14 00:43:13 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin0
[Sun Dec 14 00:43:14 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin1
[Sun Dec 14 00:43:14 2008] [error] [client 195.134.93.90] File does not exist: /var/www/phpmyadmin2

---

### Post by phillw on 2009-09-11
read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and  [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

The likes of ossecc will blacklist ip addresses for you, there are others. such as moblock, [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

Bhodi has a nice introductory here   [http://blog.bodhizazen.net/linux/how-to-blacklist-an-ip-address-in-apache/](http://blog.bodhizazen.net/linux/how-to-blacklist-an-ip-address-in-apache/)

Regards,

Phill.

---

### Post by [pl]ice on 2009-09-11
hi,
i cant install IDS as i got VPS not stand alone server etc
was using fail2ban, but it has crashed on two occasions, 
the moblock is not good, as they said that it will block lots of IPs. you can't allow that for a business etc :/
  will have to look in ip tables :/

---

### Post by phillw on 2009-09-11
> **'[pl]ice said:**
> hi,
i cant install IDS as i got VPS not stand alone server etc
was using fail2ban, but it has crashed on two occasions, 
the moblock is not good, as they said that it will block lots of IPs. you can't allow that for a business etc :/
  will have to look in ip tables :/

The blocking of lots of  IP's because they are 'bad', I would have thought would have been ideal for business :-\

Phill.

---

### Post by phillw on 2009-09-12
I noticed that the logs are dated dec 2008 - is this a recent attack ?

Phill.

---

### Post by falconindy on 2009-09-12
These aren't attacks, persay. What you're seeing in your logs are bots (notice the timing on the access requests). Put a file called robots.txt in your htdocs root with the following content:
```
User-agent: *
Disallow: /
```If I remember correctly (it's been a while since I've had apache exposed to the public), that should stop them.

---

