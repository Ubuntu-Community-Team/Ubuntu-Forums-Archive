---
title: "Replacing self signed SSL with new CA Signed SSL"
date: 2014-05-01
forum: Server Platforms
---

### Post by kosmokramer314 on 2014-05-01
I recently deployed a secure email server on my server at home and in that process I applied a new SSL certificate to the mail server.  I already had a self signed certificate in place for my website, but I'd like to delete that and put the new SSL in place since it's not self signed.  

The email server tut I used was [arstechnica from last month]("http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/")

So my question is how do I remove the self signed certificate and use the new certificate OR can I even do that?
[INDENT]do I need to generate an additional cert for the website?[/INDENT]  

When I visit startssl.com and retrieve the certificate, it says it is for mail.mydomain.com (Server - Class 1 - 2015-04-25)

---

### Post by kosmokramer314 on 2014-05-05
anything?

---

### Post by sandyd on 2014-05-05
Hi, what webserver are you using?
Can you post the configuration of the virtual host you are using?

---

### Post by kosmokramer314 on 2014-05-06
I am using Apache webserver

```
<VirtualHost *:443>
     ServerName SERVER NAME
     ServerAlias [www.MYDOMAIN.com](www.MYDOMAIN.com)
     ServerAdmin [email]webmaster@MYDOMAIN.com[/email]
     RewriteEngine On
     SSLEngine On
     SSLCertificateFile /etc/ssl/crt/apache-cert.pem
     SSLCertificateKeyFile /etc/ssl/key/apache-key.pem
     DocumentRoot /var/www/MYDOMAIN.com/owncloud/
     <Directory />
        Options FollowSymLinks
        AllowOverride All
     </Directory>
     ErrorLog /var/www/MYDOMAIN.com/logs/error.log
     CustomLog /var/www/MYDOMAIN.com/logs/access.log combined
</VirtualHost>
```

---

### Post by kosmokramer314 on 2014-05-07
After my last reply, I realized that I only need to point the virtual host to the new SSL cert and key.  Even though the cert is issued to mail.mydomain.com it still includes my top level domain.  I did have to import the cert to my desktop browser, but it worked, whereas before with the self signed cert it was never trusted.

---

