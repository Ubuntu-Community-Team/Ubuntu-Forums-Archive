---
title: "Apache SSL web site shows home directory instead of web site"
date: 2014-09-09
forum: Server Platforms
---

### Post by argo3 on 2014-09-09
Hi,

We have web server which is working fine, so the aim is to get SSL working.
Then I have configured virtual host and uploaded certificate but still cannot get SSL working properly.
Instead of loading web site it lists the home directory where it shows html directory, info.php and myvhost directory.


<VirtualHost *:80>

................
</VirtualHost>



<VirtualHost *:443>

        ServerName  myvhost.com

        ServerAlias myvhost.com


        SSLEngine On
        DocumentRoot /var/www/myvhost.com

    SSLCertificateFile     /usr/local/share/ca-certificates/myvhost.crt
    SSLCertificateKeyFile  /usr/local/share/ca-certificates/myvhost.key

</VirtualHost>



SSL module is running fine and so apache2 service, just redirection seems not working.
I assume http and https are using same location (directory) for content.

Pleaae advise as got stuck already

Thanks

---

### Post by Frogs Hair on 2014-09-09
Hello and Welcome

Moved post to Sever Platforms .

---

### Post by SeijiSensei on 2014-09-11
Did you enable SSL with "sudo a2enmod ssl"?

How did you configure the virtual host?  Did you put it in /etc/apache2/sites-available/ with a filename ending in .conf?  If so, did you activate it with "sudo a2ensite sitename" where sitename matches the corresponding configuration file sitename.conf?

Did you read the Ubuntu Server Guide sections on SSL with Apache:  [https://help.ubuntu.com/14.04/serverguide/httpd.html#https-configuration](https://help.ubuntu.com/14.04/serverguide/httpd.html#https-configuration)?

I'd modify /etc/apache2/sites-available/default-ssl.conf to point to the correct DocumentRoot and follow the Server Guide.

---

### Post by argo3 on 2014-09-15
Hi Seiji,

Appreciate your reply. Sure, SSL already activated, otherwise wouldn't work at all. Virtual host configured under /etc/apache2/sites-available/ with a filename of domain ending xxx.co.uk but it is not ending with  .conf
When I created the file I guess I made it without .conf, is that's something I have to fix and rename it ?  

It seems that after modifying DocumentRoot under /etc/apache2/sites-available/default-ssl.conf  SSL started serving the content, but I have working only main page, where the rest of links
within the site stopped working (odd). Can it be related to Wordpress that I was told potentially needs to be enabled for SSL ?

So 2 things to clarify:
1.  .conf extension ?
2.Wordpress 


Thank you support
Arunas

---

### Post by dudumomo on 2014-09-15
Hi Argo,

1) No issue if no .conf extension.
All my virtualhost have a simple name like "Owncloud", "Freedif", "deluge" etc...

2) I think the main issue is from your virtualhost.
This is for example one of my host:

```
<VirtualHost *:80>
        ServerAdmin webmaster@freedif.org
        ServerName share.freedif.org
        Redirect / https://share.freedif.org
</VirtualHost>

<IfModule mod_ssl.c>
<VirtualHost *:443>
        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/freedif.pem
        SSLCertificateKeyFile /etc/ssl/private/freedif.key

        ServerAdmin webmaster@freedif.org
        ServerName share.freedif.org

        DocumentRoot /var/www/pydio
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/pydio>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
</IfModule>
```

My virtualhost redirect all the HTTP connections to HTTPS, so you can ignore the first part.

Hope it helps

---

### Post by argo3 on 2014-09-15
Hi Dudumomo,

Thanks, I have similar config. Am just thinking why I have to have it configured in 2 different places, I mean DocumenrRoot section.
I have it under default-ssl.conf and also under my virtual host. Should I have it just in one place, but in which one ?
And why suddently I get automatic HTTP redirect to SSL as I have not configured it yet, is commented out ?

Thanks

---

### Post by SeijiSensei on 2014-09-15
On 14.04 all configuration files must end in .conf.  That wasn't true in earlier versions of Ubuntu.  The files are incorporated in the configuration via the line
```
IncludeOptional sites-enabled/*.conf
```
at the end of /etc/apache2/apache2.conf.

---

