---
title: "_default_ VirtualHost overlap on Port 80"
date: 2009-03-08
forum: Server Platforms
---

### Post by twistedtwig on 2009-03-08
Hi all,

I am having an issue.  I have had my site working for a a long time.  I am trying to get SSL to work (using 7.10).

I have 6 files in my /etc/apache2/sites-available/ folder

Each deal with a different website I host.  before hand I had them all just using <Virtualhost *>

I now changed it to <VirtualHost *:80>

within a file I have that has a load of changes and config for avoiding digg effect etc.  I have the entry

NameVirtualHost *:80             ..... its used to be NameVirtualHost *

When I restart apache I get 6 warnings all saying the same thing:

[warn] _default_ VirtualHost overlap on port 80, the first has precendence.


I have tried googling it and all I came up with was this NameVirtualHost which I already have, which has left me confused.

The site still displays but ONLY displays the first (alphabetically) site, which is the wrong one.

Can anyone point me in the right direction please?


**EDIT**

on a side note I always get > [www.houseofhawkins.com](www.houseofhawkins.com) has sent an incorrect or unexpected message. Error Code: -12263

when I try and access [https://wwww.houseofhawkins.com](https://wwww.houseofhawkins.com), don't know if this is part of my main issue or if this is a different one altogether.


Thanks

Jon Hawkins

---

### Post by mrsteveman1 on 2009-03-08
Are there any conflicting lines in /etc/apache2/httpd.conf?

Do you have a default vhost setup? It could either be in sites-enabled or at the end of /etc/apache2/apache2.conf

---

