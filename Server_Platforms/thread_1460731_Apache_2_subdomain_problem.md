---
title: "Apache 2 subdomain problem"
date: 2010-04-23
forum: Server Platforms
---

### Post by morto on 2010-04-23
Hej!

I have a problem to get a subdomain working

I have a domain, i have regged domain.com at a provider and pointend the domain.com with a A record agaist the server IP. It works and i can get to to domain.com and it shows the root katalog var/www/ on apache. I have than made a CNAME with a subdomain forum.domain.com that points to the same server. And i want that to point to the dir var/www/phpbb/
But when i go to forum.domain.com it's shows the same content as [www.domain.com](www.domain.com)

In apach directory "sites-available" i have made a config called "forum that looks like this:
<VirtualHost *:80>
ServerName forum.domän.com
DocumentRoot /var/www/phpbb
CustomLog logs/forum.domän.com-access_log common
</VirtualHost> 

Than i have made a link:
ln -s /etc/apache2/sites-available/forum /etc/apache2/sites-enabled/forum

And restarted the server.

Someone know why it nots shows the content in var/www/phpbb/

Regards

---

### Post by dudumomo on 2010-04-23
Hello,
First, your DNS records doesn't seems correct.
Why a CNAME record ? I use that for my mail. 
For my other website, I simply to an A record redirected to my IP. 
And then, with apache, I configure a virtalhost to redirect everything coming from myforum.mywebsite.com to /var/www/forum

Ie:
```
cd /etc/apache2/sites-available
sudo nano -w default
```
And I modify the virtualhost.
Here is mine:
```
<VirtualHost *:80>
        ServerAdmin spam_me@freelydifferent.com  ## your real address
        ServerName myforum.mywebsite.com   ## what you have added in your /etc/hosts
        ServerAlias myforum.mywebsite.com  ## From your domain redirection
 
        DocumentRoot /var/www/freelydifferent/forum  ## The folder you have just created
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/freelydifferent/forum> ## The folder you have just created
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
 
        ErrorLog /var/log/apache2/error.log
 
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
 
        CustomLog /var/log/apache2/access.log combined
 
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

---

### Post by cdenley on 2010-04-23
I'm assuming "forum.domän.com" isn't what you actually used, since that isn't valid.

First, eliminate the possibility that it is a browser caching issue.
```

echo -e "GET / HTTP/1.0\nHost: forum.domain.com\n"|nc 127.0.0.1 80

```

---

