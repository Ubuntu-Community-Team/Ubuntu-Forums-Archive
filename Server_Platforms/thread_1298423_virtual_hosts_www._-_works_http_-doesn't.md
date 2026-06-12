---
title: "virtual hosts: www. - works http:// -doesn't"
date: 2009-10-22
forum: Server Platforms
---

### Post by doublearon on 2009-10-22
Fellow ubuntu brethren, I have a problem that is beyond my current level of comprehension and I would sincerely appreciate a hint in the right direction for my quest to host multiple sites on one IP.


domain name: [www.lylestevens.com](www.lylestevens.com) doesn't work as [http://lylestevens.com](http://lylestevens.com) without the www. It just goes to a different domain when not using www.


Operating system 	Ubuntu Linux 9.04

Webmin version 	1.490

using Godady's "totaldns"

Kernel and CPU 	Linux 2.6.28-15-server on i686

server ip 70.91.126.213

Please forgive the silly test domain name, but when I don't use www. the wrong virtual server for drunknuderetardedgirls.com is used.


/etc/apache2/sites-available/:

```
<VirtualHost *:80>
DocumentRoot /home/user1/lylestevens
ServerName *.lylestevens.com
<Directory "/home/user1/lylestevens">
allow from all
Options +Indexes
</Directory>
ServerAlias *.lylestevens.com
</VirtualHost>
```

```

<VirtualHost *:80>
DocumentRoot "/home/user2/htdocs"
ServerName www.drunknuderetardedgirls.com
<Directory "/home/user2/htdocs">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

I used a wildcard on the hosts available for lylestevens if only to see if maybe I could get it to recognize any prefix such as http or www to no avail. I did notice that the document root for the second test domain that resolves correctly is surrounded by " ", but I'm not sure if that makes any difference as I haven't tried to do that yet.

Any hints comments or suggestions would be so sincerely appreciated. Thanks in advance!

---

### Post by R.Bucky on 2009-10-24
I have the opposite question last week. My domains only resolved when typing in [http://.](http://.) You need to add ServerAlias to your file.

---

### Post by edenCC on 2009-10-25
Plus you might need to check your dns entries as well. good luck!

---

