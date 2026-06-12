---
title: "Apache2 RewriteRule help"
date: 2010-09-06
forum: Server Platforms
---

### Post by gradysghost on 2010-09-06
If this post belongs in the Programming boards, say so, and I'll move it.

Here's what I'm trying to accomplish:

User browses to my server with something like [http://myserver.tld/p/pagename](http://myserver.tld/p/pagename) and this URL gets passed through a RewriteRule in a .htaccess file to become [http://myserver.tld/index.php?p=pagemname](http://myserver.tld/index.php?p=pagemname) on the backend.  This seems simple enough, but I can't seem to make it work.  I keep getting 404's.

Here's my .htaccess file:

```
Options +FollowSymlinks
RewriteEngine On

RewriteRule ^p/([^/]+) /index.php?p=$1 [NC]
```

I used the extent of my Google Fu to arrive at this point, and the way I understand this RewriteRule to work is basically this:

Look for URLs that have (after the TLD): /p/AnythingExceptASlashAtAnyLength and translate that into ?p=TheContentMatchingTheRegexPattern

But this isn't working.  Can anybody explain what I'm doing wrong, and more importantly, why it's wrong?

One thing that I find interesting is that if I run:

```
sudo a2enmod rewrite
```

I get:

```
Module rewrite already enabled
```

But if I run:

```
sudo apache2ctl -l
```

I get:

```
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c
```

And mod_rewrite is nowhere in that list.  This remains true if I restart Apache.  Any ideas, anybody?

---

### Post by Ryan Dwyer on 2010-09-06
Check Apache's error log to see what file it's trying to read for the 404s.

EDIT: mod_rewrite doesn't appear in my compiled in modules either, and it's working fine.

---

### Post by gradysghost on 2010-09-06
The access log shows the 404s being given as if the URL supplied is actually pointing to a file name.  In other words, if I give [http://site.tld/p/pagename](http://site.tld/p/pagename), it's actually looking for /var/www/p/pagename and not finding it.  It's as though the URL isn't even being passed through the RewriteRule.  The error log shows "File does not exist: /var/www/p"

---

### Post by gradysghost on 2010-09-06
A page that runs phpinfo() tells me that mod_rewrite is enabled.  I followed a guide elsewhere that said that in /etc/apache2/sites-available/default the AllowOverrides directive needed to be changed from None to All.  I did this and restarted Apache, but it didn't change anything.  So I reverted the change.

---

### Post by Ryan Dwyer on 2010-09-06
The AllowOverrides directive should not be none. It tells Apache how the config can be overridden, such as by .htaccess files. Change it back and restart Apache again.

Make sure you're enabling it on the correct vhost too. If you have a separate vhost set up for this hostname then you must change it there instead of default.

Finally, make sure you force refresh the page (Ctrl + F5) in case your browser cached the 404.

---

### Post by gradysghost on 2010-09-06
Looks like it worked this time.  Maybe I got the wrong vhost the first time around.  Thanks a bunch!

It looks like this screws up some of my relative file paths, but I can figure that out no problem.  Thanks again.

---

