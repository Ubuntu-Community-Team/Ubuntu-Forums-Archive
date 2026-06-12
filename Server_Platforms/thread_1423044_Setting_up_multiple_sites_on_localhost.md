---
title: "Setting up multiple sites on localhost"
date: 2010-03-06
forum: Server Platforms
---

### Post by Almeida1 on 2010-03-06
Hi

I have currently got LAMP installed and have my website files in /var/www. I access this site by going to [http://localhost](http://localhost).

However, I would like to set up a few more sites. My first site for example is called site2. Therefore, I have created a folder within /var/www/ callled site2 (/var/www/site2/) and have put my website files in here.

I then created a file called site2.com within /etc/apache2/sites-enabled/. This file looks like the following:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
        ServerName www.site2.com
    DocumentRoot /var/www/site2/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/site2/>
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
```I have restarted apache but when I go to [www.site2.com]("http://www.site2.com") I get the following error:

**HTTP Status 404 - **

**type** Status report
**message** 
**description** _The requested resource () is not available._
**Apache Tomcat/5.5.25**


Is there something else I now need to do??

Thanks.

---

### Post by ssam on 2010-03-06
have you added the domain to you /etc/hosts, eg:
```

127.0.0.1 www.site2.com

```
so that when your browser trys to look up "www.site2.com" it gets your local machine.

---

### Post by Almeida1 on 2010-03-06
> **ssam said:**
> have you added the domain to you /etc/hosts, eg:
```

127.0.0.1 www.site2.com

```so that when your browser trys to look up "www.site2.com" it gets your local machine.

THanks. I thought I had to add it in the hosts somehwere. However, not it is still looking at the /var/www/ folder instead of /var/www/site2/ ?

---

### Post by Almeida1 on 2010-03-06
Solved!!

I had to create the following symlink when I was within /etc/apache2/sites-enabled:

ln -sf /etc/apache2/sites-available/site2.com /etc/apache2/sites-enabled/site2.com

Thanks for your help anyway! :)

---

### Post by Sef on 2010-03-06
Moved to server platforms.

---

### Post by kernelnewbie1 on 2010-03-10
This thread was very helpful for me and thanks for that,
will you guys please help me by telling how to give different ip address to **site2 ([www.site2.com](www.site2.com)) **
also how to host **site2** on a different post

--- please help me --

---

### Post by WildOscar on 2010-11-23
Thanks. This Thread helped me alot for my LAMP! :)

---

### Post by Apot on 2010-11-23
You could have also done this with the command "a2ensite site2.com"

---

