---
title: "Apache2 SSL failing everytime"
date: 2008-05-19
forum: Server Platforms
---

### Post by kustomjs on 2008-05-19
Hi Guys
I am having problems getting my apache restarted all the time it said Fail

here what I tried to install:
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

```
Create virtualhost

Make a copy of the default virtualhost

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl

Modify it so it looks something like this

sudo nano -w /etc/apache2/sites-available/ssl

NameVirtualHost *:443
<virtualhost *:443>
ServerAdmin webmaster@localhost

SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem

DocumentRoot /var/www/
<directory />
Options FollowSymLinks
AllowOverride None
</directory>

<directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
# Commented out for Ubuntu
#RedirectMatch ^/$ /apache2-default/
</directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<directory "/usr/lib/cgi-bin">
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On

Alias /doc/ "/usr/share/doc/"
<directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</directory>

</virtualhost>

```

---

### Post by spiderbatdad on 2008-05-19
This guide is good:[http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)
When I did this (sometime ago) It seems I had to put the ssl engine directives in httpd.conf rather than in the virtual hosts directory. Also, so far as where that guide has mkdir /root/ca, I did everything in my /home directory.
It took several tutorials and a bit of trial and error, but I did have ssl working for a long time. I eventually disabled it, and now have a fresh system...sorry I don't have example config files for you.

---

### Post by kustomjs on 2008-05-19
now im getting a error of apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by barf1 on 2008-05-20
Did you name your server in httpd.conf?

---

### Post by kustomjs on 2008-05-20
no I didnt and that httpd.conf is blank.
and plus I get this new error " [error] Name or service not known: failed to resolve name for 192.168.1.X (check dns)
and
[warn] NameVirtualHost at 192.168.1.X has no virtual host

---

### Post by kustomjs on 2008-05-20
~~~~Bump~~~~~

---

### Post by kustomjs on 2008-05-20
~~~bump again~~~

---

### Post by spiderbatdad on 2008-05-21
Going from memory here...(weak memory) When you created the ca certificate you would have used some "company name" perhaps (something a little unexpected), or maybe it was just called "domain name" When the ssl engine tries to start, that name has to be matched by a ServerName in httpd.conf, and possibly in the Virtual host file under ServerAdmin...that is, add another line: ServerName <domain>

---

