---
title: "Server should be SSL-aware but has no certificate configured"
date: 2009-02-15
forum: Server Platforms
---

### Post by lightnb on 2009-02-15
After installing my SSL certificate (/etc/ssl/certs), and setting ports.conf to include "Listen 443 https", I get the follow error in the log, and apache refuses to start.

```
[Sun Feb 15 20:21:01 2009] [info] Init: Seeding PRNG with 656 bytes of entropy
[Sun Feb 15 20:21:01 2009] [info] Loading certificate & private key of SSL-aware server
[Sun Feb 15 20:21:01 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]
```

I have mod_ssl enabled, and the firewall is accepting inbound connections on port 443.

I have multiple virtual hosts on the machine, so I've put the SSL configuration lines in the VirtualHost file for the domain I'm trying to secure. (/etc/apache2/sites-available/domain.com). The Virtual host is enabled (a2ensite domain.com).

My VirtualHost file looks like this:

```

<VirtualHost *:80>

ServerAdmin webmaster@domain.com
ServerName domain.com
ServerAlias www.domain.com

DirectoryIndex index.html
DocumentRoot /var/www/

</VirtualHost>




<VirtualHost *:443>
ServerAdmin webmaster@domain.com
ServerName domain.com
ServerAlias www.domain.com

DirectoryIndex index.html
DocumentRoot /var/www/

SSLCertificateChainFile /etc/ssl/certs/domain.com.ca-bundle
SSLCertificateFile /etc/ssl/certs/domain.com.crt
SSLCertificateKeyFile /etc/ssl/private/domain.com.key

</VirtualHost>

```

What am I missing?

---

### Post by spiderbatdad on 2009-02-15
try placing ssl directives in httpd.conf like so:
```
ServerName YourDomain.com
<Directory /var/www>
 <IfModule mod_rewrite.c>
        <IfModule mod_ssl.c>
#       <Location /squirrelmail>
                RewriteEngine on
                RewriteCond %{HTTPS} !^on$ [NC]
                RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#       </Location>
        </IfModule>
        </IfModule>


SSLOptions +StrictRequire
</Directory>
#<Directory>
#    SSLRequireSSL
#</Directory>

SSLProtocol -all +TLSv1 +SSLv3
SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

<Directory /usr/local/apache2/htdocs>
# but finally deny all browsers which haven't upgraded
SSLRequire %{SSL_CIPHER_USEKEYSIZE} >= 128
</Directory> 

#SSLMutex file:/usr/local/apache2/logs/ssl_mutex

#SSLRandomSeed startup file:/dev/urandom 1024
#SSLRandomSeed connect file:/dev/urandom 1024

#SSLSessionCache shm:/usr/local/apache2/logs/ssl_cache_shm
#SSLSessionCacheTimeout 600

#SSLPassPhraseDialog builtin
SSLCertificateFile /etc/apache2/ssl.crt/server.crt
SSLCertificateKeyFile /etc/apache2/ssl.key/server.key

SSLVerifyClient none
SSLProxyEngine off


```Little bit of a mess, but I'm working on it now.

In /sites-available/*
have:```
   DocumentRoot /var/www/
		SSLEngine On

```

---

### Post by lightnb on 2009-02-15
Currently my httpd.conf file is empty. 

Should I place SSL directives in httpd.conf in addition to the VirtualHost file for the specific site? Or instead of?

---

### Post by spiderbatdad on 2009-02-15
instead of. also edited my previous post to show you SSLEngine on under DocumentRoot in vhosts.

---

### Post by lightnb on 2009-02-15
Awesome thanks! Looks like it's working.

One more question: Since the cert paths go in httpd.conf, and not a virtualhost specific location, what If I wanted to add another certificate for a different vhost?

Would I just have two sets of "SSLCertificateFile" entries in httpd.conf?

Thanks again,

Nick

---

### Post by spiderbatdad on 2009-02-15
Haven't tried that lately. I would try pointing to the other Document root inside <Directory> tags and under that include the location of the other cert file. You may find that you can do it in vhosts inside <VirtualHost> tags as long as you have SSLEngine ON. That was probably the main problem.

---

### Post by lightnb on 2009-02-15
> **spiderbatdad said:**
> Haven't tried that lately. I would try pointing to the other Document root inside <Directory> tags and under that include the location of the other cert file. You may find that you can do it in vhosts inside <VirtualHost> tags as long as you have SSLEngine ON. That was probably the main problem.

I'm using:
```
SSLProtocol -all +TLSv1 +SSLv3
SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

<Directory /var/www>
        SSLCertificateFile /etc/ssl/certs/mysite.net.crt
        SSLCertificateKeyFile /etc/ssl/private/mysite.net.key
        SSLCertificateChainFile /etc/ssl/certs/mysite.net.ca-bundle
</Directory>

SSLVerifyClient none
SSLProxyEngine off

```

and getting:
```
Syntax error on line 6 of /etc/apache2/httpd.conf:
SSLCertificateFile not allowed here
```

---

### Post by spiderbatdad on 2009-02-15
you can see from my httpd.conf above that the location of the ssl cert file is not inside the directory tags. I was thinking you may be able to have it in vhosts inside <VirtualHost> tags, outside <Directory> tags as long as SSLEngine On is set for the DocumentRoot.

---

### Post by lightnb on 2009-02-15
That worked. my httpd.conf is now:

```
SSLProtocol -all +TLSv1 +SSLv3
SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM
SSLVerifyClient none
SSLProxyEngine off

```

and my Vhost file has the three certificate paths after SSLEngine On.


Last question: Is there a way to restrict the cert to a specific site?

so that [https://mysite.com](https://mysite.com) works, but [https://myothersiteonthesameserver.com](https://myothersiteonthesameserver.com) doesn't try to use the first sites certificate?

I'm thinking something like <VirtualHost *mydomain.com:443>

---

### Post by spiderbatdad on 2009-02-15
That part gets a little tricky. There is probably a simple way to do this. I find creating the separate document roots, registering multiple sites, and using different ports works, but I havent tried this with all sites using ssl. You may find it just works, keeping your cert files in the same directory as DocRoot and pointing to them in vhosts. Can't hurt to try, now that you know how to make it work.

---

### Post by lightnb on 2009-02-15
It looks like from what I'm reading, that you have to place the secure site on a separate ip to isolate it's certs from the other sites on the server.

I'll have to play with this some more.

Thanks for all your help today!

---

