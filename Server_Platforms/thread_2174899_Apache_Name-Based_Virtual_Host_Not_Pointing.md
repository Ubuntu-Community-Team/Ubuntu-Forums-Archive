---
title: "Apache Name-Based Virtual Host Not Pointing"
date: 2013-09-16
forum: Server Platforms
---

### Post by mastermindg on 2013-09-16
I have a typical setup on my server with two Virtual Hosts. Here is an example of my configuration:

Ubuntu 13.04 (x64)
Apache 2.2.22

Listen 80
<VirtualHost *:80>
    ServerName [www.example.com](www.example.com)
    ServerAlias example.com
    DocumentRoot /share/websites/localhost/example.com
    # Other directives here
</VirtualHost>

<VirtualHost *:80>
    ServerName d8.example.com
    DocumentRoot /share/websites/localhost/d8.example.com

    # Other directives here
</VirtualHost>


My problem is that d8.example.com doesn't come up when I bring up the site. Instead, [www.example.com](www.example.com) comes up in it's place. I understand precedence here but the site is being called directly locally so I'm confused why Apache isn't directing traffic to the right place. Any ideas how what's wrong or how I can troubleshoot this?

---

### Post by bkline on 2013-09-16
Be sure to re-start Apache after setting up the config file.

---

### Post by mastermindg on 2013-09-16
Thanks for the advice...it is good. However, I think I've restarted about 20 times now. I restart after every configuration change.

---

### Post by sefs on 2013-09-16
> **mastermindg said:**
> I have a typical setup on my server with two Virtual Hosts. Here is an example of my configuration:

Ubuntu 13.04 (x64)
Apache 2.2.22

Listen 80
<VirtualHost *:80>
    ServerName [www.example.com](www.example.com)
    ServerAlias example.com
    DocumentRoot /share/websites/localhost/example.com
    # Other directives here
</VirtualHost>

<VirtualHost *:80>
    ServerName d8.example.com
    DocumentRoot /share/websites/localhost/d8.example.com

    # Other directives here
</VirtualHost>


My problem is that d8.example.com doesn't come up when I bring up the site. Instead, [www.example.com](www.example.com) comes up in it's place. I understand precedence here but the site is being called directly locally so I'm confused why Apache isn't directing traffic to the right place. Any ideas how what's wrong or how I can troubleshoot this?

What does the logs say?
/var/log/apache2/error.log
You may find a clue there.  Make sure you crtl+f5 when refreshing in the browser too.

---

### Post by nerdtron on 2013-09-16
Here's my 3 domain setup and the contents of the /etc/apache2/sites-available/default
And take note the 1st line. It didn't work if it is not there.
```
NameVirtualHost *

<VirtualHost *>

    ServerName www.domain1.net
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/www.domain1.net/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/www.domain1.net/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

</VirtualHost>

<VirtualHost *>

        ServerName www.domain2.ph
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/www.domain2.ph/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/www.domain2.ph/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
       
</VirtualHost>

<VirtualHost *>

        ServerName www.domain3.com
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/domain3.com/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/domain3.com/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
 
</VirtualHost>


```

---

### Post by mastermindg on 2013-09-22
> **nerdtron said:**
> Here's my 3 domain setup and the contents of the /etc/apache2/sites-available/default
And take note the 1st line. It didn't work if it is not there.
```
NameVirtualHost *

```

That did it! Thanks a bunch nerdtron.

---

