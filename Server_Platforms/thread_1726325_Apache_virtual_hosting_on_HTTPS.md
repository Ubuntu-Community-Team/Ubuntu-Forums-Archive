---
title: "Apache virtual hosting on HTTPS"
date: 2011-04-11
forum: Server Platforms
---

### Post by 1v82TIn1 on 2011-04-11
Hi,

I am trying to get name based virtual hosts all running on HTTPS (port 443) so I can run multiple sites on the one IP.

The DocumentRoot needs to be different for each host.

E.g. 
[https://wiki.mydomain.com](https://wiki.mydomain.com) /var/www/wiki
[https://forum.mydomain.com](https://forum.mydomain.com) /var/www/forum
[https://www.mydomain.com](https://www.mydomain.com) /var/www/web

However, I am unable to find where to actually enable these hosts in the configs. The apache website says to put it in httpd.conf however that file is empty on my machine. 

The existing default virtual hosts are in "/etc/apache2/sites-available/default" and "default-ssl"

The main config file is /etc/apache2/apache2.conf

I am running version 2.2.16 of apache

I need to use the same .htpasswd file for all the sites.

I have configured CNAMES on my domain for all of these hosts.


Could someone please assist me. Thanks.


Sincerely,
Ryan Brothers

---

### Post by BkkBonanza on 2011-04-11
It isn't critical where you would put them but usually you would create a file for this domain in site-available and put all it's config in that file. Then link it to sites-enabled to be active.

You will need a wildcard certificate if you want to serve mutliple sub-domains on one IP. Since the SSL connection is encrypted Apache is not able to determine the virtual host name until after it has been decrypted - hence, ssl only supports one certificate per IP. There are workarounds but they aren't universally supported.

Generally for subdomains like this it's prefereable to use A records rather than CNAME records.

---

### Post by 1v82TIn1 on 2011-04-11
I tried creating a new file in sites-available called "wiki" and then adding

```
NameVirtualHost *:443

<VirtualHost *:443>
    ServerName wiki.mydomain.com
    DocumentRoot /var/www/wiki
</VirtualHost>
```

Then I enabled the site using:
```
sudo a2ensite wiki
```

I then restarted the server which gave me an error that it failed to restart.

On the DNS aspect, I need to use CNAMEs because I have a dynamic IP, so I run it through DynDNS which gives me a hostname for my IP, my router changes automatically to change the DynDNS records and update the IP.

How might I go about this through a non-standard port or just port 80?

---

### Post by BkkBonanza on 2011-04-11
Need to check the error.log for the exact reason it wouldn't start. It's likely some ssl issue. 

I think you're going to need to specify the IP in the VirtualHost statement.

To use a non-standard port you simply change 443 to the desired port. Then to access the page you append the port, eg. wiki.mydomain.com:1443

You are missing the required ssl certificate lines inside the VirtualHost section as well.

SSLEngine on
SSLCertificateFile /path/to/server.crt
SSLCertificateKeyFile /path/to/server.key

Presumably you have already created a server key, and csr to create/get a certificate? If not then backup a few steps and do that first.

---

### Post by 1v82TIn1 on 2011-04-11
Here is the part of the error log that contains the error:
```
[Mon Apr 11 17:28:59 2011] [info] removed PID file /var/run/apache2.pid (pid=25177)
[Mon Apr 11 17:28:59 2011] [notice] caught SIGTERM, shutting down
[Mon Apr 11 17:29:00 2011] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile] ((null):0)

```

I'll try adding the other necessary directives in the VirtualHost statement.

---

