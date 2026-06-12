---
title: "apache virtual host problem"
date: 2014-05-31
forum: Server Platforms
---

### Post by Tommy_Maersk on 2014-05-31
Hey

I am trying to set up domains and subdomains, on my webserver, however the domains are resolving, but when accessing a subdomain I get a 500 internal server error.


My virtual host files looks like this for domains and for the subdomains, and I am using Apache 2.4.7


Domains: 

  <virtualhost *:80>
      ServerAdmin [email]mail@mail.mail[/email]
      ServerName  domain.com
      ServerAlias [www.domain.com](www.domain.com)


      DirectoryIndex index.html index.php
      DocumentRoot /home/user/domain.com/


        <Directory /home/user/domain.com/>
                DirectoryIndex index.php
                Options Indexes FollowSymLinks
                AllowOverride All
                Require all granted
        </Directory>
   </virtualhost>


Subdomains:


    <virtualhost *:80>
      ServerAdmin [email]mail@mail.mail[/email]
      ServerName  sub.dabagroup.com
      ServerAlias sub.dabagroup.com


      DirectoryIndex index.html index.php
      DocumentRoot /home/user/domain.com/subdomains/sub/


        <Directory /home/user/domain.com/subdomains/sub/>
                DirectoryIndex index.php
                Options Indexes FollowSymLinks
                AllowOverride All
                Require all granted
        </Directory>
   </virtualhost>

Anybody got an idea why it works on domains, and not the subdomains?

Thanks!

---

### Post by TheFu on 2014-05-31
Probably a dumb question, but are the DNS records setup for the subdomains or do you have DNS setup to send all *.domain.TLD to the same IP?

---

### Post by Tommy_Maersk on 2014-06-01
Thanks for the hint..


I had the subdomains hosted on another server, and forgot to enable mod rewrite on that, therefore the 500 error...

---

### Post by TheFu on 2014-06-01
I've never known that "subdomains" was a setting in any webserver.  We've always called them "virtualhosts" or "virtualdomains" here, since **any** valid domain can be used - i.e. it isn't limited to just 3rd-level domains (and greater).

We use a reverse proxy to handle all that name-based forwarding to the actual web servers too.  That way, everything goes through 1 place and we don't have to worry if apache, litehttp, passenger, pound, nginx or some odd tomcat web-app server is being used on the back end. We haven't needed HA on the proxy yet, but if we grow into that size, having HA-proxy on both checking the others shouldn't be too hard (assuming nginx doesn't already have HA capabilities built-in for itself, which I haven't researched at all.).  nginx as a reverse proxy will load-balance to backend servers just fine for that sort of HA.

Anyway, that is all stuff you probably already knew. Glad you figured out the solution.

---

