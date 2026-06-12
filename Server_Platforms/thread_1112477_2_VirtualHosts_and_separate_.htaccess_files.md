---
title: "2 VirtualHosts and separate .htaccess files"
date: 2009-03-31
forum: Server Platforms
---

### Post by maryon on 2009-03-31
Hi,

I have 2 VirtualHosts and I would like them to use separate .htaccess files.
First server is in /var/www/server1/, second in /var/www/server2/.
Their (separate) .conf files are:

server1.conf:

NameVirtualHost server1.com
<VirtualHost server1.com>
	ServerName [www.server1.com](www.server1.com)
	DocumentRoot /var/www/server1
</VirtualHost>

server2.conf:

<VirtualHost server2.com>
	ServerName [www.server2.com](www.server2.com)
	DocumentRoot /var/www/server2
</VirtualHost>

There are also 2 separate .htaccess files, one in /var/www/server1/ and one in /var/www/server2/. The problem is that server2 uses rules from his .htaccess PLUS rules from server1's .htaccess and I don't know why. I've probably made a mistake in .conf files, but I'm not sure. :/ Server1 uses only his own .htaccess and it's ok.

What am I doing wrong?

Thanks in advance.

M

---

### Post by BkkBonanza on 2009-03-31
Use,
NameVirtualHost *:80

Don't use a domain name in that line. Not sure what the result would be here but it could be causing this issue.

---

