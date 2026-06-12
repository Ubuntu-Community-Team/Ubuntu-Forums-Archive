---
title: "[SOLVED] Apache2 + Mongrel for RoR AUTH issue"
date: 2008-06-09
forum: Server Platforms
---

### Post by Titan8990 on 2008-06-09
I am trying to set up Redmine via Mongrel and piped through Apache. I have been following this tutorial: [http://drinkingbird.net/blog/articles/2008/02/27](http://drinkingbird.net/blog/articles/2008/02/27)

I have skipped the step on SVN which from the looks of it includes authentication. I can get to my Redmine site by going to [http://localhost:3000](http://localhost:3000) but can not get to it by entering my domain name. It works if I do [http://MYDOMAIN:3000](http://MYDOMAIN:3000). It seems to me that Apache is not sending the request to Mongrel. When I go to MYDOMAIN.com I get the following:

```
Forbidden

You don't have permission to access / on this server.

Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_perl/2.0.2 Perl/v5.8.8 Server at MYDOMAIN.com Port 80
```

From the looks of this maybe my mods are not initializing properly?

Here is a look at my httpd file for the site:

```
<VirtualHost *>

  ServerAdmin root@MYDOMAIN.com
  DocumentRoot /var/www/redmine-0.7.1
  ServerName MYDOMAIN.com
  ErrorLog /var/www/redmine-0.7.1/log/error.log

  ProxyPass /images !
  ProxyPass /stylesheets !
  ProxyPass /javascripts !
  ProxyPass /favicon.ico !
  ProxyPass /static !
  ProxyPass /holding !
  ProxyPass /templates !
  ProxyPass / balancer://redmine_cluster
  ProxyPreserveHost On

  <Proxy balancer://redmine_cluster>
    BalancerMember http://127.0.0.1:3000
    BalancerMember http://127.0.0.1:3001
  </Proxy>

  RewriteEngine On
   # Redirect all non-static requests to cluster
  RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f
  RewriteRule ^/(.*)$ balancer://redmine_cluster%{REQUEST_URI} [P,QSA,L]
</VirtualHost>
```

I always appreciate any help or suggestions I can get. 

Any ideas on why I can not get to my redmine site via [http://MYDOMAIN.com?](http://MYDOMAIN.com?) How can I force Apache to redirect to port 3000 (assuming that is the issue as that is what it looks like)?

---

### Post by Titan8990 on 2008-06-10
One bumpage before I try a more "specialized" forum.

---

### Post by xethm55 on 2008-06-18
Have you tried my guide located here:  [http://ubuntuforums.org/showthread.php?t=674598&highlight=redmine](http://ubuntuforums.org/showthread.php?t=674598&highlight=redmine)

---

### Post by Titan8990 on 2008-07-08
I had forgot about this post. Thank you for that link, I had came accross it myself and it worked like a charm.

---

