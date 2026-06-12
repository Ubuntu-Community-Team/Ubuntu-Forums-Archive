---
title: "ssl certificate help!"
date: 2006-04-19
forum: Server Platforms
---

### Post by peanut butter on 2006-04-19
i got a ssl cert from [http://www.cacert.org/](http://www.cacert.org/) and i want to kow how to get apache to recognise it. Iwould also like to know how do i get apache configured to run on a secure socket layer?

---

### Post by MJN on 2006-04-19
I recommend reading the HowTo at [http://www.vanemery.com/Linux/Apache/apache-SSL.html]("http://www.vanemery.com/Linux/Apache/apache-SSL.html") (making allowances for the fact you've already got your cert) which should answer your question (and the ones which will inevitably follow on! ;))
 
Mathew

---

### Post by peanut butter on 2006-04-19
hmm. i cant find the ssl.conf that he refers to on that page. i have one in /etc/apache2/mods-enabled/ssl.conf but i looks nothing like the one he has there. i have instaled the mod ssl package

---

### Post by MJN on 2006-04-19
That's not a problem - remember that the Apache configuration can be modular (and is to a massive extent in Debian-based distros) hence the confuration can be split across several files each being referenced by the 'main' apache2.conf file (or http.conf historically) using **Include <path to config file>** statements.

In my case, I've left my **mods-available/ssl.conf** alone (i.e. default) and have the following directives inside my appropriate container within  **sites-available/** (i.e. it could be appended to in your **sites-available/default** file (or whatever it's called)):

```

Listen 443

<VirtualHost _default_:443>
    DocumentRoot "/home/mathew/NewtonNet/shtdocs"
    ServerName secure.newtonnet.co.uk:443
    ServerAdmin webmaster(at)newtonnet.co.uk
    ErrorLog /var/log/apache2/ssl_error.log
    TransferLog /var/log/apache2/ssl_access.log
    LogLevel Warn

    <Directory />
       Options Indexes FollowSymLinks Includes
       XBitHack On
       AllowOverride None
       Order allow,deny
       Allow from all
    </Directory>

SSLEngine on

SSLCipherSuite HIGH:MEDIUM

SSLCertificateFile /etc/apache2/ssl/certs/secure.newtonnet.co.uk.crt

SSLCertificateKeyFile /etc/apache2/ssl/keys/secure.newtonnet.co.uk.key

SSLCertificateChainFile /etc/apache2/ssl/certs/newtonnet-ca.crt

SSLCACertificateFile /etc/apache2/ssl/certs/newtonnet-ca.crt

<Files ~ "\.(cgi|shtml|phtml|php3?)$">
    SSLOptions +StdEnvVars
</Files>

<Directory "/var/www/cgi-bin">
    SSLOptions +StdEnvVars
</Directory>

SetEnvIf User-Agent ".*MSIE.*" \
         nokeepalive ssl-unclean-shutdown \
         downgrade-1.0 force-response-1.0

</VirtualHost>
``` 
Is that any help? Stick with it - like anything new it can all seem overwhelming to start off with but once you hack away at it you'll reach the end... (and probably before you realise too)

Mathew

---

### Post by nagilum on 2006-04-19
The following config is for Apache 2, but should be somewhat similar with Apache 1 (don't know). And I assume you already have the default site up and running and mod-ssl is loaded (with a2enmod ssl).
Next you must make sure your server listens on the default HTTPS port (443) by adding the line "Listen 443" to /etc/apache2/ports.conf. Next you can copy the default site under /etc/apache2/sites-available/default to /etc/apache2/sites-available/default-ssl. In this new config you change the VirtualHost definition to:
```

NameVirtualHost *:443
<VirtualHost *:443>
...

```
and add the following lines somewhere in the VirtualHost definition (e.g. just after the previous example):
```

        SSLEngine               On
        SSLProtocol             -all +SSLv3
        SSLCipherSuite          SSLv3:+HIGH
        SSLCertificateFile      /etc/apache2/ssl/server.crt
        SSLCertificateKeyFile   /etc/apache2/ssl/server.key

```
This enables strong encryption via SSLv3 using the specified certificates. After you enable this site (a2ensite default-ssl) and restart apache you should be able to connect to your server using https://.

---

### Post by MJN on 2006-04-19
I think we must've both been typing at the same time there! :wink:

Thankfully our principles agree... :grin:

Mathew

---

### Post by nagilum on 2006-04-19
[QUOTE=MJN]I think we must've both been typing at the same time there! :wink:

Thankfully our principles agree... :grin:[/QUOTE]
When I started my answer yours wasn't there and after I finished I somehow missed it...  it was a long day. ;)

---

### Post by peanut butter on 2006-04-19
when i try to start apache it gives me errors about all the directives saying the following:

Invalid command 'SSLCipherSuite', perhaps mis-spelled or defined by a module not included in the server configuration
paulb@sparkie:~$ sudo apache2 -k restart
Warning: DocumentRoot [/home/paulb/public_html/forum] does not exist
Syntax error on line 59 of /etc/apache2/vhosts.conf:
Invalid command 'SSLCertificateFile', perhaps mis-spelled or defined by a module not included in the server configuration
paulb@sparkie:~$

do i have to do anything other than installing the apache mod_ssl package?

---

### Post by nagilum on 2006-04-20
[QUOTE=peanut butter]do i have to do anything other than installing the apache mod_ssl package?[/QUOTE]
For Apache 2 you don't have to install that package (there's actually none available for Apache 2), it comes with builtin SSL support.

As for the error, it looks like your ssl modules doesn't get loaded. Do you have a link called /etc/apache2/mods-enabled/ssl.load? The ssl.conf and ssl.load links both have to be present.

---

### Post by peanut butter on 2006-04-20
i had forgot the links but now it says
httpd not running, trying to start.

and it dosnt serve any pages

---

### Post by peanut butter on 2006-04-20
on second thought ssl has messed up my installation enough. i give up.

---

