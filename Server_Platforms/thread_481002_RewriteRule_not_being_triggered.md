---
title: "RewriteRule not being triggered"
date: 2007-06-22
forum: Server Platforms
---

### Post by pr0fess0r on 2007-06-22
Hi all

I have mod_rewrite set up on some live hosting sites an dit's working fine, but I'm having problems getting it to trigger the rule on my Ubuntu 7.04 Server.

The rule is simply:

```

Options +FollowSymLinks
RewriteEngine On
RewriteRule content/(.*) content.php?parameters=$1

```

which takes a search engine friendly url like [http://blah.com/content/10](http://blah.com/content/10) and turns it into http://blah.com/content.php?parameters=$1

I've enabled mod_rewrite in Apache 2 on Ubuntu, and turned on logging. I've got an .htaccess file with the above code in /var/www/vtt/film on my server, and for the url

[http://myserver/vtt/film/content/10](http://myserver/vtt/film/content/10)

the RewriteLog shows

```

[perdir /var/www/vtt/film/] add path info postfix: /var/www/vtt/film/content.php -> /var/www/vtt/film/content.php/10
[perdir /var/www/vtt/film/] strip per-dir prefix: /var/www/vtt/film/content.php/10 -> content.php/10
[perdir /var/www/vtt/film/] applying pattern 'content/(.*)' to uri 'content.php/10'
[perdir /var/www/vtt/film/] pass through /var/www/vtt/film/content.php

```

why does it not match 'content/(.*)' to uri 'content.php/10' ?

I've tried ^content/(.*), content/(.*)$ and ^content/(.*)$ to no avail...

any help would be appreciated

cheers

---

### Post by Frosty Cold Drink on 2007-06-22
It doesnt match because your regularexpresion is wrong for the URL you are using.

If you are using URLS in the FMC/Param pattern, as it seems you are doing (content.php/10) then you don't even need to rewrite for the query string. If you want to match the URL you are actualy using, you need.

```
RewriteRule content\.php/(.*) content.php?parameters=$1
```

---

### Post by pr0fess0r on 2007-06-22
Hi
I made a mistake above, I actually want to have the URL

[http://myserver/vtt/film/](http://myserver/vtt/film/)

converted to

[http://myserver/vtt/film/content.php?parameters=id/10](http://myserver/vtt/film/content.php?parameters=id/10)

using this .htaccess ruke

RewriteEngine On
RewriteRule content/(.*) content.php?parameters=$1

But in the log, this part confuses me:

add path info postfix: /var/www/vtt/film/content.php -> /var/www/vtt/film/content.php/id/10

I want it to match content/(.*) to content/id/10

why is it "applying pattern 'content/(.*)' to uri 'content.php/id/10'" instead?

cheers

---

### Post by pr0fess0r on 2007-06-22
Also, in sites-available/default, I have
```

        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

if that helps

cheers

---

