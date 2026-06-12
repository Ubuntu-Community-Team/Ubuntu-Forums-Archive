---
title: "Help with RewriteRule for second Plone site needed!"
date: 2005-02-25
forum: Server Platforms
---

### Post by istoyanov on 2005-02-25
I have a running Zope instance + Plone site behind Apache 2 on an Ubuntu-powered server and have added the following rewrite rule for the basic site:
```

RewriteRule ^/(.*)
http://localhost:8080/VirtualHostBase/http/%{SERVER_NAME}:80/basic_site/VirtualHostRoot/$1 [P,L]

```
The obvious result is that I can access the basic_site by just typing the %{SERVER_NAME} in the address bar.

Lately, I added a second Plone site and would like to access it as %{SERVER_NAME}/second_site, however I can reach it via %{SERVER_NAME}:8080/second_site.

I believe that a second RewriteRule may help me to see the site on port 80, so I ask you herewith for advice. 

Thank you in advance!

---

### Post by cpinto on 2005-02-27
[QUOTE=istoyanov]I have a running Zope instance + Plone site behind Apache 2 on an Ubuntu-powered server and have added the following rewrite rule for the basic site:
```

RewriteRule ^/(.*)
http://localhost:8080/VirtualHostBase/http/%{SERVER_NAME}:80/basic_site/VirtualHostRoot/$1 [P,L]

```
The obvious result is that I can access the basic_site by just typing the %{SERVER_NAME} in the address bar.

Lately, I added a second Plone site and would like to access it as %{SERVER_NAME}/second_site, however I can reach it via %{SERVER_NAME}:8080/second_site.

I believe that a second RewriteRule may help me to see the site on port 80, so I ask you herewith for advice. 

Thank you in advance![/QUOTE]
 Why don't you use the virtual hosts built-in apache2? In each configuration for the virtualhost you may use mod_rewrite as you already have.

---

