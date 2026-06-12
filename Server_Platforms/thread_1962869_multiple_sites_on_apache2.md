---
title: "multiple sites on apache2"
date: 2012-04-21
forum: Server Platforms
---

### Post by thunder63cs on 2012-04-21
Ok I set up my server again and used to have this working a while ago just did a fresh install of the whole server and now having an issue with getting multiple sites to work. 
 
I followed the directions from another site that seems to have dissappered now.... 
 
but I ended up with all 3 set up in apache with these directives. 
 
[ServerAdmin webmaster@vernorviewborzoi.com]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=324&type=1") /etc/apache2/sites-available/btd (2)
[ServerName FraterAdhucExcessum]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=324&type=1") /etc/apache2/sites-available/btd (3)
[DocumentRoot /var/www/btd]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=324&type=5") /etc/apache2/sites-available/btd (6)
[<Directory />]("https://99.112.166.26:10000/apache/dir_index.cgi?virt=324&idx=4")
Options FollowSymLinks /etc/apache2/sites-available/btd (8)
AllowOverride All /etc/apache2/sites-available/btd (9)
</Directory>
[<Directory /var/www/btd/>]("https://99.112.166.26:10000/apache/dir_index.cgi?virt=324&idx=5")
Options -Indexes FollowSymLinks MultiViews /etc/apache2/sites-available/btd (12)
AllowOverride All /etc/apache2/sites-available/btd (13)
Order allow,deny /etc/apache2/sites-available/btd (14)
allow from all /etc/apache2/sites-available/btd (15)
</Directory>
[ErrorLog /var/log/apache2/error.log]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=324&type=3") /etc/apache2/sites-available/btd (20)
[LogLevel warn]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=324&type=3") /etc/apache2/sites-available/btd (24)
[CustomLog /var/log/apache2/access.log combined]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=324&type=3") /etc/apache2/sites-available/btd (26)
 
for the first one,
 
[ServerAdmin webmaster@vernorviewborzoi.com]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=326&type=1") /etc/apache2/sites-available/vvb (2)
[ServerName Vernorviewborzoi]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=326&type=1") /etc/apache2/sites-available/vvb (3)
[DocumentRoot /var/www/vvb]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=326&type=5") /etc/apache2/sites-available/vvb (6)
[<Directory />]("https://99.112.166.26:10000/apache/dir_index.cgi?virt=326&idx=4")
Options FollowSymLinks /etc/apache2/sites-available/vvb (8)
AllowOverride All /etc/apache2/sites-available/vvb (9)
</Directory>
[<Directory /var/www/vvb/>]("https://99.112.166.26:10000/apache/dir_index.cgi?virt=326&idx=5")
Options -Indexes FollowSymLinks MultiViews /etc/apache2/sites-available/vvb (12)
AllowOverride All /etc/apache2/sites-available/vvb (13)
Order allow,deny /etc/apache2/sites-available/vvb (14)
allow from all /etc/apache2/sites-available/vvb (15)
</Directory>
[ErrorLog /var/log/apache2/error.log]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=326&type=3") /etc/apache2/sites-available/vvb (20)
[LogLevel warn]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=326&type=3") /etc/apache2/sites-available/vvb (24)
[CustomLog /var/log/apache2/access.log combined]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=326&type=3") /etc/apache2/sites-available/vvb (26)
 
 
for the second,
 
and this for the third,
 
[ServerAdmin webmaster@vernorviewborzoi.com]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=328&type=1") /etc/apache2/sites-available/xbg (2)
[ServerName PraetorianBlackGuard]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=328&type=1") /etc/apache2/sites-available/xbg (3)
[DocumentRoot /var/www/xbg]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=328&type=5") /etc/apache2/sites-available/xbg (6)
[<Directory />]("https://99.112.166.26:10000/apache/dir_index.cgi?virt=328&idx=4")
Options FollowSymLinks /etc/apache2/sites-available/xbg (8)
AllowOverride All /etc/apache2/sites-available/xbg (9)
</Directory>
[<Directory /var/www/xbg/>]("https://99.112.166.26:10000/apache/dir_index.cgi?virt=328&idx=5")
Options -Indexes FollowSymLinks MultiViews /etc/apache2/sites-available/xbg (12)
AllowOverride All /etc/apache2/sites-available/xbg (13)
Order allow,deny /etc/apache2/sites-available/xbg (14)
allow from all /etc/apache2/sites-available/xbg (15)
</Directory>
[ErrorLog /var/log/apache2/error.log]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=328&type=3") /etc/apache2/sites-available/xbg (20)
[LogLevel warn]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=328&type=3") /etc/apache2/sites-available/xbg (24)
[CustomLog /var/log/apache2/access.log combined]("https://99.112.166.26:10000/apache/edit_virt.cgi?virt=328&type=3") /etc/apache2/sites-available/xbg (26)
 
 
 
now when I goto any of the sites I end up going to the [www.praetorianblackguard.com]("http://www.praetorianblackguard.com") site for all 3. 
 
I can not figure out why it will not goto the other sites so I can set them up.

---

### Post by thunder63cs on 2012-04-21
[Sat Apr 21 17:01:02 2012] [warn] VirtualHost [www.vernorviewborzoi.com:80]("http://www.vernorviewborzoi.com:80") overlaps with VirtualHost [www.praetorianblackguard.com:80]("http://www.praetorianblackguard.com:80"), the first has precedence, perhaps you need a NameVirtualHost directive
[Sat Apr 21 17:01:02 2012] [warn] VirtualHost [www.btd-alliance.com:80]("http://www.btd-alliance.com:80") overlaps with VirtualHost [www.vernorviewborzoi.com:80]("http://www.vernorviewborzoi.com:80"), the first has precedence, perhaps you need a NameVirtualHost directive
[Sat Apr 21 17:01:02 2012] [warn] NameVirtualHost *:80 has no VirtualHosts

 
did a reload in putty and this is what I get then.   guess I need to know what to add to fix this.

---

### Post by newbie-user on 2012-04-21
did you edit /etc/apache2/ports.conf to uncomment NameVirtualHost?

---

### Post by thunder63cs on 2012-04-21
here is the ports.config file contents:
 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz
NameVirtualHost *:80
Listen 80
<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>
<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

---

### Post by Ryan Dwyer on 2012-04-22
Make sure your VirtualHost blocks start with this: <VirtualHost *:80>

For example:

<VirtualHost *:80>
ServerName praetorianblackguard.com
ServerAlias [www.praetorianblackguard.com](www.praetorianblackguard.com)
DocumentRoot /var/www/xbg
</VirtualHost>

<VirtualHost *:80>
ServerName vernorviewborzoi.com
ServerAlias [www.vernorviewborzoi.com](www.vernorviewborzoi.com)
DocumentRoot /var/www/vvb
</VirtualHost>

I recommend you use document roots that match the hostname (eg. /var/www/praetorianblackguard.com/).

---

### Post by SeijiSensei on 2012-04-22
As Ryan says, the <VirtualHost> declaration must match the NameVirtualHost declaration exactly.  In this case it must be 

```
<VirtualHost *:80>
```

and not something like

```
[s]<VirtualHost *>[/s]
```

Also if you read the comments in ports.conf, you'll see that a port must be specified for name-based virtual hosting.

Someone else posted [this identical problem]("http://ubuntuforums.org/showthread.php?t=1960597") the other day.

---

### Post by thunder63cs on 2012-04-22
hmm yea looking at what I had earlier was the vertualhost*:80 but now showing this when I go into the site-available it shows this now.. 
 
<VirtualHost [www.praetorianblackguard.com:80]("http://www.praetorianblackguard.com:80")>
 ServerAdmin [EMAIL="webmaster@vernorviewborzoi.com"]webmaster@vernorviewborzoi.com[/EMAIL]
ServerName PraetorianBlackGuard
 
DocumentRoot /var/www/xbg
 <Directory />
     Options FollowSymLinks
     AllowOverride All
 </Directory>
 <Directory /var/www/xbg/>
     Options -Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     allow from all
 </Directory>
 
 ErrorLog ${APACHE_LOG_DIR}/error.log
 # Possible values include: debug, info, notice, warn, error, crit,
 # alert, emerg.
 LogLevel warn
 CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
 
so just change it back to * instead of the praetorianblackguard.com

---

### Post by thunder63cs on 2012-04-22
ok changed it got rid of the one error but still just goes to the praetorian black guard site over any other  so did not solve the original problem. 
 
 
> **thunder63cs said:**
> hmm yea looking at what I had earlier was the vertualhost*:80 but now showing this when I go into the site-available it shows this now.. 
 
<VirtualHost [www.praetorianblackguard.com:80]("http://www.praetorianblackguard.com:80")>
ServerAdmin [EMAIL="webmaster@vernorviewborzoi.com"]webmaster@vernorviewborzoi.com[/EMAIL]
ServerName PraetorianBlackGuard
 
DocumentRoot /var/www/xbg
<Directory />
Options FollowSymLinks
AllowOverride All
</Directory>
<Directory /var/www/xbg/>
Options -Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
</Directory>
 
ErrorLog ${APACHE_LOG_DIR}/error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
 
so just change it back to * instead of the praetorianblackguard.com

---

### Post by Ryan Dwyer on 2012-04-22
Change the ServerName to be whatever the site's hostname is minus www. Add a ServerAlias with the same name but including www. Refer to the example I posted previously.

---

### Post by dharmavir on 2012-04-22
I think you should get help from link below:

[http://blogs.digitss.com/apache/mod_proxy-mod_vhost_alias-to-host-multiple-domains-on-web-server-and-running-apache-iis-together/](http://blogs.digitss.com/apache/mod_proxy-mod_vhost_alias-to-host-multiple-domains-on-web-server-and-running-apache-iis-together/)

---

### Post by thunder63cs on 2012-04-22
tyty .. this is solved....

---

