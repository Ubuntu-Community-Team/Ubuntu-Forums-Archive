---
title: "Not able to enable SSL in Apache"
date: 2017-04-09
forum: Server Platforms
---

### Post by digitalyours on 2017-04-09
I'm trying to enable SSL on my Apache 2.4 (Ubuntu 16.04.2), but without any success.

I can run the command a2enmod ssl and it does state that ssl is already enabled.

But whenever I try to include a "SSLEngine on" in the wiki.conf, Apache displays: 
"Invalid command 'SSLEngine', perhaps misspelled or defined by a module not included in the server configuration"

Any idea what I'm doing wrong? Could it be that mod_ssl.c is not available?

Best and thanks
Christoph

Ports Conf
```

Listen 80
<IfModule mod_ssl.c>
    Listen 443
</IfModule>


<IfModule mod_gnutls.c>
        Listen 443
</IfModule>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

wiki.conf

```

<VirtualHost *:443>
        SSLEngine On
        SSLCertificateFile /etc/ssl/certs/wiki.crt
        SSLCertificateKeyFile /etc/ssl/private/wiki.key
        ServerName wiki.xyz.com
        ServerAdmin christoph@xyz.com
        DocumentRoot /var/www/html/wiki/


        <Directory /var/www/html/wiki/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Require all granted
        </Directory>


        ErrorLog /var/log/apache2/error.log
        LogLevel debug
        CustomLog /var/log/apache2/access.log combined
        ServerSignature On


</VirtualHost>

```

---

### Post by nihvel on 2017-04-11
I was checking my Nagios conf, I am using the SSL on the default site..
```
<IfModule mod_ssl.c>
	<VirtualHost _default_:443>
		ServerAdmin webmaster@localhost
		DocumentRoot /var/www/html
		ErrorLog ${APACHE_LOG_DIR}/error.log
		CustomLog ${APACHE_LOG_DIR}/access.log combined
		SSLEngine on
        SSLCertificateFile /etc/ssl/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key

```

Different than your, of course, but actually the same... If not for "SSLEngine on" where in your case is "On".
It should not be this a case sensitive.. but.. you may want to check this.
I do not see issues in this conf..

Also, add the SSLRequireSSL in the <Directory>.

---

### Post by LHammonds on 2017-04-11
Did you restart Apache after you did the "a2enmod ssl"?

Does the ServerName need to also specify the port?

```
ServerName wiki.xyz.com:443
```

---

### Post by darkod on 2017-04-11
Also what you can try just for comparison, is to use the default-ssl site. Just to check if it will work with it. If it does, you can even consider using it instead of your own .conf site.

---

### Post by 1clue on 2017-04-11
Do your encryption key files exist? Do they contain a valid key?

---

### Post by LHammonds on 2017-04-11
> **1clue said:**
> Do your encryption key files exist? Do they contain a valid key?
I thought about that too but invalid keys wouldn't produce an Invalid command regarding SSLEngine.

Seems like he just didn't restart Apache so it doesn't know about SSL being enabled.

---

