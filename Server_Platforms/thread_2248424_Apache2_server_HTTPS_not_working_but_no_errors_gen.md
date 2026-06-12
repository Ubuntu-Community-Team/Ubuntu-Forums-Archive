---
title: "Apache2 server: HTTPS not working but no errors generated"
date: 2014-10-14
forum: Server Platforms
---

### Post by polt on 2014-10-14
Hello Ubuntu Community,

I'm having a weird problem trying to use SSL with my Apache2 server.  I am not able to connect to my website using https, but when Apache2 is restarted, there are no errors, and none in the error log, so I have no idea what is wrong.  Without SSL, my site does work.  In other words, I can connect to "http://mysite.com" but not "https://mysite.com"

Here is what I have done.

1. I enabled SSL by:

```

sudo a2enmod ssl
sudo a2ensite default-ssl

```

2.  I generated a self signed SSL certificate using:

```

openssl genrsa -des3 -out server.key 2048
openssl req -new server.key -out server.csr
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

```

I made sure that the common name field matched my website, so "mysite.com"

The "server.key" and "server.crt" files were copied to the relevant folders.

3. I edited my config file, "/etc/apache2/sites-available/default-ssl.conf", adding the relevant fields:

```

<IfModule mod_ssl.c>
  <VirtualHost *:443>
    ServerAdmin admin@mysite.com
    ServerName mysite.com
    ServerAlias www.mysite.com
    DocumentRoot /var/www # this is the same as for http and contains my index file
    SSLEngine on
    
    # these are the locations to which I copied the files generated above
    SSLCertificateFile /etc/apache2/ssl/server.crt  
    SSLCertificateKeyFile /etc/apache2/ssl/server.key
  </VirtualHost>
</IfModule>

```

And the error logs are also specified in that config file.

Similarly, I edited "ports.conf":

```

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

4.  I restarted Apache and went to "https://mysite.com".  It attempts to connect for a while and then generates a "The connection was reset" error.

So, does anyone have any idea what I could have missed?  I'm completely lost at this point.

---

Update:

I set my error log level to debug, and now I am getting this error:

```

AH02199: SSL not enabled on vhost mysite.com:80, skipping SSL setup

```

---

### Post by gopalreddy on 2014-10-15
If you are hosting single site and making it default then ideally I think, in the file "/etc/apache2/sites-available/default-ssl.conf" 
Directive should be <VirtualHost _default_:443>
rest of the config seems to be ok, even verify ssl keys and try restarting apache

You can get more info from following url 
[https://www.digitalocean.com/community/tutorials/how-to-set-up-multiple-ssl-certificates-on-one-ip-with-apache-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-multiple-ssl-certificates-on-one-ip-with-apache-on-ubuntu-12-04)

---

### Post by polt on 2014-10-16
Thanks for your idea gopalreddy!  I've actually tried that, restarting Apache afterwards, and it didn't help.  I've seen both methods mentioned but neither seems to work anyways.  I wonder if anyone has any ideas for troubleshooting?  Maybe I could run some diagnostics or other to get more info?  I don't know much about this stuff.  My best idea so far is to reset all default settings and do it over again.  I guess it's possible a setting elsewhere in the config files has messed this up... though I don't know what that would be.

---

