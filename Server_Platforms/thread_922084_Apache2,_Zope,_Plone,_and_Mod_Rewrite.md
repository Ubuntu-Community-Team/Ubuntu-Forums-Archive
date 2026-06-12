---
title: "Apache2, Zope, Plone, and Mod_Rewrite"
date: 2008-09-16
forum: Server Platforms
---

### Post by hardstatic on 2008-09-16
This is just an informative post for a problem I had with mod_rewrite and mod_proxy.  Taking some info from the [Plope]("http://plope.com/Books/2_7Edition/VirtualHosting.stx") pages to setup rewrites using Virtual Host Monster...

With a vanilla Apache2 install, the following code would go in either your httpd.conf, apache2.conf, .htaccess, OR the 000-default file in your directory root (/var/www by default).  Thanks apache2 for chopping up httpd.conf and spreading it to the four corners of the Earth.

```
NameVirtualHost *
<VirtualHost *>
ServerName my.website.com
RewriteLog /var/log/apache2/rewrite.log
RewriteLogLevel 3
RewriteEngine On
RewriteRule ^/(.*) http://127.0.0.1:8080/VirtualHostBase/http/my.website.com:80/Plone(or whatever your plone root is)/VirtualHostRoot/$1 [L,P]
</VirtualHost>
```

If your rewrites simply aren't working, make sure the AllowOverride option in your DocumentRoot is set to "All" or something other than "None":

```
DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
```

If you get some 404 Forbidden errors and are pulling your hair out, try putting the following somewhere in between your VirtualHost tags:

```
<Proxy *>
	Order deny,allow
	Allow from all
</Proxy>
```

Good luck.

---

### Post by readylee on 2009-07-16
Yo hardstatic!
THANKS!  You saved me from the insane asylum as I was spending WEEKS trying to figure out how to access my Plone site without seeing :8080 at the end of the URL!

Your simple post was EXACTLY the recipe for me, after more than a hundred hours of Rewrite HELLLLLLLL!!!!!!!!!!!!!!!!!!  The AllowOverride option and Proxy config did it, while I had tried like a trillion different RewriteRules in vain.  

THAAAAAAANK YOUUUUUUUUUUUUU!!!!!!!!!!!!!

:D:D:):):popcorn::popcorn::popcorn:

LATER!

---

### Post by vattam on 2009-07-27
Hi,

I have added the lines as suggested here, including the AllowOverride and the Proxy options but still I am not able to get Apache/Zope working. 

I am trying to run a website from a server using Plone/Zope, which already has one website being hosted on Apache. I am able to access my website using the :8080 in the URL. I followed the tutorials/docs given on 
[http://plone.org/documentation/how-to/plone-with-apache]("http://plone.org/documentation/how-to/plone-with-apache")

I hope I am on the right track, can someone please guide me. Thanks in advance.

---

