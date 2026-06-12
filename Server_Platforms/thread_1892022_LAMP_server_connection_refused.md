---
title: "LAMP server connection refused"
date: 2011-12-07
forum: Server Platforms
---

### Post by kreoso on 2011-12-07
Hi all. I have recently installed Ubuntu server 11.10 with LAMP server and it worked out of the box with the default "It works!" message. But when I change the Documentroot other than '/var/www', my web browser always shows 'connection refused' thing. 

The permission of the directories from / to the Documentroot is all 755 and index.html in Documentroot is 644. 

I googled and searched Ubuntu documents and other forums some time and read about SElinux thing, but I didn't install those things, so it cannot be a problem. 

any idea?

---

### Post by satanselbow on 2011-12-07
You might get a better response if you actually include the relevant config files - in between [code] tags.

The possibilities - from what you describe - are manyfold :(

relevant files include: httpd.conf, any virtual host definitions you may have created, .htaccess files, error.log, access.log etc

Have you had a look at your access / error logs - there can be some helpful gems in there ;)

---

### Post by kreoso on 2011-12-07
dulplicate

---

### Post by kreoso on 2011-12-07
Thanks for the reply. I installed Ubuntu server with openssh, LAMP server, etc. options and changed nothing other than that in the [Ubuntu Documentation]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")

So, /etc/apache2/httpd.conf is empty. 

/etc/apache2/apache2.conf/is default :

```
LockFile ${APACHE_LOCK_DIR}/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 5
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>
DefaultType text/plain
HostnameLookups Off
ErrorLog ${APACHE_LOG_DIR}/error.log
LogLevel warn
Include mods-enabled/*.load
Include mods-enabled/*.conf
Include httpd.conf
Include ports.conf
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
Include conf.d/
Include sites-enabled/
```
(I deleted comments)

/etc/apache2/ports.conf :
```
NameVirtualHost *:80
Listen 127.0.0.1:80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

/etc/apache2/sites-avaliable/mysite :

```
<VirtualHost *:80>
	ServerAdmin Webmaster@localhost

	DocumentRoot /home/john/Server/www/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/john/Server/www/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /home/john/Server/www/log/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /home/john/Server/www/log/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

With the completely default settings, i.e. Documentroot was on /var/www, I could access the webpages via localhost and my internet domainname. But now I can only access the site with localhost. 

What I did other than configuration is

```
# a2ensite mysite
# a2dissite default
# /etc/init.d/apache2 restart
```

The Errorlog was

```
[Wed Dec 07 02:41:38 2011] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
[Wed Dec 07 09:38:16 2011] [error] [client 127.0.0.1] File does not exist: /home/john/Server/www/public_html/favicon.ico
[Wed Dec 07 09:43:00 2011] [error] [client 127.0.0.1] File does not exist: /home/john/Server/www/public_html/favicon.ico

```

I have no idea, what is the problem. :confused:

---

### Post by kreoso on 2011-12-07
I'm sorry for the duplicated replies. 

It is solved. The problem was ports.conf

Changed 
Listen 127.0.0.1:80 -> Listen 80

then works like a charm.

Now the problem is, I don't know how to delete the duplicated rply and how to tag [Solved] to the original post.(It is my first post.)

---

### Post by volkswagner on 2011-12-07
To mark your thread solved use the "Thread Tools" drop down.

You can't delete your post, but can can choose edit and erase the content and just write "duplicate".

---

### Post by kreoso on 2011-12-07
Thanks a lot. :)

---

