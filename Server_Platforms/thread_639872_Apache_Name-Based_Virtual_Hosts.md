---
title: "Apache Name-Based Virtual Hosts"
date: 2007-12-13
forum: Server Platforms
---

### Post by s3lnt0 on 2007-12-13
Hi,

I am still new to apache and servers in general and am trying to figure out how to set up a name-based virtual host. I keep getting a,

```
NameVirtualHost *:80 has no VirtualHosts
```

error whenever I try to restart apache.

I have this is in my /etc/apache2/httpd.conf

```
NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.nothingsite.com
DocumentRoot /home/www/ns
</VirtualHost>
```

Don't know what I am doing wrong. Any help is appreciated. :)

---

### Post by bnuytten on 2007-12-15
/etc/apache2/httpd.conf is the place to put your NameVirtualHost directive, but not to put your virtualhost directives there. It can work though but I would recommend you put your virtualhosts where they belong, i.e. in /etc/apache2/sites-available/

Just create a new file with the following contents
```
<VirtualHost *:80>
ServerName www.nothingsite.com
DocumentRoot /home/www/ns
</VirtualHost>
```
Use "sudo a2ensite yourfilename" to enable the site. You can use "sudo a2dissite default" to disable the default apache website.

---

### Post by s3lnt0 on 2007-12-15
That worked, thank you for the reply.

---

