---
title: "HOWTO: Apache2 Self-Signed Certificates (No Password Prompting)"
date: 2009-03-31
forum: Tutorials
---

### Post by SuperMike on 2009-03-31
If you are a web developer trying to test https:// connections to your local web server running Ubuntu, or just have some special web app that needs SSL locally and don't have customers who expect you to have a real Thawte or Verisign certificate, then this document for at least Ubuntu 8.04 might help:

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

However, if you follow its advice, you will end up with SSL and self-signed certificates that, upon reboot of the Apache2 service, will prompt you for a password. This might be annoying, but is actually a good security measure according to the doc above.

Now, if you are a developer who doesn't want this annoyance and doesn't have real reason to worry about the security problem of not prompting for a password, you can do the self-signed certificate a different way.

[B][SIZE="3"]Self-Signed Certs on Ubuntu 8.04 (No Apache Service Start Password Version)[/SIZE]
[/B]*{Note this may work in future releases of Ubuntu past 8.04, but I have only tested on Ubuntu 8.04 workstation and Ubuntu 8.04 server.}*

1. Tell Apache2 to enable the SSL module.

**[FONT="Fixedsys"]# sudo a2enmod ssl[/FONT]**

2. Generate our certificate...

[B][FONT="Fixedsys"]# cd  /tmp
# sudo openssl req -new > new.cert.csr
[/FONT][/B]
...when prompted for info, fill it out. Here's what I typed...

US
Florida
Orlando
SpacemanWorld
(enter)
Jack Spaceman
[email]jackh@spacemanxworld.net[/email]
(enter)
(enter)

...and now we continue...
[B][FONT="Fixedsys"]
# sudo openssl rsa -in privkey.pem -out new.cert.key
# sudo openssl x509 -in new.cert.csr -out new.cert.cert -req -signkey new.cert.key -days 1825
# sudo cp new.cert.cert /etc/ssl/certs/server.crt
# sudo cp new.cert.key /etc/ssl/private/server.key[/FONT][/B]

3. Now we need to tell Apache2 to use this.
[B][FONT="Fixedsys"]
# sudo cp  /etc/apache2/sites-available/default  /etc/apache2/sites-available/ssl
# sudo vi  /etc/apache2/sites-available/default[/FONT][/B]

Change:
```
NameVirtualHost: *
```
To:
```
NameVirtualHost: *:80
```

Change:
```
<VirtualHost *>
```
To:
```
<VirtualHost *:80>
```

**[FONT="Fixedsys"]# sudo vi /etc/apache2/sites-available/ssl[/FONT]**

Change:
```
NameVirtualHost: *
```
To:
```
NameVirtualHost: *:443
```

Change:
```
<VirtualHost *>
```
To:
```
<VirtualHost *:443>
```

After the "DocumentRoot" line, add the following:```

SSLEngine on
SSLOptions +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
```
[B][FONT="Fixedsys"]
# sudo cd  /etc/apache2/sites-enabled
# sudo a2ensite ssl[/FONT][/B]

4. Now we need to adjust /etc/hosts if necessary, using the vi command:

Note this might already be done for you -- just doublecheck.

**[FONT="Fixedsys"]# sudo vi /etc/hosts[/FONT]**

```
127.0.0.1 localhost localhost.localdomain {your system name}
127.0.1.1 {your system name}
{static IP if you you have one} {fully qualified DNS host name if you have one} 

```

5. Now we restart our Apache2 service.

**[FONT="Fixedsys"]# sudo /etc/init.d/apache2 restart[/FONT]**

6. Test your server. You should be able to reach your pages on both http and https. Remember, this goal here was only to get your pages to work on https for doing things like web development testing, such as testing some eCommerce pages. However, you don't want people reaching a secured page on http when they should be on https, so remember that you'll want to trap for that in your .htaccess file in your website folder and redirect users back to the page under https.

SOURCES (HAD TO COMBINE AND GLEAN):

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)
[http://www.linuxquestions.org/linux/answers/Networking/Apache_SSL_Howto](http://www.linuxquestions.org/linux/answers/Networking/Apache_SSL_Howto)
[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)

---

### Post by slavik on 2009-03-31
This is a good tutorial. Finally, someone writes up a good one. ;)

---

### Post by guidovalduchi on 2010-02-09
Thanks for the tutorial, I can verify works with 9.10 server and desktop.

---

### Post by ravimannan2002 on 2010-02-10
yaaay! finally a good tutorial!:)
thx for posting!:D

---

### Post by newlinux on 2010-12-03
> **ravimannan2002 said:**
> yaaay! finally a good tutorial!:)
thx for posting!:D

Yes, excellent. Works well in 10.04.1 as well.

---

### Post by IvanMP on 2012-08-23
Hi,SuperMike

Great post tnx. 
But i have a problem ... i think you can help me. After following your steps i get this error message .. 

> 
1.)[Sun Aug 19 06:32:28 2012] [warn] RSA server certificate CommonName (CN) `UbuntuMail' does NOT match server name!?
2.)File does not exist: /var/www/favicon.ico
3.)[Thu Aug 23 11:53:17 2012] [notice] caught SIGTERM, shutting down
[Thu Aug 23 13:01:19 2012] [warn] RSA server certificate CommonName (CN) `IvanUbuntuMailServer' does NOT match server name!?
[Thu Aug 23 13:01:19 2012] [error] Unable to configure RSA server private key
[Thu Aug 23 13:01:19 2012] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
[Thu Aug 23 13:10:34 2012] [error] Unable to configure RSA server private key
[Thu Aug 23 13:10:34 2012] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch




---

