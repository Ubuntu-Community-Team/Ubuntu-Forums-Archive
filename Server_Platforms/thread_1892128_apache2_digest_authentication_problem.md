---
title: "apache2 digest authentication problem"
date: 2011-12-07
forum: Server Platforms
---

### Post by ene_dene on 2011-12-07
Here is my site file on Ubuntu server 11.10:
```
IfModule mod_ssl.c>
<VirtualHost *:443>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/mydir
    ServerAlias *.mydomain.no-ip.info
    <Directory />
            Options FollowSymLinks
            AllowOverride None
    </Directory>
    <Directory /var/www/mydir>
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

    CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
            Options Indexes MultiViews FollowSymLinks
            AllowOverride None
            Order deny,allow
            Deny from all
            Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    #   SSL Engine Switch:
    #   Enable/Disable SSL for this virtual host.
    SSLEngine on

    #   A self-signed (snakeoil) certificate can be created by installing
    #   the ssl-cert package. See
    #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
    #   If both key and certificate are stored in the same file, only the
    #   SSLCertificateFile directive is needed.
    SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
    SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
 </VirtualHost>
 </IfModule>

```
Now I wanted authorized access to directory:
```
/var/www/mydir/private
```
I created the digest file like this:
```
sudo htdigest -c /etc/apache2/digest_auth users enedene
```
So I added the following before the <\Virtualhost>:
```
<Directory "/var/www/mydir/private/">
            AuthType Digest
            AuthName "Private"
            AuthDigestProvider file
            AuthUserFile /etc/apache2/digest_auth
            Require enedene
</Directory>
```
I restarted the web server and when I go to link:
```
https://mydomain.no-ip.info/private
```

I get prompted with a username and password as I wanted, but the problem is that it doesn't except the user/password that I've created, it just continuously denies and prompts again, as if the username/password combination is wrong. 
What is wrong with my setup?

---

### Post by ene_dene on 2011-12-07
I found the solution at Askubuntu:
[http://askubuntu.com/questions/85852/apache2-digest-authentication](http://askubuntu.com/questions/85852/apache2-digest-authentication)

If anybody else needs the answer, here it is.

---

