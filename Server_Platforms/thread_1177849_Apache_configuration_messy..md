---
title: "Apache configuration messy."
date: 2009-06-03
forum: Server Platforms
---

### Post by japtar10101 on 2009-06-03
I ran the following to setup some project tools:
```

sudo apt-get install mediawiki imagemagick mediawiki-math mysql-server bugzilla3

```
As a consequence, none of my webpages I had before installation show up anymore, instead showing 404 errors.  My guess is the install screwed up apache's configuration files, and I wanted to know if there was a way to revert this back to normal.  All of my websites are simply links in directory /var/www/, so I'd like that alias back.

---

### Post by japtar10101 on 2009-06-03
So, while going through the error logs, I've found that the website are now pulled from /htdocs/ instead of /var/www/.  What's up with that, and how do I fix it?

By the way, I paste-binned /etc/apache2/apache2.conf ([http://pastebin.com/f3ed08a23](http://pastebin.com/f3ed08a23)) and  /etc/apache2/sites-available/defaults ([http://pastebin.com/f671d564a](http://pastebin.com/f671d564a)).

---

