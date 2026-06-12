---
title: "[SOLVED] Apache + SSL returns \x16\x03\x01 error"
date: 2008-05-25
forum: Server Platforms
---

### Post by nquinnathome1 on 2008-05-25
I'm trying to extend my 8.04 web server so that it can also use HTTPS; I have a default LAMP install and followed the guide for SSL located at **[https://help.ubuntu.com/community/forum/server/apache2/SSL#head-6097389ac6c921feb19fca8ddbc03278cb115738]("https://help.ubuntu.com/community/forum/server/apache2/SSL#head-6097389ac6c921feb19fca8ddbc03278cb115738")**, generating a certificate via the 7.10 method shown.

I then copied my available-sites/default config to available-sites/ssl, modified it so the port was 443 not 80, enabled it and reloaded, but for some reason, Apache restarts just fine, but any attempts to access my webserver with https results in a **[COLOR="Red"]"ssl_error_rx_record_too_long"[/COLOR]** error in my browser, and in the Apache error log I get the error [COLOR="Red"]**"[error] [client 192.168.1.100] Invalid method in request \x16\x03\x01"**[/COLOR]. Accessing the server by ordinary http still works absolutely fine and Apache returns no restart errors or warnings.

I don't know if it's relevant but below is my sites-available/ssl file:
```

NameVirtualHost *:443

<VirtualHost *:443>
DocumentRoot /NETWORKDISK/Web/WWW
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem

<Directory />
	Options FollowSymLinks
	AllowOverride None
</Directory>
<Directory /NETWORKDISK/Web/WWW/>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride None
	Order allow,deny
	allow from all
</Directory>

ServerName my.domain.com
</VirtualHost>

```

I've been trying to get it to work for hours, so any help will be greatly appreciated :)

EDIT: I've found the problem - the solution is to ensure your Apache SSL virtual hosts are included in your httpd.conf file and **not** in a file in your sites-available directory. As soon as I moved the SSL virtual hosts to httpd.conf the error message disappeared and I was able to connect over https.

---

### Post by flyingstar16 on 2008-10-18
I've found another (and more simple) solution:
check in /etc/apache2/sites-enabled if there is a "000-default-ssl" symlink; if not (this was my problem):
> # sudo ln -s /etc/apache2/sites-available/default-ssl /etc/apache2/sites-enabled/000-default-ssl
# sudo /etc/init.d/apache2 restart
:)

Always check this:
(thanks: [http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01](http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01))
> # telnet 192.168.0.1 443
GET /
If you get HTML code, then your server didn't load mod_ssl

---

### Post by siafulinux on 2008-10-25
> **flyingstar16 said:**
> I've found another (and more simple) solution:
check in /etc/apache2/sites-enabled if there is a "000-default-ssl" symlink; if not (this was my problem):

> 
# sudo ln -s /etc/apache2/sites-available/default-ssl /etc/apache2/sites-enabled/000-default-ssl
# sudo /etc/init.d/apache2 restart 


:)

Always check this:
(thanks: [http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01](http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01))

[quote]
# telnet 192.168.0.1 443
GET / 


If you get HTML code, then your server didn't load mod_ssl[/QUOTE]

Wonderful! Thanks, I thought I was going to end up bald tonight! :-)

---

### Post by dchky on 2009-09-23
I know this is a little bit late in the thread, but after having the same issues and spending a few hours in different forums, the solution for me was rather a red faced moment. I'd forgotten to run a2ensite <name of ssl site>

---

### Post by The Sword on 2010-12-11
Thanks flyingstar16, i had a lot of problems setting up SSL, and really found nothing about that error...
(ssl_error_rx_record_too_long)


I looked for a solution a few days, until i found this post, and it worked!


Thanks!

---

### Post by wmorse on 2012-01-07
Thank you, dchky. Forgetting to enable the ssl version of the site with a2ensite was my problem too!

---

