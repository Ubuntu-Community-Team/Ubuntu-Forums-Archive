---
title: "Virtual host in apache"
date: 2013-07-10
forum: Server Platforms
---

### Post by laloto on 2013-07-10
Hello
Im trying to configure an virtual host with the host name:
zf2-tutorial.localhost


I have followed instructions from Zend Framework tutorial  in sense to install a virtual host and i cant make it work, 
i just get :
ERR_NAME_NOT_RESOLVED
in response to url [http://zf2-tutorial.localhost/](http://zf2-tutorial.localhost/)


but when i type 
[http://localhost/zf2-tutorial/public/](http://localhost/zf2-tutorial/public/)
it shows the desired page content .






I have configured the corresponding files as follows:


**content of file: /etc/hosts**


127.0.0.1	localhost
127.0.0.1	zf2-tutorial.localhost


::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters




**content of file: /etc/apache2/httpd.conf**


NameVirtualHost *
<VirtualHost *:80>
    ServerName localhost
    DocumentRoot /var/www/
    AllowOverride FileInfo
</VirtualHost>
<VirtualHost *:80>
     ServerName zf2-tutorial.localhost
     DocumentRoot /var/www/zf2-tutorial/public
     SetEnv APPLICATION_ENV "development"
     <Directory /var/www/zf2-tutorial/public>
          DirectoryIndex index.php
          AllowOverride All
          Order allow,deny
          Allow from all
     </Directory>
</VirtualHost>




**content of file: /etc/apache2/sites-enabled/zf2-tutorial**


<Directory /var/www/zf2-tutorial/public>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
</Directory>

**also i have try **sudo a2ensite,
**it responds:** ERROR: Site zf2-tutorial does not exist!



**Im using Lubuntu, Apache2, and Zend Framework2**

[B]Please advice, any help will be appreciated.

Laloto[/B]

---

### Post by SeijiSensei on 2013-07-11
There are a variety of issues, in particular the fact that httpd.conf is deprecated in Ubuntu.  

Please read the [Ubuntu Server Guide](https://help.ubuntu.com/lts/serverguide/web-servers.html) to understand the layout of the configuration files in /etc/apache2.

One particular issue concerns NameVirtualHost. By default it is defined in /etc/apache2/ports.conf like this:
```

NameVirtualHost *:80
Listen 80

```
To use this definition, the <VirtualHost> declarations must match exactly:
```

<VirtualHost *:80>
ServerName ...
</VirtualHost>

```

---

### Post by 2Stoned on 2013-07-14
You can try something like this:

NameVirtualHost *:80

<VirtualHost *:80> 
    ServerAdmin [email]info@yoursite.com[/email]
    DocumentRoot "/var/www/zf2-tutorial" 
    ServerName localhost
    ServerAlias zf2-tutorial.localhost
</VirtualHost>

---

### Post by laloto on 2013-07-15
Thank you [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] 
[/COLOR]
So where must i use this code:? (if httpd.conf is depreciated)




<VirtualHost *:80>ServerName ...</VirtualHost>

---

### Post by laloto on 2013-07-15
Thank you 2Stoned 


id placed the code you proposed in /etc/apache2/sites-enabled/zf2-tutorial file,  has'nt worked yet.


Is it mandatory the use of "" in DocumentRoot "/var/www/zf2-tutorial"  ?




also i have used "sudo a2ensite zf2-tutorial.localhost"
The response is:
Site zf2-tutorial.localhost already enabled


Please help

---

### Post by 2Stoned on 2013-07-15
> **laloto said:**
> id placed the code you proposed in /etc/apache2/sites-enabled/zf2-tutorial file,  has'nt worked yet.


Is it mandatory the use of "" in DocumentRoot "/var/www/zf2-tutorial"  ?

Try to put the code into apache2.conf on the bottom instead, to see if it will work. The use of "" are not mandatory.

I think these could be usefull to you:

[http://stackoverflow.com/questions/8044221/does-apache2-support-virtual-hosting-of-subdomains](http://stackoverflow.com/questions/8044221/does-apache2-support-virtual-hosting-of-subdomains)

[http://www.apachelounge.com/viewtopic.php?p=23598](http://www.apachelounge.com/viewtopic.php?p=23598)

[http://wiki.apache.org/httpd/CommonMisconfigurations](http://wiki.apache.org/httpd/CommonMisconfigurations)

[http://ubuntuforums.org/showthread.php?t=983271](http://ubuntuforums.org/showthread.php?t=983271)

---

### Post by laloto on 2013-07-15
Hello again

i have read those links, very useful info there. but still does'nt work.

Im guessing that the missconfiguration is regarded to another thing.

Do PDO and MOD_rewrite has to do with this problem?

How can i check if PDO extension or mod_rewrite extension is properly installed and configured?


Thaks for your time

---

