---
title: "Apache works partially"
date: 2015-07-09
forum: Server Platforms
---

### Post by guymandude2 on 2015-07-09
How is it Apache works for my site when I use the full path in the browser but when I browse to it's URL it gives a white page?  

[www.coolintro.com](www.coolintro.com)  (white page)

[http://54.148.121.183/drupal-7.34a/drupal-7.34](http://54.148.121.183/drupal-7.34a/drupal-7.34)   (works ok)

I've been having lots of problems since I rebooted my VPS yesterday.  I have reinstalled Apache and PHP and farted around with various permissions and config files with no joy.  I'm pretty sure I've got permission problems but I can't seem to get it working.  Could use some help please.

TIA for taking the time to read and respond.

---

### Post by sandyd on 2015-07-09
Moved to *Server Platforms*
------------------------------------
Can you post your virtual host configuration for coolintro.com please?

Thanks!

---

### Post by guymandude2 on 2015-07-10
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName [www.coolintro.com]("http://www.coolintro.com")


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html/drupal-7.34a/drupal-7.34/


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        <Directory /var/www/html/drupal-7.34a/drupal-7.34/>
        AllowOverride All
        Order allow,deny
        allow from all
        </Directory>


        ErrorLog ${APACHE_LOG_DIR}/error.coolintro.log
        CustomLog ${APACHE_LOG_DIR}/access.coolintro.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

---

### Post by guymandude2 on 2015-07-10
Here is the default virtual host config too:

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com]("http://www.example.com")


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf


      <Directory /var/www/html/>
        AllowOverride All
        Order allow,deny
        allow from all
        </Directory>
</VirtualHost>


Thank you

---

### Post by Doug S on 2015-07-10
Both methods seem to be working fine for me.

---

### Post by bab1 on 2015-07-10
It's always good to include the version of Apache2 you are using.  If you are running Apache 2.4 then the directory directive should be something like theis```
<Directory {set the path here} >
    Options FollowSymlinks
    AllowOverride none
    Require all granted

```

What version of Apache are you running?  What are the permissions along the entire path to the DocumentRoot?

---

### Post by SeijiSensei on 2015-07-10
What do you see in /var/log/apache2/access.coolintro.log and error.coolintro.log when you make a request to coolintro?

Log files should always be your first source of information when you are debugging problems like these.

---

### Post by guymandude2 on 2015-07-11
Server Version: Apache/2.4.7 (Ubuntu)

Permissions
drwxr-sr-x  3 www-data www-data  4096 Feb 17 23:30 drupal-7.34a
drwxr-sr-x 9 www-data www-data 4096 Feb 17 23:38 drupal-7.34

Thanks

---

### Post by guymandude2 on 2015-07-11
Those were the first place I looked.  Error has nothing and Access has the normal entries.

---

### Post by guymandude2 on 2015-07-11
I was running OK again when I checked this morning.  I just rebooted it and it's broken again.  The permissions didn't change. Nothing in the logs.

[COLOR=#000000]Permissions[/COLOR]
[COLOR=#000000]drwxr-sr-x 3 www-data www-data 4096 Feb 17 23:30 drupal-7.34a[/COLOR]
[COLOR=#000000]drwxr-sr-x 9 www-data www-data 4096 Feb 17 23:38 drupal-7.34


[/COLOR]www.coolintro.com  (white page)
[http://54.148.121.183/drupal-7.34a/drupal-7.34/](http://54.148.121.183/drupal-7.34a/drupal-7.34/)  (working)

---

### Post by Doug S on 2015-07-11
> **guymandude2 said:**
> I was running OK again when I checked this morning.  I just rebooted it and it's broken again.Both methods still working for me.

---

### Post by guymandude2 on 2015-07-13
Hmmm, I guess I have fixed it after all.  I wish I knew what exactly I did that fixed it!.  Thanks for all the help guys.

---

