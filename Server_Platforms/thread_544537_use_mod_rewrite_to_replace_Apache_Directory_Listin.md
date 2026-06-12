---
title: "use mod_rewrite to replace Apache Directory Listing with a Script"
date: 2007-09-06
forum: Server Platforms
---

### Post by stormfrog on 2007-09-06
This is all apache2/rewrite specific and Ive looked elsewhere but yet not found a solution. I hope someone here might help me.

I am trying to use mod_rewrite to replace Apache Directory Listing with a Script. Its supposedly not hard and its been done before, but how to do it have evaded me so far.

I had it working on another server before, that server used a perl script and furthermore it does not exist anymore. Ive a new script to list files in a apache www directory but its written in php instead.

My rewrite configuration looks like this, /etc/apache2/sites-enabled/default

```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                RewriteEngine on
                RewriteCond     %{REQUEST_URI}  -d
                RewriteRule     /$      mir/browse/list.php

                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

The script is in /var/www/mir/browse/list.php
I am running Ubuntu (of course). 

When I go to my www root (server dir. /var/www/mir/) in a browser the script loads and show files. But thats the only place it loads - I want it to trigger everywhere on the server when files are listed. 

Also, I dont want it replace files like index.html/php. The list.php is only supposed to load when there are no such files and directory listing is allowed.


I would be very greatful for any replies on this, thanks!

---

### Post by kidders on 2007-09-07
Hi there,

URL rewriting *is* straightforward in theory ... in practice, at least for me, it can sometimes be tricky to be 100% confident that I have the subtleties of a particular rule sorted out in my head.

It looks as though you're trying to write your own directory listing script. So, for instance, if someone were to request http://yourhost/path/to/something/, I'm guessing you only want that rewritten to http://yourhost/mir/browse/list.php/path/to/something/ if /var/www/path/to/something/index.php doesn't exist.

One suggestion I would make is to switch REQUEST_FILENAME for REQUEST_URI in RewriteCond tests. Also, you'll need an additional RewriteCond. For instance, something along the lines of...```
RewriteCond %{REQUEST_FILENAME}/(index\.php¦index\.html)$ -f 
```...could test for the existence of default documents.

I'm no expert in this area, but I with any luck, there's *something* in this post you didn't know already.

---

