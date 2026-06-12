---
title: "Apache not parsing server side include tags"
date: 2008-07-11
forum: Server Platforms
---

### Post by apokkalyps on 2008-07-11
I'm trying to bring in some old server files I had into my current apache setup, which i was previously not using.  I would think I had all the settings right, but its parsing my server side includes.

Apache version 2.2.8-1ubuntu0.3
I have include_module enabled

> AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
is in my config file (files with tags are indeed .shtml)

as well as:
> <Directory "/var/www/">
    Options Indexes FollowSymLinks MultiViews **Includes** ExecCGI
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>



Yet apache is still somehow not parsing my include tags, (which look like <!--#include virtual="navbars/left.html" -->)  The tags are passed right through into the code the browser gets.  I can see them if I do 'view source' on my browser.


Am I missing something?

---

