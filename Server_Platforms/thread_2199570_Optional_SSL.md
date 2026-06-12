---
title: "Optional SSL"
date: 2014-01-14
forum: Server Platforms
---

### Post by codycoder2 on 2014-01-14
Is it possible to make an Apache2 named virtual host use optional SSL?

I have it setup to use https, and if you use http, it redirects you to the default site setup in apache.  I would like to have the option of using 
http OR https.

---

### Post by CharlesA on 2014-01-14
You need to create a virtual host the for the regular http site in addition to the https site. Did you already do that?

---

### Post by codycoder2 on 2014-01-15
That's what I immediately thought.  I created a new site in sites-available, and pointed it at the SSL site without the SSL details, and I tested it with apachectl configtest and it was OK.  The problem happened when I reloaded apache, it failed.  I didn't look in the logs yet.

I will try this again when I get the chance and check the logs and post back.

---

### Post by CharlesA on 2014-01-15
The logs should tell you what the problem is. I haven't used Apache much, but there should be a default and default-ssl site that you can use as a template for your site's virtualhost.

---

### Post by codycoder2 on 2014-01-15
This is what's in my log:

[Wed Jan 15 09:53:09 2014] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile] ((null):0)
[Wed Jan 15 09:53:26 2014] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile] ((null):0)
[Wed Jan 15 09:53:33 2014] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile] ((null):0)
[Wed Jan 15 09:53:50 2014] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Wed Jan 15 09:53:50 2014] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Wed Jan 15 09:53:50 2014] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?

This is my virtual host config file, that when I activate it; the problem happens (see above).

<IfModule mod_ssl.c>
        <VirtualHost *:443>
                ServerAdmin [email]me@mydomain.com[/email]
                ServerName api2.localdevelopment
                ServerAlias api2.localdevelopment
                DocumentRoot /var/www/site_development/public_html/
                ErrorLog /var/www/site_development/logs/error.log
                CustomLog /var/www/site_development/logs/access.log combined
        </VirtualHost>

</IfModule>



As I write this, I think I just figured it out. I may have made copy and paste mistakes.

The above config is for an SSL site because of the "<IfModule mod_ssl.c>" directive, yet I removed the SSL parameters from the "<VirtualHost *:443>" section and left the port at 443.  I think I made several mistake here.

It should look like this, which I will try next:

        <VirtualHost *:80>
                ServerAdmin [email]me@mydomain.com[/email]
                ServerName api2.localdevelopment
                ServerAlias api2.localdevelopment
                DocumentRoot /var/www/site_development/public_html/
                ErrorLog /var/www/site_development/logs/error.log
                CustomLog /var/www/site_development/logs/access.log combined
        </VirtualHost>

---

### Post by codycoder2 on 2014-01-15
That was it.  Thanks for helping me think through this :)
It's all good now

---

