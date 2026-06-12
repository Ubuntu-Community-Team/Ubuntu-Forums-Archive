---
title: "Apache subdomain issue"
date: 2009-11-08
forum: Server Platforms
---

### Post by MichaelGMorgan on 2009-11-08
Hi,
I'm running Ubuntu Server i386 (latest release) with typical LAMP stack on a spare system I had lying around. Then on my other computer I simply type in the servers IP address into a browser to browse as if it was a live server (it's not - it's only accessible within my home network).

I work on several sites and I'm fed up of using just sub-directories for each site, so what I would like to do is to use sub-domains...

On my dev computer (not the server, Ive edited my hosts file so that [www.dev.com](www.dev.com) maps to my servers IP... This means I can use [www.dev.com](www.dev.com) instead of the servers IP...Great!

But now I want this...

alpha.dev.com => ser.ver.ip.addy/alpha-directory
beta.dev.com => ser.ver.ip.addy/beta-directory

So basically, on my server system I'll have a folder for each subdomain (alpha, beta, etc). Then on my main system I want to type in alpha.dev.com and see my alpha site. Or beta.dev.com and see my beta site.

I've tried all sorts and I've really hit a brick wall with this.

Any help much appreciated!

Thanks!

---

### Post by Lars Noodén on 2009-11-09
The way to do that is using name virtual hosts.  

You have the separate directories.

Next create separate virtual host configurations files in /etc/apache2/sites-available and then enable them.  That will point to the document root for that vhost as well as to any other unique things like logs or scripts.

You also have to add an entry to /etc/apache2/ports.conf using the [NameVirtualHost](http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost) directive.

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html#using](http://httpd.apache.org/docs/2.2/vhosts/name-based.html#using)

---

