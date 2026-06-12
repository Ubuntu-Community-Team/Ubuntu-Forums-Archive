---
title: "apache - multiple sites"
date: 2008-12-14
forum: Server Platforms
---

### Post by mbsmooth on 2008-12-14
I have been working on this for the better part of 3 days. I have been with Linux/Ubuntu for over a year, but I am just now digging in to apache. I have definitely looked on these forums and Google, tried dozens of config changes, and always about the same result.

I am trying to setup 2 site with a single IP. 
httpd.conf is empty, like default
apache2.conf is default -except I added "ServerName Server1"

I only have one file in "sites-enabled/" called "sites"



```

NameVirtualHost www.domain1.org
<VirtualHost www.domain1.org>
        ServerAdmin mbryant@domain2.com
        ServerName www.domain1.org
        ServerAlias domain1.org

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/domain1.org/www/

        # Logfiles
        ErrorLog  /var/www/domain1.org/logs/error.log
        CustomLog /var/www/domain1.org/logs/access.log combined
</VirtualHost>



NameVirtualHost www.domain2.com
<VirtualHost www.domain2.com>
        ServerAdmin mbryant@domain2.com
        ServerName www.domain2.com
        ServerAlias domain2.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/domain2.com/www/

       # Logfiles
        ErrorLog  /var/www/domain2.com/logs/error.log
        CustomLog /var/www/domain2.com/logs/access.log combined
</VirtualHost>
```




No matter what changes I make (so far) I always get domain2.com's files for both domains.

What am I missing? :confused:

Thanks in advance.

---

### Post by martien on 2008-12-15
> **mbsmooth said:**
> I have been working on this for the better part of 3 days. I have been with Linux/Ubuntu for over a year, but I am just now digging in to apache. I have definitely looked on these forums and Google, tried dozens of config changes, and always about the same result.

I am trying to setup 2 site with a single IP. 
httpd.conf is empty, like default
apache2.conf is default -except I added "ServerName Server1"

I only have one file in "sites-enabled/" called "sites"



```

NameVirtualHost www.domain1.org
<VirtualHost www.domain1.org>
        ServerAdmin mbryant@domain2.com
        ServerName www.domain1.org
        ServerAlias domain1.org

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/domain1.org/www/

        # Logfiles
        ErrorLog  /var/www/domain1.org/logs/error.log
        CustomLog /var/www/domain1.org/logs/access.log combined
</VirtualHost>



NameVirtualHost www.domain2.com
<VirtualHost www.domain2.com>
        ServerAdmin mbryant@domain2.com
        ServerName www.domain2.com
        ServerAlias domain2.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/domain2.com/www/

       # Logfiles
        ErrorLog  /var/www/domain2.com/logs/error.log
        CustomLog /var/www/domain2.com/logs/access.log combined
</VirtualHost>
```




No matter what changes I make (so far) I always get domain2.com's files for both domains.

What am I missing? :confused:

Thanks in advance.
You need to set NameVirtualHost for your ip, not for your domains. The file should look like this:
```
NameVirtualHost xxx.xxx.xxx:80
<VirtualHost xxx.xxx.xxx:80>
        ServerAdmin mbryant@domain2.com
        ServerName www.domain1.org
        ServerAlias domain1.org

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/domain1.org/www/

        # Logfiles
        ErrorLog  /var/www/domain1.org/logs/error.log
        CustomLog /var/www/domain1.org/logs/access.log combined
</VirtualHost>
<VirtualHost xxx.xxx.xxx:80>
        ServerAdmin mbryant@domain2.com
        ServerName www.domain2.com
        ServerAlias domain2.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/domain2.com/www/

       # Logfiles
        ErrorLog  /var/www/domain2.com/logs/error.log
        CustomLog /var/www/domain2.com/logs/access.log combined
</VirtualHost>




```
If the two domains are on different ips then you have to set another NameVirtualHost for the second ip.

---

### Post by mbsmooth on 2008-12-15
Awesome, that did it! I looked back at some of the forums and Google links I was using, and I found they where all using * and I guess I assumed that that was to be the host name.

Thanks Martien!

---

### Post by martien on 2008-12-15
> **mbsmooth said:**
> Awesome, that did it! I looked back at some of the forums and Google links I was using, and I found they where all using * and I guess I assumed that that was to be the host name.

Thanks Martien!
No problem. * means everything and you can set it at all the places i wrote xxx.xxx.xxx

---

