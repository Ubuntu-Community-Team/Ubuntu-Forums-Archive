---
title: "Improper URL Redirection on server"
date: 2009-05-14
forum: Server Platforms
---

### Post by k33bz on 2009-05-14
OK, I am running 2 websites on my webserver at the moment. However somewhere I must of did some misconfiguring on the Apache2 side. One of my websites, the first one I made, [www.corpus-christi-fun.info](www.corpus-christi-fun.info) will come up fine, whether or not i place the www in front of it. However the second one I put on there [www.creative-funds.com](www.creative-funds.com) will show up fine only if the www is in front, If I leave the www out of the url it redirects itself to my first site I made. 

Can someone please help me with this?

btw, I followed the steps lined out here exactly: [http://www.corey-m.com/blog/?p=315](http://www.corey-m.com/blog/?p=315)

---

### Post by a9k3d on 2009-05-14
your probably have something like this for both sites:
```
<VirtualHost *:80>
DocumentRoot /www/example2
ServerName www.example2.org
...

```
but it sounds like only  [www.corpus-christi-fun.info](www.corpus-christi-fun.info) has:
```
ServerAlias corpus-christi-fun.info

```
You'll need to add creative-funds.com as an ServerAlias.

Once that works, you may want to double your Virtualhosts for redirects to make sure search engines index your sites with only one style of domain name. Most of my sites drop the www and permanently redirect to the stripped down domain name. A couple like the www in front so their sites redirect to add the www back on.

---

### Post by k33bz on 2009-05-14
> **a9k3d said:**
> your probably have something like this for both sites:
```
<VirtualHost *:80>
DocumentRoot /www/example2
ServerName www.example2.org
...

```
but it sounds like only  [www.corpus-christi-fun.info](www.corpus-christi-fun.info) has:
```
ServerAlias corpus-christi-fun.info

```
You'll need to add creative-funds.com as an ServerAlias.

Once that works, you may want to double your Virtualhosts for redirects to make sure search engines index your sites with only one style of domain name. Most of my sites drop the www and permanently redirect to the stripped down domain name. A couple like the www in front so their sites redirect to add the www back on.

Thank-you for the reply, I went to double check my apache2 available-sites configuration and actually neither one of the sites were setup for serveralias domain.site   Both of them had the www in front. However I decided to drop the www in front of the website for ServerAlias and that made it work. Thanks

---

