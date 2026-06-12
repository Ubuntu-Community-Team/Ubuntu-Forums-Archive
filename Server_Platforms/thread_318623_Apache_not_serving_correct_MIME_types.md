---
title: "Apache not serving correct MIME types"
date: 2006-12-14
forum: Server Platforms
---

### Post by forethought on 2006-12-14
I have an install of Dapper running Apache2 and it keeps setting the content-type of my css files to text/html, even though in the /etc/mime.types file there is clearly an entry that reads:

text/css       css

I've checked my apache2.conf file and the TypesConfig is set to /etc/mime.types, so what else could be the issue?

---

### Post by MJN on 2006-12-15
Wild guess here, but do you have the mime_magic module also loaded? If so, perhaps it is parsing the .css files and deciding they're HTML files? Maybe not, but a stab in the dark can sometimes come up trumps...
 
(of course this doesn't solve the problem but finding the potential cause is a start)
 
Has it ever worked? You are definitely retrieving fresh pages and not cached from your browser or provider?
 
Mathew

---

