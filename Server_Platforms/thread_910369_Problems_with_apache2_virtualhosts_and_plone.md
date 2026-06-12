---
title: "Problems with apache2 virtualhosts and plone"
date: 2008-09-04
forum: Server Platforms
---

### Post by Go_Bucks on 2008-09-04
Howdy...

I am having a problem figuring out how to get a subdomain to forward to a plone site on my home server. I have godaddy already configured to forward clients.mydomain.com to my home server. That works and goes right now to the default "It works!" page in apache2. My plone site (if I were to get on it from my server) is at:

[http://localhost:8081/Plone](http://localhost:8081/Plone)

Hopefully, if you are considering answering this, you are familiar with plone and understand the concept of virtualmonsters better than I do. In the version of plone/zope I installed, a virtualmonster is preconfigured. So... I followed a tutorial on the plone website for setting up apache2 with a virtualhost pointing to plone. It looks like the following:

```
<VirtualHost *:80>
 ServerAlias   clients.mydomain.com
 ServerAdmin   email@mydomain.com
 ServerSignature On

 CustomLog     /var/log/apache2/example.org-access.log combined
 ErrorLog      /var/log/apache2/example.org-error.log
 LogLevel warn

 <IfModule mod_rewrite.c>
   RewriteEngine On
   RewriteRule ^/(.*) \
      http://localhost:8081/VirtualHostBase/http/localhost:80/clients.mydomain.com/VirtualHostRoot/$1 [L,P]
 </IfModule>
</VirtualHost>
```


If you understand apache2 and plone setup, then you probably already know that I get the following when I restart apache2:

```
[error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```

I am completely stumped as I am at the limits of my understanding here. Any help would be greatly appreciated.

---

### Post by mbeach on 2008-09-04
change the <VirtualHost *:80> to <VirtualHost *> as that is likely what is being used in /etc/apache2/sites-available/default.

Then you are going to want a 
ServerName   clients.mydomain.com
instead of the ServerAlias line.

this virtual host file should be saved in /etc/apache2/sites-available as whatever you like (lets say "myclients").

Then you need to make sure you enable the site with 
sudo a2ensite myclients

then reload 
sudo /etc/init.d/apache2 reload

then try again.

If all that didn't work I'd look at that proxy rewrite rule.  Can you provide a link to the tutorial you followed.

---

### Post by mbeach on 2008-09-04
you may also need to enable the proxy module
```
sudo a2enmod proxy
```

---

