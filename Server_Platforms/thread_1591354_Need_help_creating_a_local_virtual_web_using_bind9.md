---
title: "Need help creating a local virtual web using bind9, apache2, kvm"
date: 2010-10-09
forum: Server Platforms
---

### Post by piine on 2010-10-09
Hi, I am a web developer and I need instruction on how to create a "virtual web" using bind9, apache2, and kvm.

I want to be able to create a virtual host of every site I get locally so that I can test everything locally as if it were on the web (ex. for a site name betteryourweb.com, I want to create a betteryourweb.local locally to avoid constant ftp/ssh upload and so forth across the net)

I need this because on certain projects I am working on, I have to do alot of tedious scripting between my local web server and production web server as well, there is a project I am about get that will be intranet and internet based and I need to be able to setup up a router, dns server and apache2 servers to make this work together seeminglessly. And honestly, I just like play with such technologies.

---

### Post by scrooge_74 on 2010-10-09
Well setup bind9, apache2 on a local server and just use it. KVM is not my strenght. You can also do that using Virtualbox and you set up an internal only network then you can just vrdp into the box and do stuff.

---

### Post by SeijiSensei on 2010-10-09
> **piine said:**
> I want to be able to create a virtual host of every site I get locally so that I can test everything locally as if it were on the web (ex. for a site name betteryourweb.com, I want to create a betteryourweb.local locally to avoid constant ftp/ssh upload and so forth across the net)

Unless you really need to delve into virtual hosts, I'd suggest just putting each site in a separate directory under /var/www/.  Then you can just use URLs like [http://localhost/site1/](http://localhost/site1/) to access each site.

---

### Post by piine on 2010-10-10
I need to know the setting for apache and bind9 for vhosts. Putting the sites into separate directories (which I am currently doing) is costing me alot more in development time because of the manner in which I program, I have to create definitions and alot of error control for both production and testing servers (which equates out to 3 sets of definitions, 1 for my local test server, one for my remote test server and i for production. I want to setup the vhosts so that my test server emulates my production server and cut down on dev time.

I am not concern will the time or effort it takes to setup everything as I want it. Once it's setup properly, it will save time in the long run, as well, assist me on more complex tasks, such connecting multiple intranets to emulate one

---

### Post by windsxs on 2010-10-10
when you create new site, etid like this:
```
<VirtualHost *:80>
    ServerAdmin asradau@domain.com

    DocumentRoot /var/www/subdomain.domain.com
    ServerAlias subdomain.domain.com
    ServerName subdomain.domain.com
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

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

Server alias does it quite good

---

