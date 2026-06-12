---
title: "Problems getting server to work with WebDAV"
date: 2016-04-27
forum: Server Platforms
---

### Post by clankill3r on 2016-04-27
hi,

I try to follow the instructions from this wiki page:
[http://ubuntuguide.org/wiki/WebDAV](http://ubuntuguide.org/wiki/WebDAV)

I got apache running, if I go to localhost in the browser I see the default index.html.
If I try [http://localhost/](http://localhost/)[I]webdav1 then I get a 404.

Due my inexperience I have so many ideas what could be wrong that I will just start with telling what is most likely.
I just want it to work first on the computer i´m working on, after that I will worry about access from another computer in the same network.

[/I]My ip is:
10.0.1.121

My ´mydomainhost' file looks like:

```
<VirtualHost *>
#
# UseCanonicalName off
# ServerName webdav1.mydomain.org
 ServerName myhost.mydomain.org
 ServerAlias 10.0.1.121 webdav1.mydomain.org
#
 ServerAdmin root@localhost
 DocumentRoot /var/www/
#
 Alias /webdav1 /var/www/WebDAV1/files
#
 <Directory /var/www/WebDAV1/>
  Options Indexes MultiViews
  AllowOverride None
  Order allow,deny
  allow from all
 </Directory>
</VirtualHost>
```

Can the 10.0.X.X ip be the problem?

Also my `/var/www/` contains a link called `WebDAV1` but I guess that should not be a problem for the ´mydomainhost´ above since it can use the link right?

Hope someone can help, I can provide more detail later but I wanted to start with what could be the most obvious reason.

---

