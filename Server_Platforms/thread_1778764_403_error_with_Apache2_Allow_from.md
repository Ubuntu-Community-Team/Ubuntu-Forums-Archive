---
title: "403 error with Apache2 Allow from"
date: 2011-06-09
forum: Server Platforms
---

### Post by misfit815 on 2011-06-09
I'm running a LAMP server on 10.10. I have the following in my apache2.conf:

```

<VirtualHost *:80>
  ServerName site1.org
  ServerAlias site1.org *.site1.org
  DocumentRoot /var/www/site1
</VirtualHost>

<VirtualHost *:80>
  ServerName site2.org
  ServerAlias site2.org
  DocumentRoot /var/www/site2

Alias /app1 "/srv/app1
<Directory "/srv/app1">
  AllowOverride All
  Order allow,deny
  Allow from 192.168.1.1 192.168.2.2 192.168.3
</Directory>

Alias /app2 "/srv/app2"
<Directory "/srv/app2">
  AllowOverride All
  Order allow,deny
  Allow from 192.168.1.1 192.168.2.2 192.168.3
</Directory>

Alias /wiki "/var/lib/mediawiki"
<Directory "/var/lib/mediawiki">
  Options +FollowSymLinks
  AllowOverride All
  Order allow,deny
  Allow from 192.168.1.1 192.168.2.2 192.168.3
  #Allow from all
</Directory>
<Directory "/var/lib/mediawiki/config">
  Options -FollowSymLinks
  AllowOverride None
</Directory>
<Directory "/var/lib/mediawiki/upload">
  Options -FollowSymLinks
  AllowOverride None
</Directory>

</VirtualHost>

<VirtualHost _default_:80>
  DocumentRoot /var/www/site1
</VirtualHost>

```

Note the use of "Allow from" on all three apps. This works fine for two of them, but fails for mediawiki (403 error). If I switch it to "Allow from all" it works fine.

Any suggestions on what I'm missing would be appreciated. Also, if there's an easier way to whitelist those directories by IP address, I'd love to hear it. Thanks.

---

### Post by ruffEdgz on 2011-06-09
Well, are you in any of the allowed IP's or range?
```

Allow from 192.168.1.1 192.168.2.2 192.168.3

```
So is your IP either 192.168.1.1, 192.168.2.2 or in the range of 192.168.3.0/24?

If you also check your logs in /var/log/apache2 and maybe grep for "wiki", does it say anything in there about why you are being denied (I have ideas but don't want to assume anything at this point)?

Cheers!

---

### Post by misfit815 on 2011-06-09
Yeah, the whitelist is exactly the same for all three <Directory> entries. And I've confirmed it by looking at /var/log/apache2/error.log. Here's the latest:

```

[Thu Jun 09 08:57:26 2011] [error] [client 192.168.2.2] client denied by server configuration: /var/lib/mediawiki/index.php

```

Obviously, IP addresses have been changed/obscured, but I've checked them over and over. And, like I said, works fine for the other two.

---

### Post by misfit815 on 2011-06-09
Marking this as solved. I swear I must've looked at the IP addresses a dozen times, yet I was one digit off. I'm going to go sit in a corner and sob quietly now.

---

### Post by ruffEdgz on 2011-06-09
If you change **AllowOverride All** to **AllowOverride None**?

If that does help, then that means something in /var/lib/mediawiki could be overriding your configuration file.

If it doesn't, maybe we can do some more testing with the **Allow** like making the 192.168.2.2 into 192.168.2?

Cheers!

::EDIT:: LOL, I'm so sorry man. Don't cry, we are all human. I'm just glad its working the way it should ;)

---

