---
title: "apache2 + mod_rewrite.c + wordpress"
date: 2010-01-22
forum: Server Platforms
---

### Post by artheus on 2010-01-22
Hey!

I've read about every post there is about problems with mod_rewrite on this forum, and also other forums. But I don't get any wiser on this matter.

As I've set up a small server for the company I'm currently working for. And we've installed a Wordpress test-blog on this.
I've enabled the mod_rewrite on the server, and made sure the the AllowOverride is "all" in my a2site.
I've set up a .htaccess file on the server, as the WordPress tells us to do :

```

<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteBase /kunder/clarorna_wordpress/
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteRule . /kunder/clarorna_wordpress/index.php [L]
</IfModule>

```

And any way I try to fix this, I still get

"[Fri Jan 22 11:02:23 2010] [alert] [client 192.168.0.198] /export/data/www/kunder/clarorna_wordpress/.htaccess: </IfModule> without matching <IfModule> section"

In the error log. And a "500 Internal Server Error" in the browser.

these are a few of the links I've checked without luck:

[http://ubuntuforums.org/archive/index.php/t-255556.html](http://ubuntuforums.org/archive/index.php/t-255556.html)
[http://snippets.dzone.com/posts/show/6206](http://snippets.dzone.com/posts/show/6206)
[http://ubuntuforums.org/showthread.php?p=1473118](http://ubuntuforums.org/showthread.php?p=1473118)

---

### Post by mark63 on 2010-02-12
For the "/.htaccess: </IfModule> without matching <IfModule> section" error check that the closing <ifModule> is on a separate line.

I had the same issue and found by default the .htaccess was set up with:
</IfModule># Use PHP5 as default

Moving the # onwards to a new line resolved the problem.

Dont' forget there can be more than one .htacess file.  The one I had trouble with was ABOVE the public_html dir.

---

### Post by mbehamin on 2010-02-18
try [http://blog.mehdibehamin.com/?p=30](http://blog.mehdibehamin.com/?p=30)

---

