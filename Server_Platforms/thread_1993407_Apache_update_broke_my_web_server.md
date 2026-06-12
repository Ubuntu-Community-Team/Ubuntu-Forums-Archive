---
title: "Apache update broke my web server"
date: 2012-06-02
forum: Server Platforms
---

### Post by mons00n on 2012-06-02
Hi everyone,

I recently did an apache2 update (now running 2.2.22) and my web-server stopped being accessible.  I can still access phpmyadmin, and my mumble-django setup - but my acutal website setup in my sites-available is no longer available.  All I get is a "Forbidden, You don't have permission to access / on this server".  It was working 100% before the update, and I made no permission changes to the files in my public_html directory.  I tried 'chmod -R 755 public_html' but that did no good.  Any advice on how to fix this?  I've checked the apache log files and there is nothing out of the ordinary so I suspect is has to do with the update.

Upon further inspection I'm getting this error for the website in question:
> [Sat Jun 02 00:39:02 2012] [error] [client 180.76.5.187] (13)Permission denied: access to /index.php denied


I checked all of the permissions and they look ok:
> bob@Newton:~$ namei 1TBRaid/Web/trtguild.net/public_html/index.php -m
f: 1TBRaid/Web/trtguild.net/public_html/index.php
 drwxr-xr-x 1TBRaid
 drwxr-xr-x Web
 drwxr-xr-x trtguild.net
 drwxr-xr-x public_html
 -rwxr-xr-x index.php
bob@Newton:~$ 


Any idea what may be going on?  Again everything was working 100% before the update =(

---

### Post by mons00n on 2012-06-02
I **can** get the webserver to work in /var/www, so does that mean that the owner of my site files HAS to be root as is the case for /var/www?  Is this a recent change?  And how can I link to my files without having to change the owner of all of the parent folders to root?

I just tried to make a new site in my home directory via [this link]("https://help.ubuntu.com/community/ApacheMySQLPHP"), but I encounter the same permission error.  Any help would be greatly appreciated.

---

### Post by volkswagner on 2012-06-02
Please post the vhost file in question.

Look for the directory directives.  Possibly the directory is restricted.


```
    <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/site1/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

Particularly the "allow from all" and "order allow,deny" for the directory containing the index.html.

---

### Post by pbrane on 2012-06-02
Just a little late. what volkswagner said.

---

### Post by mons00n on 2012-06-02
> **volkswagner said:**
> Please post the vhost file in question.

Look for the directory directives.  Possibly the directory is restricted.


```
    <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/site1/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

Particularly the "allow from all" and "order allow,deny" for the directory containing the index.html.
Thanks for the replies guys.  As a test I simply copied the default website and only changed the directories and port (my ISP blocks 80).  My site file looks as follows:
> <VirtualHost *:81>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/bob/webtemp
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/bob/webtemp/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


which inside of that directory is a simple index.html file.  It's the only site enabled and I still get a permission error.  Any other ideas?

---

### Post by SeijiSensei on 2012-06-02
What are the permissions on /home/bob?  They must be at least 711 so that the Apache user, www-data, can see your site.  /home/bob/webtemp needs either 755 permissions, or 750 permissions if it belongs to a group with the www-data user as one of its members.  The first is easier to administer.

---

### Post by mons00n on 2012-06-02
> **SeijiSensei said:**
> What are the permissions on /home/bob?  They must be at least 711 so that the Apache user, www-data, can see your site.  /home/bob/webtemp needs either 755 permissions, or 750 permissions if it belongs to a group with the www-data user as one of its members.  The first is easier to administer.

The thing is, I didn't change any permissions =(  I checked those directories and they are good.  I think im going to try and reinstall apache and if that doesn't work just start from scratch.  Something weird is going on.

---

