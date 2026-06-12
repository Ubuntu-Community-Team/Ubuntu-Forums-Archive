---
title: "Setting up multiple domains in one server"
date: 2013-07-31
forum: Server Platforms
---

### Post by Renaissance2011 on 2013-07-31
Hello,

I use Ubuntu 13.04 server edition operating system. I want the server to accommodate two different domain ( domain1.eu, domain2.org).
I have encountered problems.

My server configuration is such:

_**Server uses a single network card**_

/etc/hosts
# Virtual Hosts
100.0.70.1 domain1.eu    domain1
100.0.70.2  domain2.org  domain2

Bind named.conf

zone "domain1.eu" {
       type slave;
       masters { 213.168.4.8; };
       file "/etc/bind/sec/domain1.eu";
};

zone "domain2.org" {
       type slave;
       masters { 213.168.4.8; };
       file "/etc/bind/sec/domain2.org";
};

/etc/apache2/sites-available/domain1.eu

NameVirtualHost 100.0.70.1

<VirtualHost 100.0.70.1>
  ServerName domain1.eu
ServerAlias  [www.domain1.eu]("http://www.domain1.eu")
  DocumentRoot /var/www/vhosts/vh1
</VirtualHost>

/etc/apache2/sites-available/domain2.org

NameVirtualHost 100.0.70.1

<VirtualHost 100.0.70.2>
  ServerName domain2.org
ServerAlias  [www.domain2.org]("http://www.domain2.org")
  DocumentRoot /var/www/vhosts/vh1
</VirtualHost>

Finally, if I do service apache2 reload

I get the following error message ""[warn] NameVirtualHost *:0 has no VirtualHosts". And only one domain (domain1.eu) working properly. Good firends, what I've done wrong ?

---

### Post by SeijiSensei on 2013-07-31
> NameVirtualHost 100.0.70.1

<VirtualHost 100.0.70.2>


I'd start here.

If each domain has a unique IP address, then I'd avoid name-based virtual hosting and just go with the IPs.   In /etc/apache2/ports.conf, comment out the "NameVirtualHost *:80" directive.  Remove the NameVirtualHost directives from your other configuration files as well.

 I'd probably use "100.0.70.2:80" as the identifier though.  Someday you might want to run an SSL site.

---

### Post by kinglear333 on 2013-07-31
Like the previous poster said, the problem is with using the same IP for multiple domains. Apache doesn't like that as it can't bind 2 domains to 1 IP.

Instead of using an IP there, can you try this:

```
<VirtualHost *:80>

```
Let us know how it works out.

---

### Post by SeijiSensei on 2013-08-01
That's not really what I said, nor is it correct.  Apache has no problem serving an unlimited number of virtual hosts from a single IP address.  That's how "[name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")" works.  The server determines which page to send based on the ServerName used in the requested URL.

In the OP's case he has a separate IP address for each host, so he does not need to use virtual hosting.  He should just enter the appropriate IP address in each <VirtualHost> stanza.

---

### Post by Hexxus on 2013-08-01
Did you disable the default site in apache?
Did you enable the site you created in apache? 

I  accomplished exactly what you're trying to do at my home and was able  to do it by creating two seperate files in sites-available - made the  links to them in the sites-enabled folder.

Here's a copy of them individually with certain content removed or generalized:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName example.net
    ServerAlias www.example.net
    DocumentRoot /var/www/example.net/wwwroot
        DirectoryIndex index.php
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/example.net/wwwroot/>
        Options FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/examplenet_error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel info

    CustomLog /var/log/apache2/examplenet_access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```


Then the other site is named something different as so:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName example2.com
    ServerAlias www.example2
    DocumentRoot /var/www/example2/wwwroot
        DirectoryIndex index.php
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/example2.com/wwwroot/>
        Options FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/example2_error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel info

    CustomLog /var/log/apache2/example2_access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```

This is one server - two completely different sites, 1 ip address. With this setup each one has its own config file, I did try doing virtual hosts in one config file but I wasn't able to figure it out.

Here is the site that I used that answered my questions that might be able to help you out:

[https://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin](https://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin)

---

### Post by Renaissance2011 on 2013-08-04
Hello again,

I would like to thank everyone who responded to me. I have tried your suggestions and teachings. unfortunately another domain still does not work.
Lets take a closer look:
Default site is closed (a2dissite default).
I enabled two sites (a2ensite domain1.eu, a2ensite domain2.org).
Domain1.eu look like this:
<VirtualHost *:80>
ServerName  domain1.eu
ServerAlias [www.domain1.eu](www.domain1.eu)
DocumentRoot /var/www/public/domain1.eu
</VirtualHost>

Domain2.org Look like this





<VirtualHost *:8080>
ServerName  domain2.org
ServerAlias [www.domain2.org](www.domain2.org)
DocumentRoot /var/www/public/domain2.org
</VirtualHost>

if I end up doing service apache2 reload, I can not get any error message. But i still not see domain2.org on the Internet.

---

### Post by CharlesA on 2013-08-04
Are you trying to access domain2 with the domain name or IP address? I would try using the IP address and see what happens.

Next check to make sure apache is listening on port 8080:

```
netstat -nl | grep 8080
```

If it is listening, check your firewall to make sure port 8080 is open.

---

### Post by SeijiSensei on 2013-08-05
Did you add the

```

Listen 8080
NameVirtualServer *:8080
```

directives somewhere ahead of the <VirtualHost *:8080> declaration? I suggest adding them to /etc/apache2/ports.conf for consistency.

---

### Post by Renaissance2011 on 2013-08-06
Thank you to all who responded. I still have a problem.

My /etc/apache2/sites-available/domain1.org look like this

NameVirtualHost  *:80
<VirtualHost *:80>
ServerAdmin admin@localhost
ServerName domain1.org
ServerAlias  [www.domain1.org]("http://www.domain1.org")
DocumentRoot /var/www/public/domain1.org
</VirtualHost>

/etc/apache2/sites-available/domain2.eu look like this
NameVirtualHost  *:8080
<VirtualHost *:8080>
ServerAdmin admin@localhost
ServerName domain2.eu
ServerAlias  [www.domain2.eu]("http://www.domain2.eu")
DocumentRoot /var/www/public/domain2.eu
</VirtualHost>

My /etc/apache2/ports.conf look like this:
NameVirtualHost *:8080
Listen 80
Listen 8080
if I end up doing service apache2 reload, I can not get any error message. But i still not see domain2.org on the Internet. My web browser indicates "Unable to connect* domain2.eu:80*."

---

### Post by newbie-user on 2013-08-06
You set your domain2.eu to run on port 8080. In the address bar of your browser, type in domain2.eu:8080

---

