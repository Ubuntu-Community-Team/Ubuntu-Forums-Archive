---
title: "Cannot get proxy to work..."
date: 2009-03-01
forum: Server Platforms
---

### Post by jamieh on 2009-03-01
I have several Ubuntu servers on one LAN, but I only get one IP address.

I am trying accomplish this:

domain.com - points to 192.168.10.**101**
sub.domain.com - points to 192.168.10.**101**
anothersub.domain.com - points to 192.168.10.**102**

I have one server with mod_proxy installed. It is to take care of said actions.

My router is a WRT54G2. Port 80 forwards to Server A. Server A is to proxy the request for test.webs.ath.cx to Server B.  Server A refuses to do this. Here is the error log for Server A:

```

[Sun Mar 01 00:34:11 2009] [error] [client 24.207.66.82] client denied by server configuration: proxy:http://192.168.10.104/
[Sun Mar 01 00:46:53 2009] [error] [client 24.207.66.82] client denied by server configuration: proxy:http://192.168.10.104/
[Sun Mar 01 00:48:38 2009] [error] [client 24.207.66.82] client denied by server configuration: proxy:http://192.168.10.104/
[Sun Mar 01 00:48:41 2009] [error] [client 24.207.66.82] client denied by server configuration: proxy:http://192.168.10.104/

```

What could this mean. Here is the log for Server B:
```

[Fri Feb 27 22:02:40 2009] [error] [client 96.49.215.184] File does not exist: /var/www/tesr
[Sat Feb 28 23:19:28 2009] [notice] caught SIGTERM, shutting down
[Sat Feb 28 23:19:29 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sat Feb 28 23:37:27 2009] [error] [client 59.95.217.75] File does not exist: /var/www/favicon.ico
[Sat Feb 28 23:37:30 2009] [error] [client 59.95.217.75] File does not exist: /var/www/favicon.ico

```

Why does it keep complaining about "/var/www/tesr"? The directory is 'var/www/test'.

The VirtualHost entry for Server B:

```

# Test
<VirtualHost *>
DocumentRoot /var/www/test
ServerName test.webs.ath.cx

<directory /var/www/test>
Order allow,deny
allow from all
</directory>

</VirtualHost>

```

And for Server A:

```

<VirtualHost *>

ServerName test.webs.ath.cx

ProxyPreserveHost On
ProxyPass / http://192.168.10.104/
ProxyPassReverse / http://192.168.10.104/
</VirtualHost>

```

Whenever I try to access test.webs.ath.cx, I get a 403 error.

What gives?

---

