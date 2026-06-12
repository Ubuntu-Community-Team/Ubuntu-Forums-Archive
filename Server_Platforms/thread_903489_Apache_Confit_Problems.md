---
title: "Apache Confit Problems"
date: 2008-08-28
forum: Server Platforms
---

### Post by Vegan on 2008-08-28
With Ubuntu server running, I have telnet access working, and FTP working so I can manage the machine beheaded finally.

Installing Apache and testing local host worked, so now I am trying to get my virtual host working with a bunch of URLs fed into a single IP address.

I connect to the machine with its local IP address, I get forbidden to see the root /. So I know Apache is listening, its some config problem. I have 1 line in hpptd.conf as

```
NamedVirtualHosts 192.168.7.250:80 
```

and several conf files, one for each named host.
Here is one of my vhost files:

```
<VirtualHost 192.168.7.250:80>
  ServerAdmin abuse@hotmail.com
  DocumentRoot /web/computer-chess
  ServerName computer-chess.dyndns.biz
  ServerAlias www.computer-chess.dyndns.biz
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
</Directory>
<Directory /web/computer-chess>
  Options -Indexes
  AllowOverride All
  Order Allow,Deny
  Allow From All
</Directory>
</VirtualHost>

```

Any thoughts?

---

