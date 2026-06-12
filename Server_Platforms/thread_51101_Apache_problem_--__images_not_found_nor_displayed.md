---
title: "Apache problem --  images not found nor displayed"
date: 2005-07-22
forum: Server Platforms
---

### Post by spanishwasabi on 2005-07-22
Hi,

I'm trying to configure squirrelmail and Apache.

All the files are in /var/www. I did two virtual domains. [www.mydomain.tv](www.mydomain.tv) and mail.mydomain.tv. The first is for my normal webpages and the second one to access squirrelmail.

My problem is, the images are not displayed in mail.mydomain.tv when I access squirrelmail.

I tried then to symlink squirrel (/usr/share/squirrelmail) to /var/www/www and access it through: [http://www.mydomain.tv/mail](http://www.mydomain.tv/mail), and in this case the images appear without problems. The thing is, in both cases the symlink is the same.

$ ls -l /var/www
total 12
drwxr-xr-x  2 www-data www-data 4096 2005-07-21 20:48 apache2-default
-rw-r--r--  1 www-data www-data 1457 2005-07-22 18:04 index.html
lrwxrwxrwx  1 www-data www-data   23 2005-07-22 19:43 mail -> /usr/share/squirrelmail
drwxr-xr-x  2 www-data www-data 4096 2005-07-22 19:40 www

$ ls -l /var/www/www
total 12
-rw-r--r--  1 www-data www-data 5258 2005-07-20 14:04 index.html
lrwxrwxrwx  1 www-data www-data   23 2005-07-22 19:40 mail -> /usr/share/squirrelmail
-rw-r--r--  1 www-data www-data   24 2005-07-21 22:06 test.php


My httpd.conf virtual host part is:
Include /etc/apache/conf.d
ServerTokens ProductOnly

<VirtualHost *:80>
    DocumentRoot /var/www/www
    ServerName [www.guille.dyndns.org](www.guille.dyndns.org)
    <Directory "/var/www/www">
        allow from all
        Options +Indexes
    </Directory>
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot /var/www/mail
    ServerName mail.guille.dyndns.org
    <Directory "/var/www/mail">
        allow from all
        #Options +Indexes
        Options All
    </Directory>
</VirtualHost>


Thanks a lot,

G

---

### Post by pressureman on 2005-07-22
Check your Apache error log to see what files are actually trying to be read when you get the 404 errors. Also check that Apache has been configured to follow symlinks.

The server names in your virtual host declarations don't match the hostnames you are hitting the web server with. If a DNS A record points to an Apache server running virtual hosts, and the hostname specified in the HTTP header doesn't match any of the configured virtual hosts, Apache will serve the default site (usually the first defined virtual host).

---

### Post by LordHunter317 on 2005-07-23
Don't use symlinks.  Setup Aliases and use <Directory> directives in your Apaceh configuration.

---

### Post by spanishwasabi on 2005-07-23
I'm so...

Is there any reason I've missed to define all those Alias in the configuration file? I do not see the utility of the /images /icons /cgi-bin ...

Thanks to both of you. You made me think (more, at least) and have a better approach to my problem. It's the first time I set an Apache server, so I'm a bit lost...

I modified my configuration to this:
<VirtualHost *:80>
    DocumentRoot /usr/share/squirrelmail
    ServerName mail.guille.dyndns.org
    <Directory "/usr/share/squirrelmail">
        allow from all
        Options +Indexes
    </Directory>
</VirtualHost>
Simple as that. And it worked.

The problem was this:
[error] [client 192.168.1.34] File does not exist: /usr/share/images/sm_logo.png

Of course it did not exist... this alias was defined before in the configuration:

Alias /images/ /usr/share/images/

<Directory /usr/share/images>
     Options MultiViews
     AllowOverride None
     Order allow,deny
     Allow from all
</Directory>

So indeed of looking into /usr/share/squirel/images it looked because of the Alias in /usr/share/images.

Thanks a lot to both of you!

G

---

