---
title: "Apache: require all denied problem"
date: 2015-03-05
forum: Server Platforms
---

### Post by JengaBlocks on 2015-03-05
Ubuntu 14.04.1 LTS
Apache 2.4.7

I'm not able to block access to a virtual host directory. When I surf with Chrome over to the site's home (i.e. [http://mysite.com](http://mysite.com), [http://www.mysite.com](http://www.mysite.com),  [http://mysite.com/index.html](http://mysite.com/index.html), [http://www.mysite.com/index.html](http://www.mysite.com/index.html)), it shows the index.html file when I have specified that it shouldn't through require all denied. I've also tried this with a test.txt file and it shows as well.

Here's what /etc/apache2/sites-available/mysite.com.conf looks like:

```
<VirtualHost *.80>
  ServerName www.mysite.com
  ServerAlias mysite.com
  ServerAdmin admin@mysite.com
  DocumentRoot /var/www/html/mysite.com

  # The following doesn't work
  # It doesn't deny anything
  # I have an index.html in /var/www/html/mysite.com/index.html
  # and the page appears when browsed

  # This directory should be relative to the document root
  # and is thus /var/www/html/mysite.com

  <Directory />
    require all denied
  </Directory>
</VirtualHost>
```

I've also tried with an explicit directory path and it doesn't deny either.

```
<Directory /var/www/html/mysite.com>
  require all denied
</Directory>
```

And for backward compatability, I've tried:

```
<Directory />
  order deny,allow
  deny for all
</Directory>
```

as well as:

```
<Directory /var/www/html/mysite.com>
  order deny,allow
  deny for all
</Directory>
```

Both authz_core and access_compat are loaded.


Any ideas why this isn't working?

---

### Post by sandyd on 2015-03-05
I've moved your thread over to Server Platforms.

---

