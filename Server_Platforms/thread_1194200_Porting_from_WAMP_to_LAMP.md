---
title: "Porting from WAMP to LAMP"
date: 2009-06-22
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2009-06-22
Hi all

The following code is extracted from WAMP on Windows, the file being C:/wamp/bin/apache/Apache2.2.10/conf/httpd.conf
```
# Virtual hosts
Include conf/extra/httpd-vhosts.conf
```
The following code is also extracted from WAMP om Windows, the file being C:/wamp/bin/apache/Apache2.2.10/conf/extra/httpd-vhosts.conf, IOW, the 'Included' file.

```
<VirtualHost *:80>
	ServerName www.mysite1.com
	ServerAlias mysite1.com mysite1
    DocumentRoot C:/wamp/www/mysite1
    ErrorLog C:/wamp/www/mysite1/logs/error.log
    CustomLog C:/wamp/www/mysite1/logs/access.log common
</VirtualHost>

<VirtualHost *:80>
	ServerName www.mysite2.com
	ServerAlias mysite2.com mysite2
    DocumentRoot C:/wamp/www/mysite2
    ErrorLog C:/wamp/www/mysite2/logs/error.log
    CustomLog C:/wamp/www/mysite2/logs/access.log common
</VirtualHost>

<VirtualHost *:80>
	ServerName www.mysite3.com
	ServerAlias mysite3.com mysite3
    DocumentRoot C:/wamp/www/mysite3
    ErrorLog C:/wamp/www/mysite3/logs/error.log
    CustomLog C:/wamp/www/mysite3/logs/access.log common
</VirtualHost>
```

The code allows n websites to exist in their own folders below C:/wamp/www/ on Windows.

How does one setup the equivalent on a Ubuntu Server 9.04, please?

TIA

Chris

---

