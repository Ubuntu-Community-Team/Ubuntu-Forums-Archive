---
title: "Bind9 Go To Subfolder"
date: 2009-05-05
forum: Server Platforms
---

### Post by shadowayex on 2009-05-05
On bind9, when you set the domain name, you have it go to a certain IP, then it loads the index page in the www directory. How do I make it so it goes into a subfolder. Like, instead of going to 1.2.3.4/index.html (or something like that), can I make it go to 1.2.3.4/folder1/index.html?

---

### Post by gombadi on 2009-05-05
That is not set in bind. Bind only does domain names to/from ip addresses.

apache vhost is where you set the document root for a vhost.

Have a look at the /etc/apache2/sites-available directory for the vhost config files and set the DocumentRoot to the correct location for the vhost you want.

---

### Post by shadowayex on 2009-05-05
> **gombadi said:**
> That is not set in bind. Bind only does domain names to/from ip addresses.

apache vhost is where you set the document root for a vhost.

Have a look at the /etc/apache2/sites-available directory for the vhost config files and set the DocumentRoot to the correct location for the vhost you want.

I think I understand how that's supposed to work, but what if I want to host more than one site off of my server and have different domain names go to different folders?

---

### Post by ejschaefer on 2009-05-05
Hello, 

What you're looking for is name-based Virtual Hosting:

[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

Each site will have its own container in the Apache configuation. The information in the container will specify which folder the specific domain should be served from.

Here is an example of 2 sites sharing an IP but being served from 2 different folders (as seen in the above link to Apache docs):
```

NameVirtualHost 1.2.3.4:80

<VirtualHost 1.2.3.4:80>
ServerName [www.domain.tld](www.domain.tld)
ServerAlias domain.tld
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost 1.2.3.4:80>
ServerName [www.otherdomain.tld](www.otherdomain.tld)
ServerAlias otherdomain.tld
DocumentRoot /www/otherdomain
</VirtualHost>

```

---

### Post by shadowayex on 2009-05-05
Ok, I added this to that file:

```
<VirtualHost *:80>
	ServerName www.hugdontmug.com
	ServerAlias hugdontmug.com *.hugdontmug.com
	DocumentRoot /www/hugdontmug
</VirtualHost>
```

And when I went to restart apache I got this:

```
Restarting web server: apache2Warning: DocumentRoot [/www/hugdontmug] does not exist
Warning: DocumentRoot [/www/hugdontmug] does not exist

```

The folder does exist and is named hugdontmug. Is there something else I'm supposed to do?

---

### Post by shadowayex on 2009-05-05
My bad, it needed to be /var/www/hugdontmug, I forgot the **/var**.

---

