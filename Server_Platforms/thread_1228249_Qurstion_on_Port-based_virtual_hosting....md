---
title: "Qurstion on Port-based virtual hosting..."
date: 2009-07-31
forum: Server Platforms
---

### Post by XtremeGamer99 on 2009-07-31
Hello,

I have a home server that's serving up two different blogs via name-based virtual hosting (blog1.com and blog2.com go to their respective directory roots). The server itself has one public IP.

I'd like to have a "adminitrative" site that is accessible by a port number (and HTTP authentication of course), no matter which domain I use.

EG:
blog1.com - /home/www/blog1.com
blog2.com - /home/www/blog2.com
blog1.com:99 OR blog2.com:99 - /home/www/admin

This is what I have currently:
```

Listen 80
Listen 99

NameVirtualHost *:80
NameVirtualHost *:99


<Directory /home/www/>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride All
	Order allow,deny
	allow from all
</Directory>

<VirtualHost *:80>
	ServerName blog1.com	
	DocumentRoot /home/www/blog.com
</VirtualHost>
<VirtualHost *:80>
	ServerName blog2.com
	DocumentRoot /home/www/blog2.com
</VirtualHost>
<VirtualHost *:99>
	DocumentRoot /home/www/admin
</VirtualHost>

```

And it doesn't work. How would I do this?

ALSO: No reason to post a new topic. I'm using DYNDns.org to direct the two blogs to my IP address. Currently, my router is the one that does the IP address updating. However, I can only update one hostname (blog1.com) while the other hostname (blog2.com) doesn't get updated if my IP address changes. Is there a linux program that will allow to to update multiple DYNDns.org hostnames?

---

### Post by samosamo on 2009-07-31
[http://www.virtualmin.com/download](http://www.virtualmin.com/download)

---

### Post by XtremeGamer99 on 2009-07-31
Er... that's looks like an interesting peice of software, and I may look into it, but it doesn't really answer my question. <_<

---

### Post by samosamo on 2009-07-31
Not only does it answer your question. It answers all of your future questions about virtual hosts as well.

---

### Post by XtremeGamer99 on 2009-07-31
With all due respect, I'm not looking for a "product" of which you are advertising, I am looking for a simple answer to my question. I do not want to play around and try to get another application to work just so that I can have a port-based virtual host.

I am sure it is a fine application, and like I said I may look into it later. But it is not what I want at the moment.

---

### Post by bolerodan on 2009-08-01
For your virtualhost entry thats listening on Port 99, you have no servername directive in that block. How do you expect Apache to figure out to serve that virtual host with no servername?

I would think you would need to atleast supply a servername, then put in aliases to serve the other domains. Say for example

```

<VirtualHost *:99>
        ServerName blog1.com
        ServerAlias blog2.com www.blog2.com www.blog1.com
	DocumentRoot /home/www/admin
</VirtualHost>

```

try something like that.. perhaps that will work?

---

### Post by XtremeGamer99 on 2009-08-01
Thanks for the reply!

No, it still does not work. Gives me a "Unable to connect"

EDIT: Nevermind, it works. Clumsy me forgot to forward the port. <_<

Thanks so much for the help!

---

