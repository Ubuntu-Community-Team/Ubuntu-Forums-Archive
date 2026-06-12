---
title: "Apache 2 HTTPS Problems"
date: 2008-03-18
forum: Server Platforms
---

### Post by Agman on 2008-03-18
Hello all,

I'm fairly new to the Linux Server scene and though I have most of what I want working there are still some issues that are bugging me specially with Apache.

I intend to expose my server in the future but I'm working on getting all the security in place before I do so. I have https configured but I have one issue with it.

The name of my server is webserver. Per Apache's default configuration there is a default virtual host called default with no server name that handles everything that is not picked up by something else. 

I also have a second virtual host file on the sites-enabled linked to the sites-available folder called ssl. This virtual hosts uses ssl and port 443. It's server name is hbc and its DefaultRoot is /var/www/hbc

When I type in:
[http://webserver](http://webserver) or [http://hbc](http://hbc) it takes me to the default-apache2 folder which is correct since hbc should only be listening to port 443.

When I type in
[https://hbc](https://hbc) it takes me to the /var/www/hbc where I have a test page up. This is correct and how it should work.

The problem comes in this, when I type in [https://webserver](https://webserver) it takes me to the hbc website as opposed to redirecting to the default-apache2 folder like it should. I have no clue why this is happening and I can't seem to figure out how to fix.

Any help that y'all have in resolving this issue will be greatly appreciated.

Thanks!
Agman :)

---

### Post by MJN on 2008-03-18
You cannot have name-based virtual hosting with SSL (on a single IP address at least).
 
The SSL tunnel is established before the HOST-HEADER is sent declaring which site is requested hence **all** https traffic will be dealt with by the first HTTPS-configured virtual host, regardless of which HOST-HEADER the client then subsequently asks for.
 
You could set up a redirect inside the the 'hbc' HTTPS config matching the HOST-HEADER and redirecting the client to the non-SSL site for those asking for 'webserver'.
 
Mathew

---

### Post by Agman on 2008-03-18
Oh I see. I guess it makes sense

How would I go about adding that option to my hbc configuration file?

---

### Post by MJN on 2008-03-18
This is the kind of redirect that can be accomplished in many ways, however here's one:

```
RewriteEngine On
RewriteCond %{HTTPS} on
RewriteCond %{HTTP_HOST} ^webserver
RewriteRule ^/(.*) http://webserver/$1 [R=301,L]

```It will carry the full path too e.g. [https://webserver/some/path](https://webserver/some/path) will redirect to [http://webserver/some/path](http://webserver/some/path)

Mathew

---

