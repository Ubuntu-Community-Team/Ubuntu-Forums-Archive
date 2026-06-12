---
title: "one cert for 2 subdomains"
date: 2011-11-28
forum: Server Platforms
---

### Post by Luxik on 2011-11-28
Hi all,

I've generated one cert for a domain. 
I've signed by Startcom.

And I want to make a SSL for a 2. subdomains of that domain - mail.xxy.tld and phpma.xxy.tld.

So I tried to add virtualhosts into the default-ssl file, but only the domain works with ssl - [https://domain.tld](https://domain.tld).

If I look at etc. mail.xxy.tld, the browser only shows up the warning that the page is not trusted.

I've never done this before, so maybe I'm doing smt wrong.

Yeh and, I don't need SNI, it's only one domain, isn't it? so when i generated the cert, I used *.domain.tld.

Thank you.:popcorn:

---

### Post by SeijiSensei on 2011-11-28
Name-based virtual hosts and SSL usually don't mix.  In the past the standard solution was to assign each SSL host to a separate IP address.  I've noticed some recent advances in using name-based virtuals with SSL, but I haven't looked into it very carefully.  Google is your friend here.

One kludgy solution is to use a Redirect to point each virtual to a separate subdirectory underneath the DocumentRoot of the SSL host.  Suppose you have an SSL domain, secure.example.com, and you want to support harry.example.com and hermione.example.com.  You could add redirects to the virtual host definition for harry look like this:

```
Redirect / https://secure.example.com/harry/
```

You'd use the equivalent solution in the definition for hermione.example.com.

---

### Post by hawkmage on 2011-11-28
The only real way to deal with this is to either get a wildcard SSL cert that will match any host under a domain or use the X509 v3 attribute "Subject Alternative Name" with each host name the cert is going to be used for.

---

### Post by Luxik on 2011-11-29
Ok here is output of my virtual hosts:

mail.vhost:

<VirtualHost *:443>
    DocumentRoot /var/www/default/subdomains/mail/public_data
  
    ServerName mail.xxy.tld
    ServerAlias [www.mail.xxy.tld](www.mail.xxy.tld)
    ServerAdmin [email]hosting@xxy.tld[/email]

    ErrorLog /var/www/default/subdomains/mail/error.log

    ErrorDocument 400 /error/400.html
    ErrorDocument 401 /error/401.html
    ErrorDocument 403 /error/403.html
    ErrorDocument 404 /error/404.html
    ErrorDocument 405 /error/405.html
    ErrorDocument 500 /error/500.html
    ErrorDocument 503 /error/503.html
    
    <Directory /var/www/default/subdomains/mail>
        AllowOverride None
        Order Deny,Allow
        Deny from all
    </Directory>
    
    <Directory /var/www/default/subdomains/mail/public_data>
        Options FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
    
    SSLEngine on
    
    SSLCertificateFile    /etc/ssl/certs/xxy.tld.crt
    SSLCertificateKeyFile /etc/ssl/private/xxy.tld.key



</VirtualHost>


and phpma.vhost

<VirtualHost *:443>
    DocumentRoot /var/www/default/subdomains/phpma/public_data
  
    ServerName phpma.xxy.tld
    ServerAlias [www.phpma.xxy.tld](www.phpma.xxy.tld)
    ServerAdmin [email]hosting@xxy.tld[/email]

    ErrorLog /var/www/default/subdomains/phpma/error.log

    ErrorDocument 400 /error/400.html
    ErrorDocument 401 /error/401.html
    ErrorDocument 403 /error/403.html
    ErrorDocument 404 /error/404.html
    ErrorDocument 405 /error/405.html
    ErrorDocument 500 /error/500.html
    ErrorDocument 503 /error/503.html
    
    <Directory /var/www/default/subdomains/phpma>
        AllowOverride None
        Order Deny,Allow
        Deny from all
    </Directory>
    
    <Directory /var/www/default/subdomains/phpma/public_data>
        Options FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>

    SSLEngine on
    
    SSLCertificateFile    /etc/ssl/certs/xxy.tld.crt
    SSLCertificateKeyFile /etc/ssl/private/xxy.tld.key

</VirtualHost>


apache says: [Tue Nov 29 14:40:11 2011] [warn] _default_ VirtualHost overlap on port 443, the first has precedence

It  means, there is allowed only one 443 for a domain?

Here works only mail.xxy.tld and phpma shows the same page - mail page instead phpma.

How can I make it works?
Thank you.

---

### Post by Luxik on 2011-12-01
Ok, it's done, I added this line into a virtualhost:

NameVirtualHost *:443

And it works!

---

