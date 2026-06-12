---
title: "VirtualHost, Redirect and SSL problems.."
date: 2010-02-08
forum: Server Platforms
---

### Post by artheus on 2010-02-08
Hi!

I've got a little problem with redirecting from http to https in apache2 config.

One of my domains is supposed to work through https, and I've got the certificates and stuff set up. And I've checked that the https connection works fine... But, whenever I've tried to make a redirect to force that the connection to goes through https, the browser just won't connect. It just sticks for a while and then I get the error message "No response from the server"

Here's my sites-available/domain.se config

```

<VirtualHost *:80>

        ServerAdmin artheus@domain.se
        ServerName www.domain.se
        ServerAlias domain.se

        Redirect permanent / https://www.domain.se/

        KeepAlive Off

</VirtualHost>

<VirtualHost *:443>

        ServerAdmin artheus@domain.se
        ServerName www.domain.se
        ServerAlias domain.se

        SSLEngine on
        SSLCertificateKeyFile /etc/ssl/domain/server.key
        SSLCertificateFile /etc/ssl/domain/domain_se.crt
        SSLCertificateChainFile /etc/ssl/domain/domain_se.ca-bundle

        DocumentRoot /export/data/www/

        ErrorLog /var/log/apache2/domain-se.log

</VirtualHost>

```

I've been searching around the forums for a solution to this, but It seems as though all the other configs on the net looks like mine.

Cheers,
Artheus

---

