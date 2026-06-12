---
title: "(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80 no listen"
date: 2012-04-09
forum: Server Platforms
---

### Post by 1cookie on 2012-04-09
hi

It's a strange one this. Ive followed this tutorial:

[https://www.linux.com/learn/tutorials/392099:creating-self-signed-ssl-certificates-for-apache-on-linux](https://www.linux.com/learn/tutorials/392099:creating-self-signed-ssl-certificates-for-apache-on-linux)

On first boot of my machine if I restart Apache everything works fine (i.e. I can use https on localhost):

```

andy@andy-R519-R719:~$ sudo /etc/init.d/apache2 restart
[sudo] password for andy: 
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Apache needs to decrypt your SSL Keys for localhost:443 (RSA)
Please enter passphrase:                                                 [ OK ]
andy@andy-R519-R719:~$ 

```If I delay the restart, do some browsing...whatever etc... it fails with:

```

andy@andy-R519-R719:~$ sudo /etc/init.d/apache2 restart
[sudo] password for andy: 
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
andy@andy-R519-R719:~$ 

```My error logs report:

```

[Mon Apr 09 12:48:51 2012] [error] Init: Pass phrase incorrect
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 218640442 error:0D08303A:asn1 encoding routines:ASN1_TEMPLATE_NOEXP_D2I:nested asn1 error
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 67710980 error:04093004:rsa routines:OLD_RSA_PRIV_DECODE:RSA lib
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Mon Apr 09 12:48:51 2012] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error

```From /etc/apache2/sites-available/default
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride all
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
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
<VirtualHost *:443>
    ServerAdmin webmaster@localhost
    ServerName localhost
    ServerAlias localhost
    DocumentRoot /var/www

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    SSLEngine on
    SSLOptions +StrictRequire
    SSLCertificateFile /etc/ssl/certs/server.crt
    SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>


```and from /etc/apache2/ports.conf
```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>


```Can someone clarify?

---

