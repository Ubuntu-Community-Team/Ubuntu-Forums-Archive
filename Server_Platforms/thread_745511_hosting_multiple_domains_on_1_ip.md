---
title: "hosting multiple domains on 1 ip"
date: 2008-04-04
forum: Server Platforms
---

### Post by subzero06 on 2008-04-04
Hello,

Ok, i got my domain and my home server setup and working. I already have a domain name pointed to my WAN ip address. For DNS server i am using zoneedit.com
Now, what if i want to add more domains for my ip address and host more domains. What are the procedures and what do i need?

---

### Post by twistedtwig on 2008-04-05
OK so say my main site is example.com and I want to point sub1.com and sub2.com at that server but have them serving as separate sites i do the following:

I point all the sub sites to example.com (i have them registered at 1&1 for dns only).  Then I use virtualhost's in my apache to let apache serve them as separate sites:

```

<VirtualHost *>
ServerName example.com
ServerAlias www.example.com
ServerAdmin jon@example.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride All
</Directory>

#display error page if we get 502 error
ErrorDocument 502 /error.html
#if we get 503 unavailable give out different page
ErrorDocument 503 /sitedown.html
#display error page for error 404 page not found
ErrorDocument 404 /404.php

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

</VirtualHost>

################### Charlotte home page #################

<VirtualHost *>
ServerName sub.example.com
ServerAdmin jon@example.com
DocumentRoot /var/www/sub
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### Foot faerie home page #################

<VirtualHost *>
ServerName sub1.com
Serveralias www.sub1.com sub1.com
ServerAdmin jon@sub1.com
DocumentRoot /var/www/sub1
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

```

The above shows my main site.. then one sub domain of that site then the sub1.com

hope this helps...

---

### Post by subzero06 on 2008-04-06
> **twistedtwig said:**
> OK so say my main site is example.com and I want to point sub1.com and sub2.com at that server but have them serving as separate sites i do the following:

I point all the sub sites to example.com (i have them registered at 1&1 for dns only).  Then I use virtualhost's in my apache to let apache serve them as separate sites:

```

<VirtualHost *>
ServerName example.com
ServerAlias www.example.com
ServerAdmin jon@example.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride All
</Directory>

#display error page if we get 502 error
ErrorDocument 502 /error.html
#if we get 503 unavailable give out different page
ErrorDocument 503 /sitedown.html
#display error page for error 404 page not found
ErrorDocument 404 /404.php

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

</VirtualHost>

################### Charlotte home page #################

<VirtualHost *>
ServerName sub.example.com
ServerAdmin jon@example.com
DocumentRoot /var/www/sub
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### Foot faerie home page #################

<VirtualHost *>
ServerName sub1.com
Serveralias www.sub1.com sub1.com
ServerAdmin jon@sub1.com
DocumentRoot /var/www/sub1
<Directory />
Options FollowSymLinks Indexes
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

```

The above shows my main site.. then one sub domain of that site then the sub1.com

hope this helps...


Ok, so which file should i edit for the above? httpd.conf?

I CREATED A SECOND VIRTUAL HOST FOR MY SECOND DOMAIN.  its setup like this:
/home/firstdomain/www  <------my first domain
/home/seconddomain/www  <---------my second domain

those are the directories.

NOw, when i go to:

myseconddomain.info<------it loads fine the second domain and its files.
But the problem is when i put the "www" in the front
example:
[www.myseconddomain.info](www.myseconddomain.info) it always  redirects to [www.myfirstdomain.com](www.myfirstdomain.com) with that page's content, automatically for some reason...

---

### Post by dmizer on 2008-04-07
here's the howto i used for setting up virtual hosts when i did it the first time:

[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

---

