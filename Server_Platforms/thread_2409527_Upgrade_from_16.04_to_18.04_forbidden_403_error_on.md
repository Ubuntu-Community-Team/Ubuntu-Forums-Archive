---
title: "Upgrade from 16.04 to 18.04 forbidden 403 error on apache"
date: 2019-01-03
forum: Server Platforms
---

### Post by kubwit on 2019-01-03
Hallo.

i recently upgraded my ubuntu server from 16.04 to 18.04. running mysql and php 7.2.

I'm facing apache2 "forbidden access " errors in my Joomla installation and also in phpmyadmin making simple action like create and drop tables.

Upgrading vi do-release-upgrade i confirmed all config to keep the old ones.

i tried to check error.log but nothing visible.

Seems like there are some privilege problems. i checked my vhost file but it seems all ok
```
DocumentRoot /path/to/server/root
<Directory "/path/to/server/root">
AllowOverride all
Allow from all
Order allow,deny
Options None
Require all granted
</Directory>
```

First i thought something with joomla was not fine. Having the same problem in phpmyadmin made me think that there should be some different problems.

Somebody can guve me a hint please?

```

[LIST]
[*]              Server: Localhost via UNIX socket
[*]              Server type: MySQL
[*]              Server version: 5.7.24-0ubuntu0.18.04.1 - (Ubuntu)
[*]              Protocol version: 10
[*]              User: root@localhost
[*]        Server charset:                    UTF-8 Unicode           (utf8)        
[/LIST]

```

```

[LIST]
[*]              Apache/2.4.29 (Ubuntu)
[*]              Database client version: libmysql - mysqlnd 5.0.12-dev -  20150407 - $Id: 38fea24f2847fa7519001be390c98ae0acafe387 $
[*]              PHP extension:   mysqli[[IMG]https://www.ilmondodiwit.com/phpmyadmin/themes/dot.gif[/IMG]]("https://www.ilmondodiwit.com/phpmyadmin/url.php?url=https%3A%2F%2Fphp.net%2Fmanual%2Fen%2Fbook.mysqli.php")  mbstring[[IMG]https://www.ilmondodiwit.com/phpmyadmin/themes/dot.gif[/IMG]]("https://www.ilmondodiwit.com/phpmyadmin/url.php?url=https%3A%2F%2Fphp.net%2Fmanual%2Fen%2Fbook.mbstring.php")
[*]              PHP version: 7.2.13-1+ubuntu16.04.1+deb.sury.org+1
[/LIST]

```


Thanks in advance for your reply

---

### Post by Bachstelze on 2019-01-07
If you see nothing in your logs, it means your logs are not "sensitive" enough, so you should increase your LogLevel. By the way, I recommed setting separate logs for each vhost for better readability, for example in each of my vhost files I have something like that:

```
<VirtualHost *:443>
    ServerName pma.domain
    [...]
    #CustomLog /var/log/apache2/pma.access.log combined
    ErrorLog /var/log/apache2/pma.error.log
    LogLevel warn
</VirtualHost>
```

And when desired I can increase (or decrease) the LogLevel for that particular vhost, and even enable full access logging by uncommenting the CustomLog directive.

---

